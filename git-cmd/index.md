# Git Commands


- [Git reference](https://git-scm.com/docs)
- [Git cheatsheet (pdf)](https://training.github.com/downloads/github-git-cheat-sheet.pdf)
- [Common git commands](http://guides.beanstalkapp.com/version-control/common-git-commands.html)

<!--more-->

## Ordinary workflows

`HEAD`: your current working repo status.

### Create repos

```bash
git init  # Create a git worktree (repo) from current working directory

git clone <url>  # Clone a git repo from a remote repository
```

### Make changes and commit

```bash
git status      # The current state of the repository.

git add <file>  # Add a new or edited file to the staging area. i.e. telling git to track this file

git add -A      # Track all files at once

git commit -m "Commit message" # Commit staged (added) file

git commit -am "Commit message" # Commit modified files without having to run git add beforehand

git revert <SHA>                # Make a counter commit to undo the changes. The tracked files will go back to the <SHA> commit.
```

### Push and pull

```bash
git fetch # Download objects and refs from another repository without pull in the changes

git push <remote> <branch-name> # Push commits in to remote

git push --set-upstream <remote> <name-of-your-branch>  # Setup remote url before push

git pull <remote>  # Pull changes from the remote
```

### Stash

To temporarily store untracked files.

```bash
git stash -u   # Store current work with untracked files

git stash pop  # Bring stashed work back to the working directory
```

### Branches

```bash
git branch <branch_name>    # Create a new branch

git branch -a               # List all branches

git branch -d <branch_name> # Delete a branch

git checkout <branch_name>    # checkout an existing branch

git checkout -b <branch_name> # Create a new branch and checkout it

git switch <branch_name>    # Switch to a specified branch

git merge  <branch_name>    # Merge the branch into the current branch
```

## Orphan branches

Orphan branches are unrelated to others in history. Usefule in some occasions like the `gh-pages` orphan branch for GitHub pages.

```bash
git switch --orphan <branchname>  # Create a orphan branch and switch to it
```

## Git submodules

See also [gitaarik's Gist](https://gist.github.com/gitaarik/8735255) for more explanation.

### Adding a submodule

Adding the reference of other git project(s) instead the whole code base.

(Of course, the code is still copied over but version control happens on the respective origins)

```bash
git submodule add ${GIT_URL} ${DIR}
git submodule update --init --recursive
```

Or you can also use Gitkraken to add a submodule in the GUI.

Add you will see the reference in the file `.gitmodules`. For instance,

`.gitmodules`
```
[submodule "themes/CodeIT"]
	path = themes/CodeIT
	url = https://github.com/sunt-programator/CodeIT.git
```

### Update all Git submodules to the latest commit

From [StackOverflow](https://stackoverflow.com/questions/5828324/update-git-submodule-to-latest-commit-on-origin/5828396#5828396)

```bash
git submodule update --remote --merge
```

### Auto-update Git submodules by GitHub dependabot

From the [dependabot documentation](https://docs.github.com/en/github/administering-a-repository/keeping-your-dependencies-updated-automatically)

Dependabot detects updates of the submodule(s) and automatically generates PRs, and get the updates dependency tested (if you have setup CI).

Create a file `${YOUR_PROJECT}/.github/dependabot.yml` like this.

```yml
version: 2
updates:
  - package-ecosystem: "gitsubmodule"
    directory: "/"
    schedule:
      interval: "daily"
    labels:
    - "dependencies"
```

## Editing git histories

### Git reset

- Mixed reset (default): discard untracked files, but the changed files are preserved but not marked for commit.
- Hard reset: Resets the index and working tree. Any changes to tracked files in the working tree since <commit> are discarded.
- Soft reset: Does not touch the index file or the working tree at all (but resets the head to <commit>)

```bash
git reset --hard <SHA>   # Reset git history to a specific commit

git reset HEAD~          # Reset state to the previous commit (~)
```

### Removing large binary blobs

- [Azure DevOps | Rebase and force push](https://docs.microsoft.com/en-us/azure/devops/repos/git/remove-binaries?view=azure-devops)
- [GitHub docs | BFG repo cleaner](https://docs.github.com/en/github/authenticating-to-github/removing-sensitive-data-from-a-repository)
- [Phase 2 | Removing large blobs](https://www.phase2technology.com/blog/removing-large-files-git-bfg)

The [BFG Repo-Cleaner](https://rtyley.github.io/bfg-repo-cleaner/) is a faster and simpler alternative to `git filter-branch` for removing large file records (blobs)

1. Download [BFG Repo-Cleaner](https://rtyley.github.io/bfg-repo-cleaner/#download).
2. Clone the full git database
   ```bash
   git clone --mirror git://example.com/some-big-repo.git
   ```
3. Make a backup of it just in case
   ```bash
   cp -r some-big-repo some-big-repo-bak
   ```
4. Strip blobs from history
   ```bash
   bfg --strip-biggest-blobs 100 your-repo.git
   ```
5. Delete the blobs from the database. Check your repo size afterwards.
   ```bash
   cd some-big-repo.git && git reflog expire --expire=now --all && git gc --prune=now --aggressive
   ```
6. Push the changes the remote
   ```bash
   git push
   ```

#### Git filter repo

[Git filter-repo](https://github.com/newren/git-filter-repo) is a versatile tool for rewriting history written in a single-file python script.

### Purge Git database entirely

Erase all history in the Git repo to start over with all the current files. This also clears big file records in the Git database.

```bash
git checkout --orphan newBranch  # Creata an orphan branch to hold the files
git add -A  && git commit        # Add all files and commit them
git branch -D main               # Deletes the main branch
git branch -m main               # Rename the current orphan branch to main
git push -f origin main          # Force push main branch to remote (e.g. github)
git gc --aggressive --prune=all  # Remove the old files in the database
```

