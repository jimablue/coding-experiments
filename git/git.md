# Git
#notes/Git

Git has main states that your files can reside in: 
_committed_: data is safely stored in your local database 
_modified_: you have changed the file but have not committed yet
_staged_: you have marked a modified file in its current version to go into your next commit snapshot
_untracked_: files in working directory but not in last snapshot and not in staged
![](img/lifecycle.png)

Three main sections of a Git project:
_Working Directory_: a single checkout of one version of the project for you to use and modify
_Staging Area (index)_: a file in your Git directory that stores info about what will go into your next commit. 
_.git directory ( Repository)_ : where Git stores the metadata and object database for your project. What you copied when you clone a repo.
![](img/areas.png)

##  Local
For help
freenode.net
`git help <verb>`  `git <verb> -h`

### .gitignore

Using glob 
![](img/Screen%20Shot%202019-03-14%20at%2011.46.48%20PM.png)

### Faster with :
`git commit -a -m “comments”`
`git rm <file>`  `git mv <file>`

### Override previous commit with current stage area
`git commit --amend`

### Unstaging a staged file 
`git reset HEAD <staged file>`

### Unmodifying a modified file to last committed status
This will remove local changes irreversibly
`git checkout -- <file>` 

### git log to see commit history
`git log —pretty=oneline`

## Remote
`git fetch <shortname> <url>`  Simply downloads to local repo, have to merge manually 
`git clone` automatically sets up local master branch to track the remote master branch, add the `origin` remote for you 
`git pull	` fetches data from the server you originally cloned from and automatically tries merge it into the code you’re currently working on. 
`git push <remote> <branch>`
`git remote show <remote>` for pull/push status for local branches and remotes branches on the server that you don’t have
`git remote rename <remote> <new remote name>`
`git remote remove <remote>` 

### Tagging 
Git supports two types of tags: _lightweight_ and _annotated_ (annotated recommended) 
`git tag -a v1.0 -m “my version 1.0`
Show tag `git show v1.4`
Tag a previous commit `git tag -a v1.2 <commit checksum>`

Push tag to remote server `git push origin <v1.0 or --tags for all tags>`

Delete a tag `git tag -d <tagname>` 
on remote server  `git push origin --delete <tagname>`
Checkout a tag `git checkout <tag>` this will put you in `detached HEAD` state. In “detached HEAD” state, if you make changes and then create a commit, it is only accessible by the exact commit hash. You could create a new branch that starts with the tag
```
git checkout -b version2 v2.0.0
Switched to a new branch ‘version2
```

### Git Aliases
![](img/Screen%20Shot%202019-03-15%20at%203.53.19%20PM.png)

## Branching
#notes/Git/branching
![](img/commit-and-tree.png)
- - - -
![](img/commits-and-parents.png)
- - - -
![](img/branch-and-history.png)
- - - -
`git branch testing`	

![](img/head-to-master.png)
```
$ git log --oneline --decorate
f30ab (HEAD -> master, testing) add feature #32 - ability to add new formats to the central interface
98ca9 The initial commit of my project
```

To switch to an existing branch, you run the `git checkout` command.
`git checkout testing`
![](img/head-to-testing.png)

Do another commit 

![](img/advance-testing.png)
`git checkout master`
![](img/checkout-master.png)
It moved the HEAD pointer back to point to the master branch, and it reverted the files in your working directory back to the snapshot that master points to. 

Make another commit 
![](img/advance-master.png)
Create a branching and switch to it at the same time
`git checkout -b <newbranchname>`

List all branches (for both local and remote )
`git branch -a`

Merge the current branch to another branch
`git merge <branchname>`

Delete a branch
`git branch -d <branchname>`

A merge commit: when merging two branches that don’t share a direct ancestor 
![](img/basic-merging-2.png)

**Merger Conflicts**
Use 	`git status` to see unmerged files with conflict
the file that has conflict will have 
```
<<<< HEAD
Content on this branch
=====
Conflicting content from the branch that is merging in 
>>>>>> <branchname>
```

Pick one of the options then do `git add` to set the final version of the conflicted file and `git commit` to settle the conflict.

See branches that are already merged into the current HEAD branch
`git branch —-merged` 
see merged branches for a particular branch without checkouting the branch `git branch —-merged <branchname>`


### Remote branches
![](img/remote-branches-1.png)
`git fetch origin`

![](img/remote-branches-3.png)
Add another remote server
`git remote add teamone <url>
![](img/remote-branches-5.png)
To push local branch to remote branch
`git push <remote> <branch>`  e.g.  `git push origin master`
if you want the branch to be named differently on the remote server
`git push <remote> <local_branch_name>:<remote_branch_name>`

When you do a fetch that brings down the new remote-tracking branch, you don’t automatically get a local branch to work on, you have only an `origin/master` pointer that you can’t modify.

To merge this work into current branch `git merge origin/master`
To create a local branch based off the remote-tracking branch
`git checkout -b master origin/master`
Or simply =>  ` git checkout --track origin/master`
This local branch is called “tracking branch” and the remote branch is called “upstream branch” You can simply do `git pull` on a tracking branch to fetch from the corresponding upstream branch

Make a local branch track a upstream branch `git branch -u origin/master`
Shorthand for upstream branch is `@{u}`

See what tracking branches you have set up  `git branch -vv` ( the commits info is from the last time you fetched from the server) for updated info, fetch from all your remotes first `git fetch -all; git branch -vv`

`git pull ` in most cases is `git fetch; git merge`

To delete remote branch: `git push origin --delete master`

Rebasing 
![](img/interesting-rebase-1.png)
![](img/Screen%20Shot%202019-03-16%20at%2011.14.36%20PM.png)

![](img/interesting-rebase-2.png)
In general the way to get the best of both worlds is to rebase local changes you’ve made but haven’t shared yet before you push them in order to clean up your story, but never rebase anything you’ve pushed somewhere.

### Distributed Workflows 
1. Centralized workflow
2. Integration-Manage worklfow
3. Dictator and lieutenants workflow 

Check white space error in submissions before commit
 `git diff --check`

One commit per issue. If there’re changes in the same file, try to use `git add —-patch` to partially stage files 

Commit message template:
```
Short (50 chars or less) summary of changes

More detailed explanatory text, if necessary.  Wrap it to
about 72 characters or so.  In some contexts, the first
line is treated as the subject of an email and the rest of
the text as the body.  The blank line separating the
summary from the body is critical (unless you omit the body
entirely); tools like rebase can get confused if you run
the two together.

Further paragraphs come after blank lines.

  - Bullet points are okay, too

  - Typically a hyphen or asterisk is used for the bullet,
    preceded by a single space, with blank lines in
    between, but conventions vary here
```

Example use cases [Git - Contributing to a Project](https://git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project)


## Github
