# Introduction to Git and GitHub
# Class 2: GitHub

## Objectives

In the last class,
we used the GitHub Desktop application to work with version control on our own computers by creating repositories,
tracking changes using the basic Git workflow (modify-add-commit),
exploring history,
and ignoring files.

Today, we'll transfer this knowledge to remote repositories in GitHub.
By the end of this class,
you should be able to:

- differentiate between local and remote repositories
- use GitHub to publish your own code/data
- contribute to someone else's repository using GitHub


## Introduction to GitHub

Now that you have some experience with version control using Git,
you may be able to appreciate this cartoon from [XKCD](https://xkcd.com):

![XKCD Git](https://imgs.xkcd.com/comics/git_commit.png)

In our previous class,
we focused on git for local repositories,
or version control for files and directories located on our own computers.
In this class,
we'll expand our understanding of version control to include working with remote repositories vit GitHub.

GitHub is a web-based platform for sharing and collaborating with code and data.

- private vs public repos
- log in not necessary to view public repos
- when logged in, can see timeline/newsfeed
- starring repositories, following people
- settings on personal page
* GitHub organizations: fredhutch, fredhutch.io
	* email scicomp to get added to fredhutch github organization
	* interact with wiki
	* can be added to private repositories
	* teams: groups that can be used to manage permissions
* examining an example repository:
	* this course: https://github.com/fredhutchio/git_github_intro
	* research project (manuscript): https://github.com/rasilab/machkovech_2018
	* software project: https://github.com/tidyverse/ggplot2


## Publishing a local repository

* using repository from last class, review Git workflow using Desktop app (can use instructor's if you deleted yours)
* Use "Publish repository" button in center of app to initialize new repo in GitHub
	* uncheck "keep code private"
* view repo on GitHub; locate history and compare to desktop app
* commit another change locally through Desktop app and push
	* "push" sends all local changes to remote repo
	* will need to refresh remote repo page to see changes
* commit a change to remote repo
	* altering files
	* creating files
	* moving files
	* creating directories
* back to Desktop app to pull changes from remote repo
	* "pull" grabs any changes from GitHub and adds to local repository
	* view history for different change types
* can also create remote repository on GitHub and connect locally (but this takes more steps)
* Challenge: commit a change in remote repo, commit change in local repo, try to push
* deleting a repository (if desired)
	* settings
	* scroll to bottom, "Danger Zone"
	* delete repo, must type title of repo, no going back (unless you have a local copy of the repo)

## Collaboration through forking

* Example repository: https://github.com/fredhutchio/guacamole
	* have default branch set to month and year for class
* issues
	* way to interact with developers about their code, request new features, report bugs
	* anyone with GitHub account can post issue
	* not always appropriate to ask questions about how to use software (see other documentation, Google groups, etc)
* Challenge: create issue
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

* short demo of Git Kraken, RStudio interface, Atom
