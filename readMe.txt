github仓库与本地仓库通过ssh加密
在使用git中添加远程库或者是从远程库克隆之前需要将自己的SSH key添加到账户列表中
创建 SSH key
$ ssh-keygen -t rsa -C "你的邮箱"
这样会在用户主目录中生成 .ssh目录
目录中包含id_rsa和id_rsa.pub文件,id_rsa文件是私钥一定不能泄露,id_rsa.pub公钥可以公开
回到gitHub,点击setting -> SSH and GPG key -> add SSH key
title可以任意写  key将id_rsa.pub内容填入

本地添加远程库的方法
$ git remote add origin <仓库SSH地址>
例 $ git remote add origin git@github.com:gecH5Zwei/myGit.git
将本地内容推送至远程仓库
$ git push -u origin marster
  -u参数第一次推送时需要的参数,作用是将远程仓库中的master分支与本地master 进行关联
  第一次推送会有一个SHH警告输入yes就好了以后不会再出现
以后每次将内容推送至库
$ git push origin marster