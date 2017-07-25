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
git reset
- `HEAD`表示当前版本
- `HEAD^`表示上个版本，`HEAD^^`上上个版本
- `HEAD~100`上100个版本