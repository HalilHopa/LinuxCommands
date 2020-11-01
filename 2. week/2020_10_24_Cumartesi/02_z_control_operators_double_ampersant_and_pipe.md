# Control Operators

You can often see tutorials online that connect various commands with different symbols. For example:
```
command1 |  command2
command1 &  command2
command1 || command2    
command1 && command2
```
What are these things? What are they called? What do they do? Are there more of them?  

These are called shell operators and yes, there are more of them. I will give a brief overview of the most common among the two major classes, control operators and redirection operators, and how they work with respect to the bash shell.  
 
`  &   &&   (   )   ;   ;;   <newline>   |   ||   `  

- `;` -> Will run one command after another has finished, irrespective of the outcome of the first.  
```
[train@localhost healthcheck]$ echo $((3<2)) ; echo "I worked" ; echo $((2>1))
0
I worked
1
```
- `&` -> This will run a command in the background, allowing you to continue working in the same shell.  
`command1 & command2 `  
Here, command1 is launched in the background and command2 starts running in the foreground immediately, without waiting for command1 to exit.  
Example:  
Regular inline for loop sleep 1 seconds in each itaration.  
```
[train@localhost healthcheck]$ for i in {1..20}; do sleep 1; echo $i; done
1
2
..
..
19
20
```
Now send it a file 
```
[train@localhost play]$ for i in {1..20}; do sleep 1; echo $i; done > for_20_sleep.txt
[train@localhost play]$ cat for_20_sleep.txt
1
2
..
..
19
20
```
Now you can try `&`  
```
[train@localhost play]$ for i in {1..20}; do sleep 1; echo $i; done > for_20_sleep.txt & echo "I can't wait him to return from Korea."
[1] 26134
I can't wait him to return from Korea.
```
As you see shell has push for loop and run echo command. After 20 secs later we check for_20_sleep.txt file.  
```
[train@localhost play]$ cat for_20_sleep.txt
1
2
..
..
19
20
[1]+  Done                    for i in {1..20};
do
    sleep 1; echo $i;
done > for_20_sleep.txt
```


- `&&` -> Used to build AND lists, it allows you to **run one command only if another exited successfully**.  
`command1 && command2`  
Here, command2 will run after command1 has finished and only if command1 was successful (if its exit code was 0). Both commands are run in the foreground.  
This command can also be written
```
if command1
then command2
else false
fi
```
Example: You first try with curl empty port then second time jenkins 8080 port.  Former will return error while latter return html content.  
```
[train@localhost play]$ curl http://localhost && echo "I can't marry before my brother"
curl: (7) Failed connect to localhost:80; Connection refused


[train@localhost play]$ curl http://localhost:8080 && echo "Now I can :))))))))))))))))))))))))))))))"
<html><head><meta http-equiv='refresh' content='1;url=/login?from=%2F'/><script>window.location.replace('/login?from=%2F');</script></head><body style='background-color:white; color:white;'>


Authentication required
<!--
You are authenticated as: anonymous
Groups that you are in:

Permission you need to have (but didn't): hudson.model.Hudson.Read
 ... which is implied by: hudson.security.Permission.GenericRead
 ... which is implied by: hudson.model.Hudson.Administer
-->

</body></html>                                                                                                                                                                                                                                                                                                            Now I can :))))))))))))))))))))))))))))))
```
- `||`-> Used to build OR lists, it allows you to **run one command only if another exited unsuccessfully.**
`command1 || command2`  
Here, command2 will only run if command1 failed (if it returned an exit status other than 0). Both commands are run in the foreground.  
This command can also be written
```
if command1
then true
else command2
fi
```
Example:  
```
[train@localhost healthcheck]$ curl --fail http://localhost || echo "Curl didin't work I did"
curl: (7) Failed connect to localhost:80; Connection refused
Curl didin't work I did
[train@localhost healthcheck]$ ((3<2)) || echo "I worked"
I worked
```
- `!` -> This is a reserved word which acts as the “not” operator (but must have a delimiter), used to negate the return status of a command — return 0 if the command returns a nonzero status, return 1 if it returns the status 0. Also a logical NOT for the test utility.  

- `|` -> The pipe operator, it passes the output of one command as input to another. A command built from the pipe operator is called a pipeline.


For more: https://unix.stackexchange.com/questions/159513/what-are-the-shells-control-and-redirection-operators