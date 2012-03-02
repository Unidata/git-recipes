Unidata Git FAQ.

Dangerous commands (e.g. you can lose your work) are labelled ⚠.

Q: How do I list all files touched since a certain commit?

A: git diff --name-only [commit]

Q: How do I list my remote branches?

A: git remote -v

Q: How do I add a remote branch?

A: git remote add test git://github.com/user/test.git

Q: How do I delete a remote branch?

A: git remote rm <branch>

Q: How do you remove untracked files from your git working copy?

A: ⚠  git clean -f -d

Q: How do I delete a branch?

A: git branch -d [branch]

Q: How do I resolve a merge conflict?

A: git mergetool
