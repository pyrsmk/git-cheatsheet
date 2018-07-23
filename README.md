My very own git cheatsheet and aliases
======================================

Working tree
------------

- `git status --short --branch` : short version of 'git status'
- `git checkout -- <file>` : discard changes on file
- `git reset <commit>` : move your HEAD pointer to another commit
- `git reset HEAD~1` : revert changes to the last commit
- `git reset --hard` : discard all changes against the HEAD pointer
- `git reset --hard <commit>` : move your HEAD pointer to another commit and discard all changes
- `git reset --keep <commit>` : move your HEAD pointer to another commit and preserve changes
- `git clean -fd` : remove all untracked files/directories from the working tree
- `git clean -fdx` : same as before but include ignored files
- `git reset HEAD <file>` : remove file from stage

Comparing
---------

- `git diff HEAD [file]` : compare the working directory with HEAD
- `git diff [file]` : compare the working directory with the index
- `git diff --cached [file]` : compare the index with HEAD
- `git diff <commit> <commit> [files]` : compare files from two commits

Committing
----------

- `git add --patch` : review each file before adding it to the index
- `git add -A; git rm $(git ls-files --deleted) 2> /dev/null; git commit --no-verify -m "WIP"` : commit all current changes into a WIP commit
- `git log -n 1 | grep -q -c 'WIP' && git reset HEAD~1` : undo a previous WIP commit
- `git rebase -i <commit>` : interactive rebase from a specified commit

Fixing
------

- `git reset HEAD^ <file>` : remove file for the previous commit
- `git commit --amend` : re-apply the last commit
- `git add -A && git commit --amend --no-edit` : add files to the last commit
- git rm --cached -r . && git diff --cached --name-only -z | xargs -0 git add && git commit -m 'Fix CRLF' : fix Windows CRLF

Branching
---------

- `git branch --list` : list branches
- `git branch -a` : list local and remote branches
- `git checkout --track origin/<branch>` : track a remote branch in local
- `git branch -m <newname>` : rename the current branch
- `git branch -m <oldname> <newname>` : rename a branch from any other branch
- `git push --force-with-lease` : push force but before it checks that your local copy is up-to-date
- `git push --set-upstream origin $(git branch | grep \* | cut -d " " -f2)` : avoid specifying origin on the first push
- `git branch -D <branch>` : remove a local branch
- `git push origin --delete <branch>` : remove a remote branch
- `git merge --no-edit <branch>` : merge a branch into the current one without popping the editor

Browsing
--------

- `git show <commit>` : show what changes a commit has made
- `git log -p <file>` : commit log with diff for a file
- `git log -S<word>` : search for a word into the commit tree
- `git log --pretty=format:'%C(blue)[%cn] %ai%n  %C(yellow)%h %C(reset)%s %C(cyan)%d'` : beautiful and easy-to-read commit log
- `git show --pretty="" --name-only <commit>` : list modified files in that commit
- `git log --follow <path>` : list all commits that have modified that file
