# Introduction to Git and GitHub: Git Desktop

## Before class

* share URL to hack.md
* check installation of text editor, GitHub Desktop and GitHub account (need latter to set up former)
* PhD comic: http://phdcomics.com/comics.php?f=1531

## Intro to version control

* why version control? PhD comic
* ask who's been to a GitHub site before (for research purposes)
* git: version control software (there are many others)
* GitHub: online code repository for publishing/sharing code and/or data (there are others)
* using git and GitHub because they are currently popular for academic and industry groups, many folks on campus are using them

## Setup

* reference: https://help.github.com/desktop/guides/getting-started-with-github-desktop/
* open GitHub Desktop app (make sure this is the right one!)
* check Preferences: Accounts, Advanced (external editor)

## Creating a repository

* File -> new repository
* name: first_repository
* What is a repository?
* description: brief (>10 word) statement describing purpose
* local path: location where it will be saved (recommended Desktop or Documents)
* Click box to "initialize this repository with a README"
* What happened?
* Use file browser to find location in your computer where repository is saved
* What's in this folder?
* open README in text editor
* README.md: pre-populated with title of the repository and short description
* What is a README?
* What else is in the repo?

## Tracking changes

* add note to README and save
* what happens in app?
* "Changes" tab in left panel shows what files have been altered: saved on computer, but not tracked by git yet
* panel on right side shows what changes have occurred: green for additions, red for removals
* check marks next to files indicate what is slated to be added to repository and tracked by git
* to track by git, need to commit!
* at bottom of left panel, add summary (brief, <50 characters)
* longer description may be useful for more complex sets of changes
* click button for "commit to master", where "master" refers to the branch (we'll talk more about this later, but master is default)
* edit file again (right click to "Open in Atom")
* create new file
* git workflow: save changes, make sure box is checked, commit
* relate to shopping cart analogy 
* create folder
* can you commit new file?
* create file in folder
* if you uncheck everything?

## Exploring history

* history tab in left panel
* right click and "Revert commit" to undo previous
* will need to merge again
* string of alphanumeric characters are a unique label for the commit

## Ignoring things

* Repository -> Repository settings
* select tab for "Ignored Files"
* add name of file

## Wrapping up
