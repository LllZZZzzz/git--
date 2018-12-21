Git is a version control system.
Git is free software.
1.
git init -初始化本地库
git config username
git config useremail
git config --global username
git config --global useremail

2.
git log
git log --pretty=oneline
需要友情提示的是，你看到的一大串类似1094adb...的是commit id（版本号），
和SVN不一样，Git的commit id不是1，2，3……递增的数字，而是一个SHA1计算出来的一个非常大的数字，
用十六进制表示，而且你看到的commit id和我的肯定不一样，以你自己的为准。为什么commit id需要用这么一大串数字表示呢？
因为Git是分布式的版本控制系统，后面我们还要研究多人在同一个版本库里工作，如果大家都用1，2，3……作为版本号，那肯定就冲突了。

3.
git reset --hard HEAD^ 回退一步
git reset --hard commit_id
git log 查看提交历史 以便确定回退到哪个版本
git reflog (-- file) 查看命令历史 以便确定要回到未来的哪个版本
 
4.
为什么Git比其他版本控制系统设计得优秀，因为Git跟踪并管理的是修改，而非文件。
git diff HEAD命令可以查看工作区和版本库里面最新版本的区别

5.
git checkout -- file可以丢弃工作区的修改
总之，就是让这个文件回到最近一次git commit或git add时的状态。
git reset HEAD -- file可以把暂存区的修改撤销掉（unstage），重新放回工作区。
已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。

6.
git rm删掉工作区和暂存区文件，并且git commit删除本地库文件
再用git reset --hard 恢复本地库的文件
再用git ckeckout -- file恢复工作区文件

7.
首先必须知道仓库的地址，然后使用git clone命令克隆。
Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。
GitHub给出的地址不止一个，还可以用https://github.com/michaelliao/gitskills.git这样的地址。
实际上，Git支持多种协议，默认的git://使用ssh，但也可以使用https等其他协议。
使用https除了速度慢以外，还有个最大的麻烦是每次推送都必须输入口令，
但是在某些只开放http端口的公司内部就无法使用ssh协议而只能用https。