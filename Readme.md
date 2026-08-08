# Git & GitHub Complete Command Guide
## Commands, Examples, Scenarios, Use Cases, When to Use, and Shortcuts

> A practical single-file reference for Git and GitHub.  
> Examples use a typical project called `my-project`.

---

# 1. Git vs GitHub

| Tool | What it is | Use |
|---|---|---|
| Git | Version control system | Track code changes locally |
| GitHub | Cloud platform for Git repositories | Store, share, review, collaborate, CI/CD |

**Typical workflow:**

```text
Create project
   ↓
git init
   ↓
edit files
   ↓
git add
   ↓
git commit
   ↓
git branch
   ↓
git push
   ↓
GitHub
   ↓
Pull Request
   ↓
Code Review
   ↓
Merge
```

---

# 2. Install and Check Git

## Check Git version

```bash
git --version
```

### Scenario
You installed Git and want to verify that it works.

### Use when
You are setting up Git for the first time.

---

## Show Git configuration

```bash
git config --list
```

```bash
git config --global --list
```

### Scenario
You want to check your Git username/email or other settings.

---

# 3. First-Time Git Configuration

## Set username

```bash
git config --global user.name "Your Name"
```

## Set email

```bash
git config --global user.email "you@example.com"
```

### Scenario

You are making your first commit on a new computer.

### Why
Git stores the author name and email with every commit.

---

## Set default branch to main

```bash
git config --global init.defaultBranch main
```

### Scenario
You want newly created repositories to use `main` instead of `master`.

---

## Configure useful colors

```bash
git config --global color.ui auto
```

---

# 4. Create a Git Repository

## Initialize Git

```bash
git init
```

### Scenario

You already have a project on your computer:

```text
my-project/
├── index.html
├── style.css
└── script.js
```

Run:

```bash
cd my-project
git init
```

### Use when
You want to start version control in an existing local project.

---

# 5. Clone an Existing GitHub Repository

## HTTPS

```bash
git clone https://github.com/username/repository.git
```

## SSH

```bash
git clone git@github.com:username/repository.git
```

## Clone into a custom folder

```bash
git clone https://github.com/username/repository.git my-project
```

### Scenario

A company already has a project on GitHub and you need a local copy.

### Use when
The repository already exists remotely.

---

# 6. Check Repository Status

```bash
git status
```

### Scenario

You changed files and want to know what Git sees.

Example:

```text
modified: app.py
untracked: notes.txt
```

### Use when
You are unsure what has changed before adding or committing.

### Best practice

Run:

```bash
git status
```

frequently.

---

# 7. Git Working Areas

Git commonly involves:

```text
Working Directory
       ↓
   git add
       ↓
Staging Area
       ↓
 git commit
       ↓
Local Repository
       ↓
 git push
       ↓
Remote Repository / GitHub
```

---

# 8. Add Files to Staging

## Add one file

```bash
git add index.html
```

## Add multiple files

```bash
git add index.html style.css
```

## Add everything

```bash
git add .
```

## Add all tracked/untracked changes

```bash
git add -A
```

### Scenario

You changed:

```text
index.html
style.css
script.js
```

and want all three included in the next commit.

```bash
git add .
```

### Use when
You have reviewed the changes and want to prepare them for a commit.

---

# 9. Check Staged Changes

```bash
git diff --staged
```

### Scenario

You ran:

```bash
git add .
```

but want to verify exactly what will be committed.

### Best practice

```bash
git add .
git diff --staged
git commit
```

---

# 10. Commit Changes

## Basic commit

```bash
git commit -m "Add login page"
```

### Scenario

You completed a meaningful piece of work.

### Good commit message

```bash
git commit -m "Fix login validation"
```

### Bad commit message

```bash
git commit -m "changes"
```

---

## Commit all modified tracked files

```bash
git commit -am "Fix dashboard layout"
```

### Important

`-a` does NOT automatically include new untracked files.

If `newfile.txt` is untracked:

```bash
git add newfile.txt
git commit -m "Add notes file"
```

---

# 11. View Commit History

## Basic log

```bash
git log
```

## One-line history

```bash
git log --oneline
```

## Graph view

```bash
git log --oneline --graph --decorate --all
```

## Last 5 commits

```bash
git log -5
```

### Scenario

You want to understand what happened recently in a project.

### Recommended

```bash
git log --oneline --graph --decorate --all
```

---

# 12. View Changes

## Unstaged changes

```bash
git diff
```

## Staged changes

```bash
git diff --staged
```

## Compare two commits

```bash
git diff commit1 commit2
```

### Scenario

A bug appeared and you want to inspect what changed between two versions.

---

# 13. Undo Changes Before Commit

## Discard changes in a file

```bash
git restore filename.txt
```

### Scenario

You edited a file but want to return it to the last committed version.

### Warning

This permanently discards those uncommitted changes.

---

## Unstage a file

```bash
git restore --staged filename.txt
```

### Scenario

You accidentally ran:

```bash
git add .
```

but don't want `secret.txt` in the commit.

Then:

```bash
git restore --staged secret.txt
```

---

# 14. Remove a File

## Delete file and stage deletion

```bash
git rm oldfile.txt
```

## Rename file

```bash
git mv oldname.txt newname.txt
```

### Scenario

You want Git to track a file deletion or rename.

---

# 15. Amend Last Commit

```bash
git commit --amend
```

### Change the commit message

```bash
git commit --amend -m "Correct commit message"
```

### Scenario

You just committed and noticed a small mistake.

### Warning

Avoid amending commits that have already been shared with others unless you understand the consequences.

---

# 16. Git Branches

Branches allow multiple lines of development.

Example:

```text
main
 ├── feature-login
 ├── feature-payment
 └── bugfix-navbar
```

---

# 17. List Branches

## Local branches

```bash
git branch
```

## Remote branches

```bash
git branch -r
```

## All branches

```bash
git branch -a
```

---

# 18. Create a Branch

```bash
git branch feature-login
```

### Scenario

You want to develop login functionality without changing `main`.

---

# 19. Switch Branch

```bash
git switch feature-login
```

### Older command

```bash
git checkout feature-login
```

---

# 20. Create and Switch to Branch

Recommended:

```bash
git switch -c feature-login
```

Older equivalent:

```bash
git checkout -b feature-login
```

### Scenario

You are starting a new feature.

```bash
git switch main
git pull
git switch -c feature-login
```

---

# 21. Rename a Branch

## Rename current branch

```bash
git branch -m new-name
```

## Rename another local branch

```bash
git branch -m old-name new-name
```

### Scenario

You created:

```text
feature-logn
```

but want:

```text
feature-login
```

---

# 22. Delete a Branch

## Delete merged local branch

```bash
git branch -d feature-login
```

## Force delete local branch

```bash
git branch -D feature-login
```

### Scenario

A feature was completed and merged.

### Warning

`-D` can delete a branch containing unmerged work.

---

# 23. Merge Branches

## Basic merge

```bash
git switch main
git merge feature-login
```

### Scenario

The login feature is finished and should be included in `main`.

---

# 24. Merge Conflict

A conflict can happen when two branches change the same part of a file.

Git may show:

```text
<<<<<<< HEAD
main version
=======
feature version
>>>>>>> feature-login
```

Resolve the file manually.

Then:

```bash
git add filename
git commit
```

### Scenario

Two developers edited the same lines.

### Conflict workflow

```bash
git status
# edit conflicting files
git add .
git commit
```

---

# 25. Abort a Merge

```bash
git merge --abort
```

### Scenario

You started a merge and encountered conflicts, but want to cancel the merge and return to the previous state.

---

# 26. Remote Repositories

## Show remotes

```bash
git remote -v
```

Example:

```text
origin  https://github.com/user/project.git (fetch)
origin  https://github.com/user/project.git (push)
```

---

# 27. Add GitHub Remote

```bash
git remote add origin https://github.com/username/project.git
```

### Scenario

You created a project locally and then created an empty GitHub repository.

---

# 28. Change Remote URL

```bash
git remote set-url origin https://github.com/username/new-project.git
```

### Scenario

The repository moved to another GitHub URL.

---

# 29. Rename Remote

```bash
git remote rename origin upstream
```

---

# 30. Remove Remote

```bash
git remote remove origin
```

### Scenario

You connected the wrong remote repository.

---

# 31. Push to GitHub

## First push

```bash
git push -u origin main
```

### Meaning

```text
git push
│
├── origin = remote name
└── main   = branch
```

`-u` sets the upstream tracking branch.

After that, usually:

```bash
git push
```

---

# 32. Push a New Branch

```bash
git push -u origin feature-login
```

### Scenario

You created a feature branch locally and want it on GitHub.

---

# 33. Delete Remote Branch

```bash
git push origin --delete feature-login
```

### Scenario

A remote feature branch is no longer needed.

---

# 34. Fetch from GitHub

```bash
git fetch
```

### Meaning

Downloads remote changes but does not merge them into your current branch.

### Scenario

You want to inspect what teammates pushed before changing your local code.

---

# 35. Fetch All Remotes

```bash
git fetch --all
```

---

# 36. Pull from GitHub

```bash
git pull
```

### Meaning

Usually:

```text
git fetch
+
git merge
```

### Scenario

Your teammate pushed changes and you want the latest version.

---

# 37. Pull a Specific Branch

```bash
git pull origin main
```

---

# 38. Pull with Rebase

```bash
git pull --rebase
```

### Scenario

You prefer a cleaner linear history.

---

# 39. Git Fetch vs Pull

| Command | Downloads changes | Changes current branch |
|---|---:|---:|
| `git fetch` | Yes | No |
| `git pull` | Yes | Usually yes |

### Safe inspection workflow

```bash
git fetch
git log --oneline HEAD..origin/main
```

Then decide whether to merge/rebase.

---

# 40. GitHub Fork

A fork is your GitHub copy of another user's repository.

### Scenario

You want to contribute to an open-source project but don't have direct write access.

Workflow:

```text
Original GitHub Repository
        ↓
       Fork
        ↓
Your GitHub Repository
        ↓
Clone locally
        ↓
Create branch
        ↓
Make changes
        ↓
Push
        ↓
Pull Request
```

---

# 41. GitHub Fork: Clone

```bash
git clone https://github.com/YOUR-USERNAME/project.git
```

---

# 42. Add Upstream Repository

```bash
git remote add upstream https://github.com/ORIGINAL-OWNER/project.git
```

Check:

```bash
git remote -v
```

Typical setup:

```text
origin    = your fork
upstream  = original repository
```

---

# 43. Sync a Fork

```bash
git fetch upstream
git switch main
git merge upstream/main
git push origin main
```

### Alternative with rebase

```bash
git fetch upstream
git switch main
git rebase upstream/main
git push origin main
```

### Scenario

The original project received new changes and you want your fork updated.

---

# 44. GitHub Pull Request Workflow

Typical contributor workflow:

```bash
git switch main
git pull origin main

git switch -c feature-login

# edit files

git add .
git commit -m "Add login feature"

git push -u origin feature-login
```

Then create a Pull Request on GitHub.

---

# 45. Pull Request

A Pull Request (PR) asks maintainers to review and merge your changes.

### Use when

- Working with a team
- Contributing to open source
- Reviewing code
- Merging feature branches

### Typical flow

```text
feature branch
      ↓
push to GitHub
      ↓
Pull Request
      ↓
Code Review
      ↓
Changes requested / approved
      ↓
Merge
```

---

# 46. GitHub Issues

Issues are used for:

- Bugs
- Feature requests
- Tasks
- Questions
- Improvements

### Example

```text
Title:
Login button does not work on mobile

Description:
The login button is not clickable on screens below 768px.
```

### Scenario

You need to track a bug without immediately changing code.

---

# 47. GitHub Issue Linking

You can reference an issue in a commit or PR:

```bash
git commit -m "Fix mobile login button #25"
```

Some GitHub keywords can automatically close issues when the PR/commit is merged, for example:

```text
Fixes #25
Closes #25
Resolves #25
```

---

# 48. Tags

Tags mark important versions.

## Create tag

```bash
git tag v1.0.0
```

## List tags

```bash
git tag
```

## Push tag

```bash
git push origin v1.0.0
```

## Push all tags

```bash
git push origin --tags
```

### Scenario

You release version 1.0.0.

---

# 49. Annotated Tags

```bash
git tag -a v1.0.0 -m "Release version 1.0.0"
```

### Recommended for releases

Annotated tags contain metadata such as author and message.

---

# 50. Delete Tags

## Local

```bash
git tag -d v1.0.0
```

## Remote

```bash
git push origin --delete v1.0.0
```

---

# 51. Git Stash

Stash temporarily saves uncommitted work.

## Save changes

```bash
git stash
```

### Scenario

You are working on feature A, but an urgent bug needs fixing on another branch.

```bash
git stash
git switch main
git switch -c hotfix
```

Later:

```bash
git switch feature-a
git stash pop
```

---

# 52. Stash with Message

```bash
git stash push -m "Login work in progress"
```

---

# 53. List Stashes

```bash
git stash list
```

---

# 54. Apply Stash

```bash
git stash apply
```

### Difference

`apply` keeps the stash.

```bash
git stash apply stash@{0}
```

---

# 55. Pop Stash

```bash
git stash pop
```

### Difference

`pop` applies and usually removes the stash.

---

# 56. Delete Stash

```bash
git stash drop stash@{0}
```

Delete all:

```bash
git stash clear
```

### Warning

Be careful with `stash clear`.

---

# 57. Git Reset

`reset` moves the current branch pointer and can modify the staging area or working files.

## Unstage a file

```bash
git reset HEAD filename.txt
```

Modern alternative:

```bash
git restore --staged filename.txt
```

---

## Undo last commit but keep changes staged

```bash
git reset --soft HEAD~1
```

### Scenario

You committed too early and want to edit the commit.

---

## Undo last commit and keep changes unstaged

```bash
git reset HEAD~1
```

---

## Hard reset

```bash
git reset --hard HEAD~1
```

### Warning

This can permanently discard work.

### Scenario

You are absolutely sure you want to remove the latest commit and its changes locally.

---

# 58. Git Revert

```bash
git revert <commit-hash>
```

### Scenario

A bad commit was already pushed to GitHub and other developers may have based work on it.

### Why use revert?

It creates a new commit that reverses the old commit.

### Team-safe approach

Prefer:

```bash
git revert <commit>
```

over rewriting shared history.

---

# 59. Reset vs Revert

| Command | Main purpose | Shared branch? |
|---|---|---|
| `git reset` | Move history pointer | Be careful |
| `git revert` | Create reverse commit | Usually safer |

---

# 60. Git Rebase

```bash
git switch feature-login
git rebase main
```

### Scenario

`main` has advanced while you were working on your feature.

Rebase can create a cleaner history:

```text
Before:

main:    A---B---C
              \
feature:       D---E

After rebase:

main:    A---B---C
                   \
feature:            D'---E'
```

### Important

Do not casually rebase shared/public commits.

---

# 61. Interactive Rebase

```bash
git rebase -i HEAD~3
```

### Useful for

- Combining commits
- Reordering commits
- Editing commit messages
- Cleaning local history

Example:

```text
pick abc123 Add login
squash def456 Fix login
squash ghi789 Update login
```

---

# 62. Cherry-Pick

```bash
git cherry-pick <commit-hash>
```

### Scenario

A bug fix exists on another branch, but you don't want to merge the entire branch.

Example:

```bash
git switch main
git cherry-pick abc123
```

---

# 63. Git Show

```bash
git show <commit-hash>
```

### Scenario

You want to see exactly what a particular commit changed.

---

# 64. Git Blame

```bash
git blame filename.py
```

### Scenario

You want to know which commit/person last changed a particular line.

### Use responsibly

It is useful for history investigation, not for blaming people.

---

# 65. Search Git History

## Search commit messages

```bash
git log --grep="login"
```

## Search code changes

```bash
git log -S "loginUser"
```

### Scenario

You remember that a login function existed previously but don't know when it was introduced.

---

# 66. Find a Bug with Bisect

```bash
git bisect start
git bisect bad
git bisect good <known-good-commit>
```

Git checks commits between good and bad versions.

After testing:

```bash
git bisect good
```

or:

```bash
git bisect bad
```

Finish:

```bash
git bisect reset
```

### Scenario

The project worked last month but is broken now. You don't know which commit introduced the bug.

---

# 67. Git Clean

Preview untracked files:

```bash
git clean -n
```

Delete untracked files:

```bash
git clean -f
```

Delete untracked directories too:

```bash
git clean -fd
```

### Warning

This can permanently delete untracked files.

Always preview first:

```bash
git clean -n
```

---

# 68. .gitignore

Create:

```text
.gitignore
```

Example:

```gitignore
node_modules/
.env
*.log
dist/
build/
__pycache__/
*.pyc
.vscode/
.DS_Store
```

### Scenario

You don't want passwords, dependencies, build output, or temporary files committed.

### Important

`.gitignore` does not automatically stop tracking a file that is already tracked.

To remove a tracked secret/config file from Git tracking:

```bash
git rm --cached .env
git commit -m "Stop tracking environment file"
```

---

# 69. Environment Variables and Secrets

Never commit:

```text
.env
passwords
API keys
private keys
database credentials
access tokens
```

Example `.gitignore`:

```gitignore
.env
.env.*
!.env.example
```

Safe template:

```text
# .env.example
DATABASE_URL=
API_KEY=
```

---

# 70. Git Alias

Create a shortcut:

```bash
git config --global alias.st status
```

Then:

```bash
git st
```

More examples:

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm "commit -m"
```

### Scenario

You repeatedly use long commands.

---

# 71. Useful Git Aliases

```bash
git config --global alias.st "status -sb"
git config --global alias.co checkout
git config --global alias.sw switch
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.last "log -1 HEAD"
git config --global alias.lg "log --oneline --graph --decorate --all"
```

---

# 72. Git Log Shortcuts

```bash
git log --oneline
```

```bash
git log --oneline --graph --decorate --all
```

```bash
git log --stat
```

```bash
git log --name-only
```

---

# 73. Find Current Branch

```bash
git branch --show-current
```

Alternative:

```bash
git status
```

---

# 74. Show Remote Tracking Information

```bash
git branch -vv
```

### Scenario

You want to know which remote branch each local branch tracks.

---

# 75. Git HEAD

`HEAD` represents your current position in Git history.

Current commit:

```bash
git rev-parse HEAD
```

Previous commit:

```bash
HEAD~1
```

Two commits ago:

```bash
HEAD~2
```

---

# 76. Detached HEAD

A detached HEAD can happen when you checkout a commit directly:

```bash
git checkout abc123
```

or:

```bash
git switch --detach abc123
```

### Scenario

You want to inspect an old version.

If you make useful changes, create a branch:

```bash
git switch -c recovery-branch
```

---

# 77. Git Remote Branch Tracking

```bash
git switch -c feature-login --track origin/feature-login
```

### Scenario

A teammate already pushed `feature-login` to GitHub and you want a local copy.

---

# 78. Delete Stale Remote Branch References

```bash
git fetch --prune
```

### Scenario

Remote branches were deleted on GitHub but still appear locally.

---

# 79. Force Push

```bash
git push --force
```

Safer:

```bash
git push --force-with-lease
```

### Scenario

You rebased a branch and need to update its remote history.

### Recommendation

Prefer:

```bash
git push --force-with-lease
```

### Warning

Force pushing can overwrite remote history.

Never use it casually on a shared `main` branch.

---

# 80. GitHub Authentication

GitHub generally supports:

- HTTPS authentication
- SSH authentication
- GitHub CLI authentication

## SSH test

```bash
ssh -T git@github.com
```

### Scenario

You configured an SSH key and want to verify GitHub access.

---

# 81. GitHub CLI

GitHub CLI executable:

```bash
gh
```

Check installation:

```bash
gh --version
```

Login:

```bash
gh auth login
```

### Scenario

You want to manage GitHub from the terminal.

---

# 82. GitHub CLI Repository

Create a repository:

```bash
gh repo create
```

Create from current directory:

```bash
gh repo create my-project --source=. --public
```

Clone:

```bash
gh repo clone username/project
```

---

# 83. GitHub CLI Pull Requests

Create PR:

```bash
gh pr create
```

List PRs:

```bash
gh pr list
```

View PR:

```bash
gh pr view
```

Checkout PR:

```bash
gh pr checkout 25
```

Merge PR:

```bash
gh pr merge 25
```

### Scenario

You prefer terminal-based GitHub workflows.

---

# 84. GitHub CLI Issues

Create issue:

```bash
gh issue create
```

List issues:

```bash
gh issue list
```

View issue:

```bash
gh issue view 25
```

Close issue:

```bash
gh issue close 25
```

---

# 85. GitHub Actions

GitHub Actions automates tasks such as:

- Testing
- Building
- Deployment
- Linting
- Security checks

Workflow files are stored in:

```text
.github/workflows/
```

Example:

```yaml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Run tests
        run: npm test
```

### Scenario

Every time someone pushes code, tests should automatically run.

---

# 86. GitHub Releases

A release is useful for distributing stable versions.

Typical workflow:

```bash
git tag -a v1.0.0 -m "Release 1.0.0"
git push origin v1.0.0
```

Then create a GitHub Release from that tag.

### Use when

- Publishing software versions
- Creating downloadable releases
- Maintaining release notes

---

# 87. GitHub README

Typical files:

```text
README.md
LICENSE
CONTRIBUTING.md
.gitignore
```

README normally contains:

```text
Project name
Description
Features
Installation
Usage
Configuration
Screenshots
Contributing
License
```

---

# 88. GitHub LICENSE

Common licenses:

- MIT
- Apache-2.0
- GPL-3.0
- BSD

### Scenario

You publish an open-source project and want to define how others can use it.

---

# 89. GitHub Discussions

Use Discussions for:

- Questions
- Community ideas
- General conversation
- Announcements

Use Issues for:

- Bugs
- Specific tasks
- Feature requests

---

# 90. GitHub Projects

Projects can track work using:

```text
Todo
In Progress
Review
Done
```

### Scenario

A team needs project/task management around GitHub Issues and PRs.

---

# 91. GitHub Codespaces

Codespaces provides a cloud development environment.

### Use when

- Your local machine isn't configured
- You want a ready-to-use development environment
- You want consistent environments for a team

---

# 92. Git Worktree

Create another working directory for another branch:

```bash
git worktree add ../hotfix hotfix
```

List:

```bash
git worktree list
```

Remove:

```bash
git worktree remove ../hotfix
```

### Scenario

You are developing a feature but need another directory for an urgent hotfix.

---

# 93. Git Submodule

Add another Git repository inside your project:

```bash
git submodule add https://github.com/user/library.git libs/library
```

Clone including submodules:

```bash
git clone --recurse-submodules https://github.com/user/project.git
```

Initialize after normal clone:

```bash
git submodule update --init --recursive
```

### Scenario

Your project depends on another Git repository that must remain separately versioned.

---

# 94. Git Archive

Create an archive of a project:

```bash
git archive --format=zip --output=project.zip HEAD
```

### Scenario

You need a clean ZIP of the repository without the `.git` directory.

---

# 95. Git Notes

Add a note to a commit:

```bash
git notes add -m "Reviewed by QA" <commit>
```

Show notes:

```bash
git log --show-notes
```

### Scenario

You need extra metadata without changing the commit itself.

---

# 96. Git Reflog

```bash
git reflog
```

### Scenario

You accidentally reset, rebase, or delete a branch and need to find previous positions.

Example:

```bash
git reflog
```

Find the previous commit:

```bash
git reset --hard HEAD@{2}
```

### Warning

Reflog is extremely useful for recovery, but be careful with destructive commands.

---

# 97. Recover a Deleted Branch

First:

```bash
git reflog
```

Find the commit.

Then:

```bash
git switch -c recovered-branch <commit>
```

### Scenario

You accidentally deleted a local branch containing important work.

---

# 98. Recover an Accidentally Deleted Commit

```bash
git reflog
```

Then create a branch:

```bash
git branch recovery <commit-hash>
```

---

# 99. Git Config Levels

## System

```bash
git config --system
```

## Global

```bash
git config --global
```

## Repository/local

```bash
git config --local
```

### Typical priority

```text
System
   ↓
Global
   ↓
Local repository
```

More specific configuration overrides broader configuration.

---

# 100. Check a Specific Configuration

```bash
git config user.name
```

```bash
git config user.email
```

---

# 101. Find Git Executable and Help

```bash
which git
```

Windows:

```powershell
where git
```

Help:

```bash
git help
```

Command-specific help:

```bash
git help commit
```

Quick help:

```bash
git commit -h
```

---

# 102. Git Credential Helpers

Check:

```bash
git config --global credential.helper
```

### Scenario

You want Git to remember authentication credentials.

The exact credential helper depends on your operating system and security setup.

---

# 103. Git Ignore Global Files

Configure a global ignore file:

```bash
git config --global core.excludesfile ~/.gitignore_global
```

Example:

```gitignore
.DS_Store
Thumbs.db
*.swp
```

### Scenario

You have personal OS/editor files you never want in any repository.

---

# 104. Line Ending Configuration

Windows:

```bash
git config --global core.autocrlf true
```

macOS/Linux commonly:

```bash
git config --global core.autocrlf input
```

### Scenario

Your team works across Windows, macOS, and Linux and you encounter line-ending changes.

---

# 105. Common Git Workflow: Solo Developer

```bash
git clone https://github.com/user/project.git
cd project

git switch -c feature-dashboard

# edit files

git status
git add .
git diff --staged
git commit -m "Add dashboard"

git push -u origin feature-dashboard
```

Then create a PR or merge according to your workflow.

---

# 106. Common Git Workflow: Team Development

```bash
git switch main
git pull origin main

git switch -c feature-login

# work

git status
git add .
git commit -m "Add login validation"

git push -u origin feature-login
```

Then:

```text
GitHub
→ Pull Request
→ Review
→ CI tests
→ Approval
→ Merge
```

---

# 107. Common Bug Fix Workflow

```bash
git switch main
git pull origin main

git switch -c fix-login-error

# fix bug

git add .
git commit -m "Fix login error"
git push -u origin fix-login-error
```

Create a Pull Request.

---

# 108. Urgent Production Hotfix

```bash
git switch main
git pull origin main

git switch -c hotfix-payment

# fix issue

git add .
git commit -m "Fix payment failure"
git push -u origin hotfix-payment
```

Then create a PR and deploy after review.

---

# 109. Temporarily Switch Work for an Urgent Task

```bash
git stash push -m "WIP dashboard"
git switch main
git pull
git switch -c hotfix
```

After finishing:

```bash
git switch dashboard
git stash pop
```

---

# 110. Update Feature Branch with Main

Option 1: Merge

```bash
git switch feature-login
git merge main
```

Option 2: Rebase

```bash
git switch feature-login
git rebase main
```

### Choose merge when

- You want to preserve branch history
- The branch is shared
- You want the safer/simple approach

### Choose rebase when

- The branch is private
- You want cleaner history
- You understand history rewriting

---

# 111. Standard Daily Git Routine

Start work:

```bash
git switch main
git pull
git switch -c feature-name
```

During work:

```bash
git status
git diff
```

Before commit:

```bash
git add .
git diff --staged
git commit -m "Describe the change"
```

Push:

```bash
git push -u origin feature-name
```

---

# 112. Commit Message Convention

A useful convention is:

```text
type: description
```

Examples:

```bash
git commit -m "feat: add login page"
git commit -m "fix: correct password validation"
git commit -m "docs: update installation guide"
git commit -m "refactor: simplify user service"
git commit -m "test: add login tests"
git commit -m "chore: update dependencies"
```

Common types:

| Type | Meaning |
|---|---|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation |
| `refactor` | Code restructuring |
| `test` | Tests |
| `chore` | Maintenance |
| `style` | Formatting/style |
| `perf` | Performance |
| `build` | Build system |
| `ci` | CI/CD |

---

# 113. Common Git Errors

## "not a git repository"

```text
fatal: not a git repository
```

Solution:

```bash
cd your-project
git status
```

If it is a new project:

```bash
git init
```

---

## "nothing to commit"

```text
nothing to commit, working tree clean
```

Meaning:

There are no new changes to commit.

---

## "rejected - non-fast-forward"

Usually:

```text
Updates were rejected because the remote contains work
```

Try:

```bash
git pull --rebase origin main
git push
```

Review conflicts if any occur.

---

## "merge conflict"

Check:

```bash
git status
```

Resolve files, then:

```bash
git add .
git commit
```

---

# 114. Common GitHub Permission Problem

If push fails:

```text
Permission denied
```

Check remote:

```bash
git remote -v
```

Then verify:

- GitHub account
- repository access
- authentication
- SSH key
- HTTPS credentials

---

# 115. Wrong Remote Repository

Check:

```bash
git remote -v
```

Fix:

```bash
git remote set-url origin https://github.com/username/correct-repo.git
```

---

# 116. Undo a Push Safely

If a bad commit is already public:

```bash
git revert <commit-hash>
git push
```

### Prefer this for shared branches.

---

# 117. Undo a Local Commit

Keep changes:

```bash
git reset --soft HEAD~1
```

Keep changes but unstage:

```bash
git reset HEAD~1
```

Delete changes:

```bash
git reset --hard HEAD~1
```

---

# 118. Compare Local and Remote

```bash
git fetch origin
```

Commits on remote but not local:

```bash
git log HEAD..origin/main --oneline
```

Commits local but not remote:

```bash
git log origin/main..HEAD --oneline
```

---

# 119. Check Which Files Changed in a Commit

```bash
git show --stat <commit>
```

Full changes:

```bash
git show <commit>
```

---

# 120. Find a File in Git History

```bash
git log --all -- filename.txt
```

### Scenario

You want to know when a file was added, changed, or deleted.

---

# 121. Restore a File from Another Commit

```bash
git restore --source=<commit> -- filename.txt
```

### Scenario

You need an older version of a file.

---

# 122. Git Diff Between Branches

```bash
git diff main..feature-login
```

### Scenario

You want to inspect what your feature branch changes compared with main.

---

# 123. Merge Without Fast-Forward

```bash
git merge --no-ff feature-login
```

### Scenario

You want the feature branch represented explicitly in history.

---

# 124. Squash Commits

Interactive rebase:

```bash
git rebase -i HEAD~4
```

Change later commits from:

```text
pick
```

to:

```text
squash
```

### Scenario

Your feature branch has many small commits:

```text
fix
fix again
test
oops
final fix
```

and you want a cleaner history before merging.

---

# 125. GitHub Branch Protection

Branch protection can require:

- Pull Requests
- Reviews
- Passing checks
- No force pushes
- No direct pushes

### Recommended for

```text
main
production
release
```

---

# 126. Pull Request Review Commands

Checkout a PR using GitHub CLI:

```bash
gh pr checkout 25
```

Review changes:

```bash
git diff main...HEAD
```

Check commits:

```bash
git log --oneline main..HEAD
```

---

# 127. GitHub Labels

Typical labels:

```text
bug
feature
documentation
good first issue
help wanted
priority-high
```

### Scenario

A project has many issues and needs categorization.

---

# 128. GitHub Milestones

Milestones group issues/PRs around a goal or release.

Example:

```text
v2.0 Release
```

with issues:

```text
#20 Login
#21 Payment
#22 Dashboard
```

---

# 129. GitHub Code Review Best Practices

Before opening a PR:

```bash
git status
git diff main...HEAD
git log --oneline main..HEAD
```

Then verify:

- Tests pass
- No secrets committed
- No unnecessary files
- Commit messages make sense
- README/docs updated when needed

---

# 130. Useful Git Shortcuts Cheat Sheet

| Goal | Command |
|---|---|
| Status | `git status` |
| Short status | `git status -sb` |
| Add all | `git add .` |
| Commit | `git commit -m "message"` |
| Log | `git log --oneline` |
| Graph | `git log --oneline --graph --decorate --all` |
| Current branch | `git branch --show-current` |
| Branches | `git branch` |
| Create branch | `git switch -c name` |
| Switch branch | `git switch name` |
| Delete branch | `git branch -d name` |
| Merge | `git merge name` |
| Fetch | `git fetch` |
| Pull | `git pull` |
| Push | `git push` |
| First push | `git push -u origin name` |
| Remote | `git remote -v` |
| Stash | `git stash` |
| Apply stash | `git stash pop` |
| Diff | `git diff` |
| Staged diff | `git diff --staged` |
| Undo unstaged file | `git restore file` |
| Unstage file | `git restore --staged file` |
| Revert commit | `git revert hash` |
| Reflog | `git reflog` |
| Tags | `git tag` |
| Create tag | `git tag v1.0.0` |
| Cherry-pick | `git cherry-pick hash` |
| Rebase | `git rebase main` |
| Abort merge | `git merge --abort` |
| Prune remote refs | `git fetch --prune` |

---

# 131. GitHub CLI Shortcut Cheat Sheet

| Goal | Command |
|---|---|
| Login | `gh auth login` |
| Check auth | `gh auth status` |
| Create repo | `gh repo create` |
| Clone repo | `gh repo clone owner/repo` |
| Create PR | `gh pr create` |
| List PRs | `gh pr list` |
| View PR | `gh pr view` |
| Checkout PR | `gh pr checkout 25` |
| Merge PR | `gh pr merge 25` |
| Create issue | `gh issue create` |
| List issues | `gh issue list` |
| View issue | `gh issue view 25` |
| Close issue | `gh issue close 25` |

---

# 132. The Most Important Commands to Memorize

If you are a beginner, start with these:

```bash
git init
git clone
git status
git add .
git commit -m "message"
git log --oneline
git branch
git switch -c feature-name
git switch main
git merge
git pull
git push
git fetch
git remote -v
git stash
git restore
git revert
```

---

# 133. Beginner Project: Complete Example

Suppose you have:

```text
my-project/
├── index.html
├── style.css
└── script.js
```

Initialize:

```bash
cd my-project
git init
```

Configure identity:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Check:

```bash
git status
```

Add:

```bash
git add .
```

Commit:

```bash
git commit -m "feat: initial project"
```

Create a GitHub repository.

Connect it:

```bash
git remote add origin https://github.com/username/my-project.git
```

Rename branch:

```bash
git branch -M main
```

Push:

```bash
git push -u origin main
```

---

# 134. Beginner Feature Example

Create feature branch:

```bash
git switch -c feature-contact-form
```

Edit files.

Check:

```bash
git status
git diff
```

Stage:

```bash
git add .
```

Review:

```bash
git diff --staged
```

Commit:

```bash
git commit -m "feat: add contact form"
```

Push:

```bash
git push -u origin feature-contact-form
```

Create Pull Request on GitHub.

After merge:

```bash
git switch main
git pull origin main
```

Delete local branch:

```bash
git branch -d feature-contact-form
```

Delete remote branch if needed:

```bash
git push origin --delete feature-contact-form
```

---

# 135. Team Example

Developer A:

```bash
git switch main
git pull
git switch -c feature-login
```

Developer A works and pushes:

```bash
git add .
git commit -m "feat: add login"
git push -u origin feature-login
```

GitHub:

```text
Pull Request
    ↓
Review
    ↓
Tests
    ↓
Approval
    ↓
Merge
```

Developer B updates:

```bash
git switch main
git pull
```

This keeps the team synchronized.

---

# 136. Open Source Contribution Example

1. Fork repository on GitHub.
2. Clone your fork.

```bash
git clone https://github.com/YOUR-USERNAME/project.git
cd project
```

3. Add original repository:

```bash
git remote add upstream https://github.com/ORIGINAL-OWNER/project.git
```

4. Create branch:

```bash
git switch -c fix-documentation
```

5. Make changes.

6. Commit:

```bash
git add .
git commit -m "docs: fix installation instructions"
```

7. Push:

```bash
git push -u origin fix-documentation
```

8. Open Pull Request from your fork to the original repository.

---

# 137. Git Safety Rules

## Rule 1

Before destructive commands, check:

```bash
git status
```

## Rule 2

Before force push:

```bash
git push --force-with-lease
```

instead of:

```bash
git push --force
```

when appropriate.

## Rule 3

Don't commit secrets.

## Rule 4

Don't use:

```bash
git reset --hard
```

unless you understand what will be deleted.

## Rule 5

Don't force-push shared branches without agreement.

## Rule 6

Review staged changes:

```bash
git diff --staged
```

before important commits.

---

# 138. Recommended Daily Workflow

```bash
# Start
git switch main
git pull

# New work
git switch -c feature-name

# Work
git status
git diff

# Prepare
git add .
git diff --staged

# Save
git commit -m "feat: describe the feature"

# Share
git push -u origin feature-name

# GitHub
# Create Pull Request
# Review
# CI
# Merge

# Update local main
git switch main
git pull
```

---

# 139. Quick Decision Guide

## I changed a file and want to save it

```bash
git add .
git commit -m "message"
```

## I want to send my commits to GitHub

```bash
git push
```

## Someone else changed GitHub

```bash
git pull
```

## I want to see remote changes without merging

```bash
git fetch
```

## I want a new feature

```bash
git switch -c feature-name
```

## I accidentally staged a file

```bash
git restore --staged file
```

## I want to discard local changes

```bash
git restore file
```

## I committed too early

```bash
git reset --soft HEAD~1
```

## I already pushed a bad commit

```bash
git revert <commit>
git push
```

## I need to temporarily put work aside

```bash
git stash
```

## I need to recover lost Git history

```bash
git reflog
```

## I need one commit from another branch

```bash
git cherry-pick <commit>
```

## I need to combine commits

```bash
git rebase -i HEAD~N
```

---

# 140. Final Git Mental Model

Remember this:

```text
EDIT
 ↓
git status
 ↓
git add
 ↓
STAGING AREA
 ↓
git commit
 ↓
LOCAL HISTORY
 ↓
git push
 ↓
GITHUB
 ↓
PULL REQUEST
 ↓
REVIEW
 ↓
MERGE
```

And when receiving work:

```text
GITHUB
 ↓
git fetch
 ↓
inspect
 ↓
git merge / git rebase
 ↓
LOCAL
```

The four commands beginners should master first are:

```bash
git status
git add .
git commit -m "message"
git push
```

Then learn:

```bash
git pull
git branch
git switch
git merge
git fetch
git stash
git restore
git revert
```

---

# 141. One-Page Super Cheat Sheet

```bash
# SETUP
git --version
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# NEW PROJECT
git init
git add .
git commit -m "Initial commit"

# EXISTING PROJECT
git clone URL
cd project

# STATUS / HISTORY
git status
git status -sb
git log --oneline
git log --oneline --graph --decorate --all
git diff
git diff --staged

# STAGING
git add file
git add .
git restore --staged file

# COMMIT
git commit -m "message"
git commit --amend

# BRANCHES
git branch
git branch -a
git switch -c feature
git switch main
git branch -d feature

# MERGE
git switch main
git merge feature

# REMOTE
git remote -v
git remote add origin URL
git remote set-url origin URL

# GITHUB
git fetch
git pull
git push
git push -u origin main
git push -u origin feature

# STASH
git stash
git stash list
git stash pop
git stash apply

# UNDO
git restore file
git restore --staged file
git reset --soft HEAD~1
git revert COMMIT
git reflog

# REBASE
git rebase main
git rebase -i HEAD~3

# CHERRY PICK
git cherry-pick COMMIT

# TAG
git tag v1.0.0
git push origin v1.0.0

# REMOTE CLEANUP
git fetch --prune

# GITHUB CLI
gh auth login
gh repo create
gh repo clone owner/repo
gh pr create
gh pr list
gh pr checkout 25
gh pr merge 25
gh issue create
gh issue list
```

---

# 142. Important Difference: Git Command vs GitHub Feature

Not everything related to GitHub is a Git command.

### Git commands

```bash
git init
git clone
git add
git commit
git branch
git merge
git rebase
git push
git pull
```

### GitHub features

```text
Repository
Pull Request
Issue
Fork
Actions
Projects
Discussions
Releases
Packages
Codespaces
Branch Protection
Code Review
```

### GitHub CLI commands

```bash
gh repo
gh pr
gh issue
gh auth
```

---

# 143. Best Learning Order

Learn in this order:

```text
1. git status
2. git add
3. git commit
4. git log
5. git diff
6. git branch
7. git switch
8. git merge
9. git remote
10. git push
11. git pull
12. git fetch
13. .gitignore
14. git stash
15. git restore
16. git revert
17. git reset
18. git rebase
19. git cherry-pick
20. git reflog
21. GitHub Pull Requests
22. GitHub Issues
23. GitHub Actions
24. GitHub CLI
```

---

# End

This document is intended to be used as a practical Git + GitHub reference while working on real projects.
