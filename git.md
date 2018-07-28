# git的介绍和常用命令

## git介绍和安装
[参考教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)  
省略...

## 初始化git
- git init  
初始化git版本库
- git add git.md  
添加文件到暂存区
- git commit -m "submit git.md file"  
提交暂存区的文件到git库

## git版本管理
- git status  
查看工作区的状态  
- git diff git.md  
查看修改内容
- git log  
列出提交日志
- git log --pretty=oneline  
日志精简版单行显示
- git reset --hard HEAD^  
回退到上一个版本，HEAD指向的版本就是当前版本  
- git reset --hard [版本号]  
回退到指定版本
- git reflog  
查看历史命令
- git diff HEAD -- git.md  
查看工作区和版本库里面最新版本的区别
- git checkout -- git.md  
修改全部撤销，这里有两种情况
  - 一种是git.md自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
  - 一种是git.md已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态  
- git reset HEAD git.md  
可以把暂存区的修改撤销掉（unstage），重新放回工作区  
- git rm git.md  
删除文件到暂存区

## 远程仓库
- ssh-keygen -t rsa -C "youremail@example.com"  
生成公钥、密钥
- git remote add origin git@github.com:michaelliao/learngit.git  
关联一个远程库
- git push -u origin master
首次推送
- git push origin master  
推送到远程库
- git clone git@github.com:michaelliao/gitskills.git  
克隆远程库到本地

## 分支管理(dev, bug, feature)
- git checkout -b dev  
git checkout命令加上-b参数表示创建并切换，相当于以下两条命令git branch dev、git checkout dev
- git branch  
查看分支  
- git merge dev  
合并分支  
- git branch -d dev  
删除分支  
- git log --graph  
命令可以看到分支合并图
- git merge --no-ff -m "merge with no-ff" dev  
表示禁用Fast forward
- git stash  
把当前工作现场“储藏”起来，等以后恢复现场后继续工作
- git stash list  
列出存储的隐藏列表
- git stash pop  
pop出隐藏的列等同于这两个操作(git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除)
- git branch -D <name>  
强行删除未合并的分支  
- git remote -v  
查看远程库信息
- git push origin branch-name  
从本地推送分支
- git checkout -b branch-name origin/branch-name  
在本地创建和远程分支对应的分支，本地和远程分支的名称最好一致
- git branch --set-upstream branch-name origin/branch-name  
建立本地分支和远程分支的关联
- git pull
从远程抓取分支,如果有冲突，要先处理冲突
- git rebase  
rebase操作可以把本地未push的分叉提交历史整理成直线,目的是使得我们在查看历史提交的变化时更容易，因为分叉的提交需要三方对比。

## 标签管理
- git tag <tagname>  
用于新建一个标签，默认为HEAD，也可以指定一个commit id
- git tag -a <tagname> -m "blablabla..."  
指定标签信息
- git tag  
查看所有标签
- git push origin <tagname>  
推送一个本地标签
- git push origin --tags  
推送全部未推送过的本地标签
- git tag -d <tagname>  
删除一个本地标签
- git push origin :refs/tags/<tagname>
删除一个远程标签
