# Contributing Guidelines

Welcome to the project seminar "Optimizing electricity trading".

This file contains the guidelines for our project. Please read the full document, as it helps us to work consistent and efficient together.

---

## Table of contents

- [Contributing Guidelines](#contributing-guidelines)
  - [Table of contents](#table-of-contents)
  - [Basics](#basics)
  - [Team](#team)
  - [Repositories](#repositories)
  - [Issues](#issues)
  - [Branching](#branching)
    - [Convention for branch names](#convention-for-branch-names)
  - [Commits](#commits)
    - [Linear commit history and rebasing](#linear-commit-history-and-rebasing)
  - [Pull Requests](#pull-requests)
      - ["Squash and merge", "rebase and merge" or "merge commit"?](#squash-and-merge-rebase-and-merge-or-merge-commit)
  - [Code Reviews](#code-reviews)

---

## Basics

All communications (code, comments, issues, reviews, ...) should be done in English.

Always be respectful. The goal is to create the best product together.

## Team

We use **scrum** for our project management. For more information about scrum please see the [presentation from Marius](/docs/presentations/Projectmanagement%20by%20Marius%20Martin.pdf)

| Role | Person |
|---|---|
| Product Owner | Maurice Tarp |  |
| Current Scrum Master #1 | Hauke Hümpel |
| Current Scrum Master #2 | Tamaro Walter |

---

## Repositories

*Here will be a short description of the repositories*

| Repository | Description |
|---|---|
| `.github` | organization profile, Templates for pull requests, issues, ...  |

---

## Issues

Github Issues should be use to document on what the team should work. There are 3 types of issues:

- Features: Ideas for new functionality
- Task: a specific task (e.g. "change the login authentication method")
- Bug: a bug was found and needs to be fixed

Please describe your issue thoroughly. In case of bugs please explain how another team member can reproduce the bug on it's local machine.

For general questions or discussion matters please open up a [discussion](https://github.com/orgs/EnergyTrading2026/discussions) and not an issue. Alternatively, use the discord server for communication. 

---

## Branching

We work with the **Feature Branch Workflow**. Every time you want to add or change something in a repository, you need to create a new branch. Never push directly on the main branch! We have main branch protection activated anyway.

Every branch should have a single goal, at best it should solve a single issue. Please refrain from using branches like *fix/everything*, that do all kind of things. A branch should e.g. implement a new single feature or fix a single bug. Keep the amount of committed code in way that it is easy for other team members to review.

### Convention for branch names

```
<type>/<short-description>
```

| Type | Use case |
|---|---|
| `feature/` | New feature |
| `improve/` | Improve or enhance an existing feature |
| `fix/` | Bugfix |
| `redesign/` | Changes the architecture or redesigns a crucial workflow |
| `testing/` | Add missing or improve existing tests |
| `cleaning/` | Code cleaning without functional changes |
| `docs/` | Documentation |

**Examples:**
```
feature/user-login
fix/login-with-empty-password
redesign/login-authentication-method
```

---

## Commits

Commits are the most important thing. They should be clear, single-purposed and should give a direct orientation what it does to someone that reads the git history.

Keep the code in the commits simple. We prefer smaller commits with a clear description. Description should use the imperative (*"add feature"*, not "*added feature*"). A commit should only change the files that the description intends. A *add pop-up notifications* commit should only change files that have to do with showing notifications, not e.g. a database configuration files.

When creating a commit use a short header that summarize the changes. Feel free to add a longer description on a second line:
 
```
add pop-up notifications

New notifications will be shown to the user before submitting a form
```


### Linear commit history and rebasing

We should aim to have a readable commit history, so that every change in the code is traceable. But sometimes it happens that a developer creates "work in progress" commits or creates a big commit that should be split up into smaller commits on the local branch. That is fully normal and part of the every day coding experience. But before pushing (or at last merging), the local history should be tidied up. You can use `git rebase -i` for interactive rebase, where you can reorder your commits. **BUT ONLY DO THIS ON YOUR LOCAL BRANCHES, NEVER ON SHARED BRANCHES**, as it changes the commit history and can lead to ugly conflicts.

Imagine you worked today on an issue and you have the following commits at the end of the day:
```
pick abcd123 Wip: add pop up notifications
pick abcd124 wip: add pop up notifications
pick abcd125 dumb commit - delete later
```

Then you should do this with `git rebase -i HEAD~3`:
```
pick abcd123 Wip: add pop up notifications
squash abcd124 wip: add pop up notifications
drop abcd125 dumb commit - delete later
```                    

To get:
```
pick abcd126 add pop up notifications
```                    

This is a commit history you can push!

More information about [interactive rebase](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History)

---

## Pull Requests

After completing your task you can open a pull request. A pull request allows other team members to review your changes before it gets merged with the main branch. You can also use **draft pull requests** if you are still work-in-progress but want to have early feedback.

Explain in the pull request description what your changes do and what your goal is. Feel free to add graphics, diagrams and other things to explain what you did.

Before merging, at least 2 different people than the author need to approve the pull request. After approving, the author then merges to main.

#### "Squash and merge", "rebase and merge" or "merge commit"?

This is a highly philosophical question. Short explanation:

- squash and merge: squashes all your branches commits into 1 commit and places it on top of the main branch. You can use this if your branch has only a few (1-3) very small commits.
- rebase and merge: puts all your commits on top of the main branch. This gives a linear commit history but in case the merge needs to be undone you have to revert every single commit
- merge commit: puts all commits on top of the main branch + 1 commit that contain all changes in one. This looks redundant at first but makes it easy to revert the merge if needed

---

## Code Reviews

A short manual:

**If you are the reviewer:**
- be respectful and write constructive comments.
- Write when you think something **must** be changed and when you only have a suggestion

**As author:**
- Answer every comment, and discuss constructivly if you have a different opinion

---

On behalf of the Team

Tamaro Walter

*Last update: 12.04.2026*
