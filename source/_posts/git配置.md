---
title: git 对于github与gitee基本配置
tags:
- hexo
- 搭建
- git
categories:
- 工具
---
### git基本配置
```bash
git config --global user.name "username"    //（ "username"是自己的账户名，）
git config --global user.email "username@email.com" 

ssh-keygen -t rsa -b 4096 -C "469307379@qq.com" -f "id_rsa_github"
ssh-keygen -t rsa -b 4096 -C "469307379@qq.com" -f "id_rsa_gitee"

ssh-agent bash

ssh-add ~/.ssh/id_rsa_github
ssh-add ~/.ssh/id_rsa_gitee

cat ~/.ssh/id_rsa_gitee.pub 
cat ~/.ssh/id_rsa_github.pub
```
#### 将公钥部署到github和gitee上
#### 然后尝试连接
```
ssh -T git@gitee.com
ssh -T git@github.com 
```
---
### 假设开发了一个新项目，想推送到远程，具体的操作方式和命令如下：
```bash
（使用 git bash）

1、切到项目目录中，例如 

E:\httpRunner_study
2、初始化git仓库并在本地提交

//初始化git仓库 
git init

//将当前目录下的文件添加到仓库（缓冲区）
git add .

//提交到本地仓库
git commit -m "init project"
3、把本地仓库和远程关联，并推送到远程

//与远程仓库关联
git remote add origin 远程仓库地址

//例如: 关联一个远程库时必须给远程库指定一个名字，origin是默认习惯命名；
git remote add origin git@server-name:path/repo-name.git

//推送到远程仓库
git push -u origin master
执行以上操作就可以把本地新建的项目推送到 git 远程仓库了。

但在实际操作中，最后一步推送命令会报错，提示需要先  git pull 更新，而如果执行 git pull 或者 git pull origin master 都无法成功执行，会有其他的报错。

解决方案是，使用如下命令，强制推送到远程（可能会覆盖远程上已有分支、文件，使用前需要注意）

//强制推送到远程（可能会覆盖远程上已有的分支或文件）
git push -u origin master -f
注意：仅第一次需要这样执行，后续在推送代码时，git push 命令不需要再加上 -u 或者 -f 命令，使用正常推送命令就行了。

推送成功以后，就可以在本地项目中正常使用 git 命令进行更新、提交、推送等操作了。
```