git clone https://github.com/jim422/GitDemo.git (克隆远程厂库)

### git add .

git add <file> (把工作区的代码提交到暂存区)

### git reset HEAD <file> (取消暂存的文件)

### git commit -m 'message' (把暂存区的代码提交到本地库)

### git reset --hard <commit_id> (重置当前的 HEAD 到一个指定的状态。直接删除该状态后续的所有提交（就像没提交过一样），日志上表现为丢弃对应 commit id 后的所有日志, 不建议使用)

### git push origin <分支名> (将本地库的代码推送到远程服务器上)

### git branch <分支名> 创建分支

### git checkout  <分支名> 切换分支

### git checkout -b <分支名> 创建并切换分支

### git merge <分支名> 合并代码

### git merge --no-ff (no fast-forward merge 强行关闭fast-forward方式)

### git merge --squash 分支名 (git中将多次commit合并为一次commit)

### git stash(“‘储藏”“可以获取你工作目录的中间状态——也就是你修改过的被追踪的文件和暂存的变更——并将它保存到一个未完结变更的堆栈中，随时可以重新应用)
    应用场景：假如你现在再并行两个项目，一个是开发阶段，另一个是测试阶段，开发阶段的项目是再A分支，测试阶段的分支是B分支。你在A分支上开发到一半时测试提出bug，这时你需要切换到B分支上去修改，但切换到B分支的时候会把你A分支上修改的代码带过去，而你此时并不想 commit A分支的代码来产生多余的commit记录，这时git stash 就派上用场了。
    
    git stash: 直接git stash 的话 git 会给你一个hash值作为一个版本信息
    git stash save '推荐方式': git 会将 '推荐方式' 作为此次的版本信息
    
    git stash list: 查看现有的储藏
    
    git stash apply stash@{n}: 根据版本信息回到保存的版本
    
    git stash pop: 将git stash栈中最后一个版本取出来
    

附件链接：[链接](download/规范网站使用-NCC1909快捷键-Enter版 0828.xlsx)
