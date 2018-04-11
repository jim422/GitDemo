git clone https://github.com/jim422/GitDemo.git (克隆远程厂库)

git add .
git add <file> (把工作区的代码提交到暂存区)
git reset HEAD <file> (取消暂存的文件)

git commit -m 'message' (把暂存区的代码提交到本地库)
git reset --hard <commit_id> (重置当前的 HEAD 到一个指定的状态。直接删除该状态后续的所有提交（就像没提交过一样），日志上表现为丢弃对应 commit id 后的所有日志, 不建议使用)

git push origin <分支名> (将本地库的代码推送到远程服务器上)

git branch <分支名> 创建分支
git checkout  <分支名> 切换分支
git checkout -b <分支名> 创建并切换分支

git merge <分支名> 合并代码

git merge --no-ff (no fast-forward merge 强行关闭fast-forward方式)


