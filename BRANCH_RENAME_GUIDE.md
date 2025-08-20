# Branch Renaming Guide: master → main

This guide provides step-by-step instructions to rename the default branch from `master` to `main` for the try-it-editor-offline repository.

## Prerequisites
- Repository admin/owner access
- Git CLI or GitHub web interface access

## Method 1: Using GitHub Web Interface (Recommended)

1. **Navigate to Repository Settings**
   - Go to https://github.com/afeiship/try-it-editor-offline
   - Click on "Settings" tab
   - Scroll down to "Branches" section

2. **Rename the Default Branch**
   - Click the pencil icon next to "master" branch
   - Change the branch name from "master" to "main"
   - Click "Rename branch"

3. **Update Local Repositories**
   - GitHub will provide instructions for updating local clones
   - All collaborators should run:
     ```bash
     git branch -m master main
     git fetch origin
     git branch -u origin/main main
     git remote set-head origin -a
     ```

## Method 2: Using Git CLI

1. **Create and Push New Branch**
   ```bash
   git checkout master
   git branch -m master main
   git push -u origin main
   ```

2. **Update Default Branch on GitHub**
   - Go to repository settings and set "main" as default branch

3. **Delete Old Branch**
   ```bash
   git push origin --delete master
   ```

## Post-Rename Checklist

- [ ] Update any CI/CD workflows that reference `master`
- [ ] Update documentation that mentions `master` branch
- [ ] Notify all contributors about the branch name change
- [ ] Update any deployment scripts or automation

## Code References Analysis

The following files were checked for hardcoded branch references:
- ✅ No internal code references to "master" branch found
- ✅ External library references in `js/FileSaver.js` (no action needed)
- ✅ No GitHub workflow files requiring updates
- ✅ No documentation requiring updates

## Notes

- The rename is safe as no internal code references the master branch
- External URLs in FileSaver.js reference the upstream library and should not be changed
- This repository currently has no GitHub Actions workflows that would need updating