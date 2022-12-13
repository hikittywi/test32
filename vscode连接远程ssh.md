1、vscode安装 Remote-SSH 插件，左侧增加远程资源管理器图标。
2、windows下ssh功能。可以通过安装 Git 来获取 SSH 功能，在cmd中ssh测试
3、配置SSH密钥

使用如下命令，生成 SSH 公钥文件。
# 方法一 
ssh-keygen 
 
# 方法二，参考使用Git生成密钥 
ssh-keygen -t rsa -C "youremail@example.com" 

一般生成的密钥文件，路径为：C:\Users\user\.ssh ，找到公钥文件 id_rsa.pub ，复制到远程服务器 根目录 的 .ssh 文件夹中。

(1)根目录，不一定非要是 /.ssh 路径，可以是自己的用户目录，类似这样：/zhaochen/.ssh。

(2).ssh 文件夹没有怎么办?新建一个文件夹，命名为 .ssh 即可。同时要确认远程服务器是否支持 SSH ，如果此时正是通过 SSH 方式连接的，那肯定是支持了。

4、vscode配置ssh
点击左侧的 “远程资源管理器” 图标，点击右上角的小齿轮(设置)
在弹出来的窗口中，选择第一个 config 文件打开，参考下图，填写对应信息
Host ：连接的主机名称，可自定义;
Hostname ：远程主机的 IP 地址;
User ：用于登录远程主机的用户名;
Port ：用于登录远程主机的端口，SSH 默认为 22 ;
IdentityFile ：本地的私钥文件 id_rsa 路径;

如果需要连接多个远程服务器，可参考如上内容，配置多个即可

Host <远程主机名称1> 
    HostName <远程主机1 IP> 
    User <用户名1> 
    Port <ssh端口，默认22> 
    IdentityFile <本机SSH私钥路径> 
    ForwardAgent yes <VSCode 自己添加的，不用管> 
Host <远程主机名称2> 
    HostName <远程主机2 IP> 
    User <用户名2> 
    Port <ssh端口，默认22> 
    IdentityFile <本机SSH私钥路径> 
    ForwardAgent yes <VSCode 自己添加的，不用管> 

5、连接测试
进入 “远程资源管理器” 选项，右键点击主机名;
如果连接成功，左下角则会显示当前已连接的主机名。