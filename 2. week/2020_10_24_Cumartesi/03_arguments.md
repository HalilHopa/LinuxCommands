Arguments are assigned in bash $1 $2 $3 ..$n variables consecutively. $0 is reserved for scripts' name itself.  
Number of arguments: `$#`  
arguments.sh
```
echo "My name is $0 script."

MODULO=$(( $1%2 ))
if [ "$MODULO" -eq 0 ] ; then
   echo "$NUMBER is even"
else
   echo "$NUMBER is odd"
fi
```

```
[train@localhost play]$ bash arguments.sh 5
My name is arguments.sh script.
is odd
[train@localhost play]$ bash arguments.sh 6
My name is arguments.sh script.
is even
```

Above we sent a number as an argument and it is assigned to $1  
Now we will sent two and will be assigned $1 and $2 consecutively
```
# two arguments
if [ $1 -gt $2 ] ; then
   echo "$1 is greater than $2"
else
   echo "$2 is greater than $1"
fi
```
```
[train@localhost play]$ bash arguments.sh 6 9
9 is greater than 6
```

## more different ways to handle arguments
```
echo "\$0:"$0 "\$1:"$1 "\$2:"$2 "\$3:"$3

echo "\$@: " $@

echo "\$#: " $#

all=("$@")
echo ${all[0]}
```
```
[train@localhost play]$ ./arguments.sh 6 9 hello
My name is ./arguments.sh script.
 is even
9 is greater than 6
$0:./arguments.sh $1:6 $2:9 $3:hello
$@:  6 9 hello
$#:  3
6
```
$# argument count but $0  
$@ all arguments in an array but $0  


## Argument parsing with GetOpts
Script:
```
[train@localhost bash-script]$ cat args_with_getops.sh
#!/bin/bash

show_help() {
  cat <<EOF
-n  Name of person
-s  Surname of person
EOF
}

while getopts 'n:s:h' options
  do
    case $options in
      n ) echo "My name ${OPTARG}"
        ;;
      s ) echo "My surname is ${OPTARG}"
        ;;
      h ) show_help
          exit 0
        ;;
    esac
  done
exit 0;
```

Help menu usage:
```
[train@localhost bash-script]$ ./args_with_getops.sh -h
-n  Name of person
-s  Surname of person
```
Script usage
```
[train@localhost bash-script]$ ./args_with_getops.sh -n Erkan -s Şirin
My name Erkan
My surname is Şirin
```
## getopts can only parse short options.

Most systems also have an external getopt command, but getopt is not standard, and is generally broken by design as it can't handle all arguments safely (arguments with whitespace and empty arguments), only GNU getopt can handle them safely, but only if you use it in a GNU-specific way.

The easier choice is to use neither, just iterate the script's arguments with a while-loop and do the parsing yourself.

See http://mywiki.wooledge.org/BashFAQ/035 for an example.