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

## Getting set up

We'll get started by checking to make sure GitHub Desktop has installed appropriately
and has relevant settings correctly assigned.

First, open GitHub Desktop.
If you are on a Windows machine and have also installed Git for Windows,
please make sure you're opening the correct application.
The icon for GitHub Desktop show the silhouette of the GitHub mascot,
Octocat (octopus cat):

![GitHub Desktop icon with Octocat](images/octocat.jpeg)

Next,
go to the toolbar at the top and select "GitHub Desktop"
and then "Preferences."
You should now be able to see the Preferences pop-up window.
Let's check the settings in the following tabs:

- "Accounts":
you should see your GitHub handle
(begins with `@`)
and name below "GitHub.com".
If not, please sign in using your account information.
- "Integrations": this is where you can select a default text editor for opening files.
It is not essential to have this set,
but may be convenient.
The [installation instructions](http://www.fredhutch.io/software/#course-specific-software-requirements) recommended Atom.
In general,
the default text editors on your computers
(Notepad, TextEdit) will not work well for writing code.
If you don't see any text editors available here,
that's ok!
You won't be able to use the shortcut to access files from GitHub Desktop,
but you'll still be able to complete the class activities.
- "Appearance": select the Dark theme if you prefer.

There are other options available under "Advanced",
you can consider changing these once you have more familiarity with version control
and your particular needs.

## Creating a repository

If you have taken Intro to R or Intro to Python through fredhutch.io,
you should be familiar with projects as a way to organize your work.
A project is a single folder containing the files associated with a unit work work,
like a chapter of a thesis/dissertation,
analysis for a manuscript, or a monthly report.

> "Folder" and "directory" will be used interchangeable for the purposes of this lesson.
> Similarly, "project" and "repository" are generally analogous for our purposes.

Git tracks changes associated with repositories.
A repository is a project folder containing all the files,
including code and data, associated with a particular unit of work,
as well as the history of changes associated with those files.

> If you'd like another explanation of creating a repository,
> [these instructions](https://help.github.com/en/desktop/getting-started-with-github-desktop/creating-your-first-repository-using-github-desktop)
> from GitHub will walk you through the process using the
> "Create a tutorial repository and clone it" option in GitHub Desktop.

We'll get started with our first repository by clicking the button for
"Create a New Repository on your Hard Drive."
You can also access this feature under "File" -> "New repository".
Enter the following options:

- Name: `first_repository`
- Description: "first repository for training".
The description should be a brief (>10 word) statement describing the purpose of the project
- Local path: location on your computer where the repository will be saved.
We recommend saving your repository to your Desktop so it's easy to find,
and will assume for the rest of this lesson that your repository is available there.
- Check the box to "initialize this repository with a README"
- Click "Create repository" to finish

> It's good practice to avoid spaces in your file and directory names.
> We'll continue to apply best practices and convention for organizing files and directories for this class;
> if you're interested in the rationale,
> please see fredhutch.io's class Data for Data Science.

We can explore what happens following creation of a repository,
sometimes called "initializing,"
by looking on your Desktop and locating the directory named `first_repository`.

The only file we can see contained in this directory is `README.md`,
a plain text file we can open in a text editor.
The file suffix `md` stands for Markdown,
which is a method of formatting text.
README is a standard name for a descriptive file contained in a repository,
and documents the contents of the directory.
In our case,
the README is pre-populated with the title of the repository
and short description we entered when creating it.

`README.md` is the only file we can currently see,
but there is other information contained in our repository.
This other information is currently hidden,
but we can access it by using a keyboard shortcut: `CMD + Shift + .`.
There are two additional things now visible:
- `.gitattributes`: this text file is created by GitHub Desktop to help ensure appropriate settings (e.g., line endings for text files, which can differ among operating systems).
- `.git/`: directory containing the history of changes tracked by Git

The `.git/` directory is how Git recognizes your project represents a repository,
and assumes you want to track all of the files contained within it.
Git tracking is recursive,
meaning not only the files in your project,
but all the files contained in folders in that directory can be tracked as well.

**Challenge:** What would happen if you tried to create a new Git repository
inside another Git repository?

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
