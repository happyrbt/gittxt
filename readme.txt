git learning progess
-----------------------------------------------------------------------
2022.3.4:
git init //将当前文件夹设定为收GIT管理的repository
git add 文件名//将该文件列入修改列表
git commit -m " 提交修改，-m后接“备注” "
git global user.name ""
git global user.email "" //将所有库设为name，email 所有
git commit未加注释的解决办法，或注释写错了：
{git commit --amend //修改最近一次提交的注释信息，进入到vim编辑器
c进入编辑状态
Esc (退出编辑状态)
:wq 保存文件并退出vim编辑
适用于windows系统}
