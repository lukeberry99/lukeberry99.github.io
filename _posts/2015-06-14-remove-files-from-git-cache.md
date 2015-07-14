---
layout: post
title: Remove files from git cache
---

Accidentally commit a folder or file to git? Add the file name / path to your `.gitignore` and run this script to remove all files on your ignore list from the git cache.

### Script
    git ls-files -ci --exclude-standard -z | xargs -0 git rm --cached
