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
git log 
- `--pretty=oneline`:单行显示
- `--graph`：图像显示
- `--abbrev-commit`：缩写CommitID
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
git branch $branchname
# 15.切换分支
git checkout $branchname
# 16.创建并切换分支
git checkout -b $branchname
- `-b`：表示创建并切换，相当于创建`git branch $branchname`和切换`git checkout $branchname`两个命令。
# 17.查看分支
git branch
# 18.合并分支
git merge $branchname
- 合并指定分支到当前分支
- 合并结果中的`Fast-forward`表示快进模式，即直接将当前分支的指针指向指定分支的最新提交位置，故非常快。
- `--no-ff`：禁用`Fast-forward`模式，这样会在merge时生成新的commit信息。合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。
# 19.删除分支
git branch -d $branchname
# 20.解决冲突
1. 多分支同时修改同一个文件后add并commit；
2. merge分支时提示冲突；
3. 修改冲突文件后再次add并commit即可。
# 21.分支策略
1. master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；
2. dev分支干活，不稳定的.每个人都有自己的分支，时不时地往dev分支上合并就可以了。到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；
3.所以，团队合作的分支看起来就像这样：
![图1](https://www.liaoxuefeng.com/files/attachments/001384909239390d355eb07d9d64305b6322aaf4edac1e3000/0)