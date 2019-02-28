# GITHUB

## GITIGNORE in global:
- Link reference: https://kipalog.com/posts/Meo-phot-lo-files-o-cap-global-cua-git
  + command: git config --global core.excludesfile '~/.gitignore'

## GIT ADD: Have 3 type
  - Link reference: https://kipalog.com/posts/3-bien-the-cua--git-add
    + command: git add .
      * Add all file have changed
      * Add all new file
    + command: git add -U
      * Add all file have changed
      * Add all file have removed
    + command: git add -A (or --all)
      * Add all file have changed
      * Add all new file
      * Add all file have removed

## Show list of all file have change
  - Link reference: https://kipalog.com/posts/Meo-thao-tac-voi-thay-doi-voi-git-add
    + command: git add . --patch

## Delete the old branch have merged into master
  - Link reference: https://kipalog.com/posts/Git---Cach-xoa-nhanh-tat-ca-cac-branch-cu-da-merge-vao-branch-master
    + command: $ git branch --merged | grep -v "\*" | xargs -n 1 git branch -d

## ??
  - Link reference:
    + command: git merged --quash (or git merged --squash --edit)

# GIT COMMIT
  - Link reference: ...
## already edited code but not add
  - command
    + git clean -df
    + git checkout -- .
## already add but not commit
  - command
    + git reset HEAD
    + git clean -df
## already commit but not push
    + command: git reset HEAD~1 --hard
    ### More reference
    git reset does know five "modes": soft, mixed, hard, merge and keep. I will start with the first three, since these are     the modes you'll usually encounter. After that you'll find a nice little a bonus, so stay tuned.

  # soft
- When using git reset --soft HEAD~1 you will remove the last commit from the current branch, but the file changes will stay in your working tree. Also the changes will stay on your index, so following with a git commit will create a commit with the exact same changes as the commit you "removed" before.

# mixed
This is the default mode and quite similar to soft. When "removing" a commit with git reset HEAD~1 you will still keep the changes in your working tree but not on the index; so if you want to "redo" the commit, you will have to add the changes (git add) before commiting.

# hard
When using git reset --hard HEAD~1 you will lose all uncommited changes in addition to the changes introduced in the last commit. The changes won't stay in your working tree so doing a git status command will tell you that you don't have any changes in your repository.

Tread carefully with this one. If you accidentally remove uncommited changes which were never tracked by git (speak: committed or at least added to the index), you have no way of getting them back using git.

##Bonus
# keep
- git reset --keep HEAD~1 is an interesting and useful one. It only resets the files which are different between the current HEAD and the given commit. It aborts the reset if anyone of these files has uncommited changes. It's basically acts as a safer version of hard.

- This mode is particularly useful when you have a bunch of changes and want to switch to a different branch without losing these changes - for example when you started to work on the wrong branch.

You can read more about that in the git reset documentation.

# Note
When doing git reset to remove a commit the commit isn't really lost, there just is no reference pointing to it or any of it's children. You can still recover a commit which was "deleted" with git reset by finding it's SHA-1 key, for example with a command such as git reflog.
## already push
    + command: git revert HEAD~1..HEAD
=======
# GIT COMMIT
## already edited code but not add
  - command
      + git clean -df
      + git checkout -- .
## already add but not commit
  - command
      + git reset HEAD
      + git clean -df
## already commit but not push
      + command: git reset HEAD~1 --hard
## already push
      + command: git revert HEAD~1..HEAD

## Reset commit: delete all commit fail
  - Link reference: ...
    + command: git reset hashid
  - Or
    + command: git reset --hard HEAD^ (HEAD^ == HEAD~n (n = 1....n))
      * --hard: Delete commit and all file already changed but not commit
      * --soft: Delete commit, and still save already changed but not commit for times commit continue

## --amend command: edit commit massage
  - Link reference
    + command: git commit --amend -m"content need change"
  - If want add file but don't want edit commit:
    + command: git commit --amend --no-edit

## Delete file have commit into Repo
  - Link reference
    + command: git rm --cached <file name>
  * Add file into gitignore after remove:
    + command: echo "<file name>" >> .gitignore

## Change branch name
  - Link reference
    + command: git branch -m <new branch name>

## git stash
  - Link reference:
    + command: git stash
  - Show list stash:
    + command: git stash list
      * Example: stash@{0}: WIP on master: 051caab Delete file try.js
      *     stash@{1}: 
  - Apply one stash. Ex: stash@{0}.
    + command: git stash apply stash@{0}
  - Apply all stash
    + command: git stash apply
  - Delete one stash
    + command: git stash prop stash@{1}
  - Delete all stash
    + command: git stash clear
## Rebase and merge
  - Delete all stash
    + command: git stash clear
## Rebase and merge
  - Link reference: https://github.com/AsianTechInc/AST-ruby-code-review/issues/9
  
## Show list 'Stash' was clear:
  - cmd: git fsck --unreachable | grep commit | cut -d ' ' -f3 | xargs git log --merges --no-walk --grep=WIP
  - Undo Stash: git checkout 'version-commit'
