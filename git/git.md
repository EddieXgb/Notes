![](https://ws3.sinaimg.cn/large/006tNbRwly1fxtkfrm0cdj30ps0m8dhi.jpg)

#### Git基本命令

```git init```              # git初始化

```git status```  	# 查看当前git状态

```git add .```           # 添加当前目录下所有文件到版本库

```git commit -m  '提交信息'```        # 提交到版本库，并填写版本说明，以便以后回滚

```touch XXX.py```     # 创建新文件

```git log ```               # 查看历史版本提交记录（根据版本commit值可以进行回滚，--pretty=oneline 加上参数可以只显示版本号和提交时的备注）



#### Git版本回退

![](https://ws1.sinaimg.cn/large/006tNbRwly1fxtknispsij30qk156n0u.jpg)

```git reset```		#根据commit版本号回退

```git reflog```		#可以查看所有分支的所有操作记录（包括已经被删除的 commit 记录和 reset 的操作）



###Git stash

```git stash```           	# 将开发到一半的功能，临时存储到“某个地方”

```git stash pop```   	# 将第一个记录从“某个地方”重新拿到工作区（可能有冲突）

```git stash list``` 	# 查看“某个地方”存储所有记录

```git stash clear```       # 清空“某个地方”

```git stash apply ```       # 将指定编号记录从“某个地方”重新拿到工作区（可能有冲突）

```git stash drop```		# 删除指定编号的记录



### Git分支

__方案一：__

![](https://ws3.sinaimg.cn/large/006tNbRwly1fxtl2ugns5j31um0iwq7u.jpg)

```git checkout master``` 		# 切换回master分支

```git merge dev```               		# 将dev分支内容合并到master分支

__方案二：__

![](https://ws3.sinaimg.cn/large/006tNbRwly1fxtl6jgqabj326m0he0yx.jpg)

```git branch```                     		# 当前在master分支

```git branch dev```                 	# 创建dev分支用于开发新功能

```git checkout dev```			# 切换到dev分支



开发一半需要修复bug

```git checkout master```		# 切换回master分支

```git branch bug```                 	# 创建bug分支

```git checkout bug```			# 切换到bug分支

```git checkout master```		# 切换会master

```git merge bug```		# 将bug分支内容合并到master分支，表示bug修复完毕，可以上线



__branch相关常用命令：__

- git branch 分支名称             创建分支
- git checkout 分支名称          切换分支
- git branch -m 分支名称        创建并切换到指定分支
- git branch                          查看所有分支
- git branch -d 分支名称         删除分支
- git merge 分支名称              将指定分支合并到当前分支



### GitHub托管

__将项目从GitHub中获取,默认获取到得只有master分支__

```
git clone https://github.com/Eddie/pondo.git
```

__创建dev分支且和远程dev分支同步__

```
git branch dev origin/dev
```

__提交dev分支内容到远程GitHub托管仓库的dev分支__

```
git push origin dev
```

__从远程GitHub仓库获取dev分支最新内容，并合并到本地__

```
git pull origin dev 
```

__从GitHub仓库获取dev分支最新内容到版本库的分支__

```
git fetch origin dev
```

__# 将版本库的分支内容合并到工作区__

```
git merge origin/dev
```

__为地址起一个别名origin__

```
git remote add origin https://github.com/Eddie/test.git
```

__将本地master分支内容以及版本信息推送到GitHub__

```
git push origin master
```

__将本地dev分支内容以及版本信息推送到GitHub__

```
git push origin dev 
```



### 配置

__Git的配置文件有三个：__

- 系统配置： /private/etc/gitconfig
- 用户配置： ~/.gitconfig
- 项目配置：.git/config