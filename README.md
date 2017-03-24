## 搭建简易Git仓库方法

#### 1、搭建背景

	相比搭建gitlab仓库，这个搭建方法比较简单、快捷，比较适合小团队使用，只需要在服务器上搭建一个git共享库就OK了。

#### 2、建立仓库

###### 服务器端：

	a、创建项目目录：mkdir project_dir.git

	b、在project_dir.git目录中执行命令：git --bare init，现在初始化项目成功，这个目录就是项目共享库，之后所有代码都在该目录下面。

###### 本地端：

	a、clone远程共享项目：git clone user@server_ip:/home/project/project_dir.git。此时会在本地生成一个project_dir的文件夹。

	b、在project_dir目录下添加文件并commit，commit时可能会提示设置user、email，根据提示设置即可。

	c、push代码到远程仓库。push过程可能提示没有track远端的对应分支。按提示设置git —set-upstream，这时默认在master分支上面。

#### 3、建立git信任关系

	上面配置完成后，每次pull或push（因为底层执行了ssh命令去连接远端）时，都需要输入ssh连接密码，很麻烦，需要建立信任关系。

	a、server端建立~/.ssh文件夹，权限必须是700。在.ssh目录下建立authorized_keys文件，权限必须是600。

	b、本地生成私钥及公钥，把公钥添加到authorized_keys当中。

