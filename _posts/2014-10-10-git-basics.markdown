---
layout: post
title:  "Git basics"
date:   2014-10-10 03:24:54
categories: update
---


Git basics
----------------------

About Git
----------------------

- Version Control
- Collaboration Tool

Some terminology
------------------------

Repo: Short for "repository", or "that place where all the stuff is"

(Editor's note, I looked up the definition of 'repository', to make sure I had a better definition and I got "a place, building, or receptacle where things are or may be stored." This really isn't much better.)


Version control
------------------------

- Store revisions of files
- Every 'save' increases the revision by '1'
- Stores all the changes so a user can *revert* to older versions

- There are many types of version control
	- Git
	- SVN
	- Mercurial
	- CVS

Collaboration Tool
------------------------

- Two people can edit the same or different files
- They then 'save' those changes to the git repo
- The repo will automatically try to merge the files together
- Once the files are merged, others can download the new, combined version

**Allows for people to work remotely and quickly**

Git
-------------------------------

- Distributed version control
	- All parties are not checking into a central 'repo' all the time

Git Repo
-------------------------------

- Always need a local repo to check your changes into

Commits
-------------------------------

- Is the equivalent of 'saving' in GIT
- Each 'commit' adds all your local changes to the repo...
- Try to commit whenever you've made a major change that seems to be working
- **COMMITS ARE LOCAL TO YOUR MACHINE ONLY**

Adding changes
--------------------------------

- All new files and **files that were changed since the last commit** need to be 'added' to the commit
- This adds them to the *staging* area
- Files in the staging area are not yet saved to the repo, but will be when you run a commit

Pushing changes
--------------------------------

- Once you have **added** your changes 
- And **committed** your changes to you local repo
- One can then **push** these changes to a **remote repository**
- This can be used to share your code with other people
	- A la 'github'


Getting remote repos - Clone
---------------------------------

- If you want to use some code in a GIT repo, one will need to **clone it** first
- This will copy all the files in that repo to your hard drive

PULL/FETCH
----------------------------------

- Getting later changes to the code
- If the code in the remote repo changes, **PULLING** the repo will update all your code
- It will only download the changed files

Merging
------------------------------------

- Should you make changes in a file, and another collaborator changes the file too, you will need to **merge** those changes into one accepted file.
- This is usually a manual process, and requires that you do a fetch/pull before pushing your changes


Getting our own remote repo
----------------------------------------

Can set up on your own web server

Find a hosting provider

	- GitHub
	- Bitbucket
	- Stash
	- SourceForge

We'll be using GitHub

Github
-----------------------------------------

- One of the larger open source repository hosts
- Runs on git, as one might assume
- [Github](https://github.com/)
- Go ahead and sign up for an account


Working with Git
---------------------------------------------

We could do all this on the command line...

![Git command line]({{ site.baseurl }}/assets/img/git/gitcmd.png)

PHPStorm (thankfully) has built-in tools.

Making a new repo
--------------------------------------------

Click on the 'new repo' button on the Github web interface

![New repo button]({{ site.baseurl }}/assets/img/git/newGit.png)

Fill in the repo name, click create

![New repo info]({{ site.baseurl }}/assets/img/git/newRep2.png)

Take note of the git repo's URL:

![New repo info]({{ site.baseurl }}/assets/img/git/newRep3.png)


Getting that repo onto your computer
-------------------------------------------

![New repo info]({{ site.baseurl }}/assets/img/git/cloning1.png)

- Vcs ->checkout from source control -> git

![New repo info]({{ site.baseurl }}/assets/img/git/cloning2.png)

- Paste the URL

![New repo info]({{ site.baseurl }}/assets/img/git/cloning3.png)

**UNCHECK THE .IDEA DIRECTORY**


Adding something to your repo
--------------------------------------------

- Open up the folder you just made in a plaintext editor (like Dreamweaver)
- Make a new file in the folder, with the name "README.md"
- Edit that file to say "Hello world"
- Save the file

![New repo info]({{ site.baseurl }}/assets/img/git/commit1.png)

- Go to vcs->git->commit file (or vcs->commit chnages)

![New repo info]({{ site.baseurl }}/assets/img/git/commit2.png)

Select the files you want to commit and click the commit button


Pushing to your remote repo
-----------------------------------------------



![New repo info]({{ site.baseurl }}/assets/img/git/push1.png)

vcs->git->push

![New repo info]({{ site.baseurl }}/assets/img/git/push2.png)

Select your must recent commit and click 'push'.


Making changes
-----------------------------------------------

Let's go ahead and simulate someone else making a change to the readme. Click on the README file in the github web interface, then click 'edit'.

(AS A NOTE: THIS IS ONLY FOR DEMONSTRATION PURPOSES. YOU SHOULD NOT BE CODING IN THE WEB INTERFACE.)

![New repo info]({{ site.baseurl }}/assets/img/git/edit.png)

Change the text inside the file to say "Just a test". Scroll down and click "commit changes"

![New repo info]({{ site.baseurl }}/assets/img/git/edit2.png)

*Now, return to your text editor** and change that same readme file to say "This is a local change". Stage and commit this change.


Pulling (and merging)
-----------------------------------------------------

Now we have a problem. Our local file is different than our remote. And our local GIT repo is one (or more, really) commits behind the remote master. This means before we can **push** our changes to the master repo, we need to get all the updated code from the remote by  (**pulling** them down).

- Head into source tree and click 'push'

![New repo info]({{ site.baseurl }}/assets/img/git/pull.png)

You will get an error saying your 

- Head into source tree and click 'pull'

![New repo info]({{ site.baseurl }}/assets/img/git/pull.png)

- We have errors!
- We need to manaully *merge* our files

- Open up 'README.mkdn', it will look something like this:

![New repo info]({{ site.baseurl }}/assets/img/git/unmerged.png)

Edit this file so it just says, "This is the merged file" (nothing else)

- Return to source tree
- Right-click on the file marked with an issue
	- You have three possible options to resolve this issue:
		1. Resolve with 'theirs' (KEEPS THE REMOTE VERSION, OVERWRITES YOUR CHANGES)
		2. Resolve with 'mine' (KEEPS YOUR VERSION, OVERWRITES REMOTE CHANGES)
		3. Mark as resolved (keeps your local version that you have edited, like we just did)
- Go ahead and click 'mark as resolved'
- *Note that your file has been moved into the staged changes area*
	- This means we need to commit again
	- So commit.

- Then, click 'push'
- You will push your new, merged file back up to github
- Congrats.