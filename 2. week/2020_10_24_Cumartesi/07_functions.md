function_name () {
<commands>
}

or 

function_name {
<commands>
}

- Example-1  
functions.sh  
```
#!/bin/bash

my_function() {
    echo "hello there. i am the first function."
}

my_function
```
```
[train@localhost play]$ ./functions.sh
hello there. i am the first function.
```

- Example-2  
functions.sh  
```
adder(){
    echo "$1 + $2 = $(( $1+$2 ))"
}

adder 3 5
```
```
[train@localhost play]$ ./functions.sh
3 + 5 = 8
```

- Example-3: Function with return value  
functions.sh  
```
adder2() {
    result=$(( $1+$2 ))
    return $result
}
adder2 13 15
echo "adder2 result: $?"
```
```
[train@localhost play]$ ./functions.sh
hello there. i am the first function.
3 + 5 = 8
adder2 result: 28
```