# Hello Welcome to my Blog

# Git指令:
场景一: 开发分支（dev）上的代码达到上线的标准后，要合并到 master 分支
- git checkout dev
- git pull
- git checkout master
- git merge dev
- git push -u origin master
场景二: 当master代码改动了，需要更新开发分支（dev）上的代码
- git checkout master 
- git pull 
- git checkout dev
- git merge master 
- git push -u origin dev

Git 重命名:
- mv xxx xxx.md
- Git add xxx.md
- Git rm xxx
- 以上三个命令等同于: Git mv xxxx xxxx.md

提交:(修改, 合并, 重命名)
- git commit -am’XXX’ : 直接将工作区的内容, 直接提交到版本历史库中
- git commit --amend: 修改最新提交的message的变更
- git rebase -i xxx: 修改xxx提交的message(自己的分支上)(xxx是父cm)
    - pick 变为r
    - :wq!
    - 修改cm信息
- git rebase -i xxx : git 把连续多个cm合并成一个cm
    - pick 变为 s : 将s和到上面的cm中
    - :wq!
    - ##之间添加新的message
- git rebase -i xxx : git 把间隔的cm合并成一个cm
    - pick 变为 s : 将s和到上面的cm中
    - 移动后面更改的pick 分支 到 最新的下面

Git reset: 
- git reset --hard
- git reset --hard xxx: 回退到xxx提交时候的代码 (消除最近的几次提交)
- git reset HEAD: Unstaged取消暂存区的内容, 让暂存区恢复和HEAD一致(当我们提交到暂存区一部分代码时候, 又写了一段代码之后发现目前工作区的代码更好, 想清空暂存区的内容) 

查看历史:
- git log
- git log --all
- git log --all --graph
- git log --online
- git log -n4 --oneline

本地分支
- git branch -v
- Git checkout -b temp xxxx(commit号) : 创建一个临时分支

.git文件夹:
- HEAD: 整个仓库正处于哪个引用
- config: 存放本地的配置

查看文件:
- cat xxx :查看xxx文件内容
- git cat-file -t xxx: 查看xxx文件的类型
- git cat-file -p xxx: 查看xxx文件的内容

分支(创建, 删除):
- git checkout -b xxx1 xxx2: 检出xxx2, 并且创建新的xxx1分支
- git branch -d xxx: 删除xxx分支
- git branch -D xxx: 删除xxx分支

比较差别:
- git diff HEAD HEAD~2 == Git diff HEAD HEAD^^
- git diff HEAD HEAD^1: 比较HEAD和HEAD父节点的差别
- git diff cm1 cm2: 比较cm1和cm2两个分支的差别
- git diff --cached: 比较暂存区和HEAD所指向文件的差别
- git diff --xxx xxx1: 比较xxx, xxx1两个文件的差别
- git diff cm1 cm2 --xxx: 比较cm1和cm2两个分支下的xxx文件的差别

Stash:
- git stash: 暂存当前暂存区的文件
- git stash list: 查看stash列表
- git stash apply: 不删除原来的stash内容
- git stash pop: 删除原来的stash内容

删除文件:
- git rm filename: 删除filename文件

一个commit包含什么:
- Tree
- blob
- Tree
- Commit

如何比较暂存区和HEAD所含文件的差异: git diff —cached
如何比较工作区和暂存区所含文件的差异: git 
如何高效的淘到感兴趣的开源项目: 
- XX XC XV XB in:readme stars:>1000 : 搜索XX XC XV XB在readme中, 并且stars大于1000
