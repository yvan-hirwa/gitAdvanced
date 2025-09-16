# Git Advanced Exercises

## Part 1: Refining Git History

#### Exercise Source: [Click here](https://github.com/HIRWA13/Git-exercise?tab=readme-ov-file)

1. Missing File Fix:

```bash
#Using amend to include the new file to the recent commit

#Stage the new file
git add test4.md

#include the the file in the recent commit
git commit --amend --no-edit
```

2. Edit commit history:

```bash
#Using interactive rebase to edit a commit message

#Opening rebase for the last 3 commits
git rebase -i HEAD~3

# [detached HEAD 1c253c1] chore: Create second file
#  Date: Mon Sep 8 16:52:24 2025 +0200
#  1 file changed, 0 insertions(+), 0 deletions(-)
#  create mode 100644 test2.md
# Successfully rebased and updated refs/heads/main.
```

3. Squashing commits:

```bash
#Using interactive rebase to keep commit history tidy.

#Opening rebase for the last 5 commits
git rebase -i HEAD~5

# [detached HEAD a899652] chore: Create two files.
#  Date: Mon Sep 8 16:51:59 2025 +0200
#  2 files changed, 0 insertions(+), 0 deletions(-)
#  create mode 100644 test1.md
#  create mode 100644 test2.md
# Successfully rebased and updated refs/heads/main.
```

4. Splitting a Commit:

```bash
#Using interactive rebase to split a commit into two different commits.

#Opening rebase for the last 4 commits
git rebase -i HEAD~4

#Use rebase 'edit' to change edit the commit

#Used reset to remove the commit but remain with changes
git reset HEAD^

#Stage and commit third file
git add test3.md
git commit -m "chore: Create third file"

#Stage and commit fourth file
git add test4.md
git commit -m "chore: Create fourth file"

#Done
git rebase --continue
#Successfully rebased and updated refs/heads/main.
```

5. Advanced squashing:

```bash
#Using interactive rebase to sqash commits.

#Opening rebase for the last 6 commits
git rebase -i HEAD~6

#Use rebase 'squash' command to merge two commits

#Added a different commit message

```

6. Droping a commit:

```bash
#Create a 'unwanted file' for testing
echo "Unwanted commit" > unwanted.txt

#Stage and commit the unwanted file
git add unwanted.txt
git commit -m "Unwanted file to be dropped"

#Opening rebase for the last 2 commits
git rebase -i HEAD~2

#Use rebase 'drop' command to remove unwanted file from history

```

7. Cherry-picking Commits:

```bash
#Create a branch to test
git checkout -b ft/branch

#Create a file with content to test
echo "test" > test5.md

#Stage and commit
git add test5.md
git commit -m "Implemented test 5"

#Select the commit hash eg: f65c313
#Checkout to main
git checkout main

#CHERRY-PICK
git cherry-pick f65c313
#Now the commit from ft/branch is on main
```

8. Reorder Commits:

```bash
#Use git rebase to rearrange the order
git rebase -i HEAD~5

#Before re-order

# pick adbc0c7 Exercise 4
# pick ed33af4 Exercise 5
# pick feecdde Exercise 6
# pick c07d080 Implemented test 5
# pick abd7d0d Exercise 7

#After

# pick c55f7d3 Exercise 2
# pick a955314 Exercise 3
# pick f2f0be3 Exercise 7: Resolved README.md conflicts
# pick f2e0abe Exercise 6:Resolved conflicts
# pick 757096b Implemented test 5
```

9. Visualizing Commit History

```bash
git log --graph

# * commit 08d4de02bb29bc9d2cb5cfa03280d743523b53c1 (HEAD -> main, origin/main, origin/HEAD)
# | Author: yvan-hirwa <hirwakaranganwayvan@gmail.com>
# | Date:   Wed Sep 10 15:54:13 2025 +0200
# |
# |     Exercise 8
# |
# * commit 757096b6da52e2fd5fd48cf7eb35a7ed5403d022
# | Author: yvan-hirwa <hirwakaranganwayvan@gmail.com>
# | Date:   Tue Sep 9 16:42:52 2025 +0200
# |
# |     Implemented test 5
# |
# * commit f2e0abe2acd1bfd1dfa06a81032afda421f2cec5
# | Author: yvan-hirwa <hirwakaranganwayvan@gmail.com>
# | Date:   Tue Sep 9 16:36:43 2025 +0200
```

10. Git Operation

```bash
git reflog

# 08d4de0 (HEAD -> main, origin/main, origin/HEAD) HEAD@{0}: commit: Exercise 8
# 757096b HEAD@{1}: rebase (finish): returning to refs/heads/main
# 757096b HEAD@{2}: rebase (start): checkout HEAD~5
# 757096b HEAD@{3}: rebase (finish): returning to refs/heads/main
# 757096b HEAD@{4}: rebase (pick): Implemented test 5
# f2e0abe HEAD@{5}: rebase (continue): Exercise 6:Resolved conflicts
# f2f0be3 HEAD@{6}: rebase (continue): Exercise 7: Resolved README.md conflicts
# a955314 HEAD@{7}: rebase (start): checkout HEAD~5
# abd7d0d HEAD@{8}: commit: Exercise 7
# c07d080 HEAD@{9}: cherry-pick: Implemented test 5
# feecdde HEAD@{10}: checkout: moving from ft/branch to main
# f65c313 (ft/branch) HEAD@{11}: commit: Implemented test 5
# feecdde HEAD@{12}: checkout: moving from main to ft/branch
# feecdde HEAD@{13}: commit: Exercise 6
# ed33af4 HEAD@{14}: rebase (finish): returning to refs/heads/main
```

## Part 2: Branching Basics

1. Create Feature Branch

```bash
git checkout -b ft/new-feature
# Switched to a new branch 'ft/new-feature'
```

2. Working on a feature branch

```bash
# Create new file with some content'
echo "This is a new feature">feature.txt

#Stage and Commit
git add feature.txt
git commit -m "Feat: Add the the core functionality"
```

3. Switching back and Making changes

```bash
# Switching back to main
git switch main
# Switched to branch 'main'
# Your branch is up to date with 'origin/main'.

# create a new file
echo "Readme project">readme.txt

#stage and commit
git add readme.txt
git commit -m "Updated project readme"
# [main 11df35f] Updated project readme
#  1 file changed, 0 insertions(+), 0 deletions(-)
#  create mode 100644 readme.txt
```

4. Local vs. Remote Branches

```bash
#A local branches are where you write and commit code, while remote branches serve as a shared record of the project's development history on a server.
```

5. Branch Deletion

```bash
#Switch to main branch
git switch main
# Switched to branch 'main'
# Your branch is up to date with 'origin/main'.

#Merge the feature branch to main
git merge ft/new-feature

#Delete the branch
git branch -d ft/new-feature
# Deleted branch ft/new-feature (was 488a640).
```

6. Creating a Branch from a commit

```bash
#Find the commit and copy the hash
git log --oneline

#Create the branch off the commit and switch to it
git checkout -b ft/branch-from-commit 14c37d7
```

6. Creating a Branch from a commit

```bash
#Find the commit and copy the hash
git log --oneline

#Create the branch off the commit and switch to it
git checkout -b ft/branch-from-commit 14c37d7
```

7. Branch Merging

```bash
#Switch from the branch to merge
git switch main

#Create the branch off the commit and switch to it
git merge ft/branch-from-commit
```

8. Renaming Branches

```bash
#Check the brach to rename
git branch

#Before

# ft/branch
# ft/branch-from-commit
# * main

#Rename
git branch -m ft/branch-from-commit ft/commit-branch

#After
# ft/branch
# ft/commit-branch
# * main
```

10. Detached HEAD

```bash
#Check out a specific commit to detach head
git checkout A1b2c34

#To reattach checkout a branch
git checkout main

```

## Part 3: Advanced Workflows

1. Stashing changes

```bash
#Create a file to test stashing
echo "This file is for stashing">stashing.txt

#Stash the current changes with a message
git stash push -u -m "WIP: git stashing"
#The -u is for untracked files
# Saved working directory and index state On main: WIP: git stashing
```

2. Retrieve the stashed changes

```bash
#Check the stash
git stash list

#apply the latest stash
git stash apply
```

4. Merge conflicts with mergetool

```bash
#Create a conflict
#Files on different branches try to merge
#Setup or use vscode mergetool
git add
git commit # To finish the merge.
```

5. Detached HEAD

```bash
#A detached HEAD means your HEAD is pointing directly to a commit instead of a branch.
#Checkout a commit to detach a HEAD
git checkout a1b2c34 #commit hash

#Checkout a branch to reattach the the HEAD
git checkout ft/branch
```

6. Ignoring Files/Directories:

```bash
#Create a .gitignore file
#Add some file and directories like
#/tmp
# /node_modules
# *.cmd
#Save and commit
```

6. Ignoring Files/Directories

```bash
#Create a .gitignore file
#Add some file and directories like
#/tmp
# /node_modules
# *.cmd
#Save and commit
```

7. Working with Tags

```bash
#To create an annotated tag with a message do:
git tag -a v1.0.0 -m "First tag release"
#This is not a lightweight tag but the annotated tag
#This tag is on the latest commit since I didn't provide a commit hash.
```

8. Listing and Deleting Tags

```bash
#Listing
git tag #or
git tag -l "v1*" #To list every tag starting with v1
# v1.0.0

#Deleting
git tag -d v1.0.0
```
