- read.sh  
```
#!/bin/bash
# Ask the user for their name
echo Hello, what is your name?
read USER_ANSWER1
echo It\'s nice to meet you $USER_ANSWER1.
echo Then who are you?
read SUSER_ANSWER2
echo Ok, promise, I will $SUSER_ANSWER2
```
- run read.sh  
When user see `Hello, what is your name?` prompt waits user to type input and hit enter.  
When user hit enter read capture the text and assign `USER_ANSWER1` variable.  

```
[train@localhost play]$ ./read.sh
Hello, what is your name?
Çolak Salih
It's nice to meet you Çolak Salih.
Then who are you?
go and watch Küçük Ağa, but not Memo Can.
Ok, promise, I will go and read or watch Küçük Ağa, but not Memo Can.
```

