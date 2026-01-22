# Git Workflow: Merge Convert Branch to Main

## Current Situation
- **Current branch**: `convert`
- **Remote**: `origin` (git@github.com:terry81/prevodi-sema.git)
- **Problem**: The `convert` branch became the default on GitHub
- **Goal**: Get changes into `main` branch and set it as default

## Solution: Rename Branch (Recommended)

This is the simplest approach since you want to keep all your changes on the main branch.

### Commands to Run:

```bash
cd /Users/i339389_1/git/sites/prevodi-sema

# 1. Rename your local convert branch to main
git branch -m convert main

# 2. Push the main branch to GitHub
git push origin -u main

# 3. Delete the old convert branch from GitHub
git push origin --delete convert
```

### After Running Commands:

Go to GitHub and set `main` as the default branch:

1. Visit: https://github.com/terry81/prevodi-sema/settings/branches
2. Under "Default branch", click the switch icon
3. Select `main` from the dropdown
4. Click "Update"
5. Confirm the change

## Alternative: Keep Convert and Create Main

If you want to keep the convert branch and create a separate main branch:

```bash
cd /Users/i339389_1/git/sites/prevodi-sema

# 1. Create and switch to a new main branch from convert
git checkout -b main

# 2. Push main to GitHub
git push origin -u main

# 3. Optionally delete convert branch
git push origin --delete convert  # Remove from GitHub
git branch -d convert              # Remove locally
```

Then set `main` as default on GitHub (same steps as above).

## Verification

After completing the steps, verify everything:

```bash
# Check current branch
git branch

# Check remote branches
git branch -r

# Check what's on GitHub
git remote show origin
```

## Summary

The key steps are:
1. ✅ Rename `convert` → `main` locally
2. ✅ Push `main` to GitHub
3. ✅ Delete old `convert` branch from GitHub
4. ✅ Set `main` as default branch on GitHub web interface

Your 11ty site is ready to deploy once this is done!
