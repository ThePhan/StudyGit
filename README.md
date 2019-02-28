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
  - Undo Stash: git checkout '<version-commit>'
