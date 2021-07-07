####  git常用命令整理

###### 创建版本库




``` 
   mkdir [folderName]:  创建文件夹
   
   cd  [folderName]: 切换到指定的文件夹
   
   git init :将指定的文件夹变成git可以管理的仓库
   
   git add [fileName]: 将文件添加到仓库（可多次使用，添加多个文件）
   
   git commit -m [msg]:  将文件提交到仓库
   
```
   
###### 版本回退
```
   git status :查看当前仓库的状态
   
   git diff : 查看工作区内容和版本库间的difference
   
   git log : 显示从最近到最远的提交日志
   
   git reset --hard HEAD^:回退到上一版本（git中用head 表示当前版本，每上一个版本就在head后加一个 '^'）
   
   git reset --hard  [commit_id]:  回到指定的commit版本号（版本号可写部分）
   
   git reflog  用于记录用户每一次命令（输出内容前，为commit的id的部分内容）

```

###### 工作区和暂存区

> 工作区(working directory)：在电脑里能看到的目录（不包含.git）  
  版本库（repository）：.git文件夹(存放内容包括称为stage的暂存区、自动创建的第一个分支master、指向master的指针HEAD)
  
**git add**  （添加文件）：实际作用就是将文件修改添加到暂存区  
**git commit** （提交更改）：实际作用就是将暂存区的所有内容提交到当前分支   
   

###### 撤销修改

```
 git checkout -- [fileName]:   撤销工作区文件的修改
 
 git reset HEAD [file] :将暂存区的修改撤销掉，重新放回工作区

```

###### 删除文件
```
git rm [fileName]:在工作区中删除文件后，版本库中依然存在，git rm 用于删除版本库中的版本，执行操作后，需要执行git commit操作
```

###### 远程仓库
 git是分布式版本控制系统，同一个git仓库，可以分布到不同的机器上

创建SSH Key  
```
 ssh-keygen -t rsa -C "youremail@example.com"

```

本地仓库下执行命令，将远程与本地关联：

```
 git remote add origin git@github.com:HuRuilin/learngit.git
```

将当前分支master推送到远程库上
```
git push -u origin master
```


###### 创建与合并分支

```
 git checkout -b [branchName]:创建并切换分支
 
 相当于：
 
 git branch [branchName]
 
 git checkout [branchName]
 
 git branch :查看分支信息
 
 git merge [branchName]:合并指定分支到当前分支
 
 git branch -d [branchName]:删除指定分支
```

###### 解决冲突

```
git log --graph ：查看冲突合并情况
```

###### 分支管理策略

<p>合并分支时，默认使用Fast forward模式，这种模式下，删除分支后，会丢掉分支信息，若强制禁用fast foward 模式，git就会在merge时生成一个新的commit</p>

```
git merge --no-ff -m "merge with no-ff" [branchName]:取消fast foward  模式，便于查看合并历史
```

###### BUG分支

```
git stash: 可以将当前工作现场“储藏”起来，等以后回复现场后继续工作

git stash list：查看保存的工作现场

git stash pop：将保存的工作现场恢复

git branch -D feature-vulcan ：强制删除分支
```


###### 多人协作

```
git remote:查看远程仓库的信息

git remote -v：查看远程仓库稍微详细信息
```


