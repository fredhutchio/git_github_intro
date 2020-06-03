# Introduction to Git and GitHub
# Class 2: GitHub

## Objectives

In the last class,
we used the GitHub Desktop application to work with version control on our own computers by creating repositories,
tracking changes using the basic Git workflow (modify-add-commit),
exploring history,
and ignoring files.

Now that you have some experience with version control using Git,
you may be able to appreciate this cartoon from [XKCD](https://xkcd.com):

![XKCD Git](https://imgs.xkcd.com/comics/git_commit.png)

Today, we'll transfer our knowledge to working with remote repositories on GitHub.
By the end of this class,
you should be able to:

- differentiate between local and remote repositories
- use GitHub to publish your own code/data
- contribute to someone else's repository using GitHub


## Introduction to GitHub

In our previous class,
we focused on git for local repositories,
which means applying version control for files and directories located on our own computers.
In this class,
we'll expand our understanding of version control to include working with remote repositories vit GitHub.

GitHub is a web-based platform for sharing and collaborating with code and data.
It allows you to create repositories that are publicly visible,
or private but accessible to specific people to whom you provide permission.

You registered for a GitHub account and used that information when setting up the GitHub Desktop app in [our previous class](class1.md).
If you log on to [GitHub](http://github.com) with your account information,
you can access a number of features including:
- a profile,
where you can include information about yourself
- starring repositories and following other people
- a timeline/newsfeed,
which will include notifications about recent projects and activities for yourself and people you follow

In addition to individual accounts,
groups of individuals working together can create [GitHub organizations](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams).
There are two relevant GitHub organizations for us:
- [fredhutch.io](https://github.com/fredhutchio): holds repositories containing course materials,
as well as the code for the [fredhutch.io website](http://www.fredhutch.io). All of these are publicly available repositories.
- [Fred Hutch](https://github.com/fredhutch): projects from Scientific Computing and other groups at Fred Hutch,
as well as the code behind the [Fred Hutch Biomedical Data Science Wiki](https://sciwiki.fredhutch.org/). Many of these projects are public, although there are also some that are viewable only to members or specific teams.

As a Fred Hutch affiliate,
you are welcome to join the Fred Hutch GitHub organization.
To learn how, as well as other information about this feature,
please see the [Wiki GitHub page](https://sciwiki.fredhutch.org/scicomputing/software_managecode/#using-github-at-fred-hutch).

> GitHub Teams are another way of organizing individual accounts and providing permission to private repositories.
The Wiki, for example,
includes a group of members from the Fred Hutch organization who review submissions of content to the Wiki.

Now that we've looked at accounts and organizations in GitHub,
we can examine a few publicly available repositories.

[**Intro to Git and GitHub**](https://github.com/fredhutchio/git_github_intro): The materials for this course are available in a repository,
with each class' materials written in a Markdown (`.md`) file.

> [Markdown](https://guides.github.com/features/mastering-markdown/) is a lightweight text-formatting language that allows creation of attractive documents.
Markdown is especially popular for creating documents on GitHub,
because the web interface automatically renders the formatting so they are easily readable.

[**Machkovech 2018**](https://github.com/rasilab/machkovech_2018) is the data analysis associated with a publication from a lab at Fred Hutch.
This repository includes scripts, notebooks, data, and figures for the published manuscript.

[`ggplot2`](https://github.com/tidyverse/ggplot2) is a very popular data visualization package for R statistical programming.
This repository includes all of the code needed to install and run `ggplot2`.

For more information on navigating and using GitHub,
please see [this resource page](https://help.github.com/en/github/getting-started-with-github).
If you would like additional information on managing your account,
please go [here](https://help.github.com/en/github/setting-up-and-managing-your-github-user-account).

## Publishing a local repository

With this understanding of how GitHub operates,
we can now publish some of our own work.
We'll use the repository we created in our previous class.

Open up GitHub Desktop,
making sure your `first_repository` is loaded.
Use the "Publish repository" button,
and uncheck the box next to "keep code private".
This initializes a new repository in the remote GitHub servers,
and copies your repository's code there.

Now you can view your repository on GitHub.
There are two ways to get there:
- Under the "Repository" menu,
select "View on GitHub"
- Go to `github.com/USERNAME/first_repository`,
where `USERNAME` is your GitHub username

In the repository on GitHub,
try and find the same features and information you've seen in your local repository on your own computer.
In particular, the commit history should be identical to your local repository.


## Pushing and pulling

Next, go back to your local repository.
Make a change to one of your existing files and commit it.

After committing,
the button in the top right of GitHub Desktop should now show the option to "Push origin".
Pushing in Git refers to sending all local changes to the remote repository.
After clicking the button,
go back to your web browser and view your remote repository.
You'll likely need to refresh the page to see the new changes.

> It's possible to create a remote repository on GitHub,
and then connect it to an existing local repository.
The button in GitHub Desktop is a shortcut that accomplishes multiple steps for you.

Our next step will be to perform the reverse action:
make a change in the remote repository,
and then add the changes to our local repository.
The online GitHub interface allows you to edit and otherwise work with files.
The web browser interface is great for making quick changes to files.
Some things to know about this interface:
- You can edit a file by clicking the pencil icon in the top right of its window.
- After making changes in the edit window, click the "Preview" tab to see how it will render (primarily for Markdown files).
- You can edit only one file at a time;
saving the change requires you to use the "Commit" button at the bottom of the page.
This effectively saves, stages, and commits all in one step.
- Buttons to the top right of the file browser allow you to "Create a new file" and "Upload files".
- To change the name or location of files
(e.g., folder in which they are located),
click on the pencil icon.
The file name will appear in a modifiable text box near the top of the screen.
You can add slashes in that path to create folders,
or backspace at the beginning of the box to move the file to a higher level in the project structure.
This only works for text files, however;
other types of files will need to be organized in your local repository.

Once you've committed your change,
go back to GitHub Desktop.
The button in the top right will now read "Fetch origin".
Click this button so the software can compare the local and remote repositories.
The button will change to read "Pull origin",
with the number in the bubble indicating how many commits will be added to your local repository.
Click the button to synchronize the two repositories,
and check to see that your change is now found in your local version.

> #### Challenge-push
- Commit a change in your remote repository
- Without pulling the remote changes,
commit a change in your local repository.
- What happens when you try to push,
and why?

If you've decided you don't want a repository published on GitHub any longer,
you can delete it in your web browser by accessing the "Settings" tab near the top right of its GitHub page.
Scroll to the bottom of the page to the section labeled "Danger Zone",
and follow the instructions to delete it.
Note that you can't undo a repository deletion on GitHub,
although deleting the repository on GitHub does *not* affect your local copy.


## Collaboration through forking

* Example repository: https://github.com/fredhutchio/guacamole
	* have default branch set to month and year for class
* issues
	* way to interact with developers about their code, request new features, report bugs
	* anyone with GitHub account can post issue
	* not always appropriate to ask questions about how to use software (see other documentation, Google groups, etc)

> #### Challenge-issue
Create an issue in the `guacamole` repository suggesting how to improve the recipe.

* fork repository
	* this repository is owned by fredhutchio (GitHub organization)
	* you don't have permission to work directly with the repository
	* click "fork" button in the upper right hand corner of repo
	* this creates a copy of the repository of your own that is connected with the original, but which you can edit yourself
	* relate back to branches
* edit ingredients.txt to include additional ingredients
* create new file called recipe.txt to include steps in process to making guac
* compare with original version in fredhutchio
	* can choose additional comparisons (e.g., other people, or other branches)
	* create pull request (PR): way to request that original repo will accept your changes
	* text editing options, linking people, issues, etc
	* PR etiquette: explain sufficiently the changes and why; be polite
* Challenge: pair up with a partner and create pull request (PR) to send your changes to their repo
	* when comparing, your repo will be on the left and their repo will be on the right
	* don't worry yet about approving pull request


## Resolving conflicts

* instructor looks at PRs submitted to original guacamole repo
	* accept one of the PRs, modeling how conversation might take place
	* find another that causes a conflict
	* must resolve conflicts before merging new changes
	* multiple ways to accomplish this: through web app, or in local repo with Desktop app
	* each file must be handled; remind about how differences in files are reported
	* for code, it matters a lot that extra added characters (>>>>> and <<<<<) are removed
* review commit history, contributors, etc
* Challenge: reconcile changes to accept PR from neighbor's repo


## Collaborate through patches
* Challenge: try to edit Kate's wiki repo by clicking on the edit (pencil) button
	* creates new branch (patch) in own forked repo
	* "suggest changes" seamlessly integrates branch (patch) with PR to original repo


## Open science

* relate to reproducibility: more open means more citation and reuse
* a repo as a unit of a manuscript; README includes link to final paper
* can use version control as electronic lab notebook for computational work
* licensing:
	* found in LICENSE or LICENSE.txt
	* dictates how materials can be used
	* additional resources for choosing a license, etc
	* you have accepted licensing associated with software already (every time you use something!)
* web hosting
	* example: http://www.fredhutch.io, click "GitHub Project" in left menu to see code
	* .io suffix
	* gh-pages


## Wrapping up

Today, we explored the use of GitHub to publish our own code/data,
as well as how to contribute to someone else's repository using GitHub.
The [GitHub.com help documentation](https://help.github.com/en/github) includes additional examples and illustrations for the tasks we covered today (and more!).
