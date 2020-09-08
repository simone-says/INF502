Part 1: Dealing with git

(1.) Describe what is the output of the following commands:
````
git branch
````
````
➜  Downloads cd -
~/Downloads/handson
➜  handson git:(master) git branch

* master
  math
~
(END)
````
````
git checkout BRANCH_NAME (USE THE NAME OF AN EXISTING BRANCH)
````
````
➜  handson git:(master) git checkout math
Switched to branch 'math'
````
````
git log --decorate
````
````

commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e (HEAD -> math)
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:13:48 2019 -0700

    Adding some more knowledge to the function

commit 654b490a181dedf82dd6deda5f9848d6cca05918
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:12:14 2019 -0700

    Added a draft of A.py

commit 2dfb02c3f9383d6c3b2695c99e175d8b85f594a1
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:08:47 2019 -0700

     Creating all files (all empty)
(END)
````
(2.) Try git log --graph --all. What do you see?

````
* commit 18931d12a8be7cac049b73c6bc8136e9482f3371 (master)
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:15:28 2019 -0700
| 
|     Making a small change here
|   
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e (HEAD -> math)
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Wed Aug 14 23:13:48 2019 -0700
|   
|       Adding some more knowledge to the function
| 
* commit 654b490a181dedf82dd6deda5f9848d6cca05918
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:12:14 2019 -0700
| 
|     Added a draft of A.py
| 
* commit 2dfb02c3f9383d6c3b2695c99e175d8b85f594a1
  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
  Date:   Wed Aug 14 23:08:47 2019 -0700
  
       Creating all files (all empty)
:
````

(3.) Use git diff BRANCH_NAME to view the differences from a branch and the 
current branch. Summarize the difference from master to the other branch.
````
##The 'master' branch contains a file named A.py with the following contents
not present in the 'math' branch:
+   if operator == 'sum':
+      print num1 + num2
+      print 'That was easy buddy'
+   else:
+      if operator == 'subtraction':
+         print num1 - num2
+         print 'I could handle that...'
+      else:
+         print 'my knowledge is limited'
##The 'math' branch contains the file A.py with the following (not present 
in 'master' branch):
-   print 'my knowledge is limited'  
````
(4.) Write a command sequence to merge the non-master branch into master.
````
git checkout master
git merge math
````
(5.) Write a command (or sequence) to (i) create a new branch called math 
(from the master) and (ii) change to this branch (yes, math is already there, 
just report what you've done, the error and the reason you got the error. If 
you deleted and recreated the branch, you are fine too)
````
fatal: A branch named 'math' already exists.
##Cannout create a new branch with the same name as an existing branch.

handson git:(master) git checkout math
Switched to branch 'math'
````
(6.) Edit B.py adding the following source code below the content you have there:
````
handson git:(math) nano B.py

print 'I know math, look:'
print 2+2
````
(7.) Write a command (or sequence) to commit your changes:
````
 handson git:(math) ✗ git commit B.py -m "Edit B file"

[math 855b453] Edit B file
 1 file changed, 2 insertions(+)
````
(8.) Change back to the master branch and change B.py adding the following source 
code (commit your change to master):
````
handson git:(math) git checkout master
Switched to branch 'master'
➜  handson git:(master)  nano B.py 
➜  handson git:(master) ✗ git commit B.py -m "Edited B file in master"
[master cb9b2be] Edited B file in master
 1 file changed, 1 insertion(+)
````
(9.) Write a command sequence to merge the math branch into master and describe 
what happened:
````
handson git:(master) ✗ git commit B.py -m 'Commit file B'
master 2cfd3a0] Commit file B
 1 file changed, 3 insertions(+), 1 deletion(-)
handson git:(master) git merge math
error: Your local changes to the following files would be overwritten by merge:
  B.py
````
(10.) Write a set of commands to abort the merge:
````
git merge --abort
````
(11.) Now repeat item 9, but proceed with the manual merge (Editing B.py). All 
implemented functions are needed. Explain your procedure:
````
➜  handson git:(master) git checkout math
➜  handson git:(master) ✗ nano B.py
##Opened text editor via nano function. Deleted any text that was not source code.
➜  handson git:(master) ✗ git add B.py
➜  handson git:(master) ✗ git commit -m 'fixed merge'
[master 7d2e8a4] fixed merge
➜  handson git:(math) git merge master
Updating 855b453..7d2e8a4
Fast-forward
 B.py | 3 +++
 1 file changed, 3 insertions(+)
````
````
##Switched to math branch, checked File B again, added file version, committed 
changes. Then, merged from within math branch to master branch.
````
(12.) Write a command (or set of commands) to proceed with the merge and make 
master branch up-to-date:
````
➜  handson git:(master) ✗ git commit -m 'fixed merge'
[master 7d2e8a4] fixed merge
➜  handson git:(math) git merge master
Updating 855b453..7d2e8a4
Fast-forward
 B.py | 3 +++
 1 file changed, 3 insertions(+)
````

Part 2: Using GitHub

Forked the INF502-Fall2020 repo, then created Markdown file in students 
folder. Created pull request and submitted back Igor's repo.
