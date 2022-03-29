git learning progess
-----------------------------------------------------------------------
2022.3.4:
git init //将当前文件夹设定为收GIT管理的repository
git add 文件名//将该文件列入修改列表，即一个称作stage或index的缓存区
git commit -m " 提交修改，-m后接“备注” "，即将stage中的内容移到分支中，初学时即移到master区域
git status //查看当前git管理目录的状态
git reflog //查看历史commit及其ID
git global user.name ""
git global user.email "" //将所有库设为name，email 所有
git commit未加注释的解决办法，或注释写错了：
{git commit --amend //修改最近一次提交的注释信息，进入到vim编辑器
c进入编辑状态
Esc (退出编辑状态)
:wq 保存文件并退出vim编辑
适用于windows系统}
//分支Branch相关
git branch//用此命令查看当前分支
git merge <name>//合并某分支到当前分支
git rebase xxx//将xxx头部连上当前分支指针处
注:git branch实质上是对分支指针进行操作
而git switch和git checkout则是对HEAD指针操作
git branch -f xxx 位置//
注:git merge往后移，git branch往前移
位置:哈希表或快速引用(~n或^^^)

git checkout -b xxx //创建一个新的名叫xxx的仓库并切换到xxx分支,-b代表创建并切换
# 以上等同于 git switch -c xxx// -c代表创建并切换
git branch xxx
git checkout xxx//或git switch xxx

git brach -d xxx //-d代表删除当前分支

//更多1
git cherry-pick id1 id2 id3...//可将对应提交直接拉到当前分支来
git rebase -i xxid//提供一个交互界面手动删除修改
应用场景:
1:突发bug，快快debug，终于修好了，此时可直接cherry-pick把修改好的提交抓取过来
2:想要修改以前的一些提交：可rebase -i排序，然后commit --amend修改，最后再rebase --amend排序；
或者根据情况branch -f移动main然后cherry-pick

//更多2
git tag v1.0 xxid//为xxid的提交建立一个不动的指针v1.0指向它
可直接switch到v1.0，但此时处于HEAD分离状态，无法commit
git describe <refid>//查找id提交之前的最近tag，
其返回为<tag>_<numCommits>_g<hash>//标签名 距离 哈希值

//撤销相关
HEAD指指向当前分支的当前版本
git reset --hard HEAD //回退至上一个版本，强制返回至修改文件的状态，
之后的add to index,commit信息统统没掉
git reset --mixed HEAD //回退至上一个版本，返回至刚修改完文件的状态,
之后的add to index没了，commit信息也没了
git reset --soft HEAD//回退至未commit的时候
git reset --hard id;可直接回退到指定id的版本
git revert id;//提交一个新的commit作为撤销动作
git revert可用于远程撤销代码，因该撤销方便与远程代码合并
注:注意一定要给他一个id，可用引用型id
注:git revert HEAD传的是复制上一个提交的当前HEAD的副本
/* 以下为因切换代理而无法与连接github时的操作：取消代理
git config --global --unset http.proxy
git config --global --unset https.proxy
*/
/* 远程管理操作
git remote add origin github.com/xxx/filinamexxx //关联本地res
git push -u origin master //第一次推送master分支的所有内容
git pull//push origin master/xxx //同步
/*fatal: unable to access 'https://github.com/happyrbt/gittxt.git/': 
OpenSSL SSL_read: Connection was reset, errno 10054
一些错误修复：
git config http.postBuffer 524288000 //见https://blog.51cto.com/u_15326986/3328947
git config --global http.sslVerify "false"
git config --global http.proxy http://127.0.0.1:1080
git config --global https.proxy https://127.0.0.1:1080
*/