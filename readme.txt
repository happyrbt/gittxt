git learning progess
-----------------------------------------------------------------------
2022.3.4:
git init //将当前文件夹设定为收GIT管理的repository
git add 文件名//将该文件列入修改列表
git commit -m " 提交修改，-m后接“备注” "
git reflog //查看历史commit及其ID
git global user.name ""
git global user.email "" //将所有库设为name，email 所有
git commit未加注释的解决办法，或注释写错了：
{git commit --amend //修改最近一次提交的注释信息，进入到vim编辑器
c进入编辑状态
Esc (退出编辑状态)
:wq 保存文件并退出vim编辑
适用于windows系统}
//撤销相关
HEAD指指向当前分支的当前版本
git reset --hard HEAD //回退至上一个版本，强制返回至修改文件的状态，
之后的add to index,commit信息统统没掉
git reset --mixed HEAD //回退至上一个版本，返回至刚修改完文件的状态,
之后的add to index没了，commit信息也没了
git reset --soft HEAD//回退至未commit的时候
git reset --hard id;可直接回退到指定id的版本
git revert id;提交一个新的commit作为撤销动作
/* 以下为因切换代理而无法与连接github时的操作：取消代理
git config --global --unset http.proxy
git config --global --unset https.proxy
*/
/* 远程管理操作
git remote add origin github.com/xxx/filinamexxx //关联本地res
git push -u origin master //第一次推送master分支的所有内容
git pull//push origin master //同步