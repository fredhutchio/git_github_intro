# Introduction to Git and GitHub Class 3: Git on the command line

## Objectives

The first two classes in this course have provided a general overview of version control using Git for both local repositories using GitHub Desktop and remote repositories using GitHub.

This class will provide an overview of command line operations using Git.
By the end of this class,
you should be able to:

- transfer Git knowledge from GUIs to the command line
- apply the basic git workflow:
	- modify-add-commit
	- ignoring files
	- connecting local and remote repositories
	- working with branches
- understand how to perform Git tasks that may be difficult or impossible to apply with a GUI,
such as:
	- updating a local repository with a remote repository owned by someone else
 	- cherrypicking
 	- removing a file completely from git log

The following materials assume you have some familiarity with navigating files and directories on the command line.
We'll also be editing files using [`nano`](https://www.howtogeek.com/howto/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/),
though you're welcome to use a different text editor if you prefer.


## Getting started

There are a few reasons you may choose to use the command line instead of one of the various GUIs to perform version control:

- You are already working on the command line and you don't want to switch programs
- You are working on a remote computer (cloud or HPC) and only have access to the command line
- You want to perform a task that isn't possible using a GUI

Go ahead and open the program you'll be using to run Git on the command line:

- Mac: Terminal, which can be found using the "Go" menu at the top of the screen,
then selecting "Utilities".
- Windows: Git for Windows installs an application called Git Bash,
which emulates the command line.

We've already been working with Git on our local computers,
so we should be set up and prepared to work on the command line
since the same settings apply globally
(e.g., across the entire computer).
We can double check our configuration and ensure our command line tools are working appropriately using the following command:

		git config –-list

This should show relevant details,
like the user name and email,
associated with any future Git commits.

This also introduces the basic syntax for Git:

		git VERB

In this case, `VERB` represents some action (submodule)
associated with running various Git functions.
We'll continue applying this syntax throughout the rest of today's class.

## Creating a local repository

We'll begin by creating a new directory to initialize.
First, ensure you are working in your home directory:

		cd

Then create a new, empty directory called "git_command_line"
and navigate inside it:

		mkdir git_command_line
		cd git_command_line

Next, initialize your new directory:

		git init

This instructs git to create `.git/`
in your working directory,
which is the location for records of previous file versions:

		git init

We can view this file by listing everything in the directory,
including hidden files:

		ls -a

Finally, we can see the current status of the Git tracking for this directory:

		git status

Note that the output here includes multiple comments that can helpfully identify further commands.


## Tracking changes

Now that we have a repository,
we can begin creating and tracking files.

First,
create a new file to edit in `nano`:

		nano code.sh

> Here we're using the suffix of `.sh`
> to suggest we are working with a shell script,
> though we won't actually be running any scripts today.

In the editor,
enter a title for the file:

		# Simple shell script

Save the file as you exit the editor.

We can confirm this change:

		ls
		cat code.sh

Next, show the status of the project:

		git status

There is new output here,
indicating there are files present,
but not yet tracked with Git.

We can add our file:

		git add code.txt

Check status:

		git status

"Changes to be committed" indicate there are files staged,
but not yet included in the version history for this repository.
We can commit this file:

		git commit -m "creating code file"

The option `-m` indicates that you are entering a comment for the commit on the command line.
Running `git commit` alone will open your default text editor so you can add a comment there.
Remember that good commits are brief (<50 characters); if you'd like to add more text,
add an empty line (two hard returns)
and then you can include more text.

Now we can view our repository's history:

		git log

This lists all revisions in reverse chronological order,
including the full SHA identifier (same initial characters as the short identifier we've been seeing).

Make another change to `code.sh`.
Look at the difference between the version history and the untracked changes:

		git diff

In this output, you should see:

- first line: old and new version of files, similar to `diff` command in Unix
- second line: labels for revisions
-	third and fourth: name of file changing
-	last lines: actual changes

Go ahead and commit these changes:

		git commit -m "adding change"

But remember,
you haven't yet stage this file!
You need to:

		git add
		git commit

This represents the general Git workflow of
*modify, add, commit*.

If we create a new, empty file:

 		touch data.txt

We can view the difference with the version history:

		git diff

If we then stage the file,
we won't be able to view the differences using that same command:

		git add data.txt
		git diff

We can, however,
add an option that will allow us to view these changes:

		git diff –-staged

**Challenge:** Commit this last file and view the commit history.

**Challenge:** Create a new Git repository on your computer called `bio/`.
Write a three-line biography for yourself in a file called me.txt.
Commit your file, then modify one line and add a fourth line.
Display the differences between this file's updated state and its original state.


## Exploring history

* prompts in git output can help you!
* compare different versions of commits
	* HEAD~1 (HEAD minus 1) and HEAD~2 refer to old commits: most recent end of chain is HEAD
	* `git diff HEAD~1 code.txt`
	* `git diff HEAD~2 code.txt`
	* `git show HEAD~2 code.txt` : includes changes and commit message
	* `git log` gives strings of digits and letters: `git diff XXXXXXXX code.txt`
	* can also just use first few characters: `git diff XXX code.txt`
* how to revert to old version?
	* make another change to code.txt, `git status`
	* `git checkout HEAD code.txt` to remove unstaged changes (default to previous committed version)
	* `git checkout XXX code.txt` to go back further in history
	* remember that you want changes before most recent commit
	* if you use `git checkout` without a file name, may end up with detached head
	* git revert
* Challenge: git checkout can be used to restore a previous commit when unstaged changes have been made, but will it also work for changes that have been staged but not committed? Make a change to code.txt, add that change, and use git checkout to see if you can remove your change.


## Ignoring things

* sometimes backup files are created by other programs, or intermediate files we don't want to track
* create dummy files:

		mkdir results
		touch temp.dat output.dat results/a.txt results/b.txt
		git status

Lots of stuff needs to be committed, but we don't want to!
		nano .gitignore`

Then add the following content to the file:

		temp.dat
		results/
		git status

What files remain to be tracked?

		git add .gitignore output.dat
		git commit -m “add ignore file”
		git status

What happens if we try to now add an ignored file?

		git add a.dat

View all ignored files:

		git status --ignored

**Challenge:** Ignoring files that have already been committed retains the file in the git log. How could we remove these completely from the repo? https://help.github.com/articles/removing-sensitive-data-from-a-repository/


## Publishing local repository to GitHub

* log in to GitHub, click icon in top right corner, create repo called `git_command_line`
* resulting page has info about configuring repository, it's done the `mkdir git_project`, `cd git_project`, `git init` process remotely
* connect the two repos: copy https url to clipboard
* go to local repo (in shell): `git remote add origin URL`
* `git remote -v`: check that it worked
* origin is a nickname for remote repo
* now send local changes to remote repo: `git push origin master`
* check remote repo, changes should be there (may need to refresh)
* create README file and add brief comment about the purpose of the materials, commit change, go back to terminal: `git pull origin master`
* Challenge: How is `git push` different from `git commit`?
* Challenge: You have cloned a repo owned by someone else. Can you push to and pull from that repo?


## Working with branches

* Look at existing branches: `git branch`
* Create new branch called testing: `git branch testing`
* `git branch`
* Switch to new branch: `git checkout testing`
* Create new branch and checkout at same time: `git checkout -b testing2`
* Try to delete branch: `git branch -D testing2`
* `git checkout testing`
* Successfully delete: `git branch -D testing2`
* create new file (in testing), commit
* switch to master
* `git merge testing master`
* Delete old branch

##

### Updating local repositories with a remote repo owned by someone else

* Change added to guacamole repo
* obtain URL to fredhutch.io/guacamole
* git remote add upstream URL (set remote)
* git remote -v (check)
* git fetch upstream (fetch updates)
* git checkout master (checkout master fork)
* git merge upstream/master (add upstream changes without losing local changes)


### Working with Git history

[Cherrypicking](https://www.previousnext.com.au/blog/intro-cherry-picking-git) refers to merging only some commits from one branch into another


[Rebasing](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase): moving or combining a sequence of commits to a new base commit.


[Rebasing from a specific commit](https://blog.github.com/2015-06-08-how-to-undo-almost-anything-with-git/)

		git rebase -i SHA


## Wrapping up

* review today's objectives
* preview next week: optional, but need additional tools if coming (see fredhutch.io website)
* link to comment box
