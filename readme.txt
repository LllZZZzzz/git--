Git is a version control system.
Git is free software.
1.
git init -初始化本地库（版本库）
git config username
git config useremail
git config --global username
git config --global useremail

2. git remote add origin(仓库别名) 仓库地址
   git push origin(仓库别名) 分支名
3.
git log
git log --pretty=oneline
需要友情提示的是，你看到的一大串类似1094adb...的是commit id（版本号），
和SVN不一样，Git的commit id不是1，2，3……递增的数字，而是一个SHA1计算出来的一个非常大的数字，
用十六进制表示，而且你看到的commit id和我的肯定不一样，以你自己的为准。为什么commit id需要用这么一大串数字表示呢？
因为Git是分布式的版本控制系统，后面我们还要研究多人在同一个版本库里工作，如果大家都用1，2，3……作为版本号，那肯定就冲突了。

4.版本回退（工作区、版本库回退）
git reset --hard HEAD^ 回退一步
git reset --hard commit_id
git log 查看提交历史 以便确定回退到哪个版本
git reflog (-- file) 查看命令历史 以便确定要回到未来的哪个版本
 
5.
为什么Git比其他版本控制系统设计得优秀，因为Git跟踪并管理的是修改，而非文件。
git diff HEAD命令可以查看工作区和版本库里面最新版本的区别

6.工作区回退
git checkout -- file可以丢弃工作区的修改
总之，就是让这个文件回到最近一次git commit或git add时的状态。
git reset HEAD -- file可以把暂存区的修改撤销掉（unstage），重新放回工作区。
已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。

7.文件删除
git rm删掉暂存区文件，并且git commit删除本地库文件
如果是删错了
再用git reset --hard 恢复本地库的文件
再用git ckeckout -- file恢复工作区文件 其实是用版本库里的版本替换工作区的版本

8.
首先必须知道仓库的地址，然后使用git clone命令克隆。
Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。
GitHub给出的地址不止一个，还可以用https://github.com/michaelliao/gitskills.git这样的地址。
实际上，Git支持多种协议，默认的git://使用ssh，但也可以使用https等其他协议。
使用https除了速度慢以外，还有个最大的麻烦是每次推送都必须输入口令，
但是在某些只开放http端口的公司内部就无法使用ssh协议而只能用https。

9.先拉取再合并！提交冲突   ===》先解决冲突

10.git的拉取和克隆有什么区别：
从远程服务器克隆一个一模一样的版本库到本地,复制的是整个版本库，叫做clone.（clone是将一个库复制到你的本地，是一个本地从无到有的过程）
从远程服务器获取到一个branch分支的更新到本地，并更新本地库，叫做pull.（pull是指同步一个在你本地有版本的库内容更新的部分到你的本地库）
git pull相当于是从远程获取最新版本并merge（合并）到本地

11.添加远程仓库并提交
要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git；
关联后，使用命令git push -u origin master第一次推送master分支的所有内容；
此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；

12.从远程库克隆
git clone git@github.com:michaelliao/gitskills.git

13.创建dev分支并进行合并 commit之后才进行合并的
git branch dev
切换到dev分支上
git checkout dev

git checkout -b dev（创建dev分支并切换到dev分支上 相当于上面两条命令的和）
在dev分支上进行工作，dev分支的工作完成，我们就可以切换回master分支。
git checkout master
git branch查看当前分支
现在，我们把dev分支的工作成果合并到master分支上
git merge dev 
合并完成后就可以放心的删除dev分支了
git branch -d dev

14.解决冲突
两个不同分支进行合并时，发生分支冲突，应该先解决冲突，再进行提交
用git log --graph命令可以看到分支合并图。

git merge --no-ff -m "merge with no-ff" dev
合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。
如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。
合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。

15.分支管理策略
首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；
干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；
你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。


16.bug分支
修复bug时，我们会通过创建新的bug分支issue-101进行修复，然后合并，最后删除；
当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场。

17.feature分支
开发一个新feature，最好新建一个分支；
如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除。

18.多人协作？？？？？？？？？？？
多人协作时，大家都会往master和dev分支上推送各自的修改。
当你的小伙伴从远程库clone时，默认情况下，你的小伙伴只能看到本地的master分支。
现在，你的小伙伴要在dev分支上开发，就必须创建远程origin的dev分支到本地，于是他用这个命令创建本地dev分支：
现在，他就可以在dev上继续修改，然后，时不时地把dev分支push到远程：
推送分支，就是把该分支上的所有本地提交推送到远程库。推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上：
$ git push origin master
哪些分支需要推送，哪些不需要呢：（其实完全看心情就好）
	master分支是主分支，因此要时刻与远程同步；
	dev分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；
	bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；
	feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。


合并分支merge与推送分支pull (解决冲突)+push（提交）