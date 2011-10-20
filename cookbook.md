Here are a few tips on getting you going with git and github

First you will have to install a git client on your machine. There are also various git GUIs, but this document will initially focus on interacting with git from the command line.

In order to view and contribute to a project hosted at github you must first clone it:

		git clone git@github.com:Unidata/IDV.git

If the project is large, this may take a little while. For the IDV this initial clone may take ~5 minutes.

You now have the complete repository on your local system, and you are ready to start working on your project. Note that to commit files to git, you do not need to be connected to the Internet. You have the complete repository in your local file system. (We will talk about how to share your contributions later.)

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

		commit -m "Added stuff" README

Now you are ready to share your committed work with the world

		git push

Will push out your changes to github for others to see.

