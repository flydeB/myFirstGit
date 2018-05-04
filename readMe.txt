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
$ git push -u origin master
  -u参数第一次推送时需要的参数,作用是将远程仓库中的master分支与本地master 进行关联
  第一次推送会有一个SHH警告输入yes就好了以后不会再出现
以后每次将内容推送至库
$ git push origin master

 $ git remote 查看远程库的信息
 $ git remote -v 查看远程库的权限

origin  git@github.com:flydeB/myGit.git (fetch) 抓取的quanx
origin  git@github.com:flydeB/myGit.git (push) 推送到远程库的权限

远程仓库跟本地的关系就是将本地分支与远程库的分支对应起来

分支的推送
  $ git push origin dev

 当前远程库已经有分支
  $ git checkout -b dev origin/dev

  注意： 在多人开发中 推送分支可能会出现失败 原因就是远程分支
  内容比本地分支的分支更新 需要将远程更新后的内容与本地合并
  先拉 在推
  $ git pull    再 $ git push origin分支名

  如果在 $ git pull 发生错误信息为 no tracking information
  远程仓库分支与本地分支的仓库没有建立联系
  $ git branch --set-upstream 分支名 origin/分支名
  建立完毕联系后再 git pull $ git push origin 分支名
  以后在多人开发中每次上传前 先pull  如果有代码冲突先手动
  处理 再提交处理

  远程仓库的克隆
  $git clone git@github.com:flydeB/myGit.git

  克隆下来的仓库只有master 创建远程到本地

   $ git checkout -b dev origin/dev

   fork
   将别人的远程仓库克隆带自己的账号中
   去到别的项目主页点击fork 接下里克隆这个项目进行
   修改内容过新增功能  push后 点击自己页面上的new pull request
   等待对方接受你修改的内容 同不同意就看他自己的决定

  删除远程库与本地的关联

  git remote rm origin

  一个本地仓库可以即关联github 又关联
  码云  方法就是远程仓库不要同名
  git remote add github （github仓库ssh地址）
  git remote add gittte  （码云仓库ssh地址）


