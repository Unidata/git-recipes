# Unidata Git FAQ.

Dangerous commands (e.g. you can lose your work) are labelled ⚠.

Q: How do I list all files touched since a certain commit?

A: `git diff --name-only 42fe678`

Q: How do I list my remote branches?

A: `git remote -v`

Q: How do I add a remote branch?

A: `git remote add test git://github.com/user/test.git`

Q: How do I delete a remote branch?

A: `git push origin :my-branch`

Q: How do you remove untracked files from your git working copy?

A: ⚠  `git clean -f -d`

Q: How do I delete a branch?

A: `git branch -d my-branch`

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

Q: How do I unstash a stash that is not at the top of the stash queue?

A: `git stash apply "stash@{1}"`. The double quotes can be important depending on what shell you are using. Otherwise, your shell may try to interpret the curly braces.

Q: How do I clear the stash list?

A: `git stash clear`

Q: How do I edit my last commit message in git?

A: Assuming you have not pushed out your changes, `git commit --amend`

Q: I am in merge conflict hell because of whitespace or EOL differences. This sometimes happens when people are committing files from different operating systems (e.g., Unix and Windows). What do I do?

A: You can try your git command with `--ignore-whitespace `. For example `git rebase master --ignore-whitespace`.

Q: How can I see what files I changed at a particular commit?

A: `git log -p -1 --name-only 49bb54a` or `git show --pretty="format:" --name-only 49bb54a`

Q: How do I operate on a git repository from outside the git repository?

A: `git --git-dir=/tmp/repo/.git --work-tree=/tmp/repo pull`

Q: How do I pull a remote branch into my local repository so that I can work on it?

A: `git fetch` followed by `git checkout -b my-branch origin/my-branch`

Q: How do I make git ignore mode changes (chmod)?

A: From inside your git repo `git config core.filemode false`

Q: How do I prune branches that no longer exist remotely?

A: `git remote prune`

Q: How do I view an old version of a file?

A: `git show REVISION:path/to/file`  or `git show HEAD~4:src/main.c` or `git show <sha1>:src/main.c`

Q: How do I revert or rollback multiple commits?

A: Don't muck with published history. Rather than remove the commits that are no longer needed, perform the inverse of the target commits and commit that change. Here's an example of rolling back B C D.

`A <-- B <-- C <-- D <-- [(BCD)^-1]      <-- master <-- HEAD`
- Two solutions:
  - If rolling back a series of commits:

```
git checkout -f A -- .
git commit -a -m <commit msg>
```
  - If need to select commits to roll back:

```
git revert --no-commit D
git revert --no-commit C
git revert --no-commit B
git commit -m <commit msg>
```
