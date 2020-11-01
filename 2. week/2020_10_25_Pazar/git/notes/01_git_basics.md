 # Set git configs
 
 git config --global user.name "Erkan Şirin"  
 git config --global user.email "erkansirin78@hotmail.com"  

 ```
$ git config --global user.name
Erkan ŞİRİN

$ git config --global user.email
erkansirin78@hotmail.com

# Colorful output
git config --global color.ui auto
```
Close clrf warnings  
`git config --global core.autocrlf false`

# Create a git project
```
$ mkdir git_project
$ cd git_project/

# create db (kinda)
$ git init

$ ls -al
total 44
drwxr-xr-x 1 user 197121 0 Eki  3 00:36 ./
drwxr-xr-x 1 user 197121 0 Eki  3 00:35 ../
drwxr-xr-x 1 user 197121 0 Eki  3 00:36 .git/
```

# Commit & Log
Create a simple shellscript file and say hello  
```
$ touch hello.sh
$ vi hello.sh
$ chmod +x hello.sh
$ ./hello.sh
Hello git
```

Add new file to staging area  
`git add hello.sh` or `git add .`  

Commit changes to local repository  
`git commit -m "hello.sh has completed and tested"`  

List versions  
```
$ git log
commit 725c485ba552c26b73c78322adb5bfaa6105dfb0
Author: Erkan ŞİRİN <erkansirin78@hotmail.com>
Date:   Sat Oct 3 14:38:46 2020 +0300

    hello.sh has completed and tested
```

# Status 
```
git status
On branch master
nothing to commit, working directory clean
```
Add new sh file which simply lists current directory.  
```
$ vi listhere.sh

$ chmod +x listhere.sh

$ ./listhere.sh
total 2
-rwxr-xr-x 1 user 197121 30 Eki  3 14:30 hello.sh
-rwxr-xr-x 1 user 197121 18 Eki  3 14:43 listhere.sh
```
Now **git status**  
```
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        listhere.sh

nothing added to commit but untracked files present (use "git add" to track)
```
Add and commit this change  
```
$ git add listhere.sh
warning: LF will be replaced by CRLF in listhere.sh.
The file will have its original line endings in your working directory.


$ git commit -m "listhere.sh is added"
[master ddc5936] listhere.sh is added
warning: LF will be replaced by CRLF in listhere.sh.
The file will have its original line endings in your working directory.
 1 file changed, 2 insertions(+)
 create mode 100644 listhere.sh


$ git status
On branch master
nothing to commit, working directory clean

$ git log
commit ddc59363a22ac1ebafacf07baf50ca1960fa90f7
Author: Erkan ŞİRİN <erkansirin78@hotmail.com>
Date:   Sat Oct 3 14:51:09 2020 +0300

    listhere.sh is added

commit 725c485ba552c26b73c78322adb5bfaa6105dfb0
Author: Erkan ŞİRİN <erkansirin78@hotmail.com>
Date:   Sat Oct 3 14:38:46 2020 +0300

    hello.sh has completed and tested
```

# diff
```
$ vi hello.sh

$ ./hello.sh
Hello Git
I have made a change

$ git diff
diff --git a/hello.sh b/hello.sh
index 482acd7..dc72ce5 100644
--- a/hello.sh
+++ b/hello.sh
@@ -1,3 +1,5 @@
 #!/bin/bash

 echo "Hello Git"
+
+echo "I have made a change"
warning: LF will be replaced by CRLF in hello.sh.
The file will have its original line endings in your working directory.
```

You see the line we have added `echo "I have made a change" `  

Add and commit this change too.  
```
 git add hello.sh
warning: LF will be replaced by CRLF in hello.sh.
The file will have its original line endings in your working directory.


$ git commit -m "new line added in hello.sh"
[master warning: LF will be replaced by CRLF in hello.sh.
The file will have its original line endings in your working directory.
6f2128b] new line added in hello.sh
warning: LF will be replaced by CRLF in hello.sh.
The file will have its original line endings in your working directory.
 1 file changed, 2 insertions(+)
```

When you want to see diff after adding stagind area you can use `git diff <file> --staged`  

# Delete files 

We can use **rm <file>** or **git rm <file>** to delete files.   

# Roll back changes from local repo commit (checkout) 
Add a readme file  
```
$ vi readme.md

$ git add readme.md
warning: LF will be replaced by CRLF in readme.md.
The file will have its original line endings in your working directory.


$ git commit -m "readme file added"
[master a869c6d] readme file added
warning: LF will be replaced by CRLF in readme.md.
The file will have its original line endings in your working directory.
 1 file changed, 1 insertion(+)
 create mode 100644 readme.md
```
Now delete something in this file  
```
$ vi readme.md

$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   readme.md

no changes added to commit (use "git add" and/or "git commit -a")

```
Assume we have made that delete by mistake and get deleted part back
```
$ cat readme.md
this is
```

Actually it was this is readme file. Let's rollback (checkout)  
```
$ git checkout -- readme.md

$ cat readme.md
this is read me file
```

Delete a file mistakenly and rollback is similar.  

# Roll back changes from staging add (reset) 

Delete mistakenly a file and add changes to staging area  
```
$ git rm hello.sh
rm 'hello.sh'

$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        deleted:    hello.sh



$ git add .



$ ll
total 2
-rwxr-xr-x 1 user 197121 18 Eki  3 14:43 listhere.sh*
-rw-r--r-- 1 user 197121 23 Eki  3 16:00 readme.md

```
Now rollback  
```
 git reset HEAD hello.sh
Unstaged changes after reset:
D       hello.sh

$ ll
total 2
-rwxr-xr-x 1 user 197121 18 Eki  3 14:43 listhere.sh*
-rw-r--r-- 1 user 197121 23 Eki  3 16:00 readme.md

$ git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        deleted:    hello.sh

no changes added to commit (use "git add" and/or "git commit -a")

$ git checkout -- hello.sh

$ git status
On branch master
nothing to commit, working directory clean

$ ll
total 3
-rwxr-xr-x 1 user 197121 64 Eki  3 16:27 hello.sh*
-rwxr-xr-x 1 user 197121 18 Eki  3 14:43 listhere.sh*
-rw-r--r-- 1 user 197121 23 Eki  3 16:00 readme.md
```

# change version
We are versionng at every commit. We can change of our file(s) to any state in 
history.  
Add another line into readme file and commit.  
```
$ vi readme.md

$ git add .

$ git commit -m "another line added to readme"
[master ea2f6ee] another line added to readme
 1 file changed, 3 insertions(+), 1 deletion(-)

$ git status
On branch master
nothing to commit, working directory clean

$ cat readme.md
this is read me file

I have added second line into readme.
```

Now list the log and move a point  
```
$ git log
commit ea2f6eea926d56e5362c3d1fe86658c57beb2a04
Author: Erkan ŞİRİN <erkansirin78@hotmail.com>
Date:   Sat Oct 3 18:24:26 2020 +0300

    another line added to readme

commit a869c6d236ea0924b60b06086bd69d414e19adbd
Author: Erkan ŞİRİN <erkansirin78@hotmail.com>
Date:   Sat Oct 3 15:39:45 2020 +0300

    readme file added

commit 6f2128bfde7144560ed54a621c7da884ccf75fe3
Author: Erkan ŞİRİN <erkansirin78@hotmail.com>
Date:   Sat Oct 3 15:10:54 2020 +0300

    new line added in hello.sh

commit ddc59363a22ac1ebafacf07baf50ca1960fa90f7
Author: Erkan ŞİRİN <erkansirin78@hotmail.com>
Date:   Sat Oct 3 14:51:09 2020 +0300

    listhere.sh is added

commit 725c485ba552c26b73c78322adb5bfaa6105dfb0
Author: Erkan ŞİRİN <erkansirin78@hotmail.com>
Date:   Sat Oct 3 14:38:46 2020 +0300

    hello.sh has completed and tested
```
Now checkout  
```
$ git checkout a869c6d236 -- .

$ cat readme.md
this is read me file

$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   readme.md
```

