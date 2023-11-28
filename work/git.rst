git 简介
^^^^^^^^^^^^^^^^^^

git各分区转换
===================

使用git时常常对各种分区的转换犯迷糊，下面这张图很好的介绍了共有哪些状态，如何转换？
    
#. 首页了解下git所处的4种区 (工作区, 暂存取，本地仓库, 远程仓库)
    相互转化关系如下 ::

        +-------+               +----------+                  +----------+                        +----------+
        |       |  git add .    |          |  git commit      |          |  git push              |          |
        | 工作区 |  -----------> |  暂存区  | ---------------> | 本地仓库  | ---------------------> | 远程仓库  |
        |       |  <----------- |          | <--------------- |          |  <-------------------- |          | 
        |       |   git reset   |          | git reset --hard |          |  git reset --hard^ or  |          | 
        |       |               |          | origin/master    |          |  git reset --hard XXX  |          |
        |       |               |          |                  |          |  git push --force      |          |
        +-------+               +----------+                  +----------+                        +----------+
	
    - git add . (git add <file>) ：加入到暂存区
	- git commit -m "add: xxx" : 加入到本地仓库
	- git push origin master : 加入到远程仓库

#. git的5种状态
	- Origin(未修改)
	- Modified(已修改)
	- Staged(已暂存)
	- Committed(已提交)
	- Pushed(已推送)

#. git diff 对比修改
	- 已修改，未暂存：git diff
	- 已暂存，未提交: git diff --cached
	- 已提交，未推送: git diff master origin/master

#. 撤销修改(观看上面的图)
	- 已修改，未暂存：git checkout . (git checkout <file>)
	- 已暂存，未提交: git reset (git reset --hard 会覆盖)
	- 已提交，未推送: git reset --hard origin/master (远程仓库覆盖本地仓库)
	- 已推送: git reset --hard <commitID> (如果要覆盖远程必须强制推 git push -f)

#. 基本状态标识
	- A- = untracked 未跟踪
	- A = tracked 已跟踪未修改
	- A+ = modified - 已修改未暂存
	- B = staged - 已暂存未提交
	- C = committed - 已提交未PUSH

#. 各状态之间变化
	- A- -> B : git add <FILE>
	- B -> A- : git rm --cached <FILE>
	- B -> 删除不保留文件 : git rm -f <FILE>
	- A -> A- : git rm --cached <FILE>
	- A -> A+ : 修改文件
	- A+ -> A : git checkout -- <FILE>
	- A+ -> B : git add <FILE>
	- B -> A+ : git reset HEAD <FILE>
	- B -> C : git commit
	- C -> B : git reset --soft HEAD^
	- 修改最后一次提交:git commit --amend

A+ -> A-  可以git checkout命令来解决，如果被修改的文件没有回退到原始状态，检查下该目录是否属于submodules，如果是，则进入该子模块目录，恢复该文件的状态。

git 统计代码提交行
=======================

#. 统计某时间段的代码行

   .. code-block:: bash
   
       git log --since=2017-04-10 --until=2017-07-10 --oneline | wc -l
       
#. 统计某人的代码量

   .. code-block:: bash
   
        git log --author="$(git config --get user.name)" --pretty=tformat: --numstat | gawk '{ add += $1 ; subs += $2 ; loc += $1 - $2 } END { printf "added lines: %s removed lines : %s total lines: %s\n",add,subs,loc }' 
        
#. 仓库排名前5

   .. code-block:: bash
   
        git log --pretty='%aN' | sort | uniq -c | sort -k1 -n -r | head -n 5
      
参考 `CSDN代码行统计`_


.. _CSDN代码行统计: https://blog.csdn.net/carterslam/article/details/81162463