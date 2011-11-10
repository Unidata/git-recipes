# Git Basics

If you are coming from an SVN or CVS world, one concept you will have to understand immediately is that those version control systems conflate commit and publication. When you do an SVN commit, you are not only committing your work to the version control system, but you are also *sharing* it with the rest of the world. Distributed version control systems like git decouple the notion of commit and publication. Having made that contrast with earlier version control systems, here are a few tips on getting you going with git and github. Note that we are just scratching the surface here. Please take an afternoon to read [Progit](http://progit.org "Progit") or [Version Control by Example](http://www.ericsink.com/vcbe/index.html).

First you will have to [install a git client on your machine](http://progit.org/book/ch1-4.html "Installing Git"). There are also various git GUIs (like [egit for eclipse](http://eclipse.org/egit/)), but this document will initially focus on interacting with git from the command line.

This is usually the point at which people have trouble with their SSH keys which github requires to establish secure connections. Please [see instructions here](http://help.github.com/mac-set-up-git/) for setting up your SSH keys. If you are on OSX and want to include your github password on your keychain so that you do not have to authenticate when pushing, see [here](http://samuel.kadolph.com/2011/03/store-your-git-https-passwords-in-your-os-x-keychain/).

In order to view and contribute to a project hosted at github you must first clone it. Also, [please obtain a github login](https://github.com/signup/free) and let Julien know your login name.

		git clone git@github.com:Unidata/IDV.git

If the project is large, this may take a little while. For the IDV this initial clone may take ~5 minutes.

You now have the complete repository on your local system, and you are ready to start working on your project. To make sure your repository has been cloned. Try typing 

		git log --stat

Note that to commit files to git, you do not need to be connected to the Internet. You have the complete repository in your local file system. (We will talk about how to share your contributions later.)

Make a modification to a file (e.g., README) in your newly cloned repository. Now try

		git status
				
This command yields:

		# On branch master
		# Changes not staged for commit:
		#   (use "git add <file>..." to update what will be committed)
		#   (use "git checkout -- <file>..." to discard changes in working directory)
		#
		#	modified:   README
		#
		no changes added to commit (use "git add" and/or "git commit -a")
				
This is saying that the file is in the repository, but it has been modified and not committed to the repository.

You can commit that change to repository with

		git commit -m "Added stuff" README
		
Now perhaps you would like to work on a new file. Try editing a new file (e.g., stuff.txt). You will first have to add that file to the repository

		git add stuff.txt
		
Now commit your new file as described above.

At this point,  you are ready to share your committed work with the world

		git push

This command will push out your changes to github for others to see.

## Branching and Merging

A very common operation in git is to branch. Branches and merges in git have almost no cost associated to them so they are done very frequently. Typically, when you are working on a new feature, fixing bugs, or experimenting with code, you will create a new branch. In order to create a branch and start working on that branch.

		git branch my-experiment
 		git checkout my-experiment

You can list the branches that are available to you with

 		git branches

When you have made a number of commits to your branch and you are ready to bring those changes back into the trunk or a "bigger branch", you will

		git checkout other-branch
		git merge my-experiment
		
As you get more comfortable with branching and merging, you will eventually want to learn how to [re-write commit history](http://progit.org/book/ch6-4.html) before you share your changes to the world. This may seem like an esoteric feature, but it actually really nice when sharing your work with the world.

When you are done with a branch and have merged your changes

		git branch -D my-experiment

## Other useful git commands

### configuration

The .gitconfig file is the place where you set up git customizations (e.g., aliases, etc). Here is an example of a .gitconfig that lives in your home directory

		[user]
				name = Tommy DeVito
				email = Tommy.DeVito@goodfellas.com
		[core]
				editor = emacs -nw
		[diff]
				external = ~/git/bin/meldwrapper.sh


### ignore

The .gitignore files instructs git to ignore certain types of files, for example, ~ emacs files. Here is an example of a .gitignore file which lives at the top of the git repository

		#java specific
		*.class

		## generic files to ignore
		*~
		*.lock
		*.DS_Store
		*.swp
		*.out

### diffs

As with any version control system, it is often necessary to see differences between different versions of files or commits. git offers a lot of flexibility in this area, but here are some simple scenarios:

#### diffing a file has been modified but not committed

		git diff [file]

#### diffing between two commits

		git diff [SHA1] [SHA1]

Note that if you want a more attractive visual diff, you will have to configure the diff program of your choosing in your .gitconfig

### Better log output

git log is very powerful. Here is a [nice alias](http://pyrtsa.posterous.com/aligning-your-git-logs) to make git log a bit easier to view.

### Undoing stuff

First a word of warning. Do not undo commits have already been pushed out (to github)! With that out of the way, sometimes it is necessary to undo local commits (for example if you wish to improve your commit messages). To undo your last commit:

		git reset --soft HEAD^

If you wish to go back to an arbitrary commit, first do a git log, then

		git reset --soft [SHA1] 
			
This is useful when working on a local branch and you want to squash a bunch of trivial commit into one meaningful commit that you wish to share with the world.

### Going back to a previous commit

Sometimes you want to go back and look at an old commit. First do a git log to find the SHA1 of the commit you are interested in. Then

		git checkout [SHA1] 

When you are done, and want to go back to the current commit

		git checkout master

## svn git mappings

<table>
<tr><th>svn command</th><th>git command</th></tr>
<tr><td>svn checkout url</td><td>git clone url</td></tr>
<tr><td>svn update</td><td>git pull</td></tr>
<tr><td>svn diff</td><td>git diff</td></tr>
<tr><td>svn status</td><td>git status</td></tr>
<tr><td>svn revert path</td><td>git checkout path</td></tr>
<tr><td>svn add file</td><td>git add file</td></tr>
<tr><td>svn rm file</td><td>git rm file</td></tr>
<tr><td>svn mv file</td><td>git mv file</td></tr>
<tr><td>svn commit</td><td>git commit file; git push</td></tr>
<tr><td>svn log</td><td>git log</td></tr>
</table>

## Collaborative work flows

When working with external collaborators, you will want to use github to facilitate this process. In particular, the collaborator will navigate to a github project page and **fork** the project (with the fork button) into their github account. 

At this point, the collaborator will *clone their fork* and work in their forked environment for a while. Once the collaborator is ready to contribute back to the project they will submit a **pull request** via github. Again, note the *pull request* button. This will initiate a github process where the collaborator can add information about  their contributions. Once the pull request is submitted, the project owner will receive a message concerning a pull request submitted by the collaborator. This is your opportunity to preview the request via github. Note that an open pull requests have a discussion area for you and collaborator to communicate about their contributions.
