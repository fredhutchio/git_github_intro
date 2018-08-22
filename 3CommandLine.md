# Introduction to Git and GitHub: Git on the command line

##  Before class:

* set up shell:
	* enlarge text size
	* `export PS1='$ '`
	* `export PROMPT_COMMAND="history 1 >> PATH/TO/GitHistory.txt"`
* check installation of command line version
	* Terminal, Git for Windows
	* `git --help` should print help documentation


## Objectives

* configure git on command line 
* create and track work in local repositories
* practice git workflow (modify-add-commit)
* viewing and reverting history, ignoring things
* connecting with remote repos in GitHub

	
## SETUP

* why use git on command line?
	* there are some tasks you can't accomplish with GitHub Desktop
	* working on a remote computer (command line only)
	* doing work on command line already and you don't want to switch windows
* check configuration (most should've been set by Git Desktop)
	* `git config –list`
	* user.name, user.email, 
* if anything needs to be set:
	* `git config --global user.name "k8hertweck"`
	* `git config --global user.email "k8hertweck@gmail.com"`
	* nano: `git config --global core.editor "nano -w"`
	* text wrangler: `git config --global core.editor "edit -w"`
	* notepad++: `git config --global core.editor "'c:/program files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`
	* `--global` means these settings will apply to all repos
* syntax for git: `git VERB`	


## Creating a local repository

* `cd`
* `mkdir git_project`
* `cd git_project`
* tell git where to store old records and versions of file
	* `git init`
* list everything (including hidden files)
	* `ls -a`
* result is a subdirectory with information about project
* if this is removed, we don't have access to versioning anymore
* ask status of project
* `git status`
* output also adds helpful comments
* Challenge:


## Tracking changes 

* create new file: `touch manuscript.txt`
* open in text editor or use `nano manuscript.txt` or `vi manuscript.txt` 
	* add text, exit and save
	* `ls`, `cat manuscript.txt`
* show status of project: `git status`
	* "untracked files": there's something not being tracked
* add file: `git add mars.txt`
* `git status` "Changes to be committed": it's tracking, but the changes aren't recorded
* commit file: `git commit -m "creating script"`
	* commits record to history in .git, called a revision, with short identifier
	* run without -m and will open editor to add comment (you've specified your preference earlier today)
	* good commits: brief (<50 characters), for more info, add empty line (adds in separate field)
* `git status`
* check history: `git log`
	* lists all revisions in reverse chronological order: full identifier (relate to short identifier, same initial characters),
	* when created, log message
* make another change (this is just one way): `touch supplement.txt`, `cat supplement.txt`
* check status: `git status`
* look at differences: `git diff`
	* first line: old and new version of files, similar to diff command in Unix
	* second line: labels for revisions
	* third and fourth: name of file changing
	* last lines: actual changes
* commit changes: `git commit -m "adding change"`
* but change hasn't been added!: `git add`, `git commit`
* working through staging
* `nano supplement.txt`, make change
* look at differences: `git diff`
* stage file: `git add supplement.txt`, `git diff` (no output)
* `git diff –staged` (shows differences)
* `git commit -m`, `git status`, `git log`
* `git commit workflow`
* Challenge: 


## Exploring history


* compare different versions of commits
	* HEAD~1 (HEAD minus 1) and HEAD~2 refer to old commits: most recent end of chain is HEAD
	* `git diff HEAD~1 supplement.txt`
	* `git diff HEAD~2 supplement.txt`
	* `git log` gives strings of digits and letters: `git diff XXXXXXXX supplement.txt`
	* can also just use first few characters: `git diff XXX supplement.txt`
* how to revert to old version?
	* make another change, `git status`
	* `git checkout` to remove unstaged changes (default to previous committed version)
	* `git checkout XXX supplement.txt`
	* remember that you want changes before most recent commit 
* Challenge:


## Ignoring things

* sometimes backup files are created by other programs, or intermediate files we don't want to track
* create dummy files 
* `mkdir results`, `touch a.dat b.dat c.dat results/a.out results/b.out`
* `git status`: lots of stuff needs to be committed, but we don't want to!
* `nano .gitignore`, add `*.dat` and `results/`
* `git status`: now .gitignore is the only thing there!
* `git add .gitignore`, `git commit -m “add ignore file”`, `git status`
* `git add a.dat`: error
* `git status --ignored`
* Challenge:


## Remotes in GitHub

* log in to GitHub, click icon in top right corner, create repo called `git_project`
* resulting page has info about configuring repository, it's done the `mkdir git_project`, `cd git_project`, `git init` process remotely
* connect the two repos: copy https url to clipboard
* go to local repo (in shell): `git remote add origin https://github.com/k8hertweck/git_project`
* `git remote -v`: check that it worked
* origin is a nickname for remote repo
* now send local changes to remote repo: `git push origin master`
* check remote repo, changes should be there.
* create README file and add brief comment about the purpose of the materials, commit change, go back to terminal: `git pull origin master`
* Challenge:


## Wrapping up

* review today's objectives
* preview next week: optional, but need additional tools if coming (see fredhutch.io website)
* link to comment box
