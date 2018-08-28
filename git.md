# Misc git stuff

* To checkout a file from another branch (`develop` in this case) run:
  * `git checkout develop -- FILES TO CHECKOUT`
* Delete remote branch
  * `git push --delete REMOTE BRANCH`
* Get sha of a commit
  * `git rev-parse COMMIT`
  * > `COMMIT` can be a branch (local or remote) or any index of `HEAD` (e.g.
    `HEAD^^^`)
* Show what a commit changed:
  * `git diff COMMIT~ COMMIT`
  * > can modify `~` etc to change range.
* Show diff between branches [for certain files]
  * `git diff BRANCH [-- FILEA FILEB]`


* To remove branches on remote `git push REPO --delete BRANCH`
* Find files `git ls-files [PATTERN]`
