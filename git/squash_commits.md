# Squashing GIT Commits into one

## 1. Squash on merge

```bash
git merge <branch> --squash
```
This will take all the commits from the <branch>, squash them into 1 commit, and merge it with your current branch.


## 2. Squash but don't merge yet

```bash
git reset --soft HEAD~<number-of-commits-to-squash>
```

This will essentially undo all commits and place all changes in staging, allowing you to simply commit with a nice message. From here you can do whatever you want, be it push your branch, continue coding or procceed with a merge.

On the off chance you added a few more changes and wanted to add them to the squash commit but don't want to type the relatively risky reset command, you can much more confidently use the following.
```bash
git commit --amend
```
This will add your new changes to the previous commit. Without the -m flag, it will open the default editor and allow you to edit your previous message. Otherwise the -m will simply allow you to write a new message to overwrite the previous one.

Do keep in mind that if you run this command after having pushed the squashed commits, you'll be forced to either merge or use `git push -f` (-f: force push). This is because you've ammend edits the latest commit, resulting in the commit history not lining up. Generally, I prefer to use -f however do make sure you're the only person who is commiting to this branch.
