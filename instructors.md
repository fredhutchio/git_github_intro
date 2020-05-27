# Instructors

- Please see our [instructor repository](- Please see our [instructor repository](https://github.com/fredhutchio/instructors) for general guidelines relevant to all classes. Additional recommendations specific for this course can be found below.
- Administering challenges: Typing the challenge exercise into the HackMD is usually easiest.

## Setting up your shell for Class 3
	* enlarge text size
	* `export PS1='$ '`
	* `export PROMPT_COMMAND="history 1 >> ~/Dropbox/GitHistory.txt"`
	* share in HackMD
* check installation of command line version
	* Terminal, Git for Windows
	* `git --help` should print help documentation

## Collaborating with guacamole

The [`guacamole` repository](https://github.com/fredhutchio/guacamole)
is used for the collaboration with GitHub activities in class 2.
The following process should be completed after each course finishes,
to allow the next class to proceed without issue:

- default branch should be `master` for teaching
- branched `original` retains unaltered repo
- after class:
	- set default to `original`
	- delete `master`
	- create new `master` and reset as default
	- close all issues and PRs
- delete instructor fork of `guacamole`
