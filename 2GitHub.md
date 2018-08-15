# Introduction to Git and GitHub: GitHub

* XKCD comic: https://xkcd.com/1296/

## Objectives

* review previous week's materials
* today's objectives:
	* differentiate between local and remote repositories
	* use GitHub to publish your own code/data
	* contribute to someone else's repository using GitHub

## Introduction to GitHub

* Github is cool because collaboration!
* we've been working in local repo, so we're the only ones who can see our work
* GitHub is a remote repo that can be published for other folks to see
* log in to GitHub, click icon in top right corner, create repo called “planets”
* resulting page has info about configuring repository, it's done the mkdir planets, cd planets, git init process remotely
* connect the two repos: copy https url to clipboard
* go to local repo (in shell): git remote add origin https://github.com/k8hertweck/planets
* git remote -v: check that it worked
* origin is a nickname for remote repo
* now send local changes to remote repo: git push origin master
* check remote repo, changes should be there.
* create README file and add brief comment about the purpose of the materials, commit change, go back to terminal: git pull origin master

## Collaborating

## Conflicts

## Branching

## Open science

* can use version control as electronic lab notebook for computational work
* more open means more citation and reuse

## Hosting

* where to put code and data?
* can do this yourself by purchasing domain and paying ISP to host
* can also use public service
* includes web interface, plus other functionalities: ability to collaborate, get DOI, academic folks can get free private repos for education 

## Licensing

* adding license and citation info
* choosing licenses
* licensing vs. social expectations

## Wrapping up

* review today's objectives
* preview next week: optional, but need additional tools if coming
* link to comment box
