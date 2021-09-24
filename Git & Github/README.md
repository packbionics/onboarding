Git is the standard tool for managing your code base. It saves revisions of code so that previous versions are always accessible. Github is a service that hosts the repository and allows for an entire team to work together successfully.

# Goals
1. Understand basic principals of Git
2. Learn basic commands:
    * `git clone`
    * `git add`
    * `git commit`
    * `git branch`
    * `git push`
3. Get familiar with GitHub workflow

# Guide

## Getting Started
In order to start learning how to use `git` we must first check to see if `git` is installed. 

* On macOS, open the "Terminal" application.
* On Windows, open either "Command Prompt" or "Git Bash"

Once you have opened your terminal, type `git version`. If `git` is installed the installed version should be outputted. If you are alerted that `git` is an unknown command you must install Git.

### Installing Git
* On macOS, visit the [macOS Git Installer](https://sourceforge.net/projects/git-osx-installer/files/git-2.23.0-intel-universal-mavericks.dmg/download?use_mirror=autoselect) and download the latest version.
* On Windows, vist the [Git for Windows installer](https://gitforwindows.org/) and download the latest version.
* On Linux, use your package management tool to install `git-all`

For a more indepth guide on installing Git visit this [page](https://github.com/git-guides/install-git).

## Repositories
There are 2 ways to start a repository, either through `git init` or `git clone`.

`git init` allows you to turn the current directory you are in into a Git repository. However this repository would only be local and would be unable to be accessed through GitHub until the repository is pushed to GitHub. This will be discussed later in the guide. Some common options for the `git init` command are:

* `git init`: Turn the current directory into a Git repository.
* `git init <directory>`: Turn `<directory>` into a Git repository.

All of the `git init` options can be found on [git-scm's documentation](https://git-scm.com/docs/git-init).

To copy an existing repository from a site like GitHub the command `git clone` would be used. This will download the repository localy and allow you to edit the files in anyway. The files would change locally but would remain unchanged on the GitHub repository. Later in this guide we will discuss how to modify the remote files in the GitHub repository. Common options for the `git clone` command are:

* `git clone [url]`: Download a repository that already exists on GitHub.
* `git clone [url] --branch <branch>`: Download only a single branch of a repository on GitHub.

All of the `git clone` options can be found on [git-scm's documentation page](https://git-scm.com/docs/git-clone).

## Committing 
While you are able to modify the files in your repository just as easily as anyother directory you are not taking advantage of the power of `git`. `git` allows you to create something called a commit which is similair to a save file but is never overwritten, this means that no matter how much the repository changes, if you had a previous commit you would be able to revert your repository to that state. This is really powerful for version control and tracking changes. 

In order to make a commit desired files must first be added to the Git staging area using the `git add` command. For example a possible ussage would be:

```
git add README.md
```

This would add the `README.md` file to the Git staging area. Common usages and options for the `git add` command are:

* `git add <path>`: Stages a specific directory or file.
* `git add .`: Stages all files in the current directory.
* `git add -A`: Stages all files in the entire Git repository.
* `git add -u`: Stages all files EXCEPT for deleted files in the entire Git repository.

All of the `git add` options can be found on [git-scm's documentation page](https://git-scm.com/docs/git-add).

In order to remove all files from the staging area the `git reset` command can be used, specifically `git reset HEAD`. This command removes all staged files from the staging area without removing the edits made the local repository.

To view the staging area the command `git status` can be used which shows the current state of your Git working directory and staging area.

Now that we know how to add files to the staging area we can use the `git commit` command to create a commit. As discussed previously a commit is similair to a snapshot of the entire repository at the time when the commit was created. For example the command:

```
git commit -m "Inital Commit"
```

Would create a commit with the message "Inital Commit". Other common ways to use `git commit`  are:

* `git commit`: Creates a commit using a commit message made in a text editor.
* `git commit -m "commit message"`: Creates a commit with the commit message that follows the `-m` flag.

To see all of the possible options you have with `git commit`, check out [Git's documentation](https://git-scm.com/docs/git-commit).

To undo a commit in Git there are a one thing to keep in mind is that"undoing" a commit that exists on the remote is very tedious and problematic and should only rarely be done. However if the commit is on local work it is very easy, two commands that can be used to undo a commit are, `git revert` or `git reset`.

`git revert` is very safe and undos a commit by creating a new commit which applies the opposite of the last commit making it seem as though the commit was undone without having to sacrafice the integrity of your repository's history. `git revert` is always the recommended way to change history when it's possible.

`git reset` is much more powerful the `git revert` and is able to properly delete a commit but could potentially cause you to loose work if used incorrectly.

While not the same as "undoing" a commit, using the command `git commit --amend` allows you to edit the previous commit.

## Branches
Another very important feature of `git` are branches. When you first create a repository there is only a single branch called *main* and every commit you make is made on that branch. Using the `git branch` command you are able to make new branches which allow you to test and experiment without directly affecting the source code. Common options for the command `git branch` are:

* `git branch <name>`: Create a new branch called `<name>`.
* `git branch -d <name>`: Delete a branch named `<name>`.

All of the `git branch` options can be found on [git-scm's documentation page](https://git-scm.com/docs/git-branch).

Now that you can make branches you need to learn how to switch to them. To switch between branches `git checkout` is used. For example if you wanted to switch to a branch called *test_branch* you would write the command:

```
git checkout test_branch
```

As branches are often used for testing and experiementing without altering the source code, when the test or experiment is succesful you can merge the test branch back with the *main* branch which would cause the source code to become the same as the test branch. This is done using the `git merge` command. `git merge` causes all the commits on one branch to be replayed on another branch, effectivley merging the two branches. Additonal `git merge` options can be found on [git-scm's documentation page](https://git-scm.com/docs/git-merge).

Sometimes if edits have occured to a branch after a new branch was made and then the two branches are tried to merge, a merge conflict will likely appear. This is not a big deal and just involves fixing the overlapping code so that the two branches can merge.

## Pushing
Now that we know how to properly manage a local repository we can now learn how to push the local repository to GitHub. First in order to push to GitHub we should figure out where we would be pushing the repository and if there is not a preset location we must set the upstream location. This can be done using the `git remote` command, which allows us to manage the repositorys remote host. Common `git remote` commands are:

* `git remote -v`: List the current remotes associated with the local repository
* `git remote add [name] [URL]`: Add a remote
* `git remote remove [name]`: Remove a remote

Now that we have set the upstream location we can push our local repository to the remote GitHub repository using `git push`. Using `git push` for the first time will cause you to have to sign into your GitHub account. All of the options for `git push` can be found in [git-scm's documentation](https://git-scm.com/docs/git-push). Once you used `git push` to push your local changes to the remote repository your commits are made acccessible to others after they use the command `git pull`.

`git pull` updates your current local working branch, and all of the remote tracking branches. It's a good idea to run git pull regularly on the branches you are working on locally. Without `git pull`, your local branch wouldn't have any of the updates that are present on the remote. You can see all of the many options with `git pull` in [git-scm's documentation](https://git-scm.com/docs/git-pull).

# Exercise

# Resources
* https://github.com/git-guides/
* https://git-scm.com
* https://gitimmersion.com/index.html
