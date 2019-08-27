# guacamole
Repository from software carpentry class  
2019-08-27  
  
http://byronjsmith.com/2019-08-26-genentech/  
https://pad.carpentries.org/2019-08-26-genentech  








# Notes re: using Git/Github

Configuring Git  
$ git config --global user.email "****.*******@gmail.com"  
$ git config --global color.ui "auto"  
$ git config --global core.editor "nano -w"  
$ git config --global core.autocrlf input

$ mkdir testdir  
$ cd testdir  
$ git init  
$ ls -a  

if you want to get rid of history/version controlling delete .git directory within the repository   

$ git status  
$ git add filename.txt 			#can also use e.g. $ git add *.txt  
$ git commit -m "Message about what changes were made"  

to see a history of commits   
$ git log  

output of all differences within a repository  
$ git diff  

output of all differences within a single file  
$ git diff filename.txt  

compare file that is already in the staging area (e.g. has been "added")  
$ git diff --staged  

$ git commit --amend   		#to change the last commit message  

to see more infomration about history use HEAD is last commit, HEAD~1 is second to last, etc  
$ git show  
$ git show HEAD  
$ git show HEAD~1  

$ git diff HEAD~1 recipe.txt  

$ git log
$ git diff 1a06d51c4b927c7a178f74e932628cee5316a9c0  
$ git diff 1a06d51c4b927c7a178f74e932628cee5316a9c0 recipe.txt  

Reverting back to last commit (only works before you add a file to the staging area w/ git add)  
$ git checkout -- ingredients.txt  

When you make commits try to do one thing at a time! that way you can revert logically, e.g. fix typos, add funtion should be two functions >>if there's an "and" in the commit message you did it wrong<<  

after you have said git add to revert to the last commit  
$ git checkout HEAD ingredients.txt  

"Detached head state"  
If you made a bunch of changes but then ended up back at a previous version by accident you can get an error for "detached head"  
$ git checkout master  

To revert to last commit  
$ git checkout HEAD~1 ingredients.txt  
$ git commit -m "reverted to previous commit"  


$ git checkout -- ^C  
$ git checkout -- ingredients.txt  

git only cares about files, not directories   
if you want a directory to be saved you can create an invisible file called .gitkeep with touch (creates empty files)  
$ mkdir dir  
$ cd dir  
$ touch .gitkeep  
$ cd ..  
$ git status  
$ git add dir/  
$ git commit -m "added dir"  

now you will be able to see/add/commit the change  

if you want files within the repository to NOT be backed up create a hidden file called .gitignore containing filenames / patterns for files you don't want backed up for example:  

*.draft   
!recipe_grandma.draft  
^^^^^The order is important!   

$ nano .gitignore  
$ git add .gitignore  
$ git commit -m "Added ignore rules for drafts"  

if you want to override the .gitignore rules use:  
$ git add -f filename.draft  

you don't want nested repositories! just have one .git file at the top level of the repository  

removing files from github! you will have a record of their previous existance   
$ touch garbage.txt  
$ git add garbage.txt  
$ git commit -m "Garbage file"  
$ git rm garbage.txt  
$ git commit -m "deleted garbage file"  

Go to git up, create new repository  
(do not iniitialize w/ README)  
go to repository on terminal  
paste command from github website  
$ git remote add origin https://github.com/kcarbone/guacamole.git  
$ git push -u origin master  

to clone a collaborator's repository
Don't put repositories into repositories you already have! 
$ git clone https://github.com/cliuuu/guacamole.git chad-guac

$ nano suggestions.txt
$ git add suggestions.txt
$ git commit -m "Adds serving suggestions"
$ git push origin master

To update my guac repository 
cd gucamole 
$ git pull origin master

to find out what to pull from you can use:
$ git remote -v

resolving a failed push b/c conflict
$ git pull origin master
gives and error! merge failed 
$ git status
your branch and origin master have diverged
open the file github tells you contains the conflict
$ git add suggestions.txt
$ git status
$ git commit 
$ git status
$ git push origin master


Sharing individual files that are under version control:
https://gist.github.com/
