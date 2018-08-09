# Introduction to Git and GitHub: Git Desktop

## Before class

* share URL to hack.md
* check installation of text editor, GitHub Desktop and GitHub account (need latter to set up former)
* PhD comic: http://phdcomics.com/comics.php?f=1531

## Introductions and motivation

* introduce myself
* sign in to hackmd with name and motivation
* informal pre-class survey:
	* who's used Git or GitHub before?
	* show comic: who wants a better way?
* course overview: desktop app, GitHub, command line to integrate both
* objectives:
	* describe why and when to use version control
	* apply git workflow to tracking changes using GitHub Desktop app
	* view and recall history of tracked changes
	* ignore files that don't need to be in repository


## Intro to version control

* why version control? 
	* other places version control is used: MS Word "track changes", Google Docs versions, Mac OSX Time Machine
	* version control (and git) can be used for anything, but is especially important for code
	* code is like a list of instructions, in which changes may have unexpected consequences elsewhere in the code
	* working across complex code may require being able to interpret which changes affect other parts downstream, many changes later
	* knowing what code works at which point in time and what changes to the code may have caused problems is what version control allows us to manage
	* simplest case: a single document, make changes to code, then make more changes
	* more complex case: multiple copies of a document, with different changes made to each that need to be reconciled.
* git: version control software (there are many others)
* GitHub: online code repository for publishing/sharing code and/or data (there are others)
* using git and GitHub because they are currently popular for academic and industry groups, many folks on campus are using them
* lots of help documentation about git and GitHub, so today is a crash course and brief overview of functionality


## Setup

* reference: https://help.github.com/desktop/guides/getting-started-with-github-desktop/
* open GitHub Desktop app (make sure this is the right one!)
* check Preferences: Accounts, Advanced (external editor)


## Creating a repository

* What is a repository? analogy of a book in a library
* File -> new repository
	* name: first_repository
	* description: brief (>10 word) statement describing purpose
	* local path: location where it will be saved (recommended Desktop or Documents)
	* Click box to "initialize this repository with a README"
	* Click "Create repository" to finish
* What happened?
	* Use file browser to find location in your computer where repository is saved
	* What's in this folder?
* README: plain text file, open in text editor
	* documents contents of repository, can describe code and/or data
	* pre-populated with title of the repository (and short description?)
	* .md suffix indicates markdown format, which is for text formatting (same as hackmd)
* What else is in the repo?
	* use CMD + Shift + . to reveal hidden files
	* .gitattributes: created by app to maintain line endings, which can differ between operating systems
	* .git directory: contains tracking of changes as recorded by git software
	* entire directory is a unit
* Challenge: Why would it be a bad idea to create another git repository inside this directory?

## Tracking changes

* overview of text editors and why to use them
* add note to README and save
* what happens in app?
	* "Changes" tab in left panel shows what files have been altered: saved on computer, but not tracked by git yet
	* panel on right side shows what changes have occurred: green for additions, red for removals
	* check marks next to files indicate what is slated to be added to repository and tracked by git
	* if you uncheck files, you can't make a commit (no changes)
* to track by git, need to commit!
	* at bottom of left panel, add summary (brief, <50 characters)
	* longer description may be useful for more complex sets of changes
	* click button for "commit to master", where "master" refers to the branch (we'll talk more about this later, but master is default)
* git workflow: save changes, make sure box is checked, commit
	* edit file again (right click to "Open in Atom"), commit changes
	* create new file named notes.txt in text editor, add brief content, commit changes
	* relate to shopping cart analogy
* Challenge:
	* create new file named analysis.txt, add content, save, and commit
	* make and save changes to both analysis.txt and notes.txt, commit both at once
* create folder named data/
	* can you commit new folder?
	* create file data1.txt in folder, can you commit now?


## Exploring history

* "Undo" button at bottom of changes tab, can undo one at a time
* history tab in left panel
	* shows every time you've committed changes (remember, this is different than each time you hit save on a file)
	* right click
	* "Revert commit" to go directly back to that point in history: this retains all changes, but undoes the tracking in Git
* SHA: Secure Hash Algorithm
	* string of alphanumeric characters, unique label for the commit
	* can be just the first seven characters


## Ignoring things

* create new file, temp.txt, save and commit
* Repository -> Repository settings
* select tab for "Ignored Files"
* add temp.txt to this file; what happens?
* add notes.txt to the ignore file; what happens?
	* this is an example of a specific task which may be better accomplished with command line functions
	* preview concerns with managing large data files or secure info
* can ignore entire directories, or use wildcards to indicate types of files 


## Wrapping up

* review objectives
* short demo of Git Kraken
* preview next week
* link to comment box
