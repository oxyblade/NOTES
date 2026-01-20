### Git Configuration

```
git config --global user.name "oxyblade"
git config --global user.email oxyblade@gmail.com
```

### Resolve large files

```
git status
git add .
git commit -m "Commit: `date`"
git filter-branch -f --index-filter 'git rm --cached --ignore-unmatch /server8/DB.sql'
```

### Delete remote branch

Удаление папки / каталога только из репозитория git, а не из локальной:

```
git push origin --delete branchName

git rm -r --cached FolderName
git commit -m "Removed folder from repository"
git push origin master
```

### fatal: cannot exec '/usr/bin/ksshaskpass': No such file or directory

```
sudo dnf install ksshaskpass
```

Alternative:
```
sudo dnf install /usr/bin/ksshaskpass
```