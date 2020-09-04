## General tips
This note only gives an introduction to the basic usage of most common commands. For more detailed info about the other Git commands and other options of the given commands, please refer to [the full official documentation](https://git-scm.com/docs).

For basic understanding of Git, refer to [this section in the Pro Git book](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F) and [this tutorial in Git documentation](https://git-scm.com/docs/gittutorial).

`--`: option to explicitly separate command-line options from the list of files (useful when filenames start with -).

You can refer a commit (or revision) by its hash, its tag, HEAD (tip of current branch), FETCH_HEAD  or `<rev>^`, `<rev>^^`, `<rev>^2` (second parent), `<rev>~3` (first 3rd-generation ancestor), etc.  

You can use the name of a branch to refer to its head.

Commit1 is reachable from commit2 if: (1) commit1==commit2; (2) commit1 is an ancestor of commit2.


## Create or clone a repo
`git init`: create an empty Git repository (a .git directory) under the current directory.

`git clone <repository_url>`: clone a Git repo from a remote URL (preferably https URL).


## Snapshotting
`git add <pathspec>`: add files from the working tree to the staging area (also named the index).

`git add -p <pathspec>`: interactively add *part of the changes* to files in the working tree to the index.

`git reset <paths>`: copy files from HEAD to the index (opposite to add, revert staging made by add).

`git reset <commit>`: reset the current branch to the given commit. Also reset the index but not the working tree by default (more options available). The default value of `<commit>` is HEAD. If the given commit is not HEAD, it will *remove all later commits* from this branch, so use it carefully.

`git rm [-r] [--cached] <file>`: remove files from the working tree and the index. Using `[-r]` to remove directories recursively. The files removed will not be included in the next commit (but previous commits are not affected). When `[--cached]` is used, files are removed from the index but not from the working tree.

`git mv <options> <args>`: the git version of mv.

`git commit -m <msg>`: commit the current index with a commit message.

`git commit -a -m <msg>`: commit all the modified files with a commit message (do not need to do `git add` first).

`git commit --amend`: amend the last commit, adding new changes and/or change the commit message.

`git tag -m <msg> <tagname> <commit>`: add annotated tag name to the given commit, with a tag message.


## See current status and history
`git status`: show differences between: (1) the staging area (the index) and the current HEAD commit; (2) the working tree and the index.

Git DAG (part of Git Cola, run using krunner): a GUI program showing the history of commits in a DAG.

`git log --stat`: show the complete log of the repo with diff stats.

`git log <commit1>..<commit2> --stat`: show the log of commits reachable from commit2 but not reachable from commit1. When any of the commit parameter is missing, it is defaulted to HEAD.

`git log <commit1>...<commit2> --stat`: show the log of commits reachable from either commit1 or commit2 but not both (hence symmetric). When any of the commit parameter is missing, it is defaulted to HEAD.

`git show <commit>`: show log and diff of a commit.

`git diff [<paths>]`: show the difference of the working tree and the index. When paths is given, only show the difference of that path (the same in the following).

`git diff --cached [<paths>]`: show the difference between the index and HEAD.

`git diff <commit1> <commit2>`: show the difference between commit1 and commit2, treating commit1 as base (usually the older one).


## Branching and merging
`git branch <branch_name> [<start-point>]`: create a new branch whose head points to `<start-point>`. The starting point is current HEAD if not given.
git branch: list existing branches.

`git checkout <branch_name>`: switch to the given branch, also updating the working tree and the index.

`git branch -d <branch_name>`: delete a fully-merged branch.

`git branch -D <branch_name>`: delete a branch regardless of its merge status.

`git merge <commit>`: add the changes from the given commit (e.g. head of a branch) into the current branch since the divergence point. If conflicts exist, it is recommended to use GUI instead of CLI to do the merge.


## Collaborating using remote server
`git pull`: pull the changes of the current branch from default upstreaming remote. Equivalent to fetch+merge. Should first commit local changes in the working tree.

`git pull origin <branch_name>`: pull the changes of the given branch from the default upstreaming remote. `git fetch` and `git push` also have this option. Should first commit local changes in the working tree.

`git fetch`: fetch the changes of the current branch from remote and generate FETCH_HEAD, but do not merge it.

`git merge`: merge FETCH_HEAD to the current branch.

`git push`: update the current branch of the remote origin.

