<h3 id="lZPfQ">6 给文件重命名的简便方法</h3>
+ <font style="color:rgb(80, 80, 80);">git reset --hard </font>
+ <font style="color:rgb(80, 80, 80);">git mv </font>

<h3 id="RQA4K">7 通过 git log 查看版本演变历史</h3>
+ <font style="color:rgb(80, 80, 80);">git log --all 查看所有分支的历史</font>
+ <font style="color:rgb(80, 80, 80);">git log --all --graph 查看图形化的 log 地址 </font>
+ <font style="color:rgb(80, 80, 80);">git log --oneline 查看单行的简洁历史。 </font>
+ <font style="color:rgb(80, 80, 80);">git log --oneline -n4 查看最近的四条简洁历史。 </font>
+ <font style="color:rgb(80, 80, 80);">git log --oneline --all -n4 --graph 查看所有分支最近 4 条单行的图形化历史。 </font>
+ <font style="color:rgb(80, 80, 80);">git help --web log 跳转到git log 的帮助文档网页</font>

<h3 id="CuYLV"><font style="color:rgb(80, 80, 80);">8  git GUI界面 gitk 的使用方法 </font></h3>


<h3 id="oV5JB">9 探秘.git目录</h3>
+ HEAD：指向当前的工作路径
+ config：存放本地仓库（local）相关的配置信息
+ refs/heads：存放分支
+ refs/tags：存放 tag
+ objects：存放对象。.git/objects/文件中的的子文件都是以哈希值的前2位字符命名。每个 object 由 40 个字符组成，前 2 位字符用来当文件夹，后38位用作文件。	
+ git cat-file -t  // 显示版本库对象的类型
+ git cat-file -s // 显示版本库对象的大小
+ git cat-file -p // 显示版本库对象的内容
+ git branch -av // 查看本地分支

<h3 id="Fss43">10 commit tree blob 对象之间的关系</h3>
![](https://cdn.nlark.com/yuque/0/2024/png/166664/1728182389133-923935fc-bc9b-45d3-a52e-09a209698d89.png)



<h3 id="nbPQQ">12 分离头指针情况下的注意事项</h3>
+ <font style="color:rgb(80, 80, 80);">git checkout commitId：会出现分离头指针的情况，这种情况下比较危险，因为这个时候你提交的代码没有和分支对应起来，当切换到其他分支的时候(比如master分支)，容易丢失代码； 但是分离头指针也有它的应用场景，就是在自己做尝试或者测试的时候可以分离头指针，当尝试完毕没有用的时候可以随时丢弃，但是如果觉得尝试有用，那么可以新建一个分支，使用 git branch <新分支的名称> commitId</font>

<h3 id="iHyIA"><font style="color:rgb(80, 80, 80);">13 HEAD 和 branch 的区别</font></h3>
+ <font style="color:rgb(80, 80, 80);">一个节点，可以包含多个子节点（checkout 出多个分支） </font>
+ <font style="color:rgb(80, 80, 80);">一个节点可以有多个父节点（多个分支合并） </font>
+ <font style="color:rgb(80, 80, 80);">^是~都是父节点，区别是跟随数字时候，^2 是第二个父节点，而~2是父节点的父节点</font>
+ <font style="color:rgb(80, 80, 80);"> ^和~可以组合使用,例如 HEAD~2^2</font>

<font style="color:rgb(80, 80, 80);"> </font>

<h3 id="k6vAG"><font style="color:rgb(80, 80, 80);">14 怎么删除不需要的分支</font></h3>
+ git branch -d ：<font style="color:rgb(80, 80, 80);">在删除前Git会判断在该分支上开发的功能是否被merge的其它分支。如果没有，不能删除。如果merge到其它分支，但之后又在其上做了开发，使用-d还是不能删除</font>
+ <font style="color:rgb(80, 80, 80);">git branch -D ：强制删除</font>

<font style="color:rgb(80, 80, 80);"></font>

<h3 id="Ndlno"><font style="color:rgb(80, 80, 80);">15 怎么修改最新 commit 的 message</font></h3>
+ git commit --amend 

<h3 id="CArFx">16 怎么修改老旧 commit 的 message</h3>
+ git rebase -i [父节点的 commitId]   
+ 如果要更改第一次提交：git rebase -i --root 



<h3 id="nwOpk">19 怎么比较暂存区和 HEAD 所含文件的差异</h3>
+ git diff --cached [文件名]



<h3 id="WSw8y">20 工作区与暂存区的差异</h3>
+ git diff -- [文件名] [文件名] 



<h3 id="CKGjU">21 如何让暂存区恢复成和HEAD的一样</h3>
+ git reset HEAD 



<h3 id="MOhqM">22 如何让工作区的文件恢复为和暂存区一样</h3>
+ git checkout -- [文件名]



<h3 id="hkLCq">23 怎么取消暂存区部分文件的更改</h3>
+ git reset HEAD -- [文件名] [文件名]



<h3 id="EWBfD">24 消除最近的几次提交</h3>
+ git reset --hard [commitId] 

<h3 id="b5YKv">25 看看不同提交的指定文件的差异</h3>
+ git diff temp master -- index.html
+ git diff [branchId] [branchId] -- [文件名]



<h3 id="gTYCa">26 正确删除文件的方法</h3>
+ git rm [filename]



<h3 id="MDCCW">27 开发中临时加塞了紧急任务怎么处理</h3>
+ git stash list
+ git stach apply

<h3 id="VYMT6">28 如何指定不需要 Git 管理的文件</h3>
+ 创建 .gitignore 文件
+ doc/ 不管 doc 文件夹下面的文件，doc 还是管的

