### Git Basics

Here are a few tips on getting you going with git and github. We are just scratching the surface here. Please take an afternoon to read [Progit](http://progit.org "Progit").

First you will have to [install a git client on your machine](http://progit.org/book/ch1-4.html "Installing Git"). There are also various git GUIs, but this document will initially focus on interacting with git from the command line.

In order to view and contribute to a project hosted at github you must first clone it. Also, please obtain a github login and let Julien know your login name.

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
				
This is saying that the file is in the repository, but it has been modified and not commited to the repository.

You can commit that change to repository with

		git commit -m "Added stuff" README
		
Now perhaps you would like to work on a new file. Try editing a new file (e.g., stuff.txt). You will first have to add that file to the repository

		git add stuff.txt
		
Now commit your new file as descibed above.

At this point,  you are ready to share your committed work with the world

		git push

This command will push out your changes to github for others to see.

### Branching and Merging

A very common operation in git is to branch. Branches and merges in git have almost no cost associated to them so they are done very frequently. Typically, when you are working on a new feature, fixing bugs, or experimenting with code, you will create a new branch. In order to create a branch and start working on that branch.

		git branch my-experiment
 		git checkout my-experiment

You can list the branches that are available to you with

 		git branches

When you have made a number of commits to your branch and you are ready to bring those changes back into the trunk or a "bigger branch", you will

		git checkout other-branch
		git merge my-experiment
		
As you get more comfortable with branching and merging, you will eventually want to learn how to [re-write commit history](http://progit.org/book/ch6-4.html) before you share your changes to the world. This may seem like an esoteric feature, but it actually really nice when sharing your work with the world.

### Other useful git commands

This command will undo commits. Do not do this if the commits have already been pushed!

		git reset --soft [SHA1] 
		
		
