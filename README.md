Git Subtle
---

You can use both `submodule` and `subtree` to keep track of different versions of the same directory (i.e., a code template that may change where you may want to merge in changes) within the same project using multiple branches.

The main commands of interest are:

*	`git checkout --orphan sub/${BRANCH}`
*	`git submodule add -b sub/${BRANCH} ./ ${DEST}`
*	`git subtree add --prefix=${DEST} sub/${BRANCH}`, `git subtree [push | pull] --prefix=${DEST} ./ sub/${BRANCH}`

To see an example of creating such a repository, you can run `example.sh` in this directory. It will create a repository named `example` in the current working directory, and make a setup similar to this repository.

**NOTE**: There will be an issue with relative paths and confusion with remotes... Will need to fix this.
