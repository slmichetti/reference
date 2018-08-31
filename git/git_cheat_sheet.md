#Git Cheat Sheet

##Commands
* git init - create a new repo
* git clone - clone a repo

* git log - show the log on the file
    * --oneline  (--oneline flag is used to alter how git log displays information)
    * --stat ("stat" is short for "statistics"):
    * -p (--patch) display the actual changes made to a file
    * -w ignores whitespace changes
    * -p SHA(first7) - Use the SHA of a commit as the final argument of all these commands to start at that commit git log

*git show - shows only one commit
    * --stat
    * -p or --patch
    * -w 

* git status
* git add - command is used to move files from the Working Directory to the Staging Index.
* got add . - will add all files in the current directory
* git commit - commits the changes and prompts for commit message
* git commit -m "Comments"  pass your message directly on the command line for the commit
* git commit --amend  lets you add a new commit message to the last commit as long as your working directory is clean
* git revert - the git revert command is used to reverse a previously made commit
    * $ git revert <SHA-of-commit-to-revert>
* git reset <reference-to-commit>
    * move the HEAD and current branch pointer to the referenced commit
    * erase commits with the --hard flag
    * moves committed changes to the staging index with the --soft flag
    * unstages committed changes --mixed flag
    * Ancestry references are typically used to indicate previous commits. The ancestry references are:
        * /^ – indicates the parent commit
        * /~ – indicates the first parent commit
        * /^ – indicates the parent commit
* .gitignore - keeps a file from being committed
* git diff - displays difference between 2 versions of a file
* .gitignore - keep a file in your project directory structure but prevents it from being accidentally committed to the project
* git tag to add a tag; -a nameit SHA7 
* git branch "name" - will create a branch with that name
* git checkout - to check out that branch
* # to list all branches
* git branch
* git branch "name" to create a branch w/ that name
* git branch -d "name" to delete that branch
* # to create a new "footer-fix" branch
    * git branch footer-fix
* # to delete the "footer-fix" branch
    * git branch -d footer-fix
* git checkout -b "name" master - creates a branch at the same location as master and checks it out
* git log --oneline --decorate --graph --all  - Running this command will show all branches and commits in the repository:
* git merge name-of-branch-to-merge  -- merge branch into master (if its ahead -- fast-forward merge)
* git reset --hard HEAD^ to undo a merge
* git commit --amend (type or commit message change)
* git revert -
* git reset - erases commits (potentially dangerous b/c you are removing commits from the repository). Types of resets:
    * --mixed
    * --soft
    * --hard
* git shortlog displays an alphabetical list of names and the commit messages that go along with them
* git shortlog -s -n  to show only the number of commits each author has made, sorted numerically
* git log --author=NAME to display all the commits by tan author
* git log --author "FNAME LNAME" to show full names must use quotes
* git show SHAfirst7 (git show 5966b66) to see extra details in a commit
* --grep flag to filter comments
    * to filter just specific words 
        * git log --grep=bug   
        * git log --grep bug
    * remember spacing
        * multiple words must be wrapped "in quotes"
* git remote - to access a remote repository
* git remote add is used to add a connection to a new remote repository.
* git remote -v is used to see the details about a connection to a remote.
* git remote add upstream URL for the original repo that you forked/cloned
* git push origin master 
* git fetch upstream master - updates my local repository
* git rebase to squash commits together
* git rebase -i HEAD ~3 will squash the commits to the pevious 3 from the HEAD. Use the number of commits you want to combine

**************************************************************************************************************
##Navigating The Git Log

To move through the log:
> to scroll down, press
> j or ↓ to move down one line at a time
> d to move by half the page screen
> f to move by a whole page screen
> to scroll up, press
> k or ↑ to move _up_ one line at a time
> u to move by half the page screen
> b to move by a whole page screen
> press q to quit out of the log 

**************************************************************************************************************
##Commits
The goal is that each commit has a single focus. Each commit should record a single-unit change. 

Globbing lets you use special characters to match patterns/characters. In the .gitignore file, you can use the following:
    * blank lines can be used for spacing
    * # - marks line as a comment
    * \* - matches 0 or more characters
    * ? - matches 1 character
    * [abc] - matches a, b, _or_ c
    * \*\* - matches nested directories - a/\*\*/z matches
    * a/z
    * a/b/z
    * a/b/c/z

**************************************************************************************************************
##Merging Branches
In a merge, you're merging some other branch into the current (checked-out) branch. We're not merging two branches into a new branch. We're not merging the current branch into the other branch.

Another type of merge where two divergent branches are combined. 
Fast Forward merge brings the HEAD up to where that branch is with the uncommitted changes (ex of merging head to footer)

Merge Conflicts
A merge conflict happens when the same line or lines have been changed on different branches that are being merged. Git will pause mid-merge telling you that there is a conflict and will tell you in what file or files the conflict occurred. Be careful that a file might have merge conflicts in multiple parts of the file, so make sure you check the entire file for merge conflict indicators - a quick search for <<< should help you locate all of them.

Resolve the conflict:
    * locate and remove all lines with merge conflict indicators
    * determine what to keep
    * save the file(s)
    * stage the file(s)
    * make a commit


**************************************************************************************************************
##Remote Repositories

The git push command is used to send commits from a local repository to a remote repository.
> $git push origin master

The git push command takes:
    * the shortname of the remote repository you want to send commits to
    * the name of the branch that has the commits you want to send

To pull in changes to your local repository from your remote repository:
    * $ git pull origin master

When git pull is run, the following things happen:
    * the commit(s) on the remote branch are copied to the local repository
    * the local tracking branch (origin/master) is moved to point to the most recent commit
    * the local tracking branch (origin/master) is merged into the local branch (master)

The git fetch command is just the first step. It just retrieves the commits and moves the tracking branch. It does not merge the local branch with the tracking branch. The same information provided to git pull is passed to git fetch:
    * the shorname of the remote repository
    * the branch with commits to retrieve
    * /$ git fetch origin master

##Forking Repositories
Forking creates an identical repository
To get commits from a source repository into your forked repository on GitHub you need to:
    * get the cloneable URL of the source repository
    * create a new remote with the git remote add command
    * use the shortname upstream to point to the source repository
    * provide the URL of the source repository
    * fetch the new upstream remote
    * merge the upstream's branch into a local branch
    * push the newly updated local branch to your origin repo


A pull request is a request for the source repository to pull in your commits and merge them with their project. To create a pull request:
    * fork the source repository
    * clone your fork down to your machine
    * make some commits (ideally on a topic branch!)
    * push the commits back to your fork
    * create a new pull request and choose the branch that has your new commits

**************************************************************************************************************
##Rebase Command
The git rebase command will move commits to have a new base. In the command git rebase -i HEAD~3, we're telling Git to use HEAD~3 as the base where all of the other commits (HEAD~2, HEAD~1, and HEAD) will connect to.

The -i in the command stands for "interactive". You can perform a rebase in a non-interactive mode. While you're learning how to rebase, though, I definitely recommend that you do interactive rebasing

Rebase Commands
The different commands that you can do with git rebase:
    * use p or pick – to keep the commit as is
    * use r or reword – to keep the commit's content but alter the commit message
    * use e or edit – to keep the commit's content but stop before committing so that you can:
    * add new content or files
    * remove content or files
    * alter the content that was going to be committed
    * use s or squash – to combine this commit's changes into the previous commit (the commit above it in the list)
    * use f or fixup – to combine this commit's change into the previous one but drop the commit message
    * use x or exec – to run a shell command
    * use d or drop – to delete the commit

When to rebase
    * /# interactive rebase
        * /$ git rebase -i <base>
    * /# interactively rebase the commits to the one that's 3 before the one we're on
        * /$ git rebase -i HEAD~3

Its recommended to create a backup branch before rebasing, so that it's easy to return to your previous state. If you're happy with the rebase, then you can just delete the backup branch!