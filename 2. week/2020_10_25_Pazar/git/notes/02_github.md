It is a remote repo integrated with git.  
It is not git. Not part of git. But works with git.  
Similar remote repos gitlab and bitbuckets.

# Create a github project and integreate with local repo  

1. On browser Create a github project  (for example **git-lessons**)

2. On browser Copy https link from newly created github repo  

3. On terminal if you have not done yet please do the global configs (user.name and user.email)  

4. On terminal navigate to your local repo folder  

5. On terminal  
`$ git remote add origin https://github.com/erkansirin78/git-lessons.git`  

6. Check if the repo is added  
```
$ git remote
origin
```

7. Push your local repo to remote (github) repo.  
```
$ git push origin master
Fatal: HttpRequestException encountered.
Username for 'https://github.com': <your_username>
Counting objects: 15, done.
Delta compression using up to 12 threads.
Compressing objects: 100% (11/11), done.
Writing objects: 100% (15/15), 1.38 KiB | 0 bytes/s, done.
Total 15 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), done.
remote:
remote: Create a pull request for 'master' on GitHub by visiting:
remote:      https://github.com/erkansirin78/git-lessons/pull/new/master
remote:
To https://github.com/erkansirin78/git-lessons.git
 * [new branch]      master -> master
```

8. On browser go and see your remote repo.  

9. On terminal add new file and write anything inside.  


# .gitignore  
We put files that we don't want to tracted by git.  
```
$ vi my_private_file.txt

$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        aftergithub.txt
        my_private_file.txt

nothing added to commit but untracked files present (use "git add" to track)


$ vi .gitignore


$ cat .gitignore
my_private_file.txt


$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        .gitignore
        aftergithub.txt

nothing added to commit but untracked files present (use "git add" to track)
```

As you see once we `put my_private_file.txt` into `.gitignore` it is ignored.  

Now we try a folder and exlude some file in it  

Create a folder and two files in it.  
```
$ mkdir my_private_folder

$ cd my_private_folder/

my_private_folder (master)
$ touch private_file.txt

my_private_folder (master)
$ vi private_file.txt

my_private_folder (master)
$ vi public_file.txt
```
Add this folder to .gitignore

```
my_private_folder (master)
$ cd ..

$ vi .gitignore
```
Now see newly created folder and files in it untracted.
```
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        .gitignore
        aftergithub.txt

nothing added to commit but untracked files present (use "git add" to track)
```
Now exclude a file with **!** in .gitignore
```
$ vi .gitignore

$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        .gitignore
        aftergithub.txt
        my_private_folder/

nothing added to commit but untracked files present (use "git add" to track)
```
How di we do it?
```
$ cat .gitignore
my_private_file.txt
my_private_folder/*
!my_private_folder/public_file.txt
```
Now we add, commit, and push changes  
```
$ git add .

$ git commit -m "a folder added to .gitignore"

$ git push origin master
```
See changes on browser

# Branches 
master is default  
Can create on github or command line  

List branches  
```
$ git branch
* master
```
* means it is default branch  
Create a new branch, change to new branch and create file  
```
$ git branch dev

$ git branch
  dev
* master
```
Change branch  
```
$ git checkout dev
Switched to branch 'dev'
```
Crete a file write sth in it, add and commit
```
$ vi after_dev

$ git status
On branch dev
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        after_dev

nothing added to commit but untracked files present (use "git add" to track)

$ git add .

$ git commit -m "a file added after dev branch"
```
See the difference between dev and master branch
```
$ git diff dev master
diff --git a/after_dev b/after_dev
deleted file mode 100644
index f120bab..0000000
--- a/after_dev
+++ /dev/null
@@ -1,2 +0,0 @@
-This file created after dev branch.
-


$ git status
On branch dev
nothing to commit, working directory clean
```
Now push to remote and see the change on web browser
```
$ git push origin dev
```

# Merge branches
Switch to master
```
$ git checkout master
Switched to branch 'master'
```
Merge with dev
```
$ git merge dev
Merge made by the 'recursive' strategy.
 after_dev | 2 ++
 1 file changed, 2 insertions(+)
 create mode 100644 after_dev
```
Now push remote master and see changes on browser
```
$ git push origin master
```
## Github README.md

## Github watch 
Inform me what happens in that project.  

## Github fork 
You can fork and work on any project.  

## Github Issue 
Define a problem and discuss with team members.  
From labels you can categorize your issue. E.g bug.
When you solve problem you can close issue.

## Search in github
