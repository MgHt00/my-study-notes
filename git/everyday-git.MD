Set the New Branch to Track the Remote Branch (Optional but recommended):
```bash
git push --set-upstream origin <branch-name>
```

To delete the remote branch, you can use the following command:
```bash
git push origin --delete branch_name
```

Run the following command to see what branches have been merged into main (without switching to main):
```bash
git branch --merged main
```

This command explicitly specifies that you want to push to the main branch on the origin remote.
```bash
git push origin main
```
`git push`: Uses the default settings (typically origin and the branch you’re currently on). It pushes the changes to the upstream branch set in your repository.
