Git 常用命令速查表（完整版）
一、基础配置
bash
运行
# 设置用户名和邮箱（全局）
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"

# 查看配置
git config --global --list
二、仓库初始化 & 克隆
bash
运行
# 本地新建Git仓库
git init

# 克隆远程仓库到本地
git clone 仓库地址
# 克隆并指定文件夹名
git clone 仓库地址 自定义文件夹名
三、文件暂存 & 提交
bash
运行
# 查看文件状态
git status

# 添加单个文件到暂存区
git add 文件名
# 添加所有文件到暂存区
git add .

# 提交到本地仓库
git commit -m "提交说明"

# 修改上一次提交注释（未推送远程）
git commit --amend
四、分支操作（高频）
bash
运行
# 查看本地分支
git branch
# 查看所有分支（本地+远程）
git branch -a

# 新建分支
git branch 分支名

# 切换分支
git checkout 分支名
# 新建并直接切换到该分支
git checkout -b 分支名

# 合并分支（把目标分支合并到当前分支）
git merge 目标分支名

# 删除本地分支
git branch -d 分支名
# 强制删除本地分支
git branch -D 分支名
五、远程仓库
bash
运行
# 关联远程仓库
git remote add origin 仓库地址

# 查看远程关联
git remote -v

# 拉取远程代码（合并到本地）
git pull

# 推送本地分支到远程
git push origin 分支名
# 首次推送绑定远程分支
git push -u origin 分支名
六、代码回滚（重点）
bash
运行
# 查看提交记录
git log
# 简洁版查看记录
git log --oneline

# 1. 工作区撤销修改（未add）
git checkout -- 文件名
# 撤销所有文件工作区修改
git checkout -- .

# 2. 撤销暂存区（已add，未commit）
git reset HEAD 文件名
git reset HEAD .

# 3. 版本回滚（已commit）
# 软回滚：保留代码改动，回到暂存前
git reset --soft 版本号
# 混合回滚（默认）：回到工作区
git reset 版本号
# 硬回滚：彻底丢弃所有改动，谨慎用！
git reset --hard 版本号
七、冲突解决
拉取代码出现冲突
bash
运行
git pull
打开冲突文件，手动修改：
保留自己代码：删掉 <<<<HEAD、=====、>>>>远程分支 标记
解决完后重新提交
bash
运行
git add .
git commit -m "解决分支合并冲突"
git push
八、暂存临时修改（stash）
适合临时切分支，不想提交当前改动
bash
运行
# 暂存当前所有修改
git stash

# 查看暂存列表
git stash list

# 恢复最近一次暂存（不删除暂存记录）
git stash apply
# 恢复并删除暂存记录
git stash pop

# 删除所有暂存
git stash clear