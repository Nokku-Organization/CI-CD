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


