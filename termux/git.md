# 创建远程分支

### 创建本地分支并切换

```shell
git branch -b branch_name
```
### 推送到远程仓库

```shell
git push -u branch_name(本地分支名):branch_name(远程分支名)
```

# 合并本地分支

### 删除dev分支

```shell
git merge dev
```

### 删除本地分支dev

```shell
git branch -d dev
```

### 推送远程仓库

```shell
git push -u origin main
```

# 删除远程仓库分支

```shell
git push origin -d dev(远程分支名)
```

# 创建repo时的提示

```shell
echo "# tmux" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main

git remote add origin git@github.com:develop202/tmux.git

git push -u origin main
```

```shell
git remote add origin git@github.com:develop202/tmux.git

git branch -M main
git push -u origin main
```