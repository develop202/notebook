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

# 单用户创建多个私钥连接不同平台云端仓库

1. 生成ssh密钥，第一次输入文件名，第二次输入密码

```shell
ssh-keygen -t rsa -b 2048 -C "tt"
```

1. 添加配置到~/.ssh/config

```shell
Host xxx.com # 随便填，不能重复
AddKeysToAgent yes # 减去反复ssh-add的烦恼
HostName xxx.com # 目标主机
PreferredAuthentications publickey # 不知道是啥，看着都有，我也加上
IdentityFile ~/.ssh/tt # 生成的私钥位置
```
