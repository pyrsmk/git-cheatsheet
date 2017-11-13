My very own git cheatsheet and aliases
======================================

Working tree
------------

- `git reset <commit>` : move your HEAD pointer to another commit
- `git reset --hard` : discard all changes against the HEAD pointer
- `git reset --hard <commit>` : move your HEAD pointer to another commit and discard all changes
- `git reset --keep <commit>` : move your HEAD pointer to another commit and preserve changes
- `git clean -f` : remove all untracked files from the working tree

Commits
-------

- `git add --patch` : review each file before adding it to the index
- `git commit --amend` : rename the last commit
- `git add -A; git rm $(git ls-files --deleted) 2> /dev/null; git commit --no-verify -m "WIP"` : commit all current changes into a WIP commit
- `git log -n 1 | grep -q -c 'WIP' && git reset HEAD~1` : undo a previous WIP commit

Branches
--------

- `git checkout --track origin/<branch>` : track a remote branch in local
- `git branch -m <newname>` : rename the current branch
- `git branch -m <oldname> ≤newname>` : rename a branch from any other branch
- `git push --set-upstream origin $(git branch | grep \* | cut -d " " -f2)` : avoid specifying origin on the first push
- `git push origin --delete` : remove a remote branch
- `git merge --no-edit <branch>` : merge a branch into the current one without popping the editor

Browse
------

- `git log -S<word>` : search for a word into the commit tree
- `git log --oneline --decorate --graph --pretty=format:'%C(yellow)%h%Cred%d %C(reset)%s %C(green)(%cr) %C(blue)[%cn]` : commit log
