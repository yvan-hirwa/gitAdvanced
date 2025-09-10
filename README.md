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
