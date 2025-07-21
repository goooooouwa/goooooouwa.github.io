---
title: Git tips & tricks
category: coding
tags: git
published: true
---

{{TOC}}

## Find and restore a deleted file in a Git repo

[Source URL](http://stackoverflow.com/questions/953481/find-and-restore-a-deleted-file-in-a-git-repo)

Find the last commit that affected the given path. As the file isn't in the HEAD commit, this commit must have deleted it.

`git rev-list -n 1 HEAD -- <file_path>`

Then checkout the version at the commit before, using the caret (`^`) symbol:

`git checkout <deleting_commit>^ -- <file_path>`

Or in one command, if `$file` is the file in question.

`git checkout $(git rev-list -n 1 HEAD -- "$file")^ -- "$file"`

## GIT clone repo across local file system

[Source URL](http://stackoverflow.com/questions/2519933/git-clone-repo-across-local-file-system)

This worked for me:

`git clone file:////<host>/<share>/<path>`

edit: For example, if your main machine has the IP `192.168.10.51` and the computer name main, and it has a share named code which itself is a git repository, the both of the following commands should work equally:

`git clone file:////main/code`

`git clone file:////192.168.10.51/code`

If the git repository is in a subdirectory, simply append the path.

## Change commit messages of past Git commits

[Source URL](http://makandracards.com/makandra/868-change-commit-messages-of-past-git-commits)

To change a commit message of the most recent (unpushed) commit, you can simply use

`git commit --amend -m 'new message'`

To change messages of (unpushed) commits further in the past:

`git rebase -i [COMMIT BEFORE THE FIRST YOU WANT TO EDIT]`

Mark all messages to be changed with "edit".
Git will start the rebasing and stop at every marked commit. For each of those, do a

`git commit --amend -m 'new message'git rebase --continue`

## github - How do I delete a Git branch both locally and remote?

[Source URL](http://stackoverflow.com/questions/2003505/how-do-i-delete-a-git-branch-both-locally-and-remote)

`git push origin --delete <branchName>`

## clean unstaged files in Git

`git clean -fd`

## How to grep (search) committed code in the git history?

[Source URL](http://stackoverflow.com/questions/2928584/how-to-grep-search-committed-code-in-the-git-history)

To search for commit content (i.e., actual lines of source, as opposed to commit messages and the like), what you need to do is:

`git grep <regexp> $(git rev-list --all)`

Updates: `git rev-list --all | xargs git grep expression` will work if you run into an "Argument list too long" error

## Applying .gitignore to committed files

[Source URL](https://stackoverflow.com/questions/7527982/applying-gitignore-to-committed-files)

1. Edit `.gitignore` to match the file you want to ignore
2. `git rm --cached /path/to/file`

## Git gitignore syntax

A leading slash matches the beginning of the pathname. For example, "/*.c" matches "cat-file.c" but not "mozilla-sha1/sha1.c".