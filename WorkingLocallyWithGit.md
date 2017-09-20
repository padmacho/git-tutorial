# Creating a Local repository
Create an empty directory
```bash
$ mkdir my-local-repo
```
Convert the local empty directory to git local repo
Change to created directory
```bash
~/my-local-repo$ git init
Initialized empty Git repository in /home/ubuntu/my-local-repo/.git/
```
The above command will create .git folder that has meta data
```bash
~/my-local-repo$ ls -a
.  ..  .git
```
Add file named Hello.txt
```bash
~/my-local-repo$ echo "Hello Wrold!!" > Hello.txt
echo "Hello Wroldls" > Hello.txt
```
Git status shows the file **Hello.txt** is untracked and doesn't have in repository
```bash
~/my-local-repo$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        Hello.txt

nothing added to commit but untracked files present (use "git add" to track)
```
Add file to repository and see it status
```bash
~/my-local-repo$ git add Hello.txt
~/my-local-repo$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   Hello.txt
```
**Note:** Here the file is staged to repository and yet to be added. Use git commit to add to repository

```bash
~/my-local-repo$ git commit
[master (root-commit) 8020da2] my initial file
 1 file changed, 1 insertion(+)
 create mode 100644 Hello.txt
```
The above command opens default editor and you can provide message like "my initial file" for the commit

You can use **-m** flag to add comments
```bash
~/my-local-repo$ git commit Hello.txt -m "init"
[master 9639b79] init
 1 file changed, 1 insertion(+), 1 deletion(-)
```
You can view the commit history using command **git log**
```bash
commit 17e97d3c9b897b6f241b0153aa868a2b1620f01f
Author: mighty.raju <mighty.raju@gmail.com>    
Date:   Wed Sep 20 04:17:21 2017 +0000         

    update messages                            

commit 40dc9d5e5e841f677cecad71de98d6130797f74c
Author: mighty.raju <mighty.raju@gmail.com>    
Date:   Wed Sep 20 04:16:18 2017 +0000         

    Initial                                    
```
## Add update files
Adds all the updated files
```bash
~/my-local-repo$ git add -u
~/my-local-repo$ git commit -m "New updates"
[master 47c0a84] New updates
 1 file changed, 1 insertion(+)
```

# History and diff
## History
Commit history of the file or repository can be found using git log. It provides history in reversed chronological order
```bash
:~/my-local-repo$ git log  
commit 47c0a841509a930258475c5358846fd2afd9c55e
Author: mighty.raju <mighty.raju@gmail.com>     
Date:   Wed Sep 20 04:20:21 2017 +0000          

    New updates                                 

commit 17e97d3c9b897b6f241b0153aa868a2b1620f01f
Author: mighty.raju <mighty.raju@gmail.com>     
Date:   Wed Sep 20 04:17:21 2017 +0000          

    update messages                             

commit 40dc9d5e5e841f677cecad71de98d6130797f74c
Author: mighty.raju <mighty.raju@gmail.com>     
Date:   Wed Sep 20 04:16:18 2017 +0000          

    Initial                                     
```
## Diff
## Using SHA1
```bash
~/my-local-repo$ git diff 47c0..17e97        
diff --git a/Hello.txt b/Hello.txt                                 
index be0aefb..add4189 100644                                      
--- a/Hello.txt                                                    
+++ b/Hello.txt                                                    
@@ -1,2 +1 @@                                                      
 How are you                                                       
-I am fine                                                         
```
## Using HEAD
 The latest commit is known as Head. I can also go back from the head by using a tilde syntax, so tilde1 is one commit back from the Head so I can go from Head tilde1 to Head which provides with the same one
```bash
~/my-local-repo$ git diff HEAD ... HEAD~1
diff --git a/Hello.txt b/Hello.txt
index 97f8c93..a29bdeb 100644
--- a/Hello.txt
+++ b/Hello.txt
@@ -1,2 +1 @@
 line1
-Line 2
```

The second option is optional
```bash
~/my-local-repo$ git diff HEAD~1
````
# Staging changes as multiple commits
Stage a file named 3.txt
```bash
 $ git add 3.txt
```
Stage multiple files. To stage files 4.txt 5.txt 6.txt
```bash
$ git add -A
```
Stage only the files that are in staging area. (i.e) The files which are already in staging aread and updated in local copy
```bash
$ git add -u
```

# Deleting and renaming files
## Delete a file
Delete file 6.txt
- Delete using operating system command for example : rm
- Stage the file
- Commit to repository (Remove from repository)

```bash
$ rm 6.txt
$ git add -u
$ git commit -m "file 6 is removed"
```

## Rename a file
Rename file named 5.txt
- Rename using operating system command for example : mv
- Stage the file
- Commit the file to repository

```bash
$ mv 5.txt 51.txt
$ git add -u
$ git status
On branch master                                  
Changes to be committed:                          
  (use "git reset HEAD <file>..." to unstage)     

        renamed:    5.txt -> 51.txt               
$ git commit -m "file 5 is renamed to 51"

```
**Note:** Git is intelligent to identify 5.txt file is changed

# Undoing changes to the working copy
I made change to file 1.txt and I want to discard them.  Simply chekout the file from repository
```bash
$ git checkout 1.txt
```
**Note**: The contents of working copy will replaced with HEAD contents

# Undoing/redoing changes in the repository
Reset the working copy and repository to HEAD~1
```bash
$ git reset --hard HEAD~1
```
# Cleaning the working copy
Delete the unstaged files from wroking copy. For example I have file 2.txt and 3.txt that are not staged they can be easily removed
```bash
$ touch 2.txt 3.txt
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        2.txt
        3.txt

nothing added to commit but untracked files present (use "git add" to track)
$ git clean -f
Removing 2.txt
Removing 3.txt
$ ls
1.txt
```
# Ignoring files with .gitignore
For example to ignore a folder named logs. Simply create a file .gitignore and specify the logs folder
```bash
$ mkdir logs
$ touch logs/log.txt
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        logs/

nothing added to commit but untracked files present (use "git add" to track)
$ echo "/logs" >> .gitignore
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        .gitignore

nothing added to commit but untracked files present (use "git add" to track)
$ cat .gitignore
/logs
```
**Note:** The logs folder is ignored . /logs is relative to repository path not to OS path
