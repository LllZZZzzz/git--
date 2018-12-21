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
git reflog 查看命令历史 以便确定要回到未来的哪个版本
 4.
123