create a script file 

- Check given path is a directory (file check)
```  
[train@localhost play]$ nano conditionals.sh
#! /bin/bash
DIRECTORY="/home/train/test"
if [ -d $DIRECTORY ] ; then
    echo "The $DIRECTORY exists"
else
   echo "The $DIRECTORY doesn't exist"
fi
```

Make it executable  
` [train@localhost play]$ sudo chmod +x conditionals.sh `  

Execute it it will tell us if /home/train/test file exists.  
```
[train@localhost play]$ ./conditionals.sh
The /home/train/test doesn't exist
```
Create directory and try again  
```
[train@localhost play]$ mkdir ~/test
[train@localhost play]$ ./conditionals.sh
The /home/train/test exists
```

### spaces are important in conditionals  
### if you use `<, >` in condition, you have to use double `(( ))`  
conditional.sh
```
NUMBER=8
if (( $NUMBER > 9 )) ; then
   echo "$NUMBER is two-digit"
else
   echo "$NUMBER is one-digit"
fi
```
```
[train@localhost play]$ ./conditionals.sh
The /home/train/test exists
8 is one-digit
```

## using logical operators in conditions  
```
if [ "$NUMBER" -gt 0 ] && [ "$NUMBER" -lt 9 ] ; then
   echo "$NUMBER is one-digit positive number"
else
   echo "$NUMBER is not one-digit positive number"
fi
```
```
[train@localhost play]$ ./conditionals.sh
8 is one-digit positive number
```
We can use operators **AND ( && ) -a** and **OR ( || ) -o**   
```
if [ "$NUMBER" -gt 0 -a "$NUMBER" -lt 9 ] ; then
   echo "$NUMBER is one-digit positive number"
else
   echo "$NUMBER is not one-digit positive number"
fi
```

```
[train@localhost play]$ ./conditionals.sh
8 is one-digit positive number
```

expressions in condition 
```
MODULO=$(( $NUMBER%2 ))
if [ "$MODULO" -eq 0 ] ; then
   echo "$NUMBER is even"
else
   echo "$NUMBER is odd"
fi
```
- Inline conditionals
```
[train@localhost play]$ x=5
[train@localhost play]$ if [ $x = 5 ]; then echo "true"; else echo "false"; fi
true
[train@localhost play]$ x=4
[train@localhost play]$ if [ $x = 5 ]; then echo "true"; else echo "false"; fi
false


[train@localhost linux]$ if (( $x > 5 )); then echo "yes gt 5"; else echo "lt 5"; fi
lt 5
```
- Inline healthcheck. If curl works  echo "doesn't work" won't be tested. If curl doesn't work  echo "doesn't work" will be tested.
```
[train@localhost ~]$ curl localhost:880  ||  echo "doesn't work"
curl: (7) Failed connect to localhost:880; Connection refused
doesnt work
```