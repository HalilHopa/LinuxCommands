
# Born Again Shell (bash)

# Why use bash script?

It makes the things easier and more automated.

`[train@localhost play]$ nano simple.sh`

#!/bin/bash  
echo "I am a simple bash script"
```
[train@localhost play]$ sudo chmod +x simple.sh
[sudo] password for train:
[train@localhost play]$ ./simple.sh
I am a simple bash script
```

If we are in the same directory with the script file to run we use ./, bash, sh ..  

Always start with to tell OS which shell to use  
 List available shells  
 ```
 [train@localhost play]$ cat /etc/shells
/bin/sh
/bin/bash
/usr/bin/sh
/usr/bin/bash
/bin/tcsh
/bin/csh
```