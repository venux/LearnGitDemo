# [git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
# 1.初始化
git init
# 2.添加到仓库
git add $filename
# 3.提交到仓库
git commit -m "$comment"
# 4.查看状态
git status
# 5.对比修改记录
git diff
# 6.查看提交日志
git log [--pretty=oneline]
# 7.版本回退
git reset --hard
- `HEAD`表示当前版本
- `HEAD^`表示上个版本，`HEAD^^`上上个版本
    - git reset --hard HEAD^
    -  **注意：^在CMD中需要用双引号括起来**
- `HEAD~100`上100个版本
- `versionId`版本号（可只写前几位）：
    -  git reset --hard cfab68213adec8795db301414287dfccadb30499
# 8.查看命令历史
git reflog
# 9.撤销修改
-  未添加到暂存区：git checkout -- $filename
-  已添加到暂存区：git reset HEAD $filename
# 10.删除文件
git rm $filename
# 11.添加远程库
git remote add origin $giturl
- 远程库默认名为`origin`
# 12.推送当前分支master到远程库origin
git push -u origin master
- `-u`：由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
- 第二次后就可去掉`-u`参数直接推送。
# 13.克隆
git clone $giturl
# 14.创建分支
git checkout -b $branchname
- `-b`：表示创建并切换，相当于`git branch $branchname`和`git checkout $branchname`