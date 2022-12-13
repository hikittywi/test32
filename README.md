# ssh连接github方法
===

一、软件安装
----
1、安装git      https://git-scm.com/
2、vscode

二、在Github上创建空的仓库/项目
----
1、选择公开项目创建

三、设置git bash全局变量
----
1、打开Git Bash
2、给你这个电脑取一个名字和邮件地址：
···python
$ git config --global user.name "Your Name"
···
···
$ git config --global user.email "email@example.com"
···

四、设置本地公钥和私钥也即ssh key
----
创建SSH Key，之前看下在C:\Users\&yourname&目录有没有.ssh文件夹，如果有打开看看有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接使用。如果没有，打开Git Bash （这个和前面设置全局用户名邮箱那个步骤是一样的，打开输入即可，由于是全局设置没必要纠结在哪个文件夹打开），输入一下命令，创建SSH Key：

$ ssh-keygen -t rsa -C "youremail@example.com"

你需要把邮件地址换成你自己的邮件地址，然后一路回车，使用默认值即可，由于这个Key是自己使用的，为了方便无需设置密码。
在C:\Users\&yourname\.ssh&文件夹里面找到id_rsa.pub这个文件，使用vscode打开（不要用记事本），复制其中的内容备用。

五、在github中设置公钥
---
1、打开GitHub的账户设置
2、点击左侧的SSH and GPG keys，点击New ssh key按钮
3、把从vscode里面打开的，之前复制备用的id_rsa.pub文件内容复制进来

4、打开本机安装的Git Bash，输入
ssh -T git@github.com

若返回Hi XXX! You've successfully authenticated, but Github.com does not provide shell access. 内容，则证明添加成功。

五、从远程克隆
1、在github仓库复制仓库的ssh地址

六、上传
1、修改后保存
2、点击加号确认，版本修改内容，提交
3、点击左下角连接远程更新。

参考文章：
https://blog.csdn.net/qq_38981614/article/details/115013188