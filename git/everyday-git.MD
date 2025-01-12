## To Track the Remote Branch
Set the New Branch to Track the Remote Branch (Optional but recommended):
```bash
git push --set-upstream origin <branch-name>
```

## To delete the remote branch
To delete the remote branch, you can use the following command:
```bash
git push origin --delete branch_name
```

## to see what branches have been merged into
Run the following command to see what branches have been merged into main (without switching to main):
```bash
git branch --merged main
```

## push to the main branch on the remote
This command explicitly specifies that you want to push to the main branch on the origin remote.
```bash
git push origin main
```

The Following uses the default settings (typically origin and the branch you’re currently on). It pushes the changes to the upstream branch set in your repository.
```bash
git push
```

## To merge changes from the remote-tracking branch
When you run this command, you are telling Git to merge changes from the remote-tracking branch origin/main (which is your local copy of the remote main branch) into your current branch. This way, you bring in the changes from the remote main branch into your current branch.
```bash
git merge origin/main
```

## Merge without fast-forward
Merge branch without fast-forward
```bash
git merge develop --no-ff
```
Using --no-ff when merging can be a valuable strategy for maintaining clarity in your project's commit history. It provides a clear understanding of when features or changes were integrated, which can be especially useful for larger teams or long-term projects.

## ERR: your branch and `origin/main` have diverged
When you see a message indicating that your branch and `origin/main` have diverged, it means that:

1. **Your local `main` branch** has commits that are not on the remote `main` branch.
2. **The remote `main` branch** has commits that are not on your local `main` branch.

To resolve this, 

### Merge the Remote Changes

1. **Fetch the latest changes from the remote**:
   ```bash
   git fetch origin
   ```
   This updates your local tracking branches without modifying your working directory.

2. **Merge the remote `main` branch into your local `main`**:
   ```bash
   git merge origin/main
   ```
   This will merge the changes from the remote `main` into your local `main`. If there are conflicts, Git will notify you, and you’ll need to resolve them.

3. **Push the merged changes back to the remote** (if needed):
   ```bash
   git push origin main
   ```
   This updates the remote repository with your merged changes.

## New Branch from the commit hash or the branch
This command create a new branch `fix01` starting from the end of `bugfix` branch
```bash
git branch fix01 bugfix
```

### Set the Correct Upstream Branch
To set the upstream branch for your local `develop` branch correctly, use the following command:
```bash
git branch --set-upstream-to=origin/develop develop
```
