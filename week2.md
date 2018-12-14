# Introduction to Git and GitHub: GitHub

* XKCD comic: https://xkcd.com/1296/

## Objectives

* review previous week's materials
* today's objectives:
	* differentiate between local and remote repositories
	* use GitHub to publish your own code/data
	* contribute to someone else's repository using GitHub


## Introduction to GitHub

* differentiating between Git and GitHub:
	* local repository: only available on your own hardware (computer)
	* remote repository: available on someone else's computer and visible to other people
* overview of GitHub
	* log in not necessary to view public repos
	* when logged in, can see timeline/newsfeed
	* starring repositories, following people
	* organizations (fredhutchio as example)
	* paid accounts can have private repos (also education discounts)
	* settings on personal page
* examining an example repository:
	* this course: https://github.com/fredhutchio/git_github_intro
	* research project (manuscript): https://github.com/rasilab/machkovech_2018
	* software project: https://github.com/tidyverse/ggplot2


## Publishing a local repository

* using repository from last week, review Git workflow using Desktop app (can use instructor's if you deleted yours)
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

* review today's objectives
* preview next week: optional, but need additional tools if coming (see fredhutch.io website)
* link to comment box
