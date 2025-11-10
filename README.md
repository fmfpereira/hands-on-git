# Hands-on Git

## Setup
1. Login / Register on github.com
2. Visit https://github.com/fmfpereira/hands-on-git
3. Select <> Code  -> Codespaces -> Create codespace on main

### What is **GitHub Codespaces** 
**GitHub Codespaces** is an online development environment that runs in the cloud — basically a full VS Code setup (with terminal, extensions, and Git) running on GitHub’s servers.
## Hands-on 

### Git branch
In Git, a `branch` is like a separate workspace where you can make changes and try new ideas without affecting the main project. Think of it as a "parallel universe" for your code.

1. Create a new branch
```shell
git branch filipe-branch
```

2. List all branches
```shell
git branch
```

```shell
  filipe-branch
* main
```

3. Switching Between Branches
```shell
git checkout filipe-branch
```

### Untracked and tracked files
An **untracked file** is any file in your project folder that Git is not yet tracking.
These are files you've created or copied into the folder, but haven't told Git to watch.

A **tracked file** is a file that Git is watching for changes.
To make a file tracked, you need to add it to the staging area (covered in the next chapter).

1. Open the **index.html** file and replace **[name]** with your own name.
2. Create a new to-do file in the **todos** folder named **yourname.txt** (you can use **example.txt** as a template).
3. Check File Status with git status
```shell
git status
```

```shell
On branch filipe-branch
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	todos/filipe.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

### Git Staging Environment
The **staging environment** (or **staging area**) is like a waiting room for your changes.
You use it to tell Git exactly which files you want to include in your next commit.
This gives you control over what goes into your project history.

1. Stage a File
```shell
git add index.html

git status
```

```shell
On branch filipe-branch
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	todos/filipe.txt
```

2. Unstage a File
```shell
git restore --staged index.html

git status
```

```shell
On branch filipe-branch
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	todos/filipe.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

3. Stage all files
```shell
git add --all

git status
```

```shell
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   index.html
	new file:   todos/filipe.txt
```
### Git Commit
A **commit** is like a save point in your project.
It records a snapshot of your files at a certain time, with a message describing what changed.
You can always go back to a previous commit if you need to.

1. To save your staged changes, use `git commit -m "your message" and replace [name] by your name`.
```shell
git commit -m "First commit from [name]"
```

```shell
[filipe-branch fad9d9e] First commit from Filipe
 2 files changed, 5 insertions(+), 1 deletion(-)
 create mode 100644 todos/filipe.txt
```

- Note: If you just type `git commit` (no `-m`), your default editor will open so you can write a detailed, multi-line message.

### Git History
Git keeps a detailed record of every change made to your project.
You can use history commands to see what changed, when, and who made the change.
This is useful for tracking progress, finding bugs, and understanding your project's evolution.

1. See Commit History (`git log`)
```shell
git log
```

```shell
commit fad9d9e424ec0fcc3416da05d3dca4d050af3adb (HEAD -> filipe-branch)
Author: fmfpereira <fmfpereira@gmail.com>
Date:   Mon Nov 10 21:44:12 2025 +0000

    First commit from Filipe

commit 57b3a0b75082164012acba9addc7b69e4da50a8f (main)
Author: fmfpereira <fmfpereira@gmail.com>
Date:   Mon Nov 10 21:41:34 2025 +0000

    Initial commit
```

2. Show a Summary of Commits (`git log --oneline`)
```shell
git log --oneline

```

```shell
fad9d9e (HEAD -> filipe-branch) First commit from Filipe
57b3a0b (main) Initial commit
```

3. Show Commit Details (`git show <commit>`)
```shell
git show 57b3a0b
```

```shell
commit 57b3a0b75082164012acba9addc7b69e4da50a8f (main)
Author: fmfpereira <fmfpereira@gmail.com>
Date:   Mon Nov 10 21:41:34 2025 +0000

    Initial commit

diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000..5c0e24a
--- /dev/null
+++ b/.gitignore
@@ -0,0 +1,3 @@
+# Ignore tools
+.obsidian
+.obsidian/*
diff --git a/index.html b/index.html
new file mode 100644
index 0000000..c612f05
--- /dev/null
+++ b/index.html
@@ -0,0 +1,10 @@
+<!DOCTYPE html>  
+<html>  
+  <head>  
+    <title>Git hands-on</title>  
+  </head>  
+  <body>  
+    <h1>Hello!</h1>  
+    <p>My name is [name], and I’m currently doing the Git hands-on exercise!</p>  
+  </body>  
+</html>
diff --git a/todos/example.txt b/todos/example.txt
new file mode 100644
index 0000000..8bea355
--- /dev/null
+++ b/todos/example.txt
@@ -0,0 +1,4 @@
+wake up
+eat
+sleep
+repeat
\ No newline at end of file

```

4. Compare Changes (`git diff`)
	- Edit the index.html and your new todo file; and update some content.
```shell
git diff
```

```shell
diff --git a/index.html b/index.html
index 3c15d2a..e0bcdd0 100644
--- a/index.html
+++ b/index.html
@@ -5,6 +5,6 @@
   </head>  
   <body>  
     <h1>Hello!</h1>  
-    <p>My name is Filipe, and I’m currently doing the Git hands-on exercise!</p>
+    <p>My name is Filipe Pereira, and I’m currently doing the Git hands-on exercise!</p>
   </body>  
 </html>
diff --git a/todos/filipe.txt b/todos/filipe.txt
index 8bea355..7bd2a1b 100644
--- a/todos/filipe.txt
+++ b/todos/filipe.txt
@@ -1,4 +1,5 @@
 wake up
 eat
+have fun
 sleep
 repeat
\ No newline at end of file

```

5. Compare Staged Changes (`git diff --staged`)
	- Add the index.html file to the stage and diff the changes in the stage.
```shell
git add index.html

git diff --staged
```

```shell
git diff --staged
diff --git a/index.html b/index.html
index 3c15d2a..e0bcdd0 100644
--- a/index.html
+++ b/index.html
@@ -5,6 +5,6 @@
   </head>  
   <body>  
     <h1>Hello!</h1>  
-    <p>My name is Filipe, and I’m currently doing the Git hands-on exercise!</p>
+    <p>My name is Filipe Pereira, and I’m currently doing the Git hands-on exercise!</p>
   </body>  
 </html>
```

### Git Branch Merge
Merging in Git means combining the changes from one branch into another.

This is how you bring your work together after working separately on different features or bug fixes.

1. Merge the main-to-merge branch
```shell
git merge main-to-merge
```

```shell
Auto-merging index.html
Merge made by the 'ort' strategy.
 index.html | 1 +
 1 file changed, 1 insertion(+)
```

#### What is a Merge Conflict?
A **merge conflict** happens when changes in two branches touch the same part of a file and Git doesn't know which version to keep.

Think of it like two people editing the same sentence in a document in different ways—Git needs your help to decide which version to use.

Git will mark the conflict in your file.

You need to open the file, look for lines like `<<<<<<< HEAD` and `=======`, and decide what the final version should be.

1. Merge the main-to-merge-conflict
```shell
git merge main-to-merge-conflict
```

```shell
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

2. Fix the merge conflicts using your IDE or diff tool.
3. Stage your changes and commit.
```shell
git add --all

git commit -m "Fix merge conflicts"
```

```shell
[filipe-branch e1e5432] Fix merge conflicts
```

4. Check the commit log.
```shell
git log
```

```shell
commit e1e54324d5e80d58c6113460c0a92c919ba91e41 (HEAD -> filipe-branch)
Merge: fad9d9e f0957fb
Author: fmfpereira <fmfpereira@gmail.com>
Date:   Mon Nov 10 22:10:23 2025 +0000

    Fix merge conflicts

commit f0957fb354215e8e15602cd6e60104ef0061e388 (main-merge-conflict)
Author: fmfpereira <fmfpereira@gmail.com>
Date:   Mon Nov 10 22:05:49 2025 +0000

    Add name and surname tokens to index

commit fad9d9e424ec0fcc3416da05d3dca4d050af3adb
Author: fmfpereira <fmfpereira@gmail.com>
Date:   Mon Nov 10 21:44:12 2025 +0000

    First commit from Filipe

commit 57b3a0b75082164012acba9addc7b69e4da50a8f (main)
Author: fmfpereira <fmfpereira@gmail.com>
Date:   Mon Nov 10 21:41:34 2025 +0000

    Initial commit

```

### Push changes to github
When we have made changes locally, we want to update our remote repository with the changes.

Transferring our local changes to our remote is done with a `push` command.

1. Push your current branch to the remote repository/

```shell
git push origin
```

### Pull changes from github

When working as a team on a project, it is important that everyone stays up to date.

Any time you start working on a project, you should get the most recent changes to your local copy.

`git fetch` downloads new data from a remote repository, but does not change your working files or branches. It lets you see what others have pushed before you merge or pull.

But what if you just want to update your local repository, without going through all those steps?

`pull` is a combination of `fetch` and `merge`.

It is used to pull all changes from a remote repository into the branch you are working on.

1. Execute the following command (be sure that the mail-pull branch is available)

```shell
git fetch

git checkout main-pull

git pull
```

### Pull request
Pull requests are a key part of GitHub.

A Pull Request notifies people you have changes ready for them to consider or review.

You can ask others to review your changes or pull your contribution and merge it into their branch.

Go to https://github.com/fmfpereira/hands-on-git and do a Pull request from your branch to the main branch.

## Credits
- Hands-on based on the git tutorial from [w3schools](https://www.w3schools.com/git)