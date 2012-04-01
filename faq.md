# Unidata Git FAQ.

Dangerous commands (e.g. you can lose your work) are labelled ⚠.

Q: How do I list all files touched since a certain commit?

A: `git diff --name-only 42fe678`

Q: How do I list my remote branches?

A: `git remote -v`

Q: How do I add a remote branch?

A: `git remote add test git://github.com/user/test.git`

Q: How do I delete a remote branch?

A: `git remote rm my-branch`

Q: How do you remove untracked files from your git working copy?

A: ⚠  `git clean -f -d`

Q: How do I delete a branch?

A: `git branch -d my-branch`

Q: How do I delete a remote branch?

A: `git push origin :my-branch`

Q: How do I resolve a merge conflict?

A: `git mergetool`

Q: How do I push a local branch to github

A: `git push origin newfeature`

Q: How do I rename a branch

A: `git branch -m old_branch new_branch`

Q: How do I stash (usually uncommitted) work?

A: `git stash save "work in progress for foo feature"`

Q: How can I see what is on the stash queue?

A: `git stash list`

Q: How do I unstash what I just stashed?

A: `git stash apply`

Q: How do I clear the stash list?

A: `git stash clear`

Q: How do I edit my last commit message in git?

A: Assuming you have not pushed out your changes, `git commit --amend`

Q: I am in merge conflict hell because of whitespace or EOL differences. This sometimes happens when people are committing files from different operating systems (e.g., Unix and Windows). What do I do?

A: You can try your git command with `--ignore-whitespace `. For example `git rebase master --ignore-whitespace`.

Q: How can I see what files I changed at a particular commit?

A: `git log -p -1 --name-only 49bb54a` or `git show --pretty="format:" --name-only 49bb54a`
