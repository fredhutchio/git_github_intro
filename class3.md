# Introduction to Git and GitHub
# Class 3: Git on the command line

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
- understand how to find help to perform Git tasks that may be difficult or impossible to apply with a GUI,
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

> If you are on a Mac and receive an error starting with `xcrun`,
>follow [these instructions](http://www.fredhutch.io/software/#command-line-tools-mac-only-for-optional-third-week) to install command line tools.

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
which is the location for records of previous file versions.
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

		git add code.sh

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

> #### Challenge-commit
> Commit this last file and view the commit history.

> #### Challenge-init
> Create a new Git repository on your computer called `bio/`.
> Write a three-line biography for yourself in a file called me.txt.
> Commit your file, then modify one line and add a fourth line.
> Display the differences between this file's updated state and its original state.


## Exploring history

Now that we have some commits in our history,
we can start to explore commands to work with that history.

The first common task is to compare previous versions in our history.
We discussed `git diff` earlier in the context of changed and stage files,
but we can compare a single file between two different commits as well:

		git diff HEAD~1 code.sh

`HEAD` refers to the most recent commit in history.
You can interpret `HEAD~1` as "HEAD minus 1",
meaning this shows the differences between the last two commits.
You may not see any differences if you didn't have a change to `code.sh` between the last two commits.
You can use the same notation to explore other commits in history:

		git diff HEAD~2 code.sh

This shows the differences between the most recent commit and the third most recent commit.
If you would like more information about these differences:

		git show HEAD~2 code.sh

This shows the changes as well as the commit message.

This notation works for relatively recent commits, but can be difficult if you're dealing with commits much further back in history.
You can use the SHA key (string of letters and numbers)
for a commit (as reported in `git log`)
to compare `HEAD` with a specific commit:

		git diff 10752e9 code.sh

Remember that your SHA will differ,
as these are unique identifiers for each commit.
While the original SHA is very long,
you can use the beginning of the sequence.

Now that we know how to inspect changes,
we can address how to access earlier versions of files.
Make another change to `code.sh`,
and commit it to history.
If you execute `git status`,
you'll see the output includes a message telling you there is a file ready to be staged,
and an alternative if you do not want to keep those changes.
If we follow those directions:

		git restore code.sh

The changes we made are removed from `code.sh`,
as that command instructs git to revert to the previous commmitted version.
Please note that you can't undo that change!

> Older versions of git instruct to use `git checkout -- FILENAME`,
> which also works on newer versions,
> but is less intuitive.

> #### Challenge-checkout
> `git restore` (and `git checkout`)
> can be used to restore a previous commit when unstaged changes have been made.
> Will it also work for changes that have been staged but not committed?
> Make a change to `code.sh`,
> add the change to stage it,
> and then identify the steps needed to discard the changes.

You can also use the abbreviated SHA to work with the content of a previous commit
(remember that the SHA will be different for your repository!):

		git checkout 1dffd8a code.sh

You can use the previous tools we've explored,
like `git status` and `git diff`,
to inspect how this file differs from the most recent commit.
The changes you see here reflect the status of the file at the commit you specified above.


> If you receive a rather alarming error referencing `detached HEAD`,
> you've executed `git checkout` without a filename.
> You can resolve this by executing `git checkout main` 
> (replacing `main` with whatever branch you were previously working with),
> which will return you to the `HEAD` state of `main`.

> #### Challenge-revert
> In our first class,
> we discussed use of the "revert" feature to work with our revision history.
> Using either the [online Git documentation](https://git-scm.com/docs)
> or the command line tools,
> how does `git revert` differ from the process we covered above?


## Ignoring things

We talked in our first class about ignoring files that aren't necessary (or are inappropriate)
to include in the repository.
We can examine ignoring files on the command line by first creating some empty files representing things we wish to ignore:

		mkdir results
		touch temp.dat output.dat results/a.txt results/b.txt

Let's check what Git thinks we need to commit:

		git status

Git thinks lots of stuff needs to be committed,
but we don't want to!
Let's use `nano .gitignore` to create our file listing things to ignore,
then add the following to the file:

		temp.dat
		results/

Let's view what git recognizes as untracked files now:

		git status

What files remain to be tracked?
Let's add and commit these files:

		git add .gitignore output.dat
		git commit -m “add ignore file”

And again check our status:

		git status

What happens if we try to now add an ignored file?

		git add a.dat

As the response indicates,
we can forcibly ignore a file.
This may be useful in cases where we might induce changes in a file,
but don't want those changes added to the repository.

In these cases, it may be useful to examine the status of ignored files:

		git status --ignored

>#### Challenge-ignoring
> Ignoring files that have already been committed retains the file in the git
> history. How could we remove these completely from the repo, and check to be sure
> that we were successful?

Git on the command line has many more options to flexibly ignore files,
so please keep in mind the following resources to ensure your repository's history is maintained in an appropriate manner:
- [Removing sensitive data from a repository](https://help.github.com/articles/removing-sensitive-data-from-a-repository/)
- [Removing files from a repository's history](https://help.github.com/en/github/managing-large-files/removing-files-from-a-repositorys-history)


## Publishing a local repository to GitHub

Now that we've covered the general Git workflow for local repositories,
we can start to explore connections with remote repositories on the command line.

We'll start by logging on to GitHub.
Click on the "+" icon in the top right corner of the screen,
and then select "New repository".
Enter `git_command_line` as the name for the repository.
As the page indicates,
you shouldn't change other options if you're connecting an existing repository.
By clicking "Create repository",
you're effectively performing `mkdir git_command_line`,
`cd git_command_line`,
and `git init` in the remote server.
The following webpage is the placeholder for the content of your repository,
and includes the instructions for how to connect them.
We'll be using the instructions under the section header "…or push an existing repository from the command line".
Click on the button to the right of the code to copy the lines to your clipboard so they can be pasted into your shell and executed.
The first of these lines informs git where the remote repository can be found:

		git remote add origin https://github.com/USERNAME/git_command_line.git

The second line sends (pushes) the local changes to the remote repository:

		git push -u origin main

`origin` references the remote repository,
and `main` indicates the branch.
You should refresh the webpage following pushing to see the contents of your remote repository match those in your local.

If you are unsure what remote repository (or repositories) are connected to your local repository,
you can also run:

		git remote -v

The two lines output from that command include successfully connected `origin` for both pushing and pulling.

Now that you have connected your repositories,
on the online GitHub interface (remote repository)
you should see an option asking if you'd like to create a README file.
After clicking on that button,
add a line or two of text in the document describing the purpose of the materials and commit the change.
Return to your shell interface (local repository)
and run the following:

		git fetch

This command compares the two repositories (local and remote)
and provides a report of what differences exist between them.
This report should indicate that your branch (meaning the local repository) is behind the remote repository by one commit,
and can be fast-forwarded (meaning there are no conflicts and can be merged easily).
You can follow the instructions and execute:

		git pull

This command is a shortcut for `git pull origin main`.
You aren't required to use `git fetch` prior to pulling,
but it's often a good idea to know what changes you'll be adding to your local repository prior to pulling.

> #### Challenge-pull
> Make a change to the README in your *remote* `git_command_line` repository.
> Now make a conflicting change (e.g., on the same line) in the README in your local repository.
> What does Git do when you attempt to push changes from your local repository?


## Collaborating on the command line

This section will allow us to explore workflows for collaborating with git on the command line,
including the following tasks:
- cloning repositories
- setting upstream repositories
- branching

We'll be revisiting the [guacamole](https://github.com/fredhutchio/guacamole)
repository we used in our previous class.
During our exploration of GitHub,
we forked the repository to create our own copies,
made changes to our own repositories,
and submitted pull requests to the original repository.
All of these tasks were completed using the online web-based GitHub interface.

Here, we'll explore how to use command line tools to make changes to the repository locally.
First, go to the webpage for *your* fork of this repository
(the URL should be `https://github.com/USERNAME/guacamole`,
where USERNAME is your GitHub ID).
Click on the button to "Clone or download",
and click the button next to the web URL to copy the address.

Switch over to your shell interface.
Navigate to the location in your computer where you'd like the repository to be stored,
then clone it:

		git clone https://github.com/USERNAME/example_analysis_repo.git

You should now have a folder in your working directory named `guacamole`.

We'll be using a new branch to make changes to this repository.
First, let's look at our existing branches:

		git branch

We can make a new branch named `recipe`:

		git branch recipe

If we used `git branch` again,
we'd see that we are still working on our main branch,
but our new branch is now listed as another option.

We can checkout the new branch:

		git checkout recipe

Executing `git branch` or `git status` will now report that your working branch is `recipe`.

> It's possible to create a new branch and check it out at the same time using: `git checkout -b recipe`

Create a new file called `recipe.md` and add a few lines of instructions about how to use the foods in `ingredients.txt` to make guacamole.
Add and commit your changes.

If you would like to submit these changes to the original guacamole repository,
you'll need to publish your changes for the new branch to GitHub.
You could try:

		git push

But you'll receive an error: "fatal: The current branch testing has no upstream branch."
Luckily, you'll also see a suggestion for how to resolve this:

		git push --set-upstream origin recipe

When you refresh the webpage for your repository,
you'll now see the `recipe` branch available there,
ready to compare and submit as a pull request.

If, instead, you wanted to incorporate the changes from `recipe` into your own `main` branch,
you could switch to the `main` branch in your local repository:

		git checkout main

Then execute the merge:

		git merge recipe main

This adds the change you made in `recipe` to your default branch.

Whichever way your workflow proceeds,
you will likely want to delete a branch when you're done working with it:

		git branch -D recipe

Note that you cannot delete your current working branch.
This is the *opposite* of GitHub Desktop,
where you can only delete your working branch!

> #### Challenge-clone
> Let's assume you would like to work with the code present in this [example analysis repository](https://github.com/fredhutchio/example_analysis_repo),
> which is owned by fredhutch.io.
> 1. Describe the process you would undertake to contribute a new file to this repository.
> 2. Next, assume there has been a potentially conflicting change to the original repository (owned by fredhutch.io) since you made your change,
> and you need to pull these changes into your local repository.
> What would you search for in help documentation to identify the commands required for this task?


### Advanced options on the command line

We aren't able to cover all possible use cases for Git in this class.
Here we'll briefly discuss a few other tasks sometimes discussed with version control.

[Cherrypicking](https://www.atlassian.com/git/tutorials/cherry-pick) refers to selecting some commits from a branch and adding to another.
It differs from a standard merge in that it allows only *some* changes between branches to be applied,
and is useful in the following cases:
- during collaboration,
when a part of someone else's (yet uncompleted)
work is needed for you to continue your task
- to repair bugs in code that need to be reconciled quickly
- selecting parts of a branch prior to closing/discarding the rest of the work

[Rebasing](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase) is similar to merging in that it integrates changes from one branch into another.
Whereas merging always continues forward in the version history,
rebase reconciles previous changes to a repository.
More specifically,
it combines a sequence of commits in a branch with a new base commit.
In effect,
this causes your branch's history to appear that it was created at a different
(usually more recent)
point in the verion history.
[Squash is often included with rebase](https://medium.com/@slamflipstrom/a-beginners-guide-to-squashing-commits-with-git-rebase-8185cf6e62ec)
as a part of collaborative workflows.


## Wrapping up

In this class,
we reviewed material from the first two classes and how to accomplish the same tasks on the command line.
We also discussed a few special cases that can be performed on the command line,
but which aren't accessible via most stand-alone software.

This introductory course has provided an overview of many of the common terms, tasks,
and workflows associated with Git.
It is certainly not exhaustive,
and Git is continually updated,
so don't worry if you find yourself periodically frustrated.
The [documentation for git](https://git-scm.com/docs) includes a complete list of all commands,
as well as a few options for different cheat sheets.

Good luck, and happy version control!
