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
* examining an example repository: https://github.com/fredhutchio/git_github_intro


## Publishing a local repository

* using repository from last week, review Git workflow using Desktop app (can use Kate's if you deleted yours)
* create remote repository
	* on GitHub profile page, click Repositories tab
	* click green button to create new repository
	* name (same as existing local repo)
	* leave all other options as default
	* this has created and initialized remote but empty repo
* connect the local and remote repos
	* click button to "set up in Desktop"
	* opens app
	* locate appropriate local repository
	* "push" sends all local changes to remote repo
* view repo on GitHub
	* may need to refresh page
	* locate history and compare to desktop app
	* make change and commit
* back to Desktop app
	* "pull" grabs any changes from GitHub and adds to local repository
* deleting a repository (if desired)


## Collaborating

* https://github.com/fredhutchio/guacamole
* issues
	* what are they, who can use, how?
* fork repository
	* this repository is owned by fredhutchio (GitHub organization)
	* you don't have permission to work directly with the repository
	* click "fork" button in the upper right hand corner of repo
	* this creates a copy of the repository of your own that is connected with the original, but which you can edit yourself
	* relate back to branches
* edit ingredients.txt to include additional ingredients
* create new file called recipe.txt to include steps in process to making guac
* compare with original version in fredhutchio
* can choose additional comparisons (e.g., other people)
* create pull request (PR)
* PR etiquette


## Conflicts

* Kate demo: accept one of the PRs, then try to accept another
* if they don't match, there is a conflict that must be managed


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
	* example of fredhutch.io webpage 
	* .io suffix	
	* gh-pages
* demo git integration with RStudio

	
## Wrapping up

* review today's objectives
* preview next week: optional, but need additional tools if coming
* link to comment box
