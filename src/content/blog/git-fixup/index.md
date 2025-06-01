---
title: "Level Up Your Git Game: Modify a Previous Commit with Fixup"
description: "Learn how to use git commit --fixup and git rebase --autosquash to cleanly modify previous commits without messy history."
date: "Oct 8 2024"
---

## The motivation behind this series

As an analytics engineer, I've noticed that while most team members understand the fundamentals of Git, they often struggle with more advanced techniques that can drastically improve their workflows. This series of articles aims to close that gap, offering practical solutions to everyday challenges.

## The Problem

Let's say you're working on a branch with several commits, and you realize you need to make changes to one that isn't the most recent. Maybe you spotted a typo, forgot to add a file, or need to tweak some logic. What do you do?

Many developers would create a new commit with the fix, resulting in a messy history like:
- "Add feature X"
- "Fix typo in feature X"
- "Oops, forgot a file"

There's a better way:

```
git commit --fixup
```

## Step-by-Step Process

### 1. Locate the Target Commit

First, find the commit you want to modify:

```bash
git log --oneline
```

This will show something like:

```
b9f1e3c (HEAD -> staging, origin/staging) feat: stage customer table
d4a2c7a feat: stage product table
a7c6b5e feat: stage company table
b2a2e99 (origin/main, origin/HEAD, main) feat: create dim_calendar
```

Let’s say you want to correct the commit with the message **feat: stage company table**. You’ll need the hash associated with that commit. In this case **a7c6b5e**.

### 2. Make Your Changes and Create a Fixup Commit

After making and staging your changes, create a fixup commit:

```bash
git add <file>
git commit --fixup a7c6b5e
```

Git will create a commit with a specially formatted message: **fixup! feat: stage company table**. This tells Git that this commit is meant to fix up the specified commit.

### 3. Start an Interactive Rebase with Autosquash

Now, integrate the fixup commit with its target. Use the following command to start an interactive rebase with the **--autosquash** option.

```bash
git rebase -i --autosquash b2a2e99
```

**Important:** You need to provide the commit hash *before* the commit you want to fix (in this case, the commit before **b2a2e99**).

### 4. Review and Complete the Rebase

After running the rebase command, your text editor will open with a rebase plan. Thanks to **--autosquash**, the fixup commit will be automatically placed right after its target commit and marked with **fixup**:

```
pick a7c6b5e feat: stage company table
fixup c26ffed7 fixup! feat: stage company table
d4a2c7a feat: stage product table
b9f1e3c feat: stage customer table
```

No manual changes needed, just save and close the editor. Git will automatically squash the fixup commit into the target commit.

### 5. Force Push (If Needed)

If your branch is already pushed to a remote, you'll need to force-push:

```bash
git push --force-with-lease
```

Using **--force-with-lease** is safer than **--force** because it checks if the remote branch has changed since your last pull.


## Conclusion

The **--fixup** and **--autosquash** combo is a powerful technique for maintaining a clean commit history. Instead of cluttering your history with "fix typo" commits, you can seamlessly integrate fixes into the commits where they belong.
