# git常用命令



### 初始化仓库

```git command
git init
```



### 本地仓库关联到远程仓库

```git command
git remote add origin git@github.com:xxx.git
```



### 将远程仓库拉到本地

```git command
git pull --rebase [[origin] master]
```



### 删除本地分支

```
git branch -d dev_1.0
```



### 删除远程分支

```
git push origin --delete dev_1.0

git push origin :dev_1.0
```

