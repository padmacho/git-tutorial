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
Commit history of the file can be found using git log. It provides history in reversed chronological order
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
ubuntu@git-standalone:~/my-local-repo$ git diff HEAD ... HEAD~1
diff --git a/Hello.txt b/Hello.txt
index 97f8c93..a29bdeb 100644
--- a/Hello.txt
+++ b/Hello.txt
@@ -1,2 +1 @@
 line1
-Line 2
```
