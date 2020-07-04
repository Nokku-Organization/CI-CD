## GIT
- Git is a open-source-tool,version control which doesn't give UI
- But Github,codecommit,bitbucket can be taken as UI services built on Git
- Free and open-source distributed version control system.
- Supports non linear distributed workflows
- Provide data assurance for developing software
- Created by Linux Torvalds, creator of Linux in 2005

## Github
- Code hosting platform for collabaration and version control
- Built on Git

We need to install git for using github
## Installing git :
For Amazon-Ec2-Linux :
- [ec2-user@ip-0-0-0-0]$ sudo yum update -y
- [ec2-user@ip-0-0-0-0]$ sudo yum install git
- [ec2-user@ip-0-0-0-0]$ git --version

For Debian/ubuntu :
$ sudo apt-get update
$ sudo apt-get install git

Refer the above file for log.( https://github.com/Nokku-Organization/CI-CD/blob/master/1.source-control/github/installing-git-ec2-linux.txt )
official-reference: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git


After Installation , credentials need to be configured.
Two ways to configure credentials i.e, via (username and password) or via ssh key configration

Configure crentials Via Username and password:
Run the following command to enable credentials storage in your Git repository:
$ git config credential.helper store
To enable credentials storage globally, run:
$ git config --global credential.helper store

When credentials storage is enabled, the first time you pull or push from the remote Git repository, you will be asked for a username and password, and they will be saved in ~/.git-credentials file.

During the next communications with the remote Git repository you won’t have to provide the username and password.

Each credential in ~/.git-credentials file is stored on its own line as a URL like:

https://<USERNAME>:<PASSWORD>@github.com
Config Username and Password for Different Repositories
Sometimes you may need to use different accounts on the same Git server, for example your company’s corporate account on github.com and your private one.
To be able to configure usernames and passwords for different Git repositories on the same Git server you can enable the useHttpPath option.

By default, Git does not consider the “path” component of an http URL to be worth matching via external helpers. This means that a credential stored for https://example.com/foo.git will also be used for https://example.com/bar.git. If you do want to distinguish these cases, set useHttpPath option to true (source)

Run the following commands to configure Git credentials storage and separate credentials for different repositories on github.com:

$ git config --global credential.helper store
$ git config --global credential.github.com.useHttpPath true
The usernames and passwords for different GitHub repositories will be stored in ~/.git-credentials file separately on their own lines:

https://<USERNAME>:<PASSWORD>@github.com/path/to/repo1.git
https://<USERNAME>:<PASSWORD>@github.com/path/to/repo2.git
Cool Tip: Create a new Git branch and checkout in one command! Read More →
 
 reference: https://www.shellhacks.com/git-config-username-password-store-credentials/
 
 
 Using ssh also you can access git
 $ssh-keygen
 $cat ~/.ssh/id_rsa.pub
 #copy the above content and place in github account (drop down menu ->settings - >SSH and GPG keys->New SSh Key(tiitle-any))
 
 $git clone git@github.com:Nokku-Organization/CI-CD.git
- use ssh link to clone the git-path

- git config --global user.name "Your Name"
- git config --global user.email you@example.com



You need to remote server as using
$git remote add origin https://github.com/Nokku-Organization/machine-learning.git
Note: Gives error in using git push, git pull if using in new repo initialised with README.md file. IN that case make use of "git pull origin master --allow-unrelated-histories"




- 2 ways of working with git
2)or you can create entire new repo and work on
1)you can clone it via fit-url ,with specific branch and make relaevant changes

For working with new-repo, above installion and configuration steps need to be taken care.
Note : dont intialise repo with README.md file when creating repo via console
Objectives
- Initialise a 'webapi' repository
- Create a README.md file with contents of "NEw development project-1"
- Add the file to 
- commit the file with commit message
- Finally push your changes to github

-$echo "NEw development project-1">README.md
- $ git add README.md
- $ git status
- $ git commit -m "first commit"
- $ git commit --amend --reset-author //you may fix the identity used for this commit with this command
- $ Ggit pull origin master //refer above command for adding remote-origin.
- $ gir puah origin master


#detailed analysis of happening at beackend 



branching and merging with git source contraol:
- Using the abilty to branch the repo and make changes off the mainline is the biggest advantage pf using git
- However eventually that branch will need to rejoin the master branch and you will need to perform merge.:

Objective 
- create a dev branch
- correct the README.md file 
- Merge the correct README,md file into master branch

$ git branch //list of all branches present
$ git branch dev //creates new branch
$ git checkout dev //shifts the HEAD point to dev-branch
$ git checkout -b dev //created new branch and shifts HEAD point to dev branch in one command
$ echo "branching">>README.md
$ git add README.md
$ git commit -am "second commit"
$ git checkout master 
$ git merger dev
$ git push origin master

Above Method is ok to achieve goal but not recommended. its better to push to dev-branch first and then raise pull-request for review to master branch.
pull request can be done via console but found one document to automate but using this automation can be validated on personal coice.
https://medium.com/mergify/managing-your-github-pull-request-from-the-command-line-89cb6af0a7fa

So, the recommended process:

$ git branch //list of all branches present
$ git checkout -b dev //created new branch and shifts HEAD point to dev branch in one command
$ echo "branching">>README.md
$ git add README.md
$ git commit -am "second commit"
$ git pull origin dev
$ git push origin dev
Then raise pull request from dev to master branch
$ git checkout master
$ git pull origin master

 Sometimes its better to generate pull request (for review )to master branch from current branch instaed of directly merging
 






## Additional Content:
- .gitignore
- git reflog //reference logging
- git reset --hard //to delete the changes after committed
- git reset --soft //to delete the changes before committed



## There are three areas:
 base directory->staging-area(like a box, so we add to box by 'git add' command. we can change those changes done in this area)->permenatant storage(.git,like 
 a mail. After packing in a box we can send a mail.once sent to this stage changes can't be reverted.'git commit -m "message-log"' command can be used to push 
 this stage)
 
- 'git diff' command will give the difference between staging area and normal.(i.e, the changes you made after 'git status add' )

- A diff is a formatted display of the differences between two sets of files. Git displays diffs like this:

diff --git a/report.txt b/report.txt
index e713b17..4c0742a 100644
--- a/report.txt
+++ b/report.txt
@@ -1,4 +1,5 @@
-# Seasonal Dental Surgeries 2017-18
+# Seasonal Dental Surgeries (2017) 2017-18
+# TODO: write new summary
This shows:

The command used to produce the output (in this case, diff --git). In it, a and b are placeholders meaning "the first version" and "the second version".
An index line showing keys into Git's internal database of changes. We will explore these in the next chapter.
--- a/report.txt and +++ b/report.txt, wherein lines being removed are prefixed with - and lines being added are prefixed with +.
A line starting with @@ that tells where the changes are being made. The pairs of numbers are start line and number of lines (in that section of the file where changes occurred). This diff output indicates changes starting at line 1, with 5 lines where there were once 4.
A line-by-line listing of the changes with - showing deletions and + showing additions (we have also configured Git to show deletions in red and additions in green). Lines that haven't changed are sometimes shown before and after the ones that have in order to give context; when they appear, they don't have either + or - in front of them.
Desktop programming tools like RStudio can turn diffs like this into a more readable side-by-side display of changes; you can also use standalone tools like DiffMerge or WinMerge.


*To compare the state of your files with those in the staging area, you can use 
 'git diff -r HEAD'. The -r flag means "compare to a particular revision", and HEAD is a shortcut meaning "the most recent commit".
 
*You can restrict the results to a single file or directory using 
 'git diff -r HEAD path/to/file', where the path to the file is relative to where you are (for example, the path from the root directory of the repository).
 
*This 'git diff -r HEAD' command compares present file changes with last commit (i.e, in mail) , but not in staging area (i.e, not in box,git add)

- How can I view a repository's history?
The command git log is used to view the log of the project's history. Log entries are shown most recent first, and look like this:

commit 0430705487381195993bac9c21512ccfb511056d
Author: Rep Loop <repl@datacamp.com>
Date:   Wed Sep 20 13:42:26 2017 +0000

    Added year to report title.
The commit line displays a unique ID for the commit called a hash; we will explore these further in the next chapter. The other lines tell you who made the change, when, and what log message they wrote for the change.

When you run git log, Git automatically uses a pager to show one screen of output at a time. Press the space bar to go down a page or the 'q' key to quit.



*How can I view a specific file's history?
A project's entire log can be overwhelming, so it's often useful to inspect only the changes to particular files or directories. You can do this using git log path, where path is the path to a specific file or directory. The log for a file shows changes made to that file; the log for a directory shows when files were added or deleted in that directory, rather than when the contents of the directory's files were changed.

You have been put in the dental repository. Use git log to display only the changes made to data/southern.csv. How many have there been?



You may wonder what information is stored by each commit that you make. Git uses a three-level structure for this.

A commit contains metadata such as the author, the commit message, and the time the commit happened. In the diagram below, the most recent commit is at the bottom (feed0098), underneath its parent commits.
Each commit also has a tree, which tracks the names and locations in the repository when that commit happened. In the oldest (top) commit, there were two files tracked by the repository.
For each of the files listed in the tree, there is a blob. This contains a compressed snapshot of the contents of the file when the commit happened (blob is short for binary large object, which is a SQL database term for "may contain data of any kind"). In the middle commit, report.md and draft.md were changed, so the blobs are shown next to that commit. data/northern.csv didn't change in that commit, so the tree links to the blob from the previous commit. Reusing blobs between commits help make common operations fast and minimizes storage space.


*How can I view a specific commit?
To view the details of a specific commit, you use the command git show with the first few characters of the commit's hash. For example, the command git show 0da2f7 produces this:


