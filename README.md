# Git Introduction
The easiest way to get onself familier with git is to do a practical example, such that one can experience all the trouble one will meet when working on your own project. By the way using git via terminal on you local machine needs a setup that wont take you more than 5 minutes, so if you havent done so, please follow the git startup using this link: https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup.
let's think of a scenerial, when we have two files in our working directory, and then you have decided that this working directory would be your project directory. I created a file called "tutorial_git", then created two random text files, for demonstration, I call them "First_file.txt" and "Second_file.txt". So, the directory might look like this…
```
$ pwd
/Users/andrewtseng/Desktop/tutorial_git
$ ls
First_file.txt Second_file.txt
"tutorial_git/" will be our project directory, so lets initialize it such that git could keep track of this project folder.
$ git init
```
Initialized empty Git repository in /Users/andrewtseng/Desktop/tutorial_git/.git/
Now the local repository is established, we could connect this local repo to the remote repo. "git remote add" means that we try to connect a remote repo (that's why it has a URL) to your local repo. to see what remote site is connected, use "git remote -v". as you can see, the remote server now has a name called "origin", so later on when we push a file to remote, we puch it to origin. 
git remote add origin https://github.com/atseng17/git-tutorial.git
git remote -v
origin https://github.com/atseng17/git-tutorial.git (fetch)
origin https://github.com/atseng17/git-tutorial.git (push)
Once connected, we could freely "push" the changes made on the local repo to the remote repo and also "pull" the changes that was made from others to the remote repo to our local repo. Note that there are two terminologies "pull" and "push". Push means to make changes to the remote repo based on the changes that are made on the local repo. Pull, does the same thing but in the reverse direction, adapting the changes on the remote to the local.
now lets see how git keeps track of the local repo by using "git status"
$ git status
On branch master
No commits yet
Untracked files:
(use "git add <file>..." to include in what will be committed)
First_file.txt
Second_file.txt
nothing added to commit but untracked files present (use "git add" to track)
As you can see, the only two files that exist in the project directory are listed under "Untracked files". Note that the project folder is currently called the working directory, which is still not in the "local repo". the changes are all in the "working directory". in order to push the changes to the remote, we have to let git know what has changed, we we need to move the changes to the "staging area" such that git recognizes it. I Lets add "First_file.txt" to the staging area. The staging area is a "copy" of your latest commit, its like a cache file that is managed by it that stores the changes you made. you can add them one by one until you want to make all the things in the staging area the version that you are going to push to the remote.
$ git add First_file.txt
$ git status
On branch master
No commits yet
Changes to be committed:
(use "git rm --cached <file>..." to unstage)
new file:   First_file.txt
Untracked files:
(use "git add <file>..." to include in what will be committed)
Second_file.txt
beware we only added changes to the staging area, but without commiting it, the changes will not be added to the commit history.
$ git commit -m "adding first file"
[master (root-commit) bda8444] adding first file
1 file changed, 4 insertions(+)
create mode 100644 First_file.txt


$ git status
On branch master
Untracked files:
(use "git add <file>..." to include in what will be committed)
Second_file.txt
nothing added to commit but untracked files present (use "git add" to track)
as you can see that git recognized that a file is "created" in this version. what is I for got to add a line in the file that is copied to the staging area? so what I would do is to directly modify the file and re add it ot the stagin area. After modifying the file …
$ git status
On branch master
Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git checkout -- <file>..." to discard changes in working directory)
modified:   First_file.txt
Untracked files:
(use "git add <file>..." to include in what will be committed)
Second_file.txt
no changes added to commit (use "git add" and/or "git commit -a")
now add it to the staging area…
$ git add First_file.txt
Andrews-MacBook-Plus:tutorial_git andrewtseng$ git status
On branch master
Changes to be committed:
(use "git reset HEAD <file>..." to unstage)
modified:   First_file.txt
Untracked files:
(use "git add <file>..." to include in what will be committed)
Second_file.txt
As you can see that the file in the status of the file in the staging area is now "modified". Finally lets commit it and push it to remote repo.
$ git commit -m "adding lines in  first file"


git push origin master
Username for 'https://github.com': atseng17
Password for 'https://atseng17@github.com':
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 4 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 587 bytes | 587.00 KiB/s, done.
Total 6 (delta 0), reused 0 (delta 0)
To https://github.com/atseng17/git-tutorial.git
* [new branch]      master -> master
now you should see a file in you git remote repo
reference:
https://frontendmasters.com/courses/git-in-depth/working-area-staging-area-repository/
https://www.google.com/search?q=git+add+commit&sxsrf=ALeKk02kMt5ckWx74qc7uixu5eujEx3FBA:1593826718687&tbm=isch&source=iu&ictx=1&fir=d7sk_Httjsin4M%252CA6TjBZTtF7Ni_M%252C_&vet=1&usg=AI4_-kQKii9p6pbrJzlZvmXtA0wQmOUxjQ&sa=X&ved=2ahUKEwiBgpqbu7LqAhWvgXIEHTtSDpoQ_h0wAHoECAkQBA&biw=1336&bih=672#imgrc=yfW5rzkHU64b8M
