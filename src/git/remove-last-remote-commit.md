# Remove last remote commit

1. Remove commit locally
```
git reset --soft HEAD^
```
2. Force push to remote repository
```
git push origin +branch_name --force
```
3. If you need to delete made changes in commit
```
git reset --hard
```