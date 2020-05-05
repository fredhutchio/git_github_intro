# Introduction to Git and GitHub: Git Desktop

## Objectives

Welcome to Introduction to Git and GitHub from fredhutch.io!
This course is designed for researchers who are interested in version control for code or data files,
and assumes no prior programming experience.
There are no prerequisites for this course
(though see below regarding the optional third class).

This course will introduce you to
the Git Desktop application to manage version control on your own computer and
GitHub to publish and collaborate with files tracked in remote repositories.
The optional third class applies skills from the first two classes using Git on the command line,
and requires some familiarity with navigating files and directories using the Unix commands.

To complete the activities associated with this course,
please ensure you have completed the following tasks (additional information can be found [here](http://www.fredhutch.io/software/#course-specific-software-requirements)):

- register for a GitHub account
- install GitHub Desktop (including the command line tools, if you are on a Windows computer and planning to complete the optional third session)
- (optional) install a text editor (like Atom or Notepad++)

By the end of this first session, you should be able to use the GitHub desktop app to:

- describe why and when to use version control
- apply the Git workflow to tracking changes using GitHub Desktop
- view and recall the history of tracked changes
- ignore files that don't need to be tracked


## What is version control?

Jorge Chan's [PhD Comics](http://phdcomics.com) illustrates why you might be interested in version control:

![final.doc from PhD Comics](images/phd101212s.gif)

In fact,
you may already be familiar with the use of version control,
through:

- Microsoft Word's "track changes" option
- Google Docs version history
- Mac OSX Time Machine

Version control is used to record changes to all types of files,
but is especially important for code.
This is because changes made to code may have consequences for other parts of the file or project,
and being able to understand where changes caused problems is especially important.

In the simplest case,
version control allows you to identify what changes have occurred in a single file over time,
such as edits to a written document made by one person over time.
In more complex cases,
you may possess multiple copies of the same document,
with multiple individuals making changes at the same time,
some of which may be inconsistent with each other and need to be reconciled.
[Git](https://git-scm.com/about) is software that allows you to perform version control.
[GitHub](https://help.github.com/en/github) is website for publishing and sharing projects that are tracked using Git.
Git and GitHub are a very popular set of tools used by both academic and commercial organizations,
and correspondingly,
have well-developed help documentation and a large community of users to assist in their use.

This class will give you a basic introduction to the general Git workflow to track changes to files.
There are many additional resources available online through [GitHub](https://help.github.com/en/github) to help you along the way.

## Creating a repository

* reference: https://help.github.com/desktop/guides/getting-started-with-github-desktop/
* open GitHub Desktop app (make sure this is the right one!)
* check Preferences: Accounts, Advanced (external editor)

* What is a repository? a project folder including all files and their history as tracked with Git. A repository can represent a variety of projects, including a piece of software, quarterly report, or research manuscript
* analogy of repository as a book in a library
* File -> new repository
	* name: first_repository
	* description: brief (>10 word) statement describing purpose
	* local path: location where it will be saved (recommended Desktop)
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
* "Discard changes" allows you to reset to where you were previously


## Ignoring things

* create new file, temp.txt, save and commit
* Repository -> Repository settings
* select tab for "Ignored Files"
* add temp.txt to this file; what happens?
* add notes.txt to the ignore file; what happens?
	* this is an example of a specific task which may be better accomplished with command line functions
	* preview concerns with managing large data files or secure info
* can ignore entire directories, or use wildcards to indicate types of files


## Branches

* branch: a parallel version of the “master” repository that allows you to test changes without affecting the original (or live) version; changes in a branch can be merged back to the “master” when a particular task has been completed
* why use branches?
	* when working collaboratively, someone else may want to try something but you need to keep working without seeing their changes
	* you may want to try something that has a chance of not working, and you don't want to risk having to undo a bunch of stuff
* create new branch called "wacky-branch"
* add some data files, commit
* show original branch and note files aren't there (also show on Desktop!)
* merge branches and show history
* deleting old branch: when on branch, menu option (note that branch is completely gone forever!)


## Wrapping up

This class introduced you to version control using Git Desktop.
We covered the general Git workflow,
its implementation using GitHub Desktop,
working with the tracked history,
and ignoring files that don't need to be tracked.

In the next class,
we'll learn about publishing repositories and collaborating using remote repositories in GitHub.
