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
