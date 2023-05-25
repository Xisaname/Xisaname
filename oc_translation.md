# 关于GitHub开源社区贡献步骤
本教程针对GitHub下的oc发布的翻译issue的开发步骤

# 将项目安装到本地
## 代码克隆
首先，点击[官方仓库](https://github.com/OpenCloudOS/opencloudos.github.io)页面右上角的`fork`选项，新建一个属于你的分支，这样你就可以在你的分支上任意修改并且不会影响到官方分支。`fork`按钮如下图:
![图片](https://github.com/Xisaname/Xisaname/assets/52352730/342d9768-447a-46a5-aeb0-4e722e78997a)

接着，在你的系统终端运行git命令，也可以运行git bash（如果你是Windows用户的话）
```
git clone git@github.com:yourname/opencloudos.github.io.git
```
以上命令是ssh协议，也可以用https协议，只要将代码clone到本地就行。

## 项目安装
**首先，命令行进入你的项目：**
```
cd opencloudos.github.io
```
之后，运行以下命令安装mkdocs-material及多语言插件
```
pip install mkdocs-material mkdocs-static-i18n
```

最后，执行以下命令在本地运行预览服务器：
```
mkdocs serve
```
注意，执行之后服务器会一直保持运行状态，不是程序卡了，也不是宕机了！！！

# 提交项目
GitHub的push机制和gitee的push不同。自从2022年中旬开始，GitHub提交的方式变得更为严苛，仅靠输入用户名和密码不能push代码到远程仓库。

因此，为了适应新的机制，需要做出以下改变：
## 方法一
官方给出的令牌方法

[链接](https://docs.github.com/cn/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)

上述方法每次push时将password填成生成的token即可，不过要记得保存token。
## 方法二
针对方法一的问题，需要改进，即一次修改，之后便不需要重新输入用户名和token了。

步骤如下：
### 生成密钥文件
```
ssh-keygen -t rsa -C “邮箱”
```
这一步的目的是在本地生成一对公钥，邮箱填你的邮箱即可。然后它会让你一直确认啥的，只需一路回车即可。

### 查看你的密钥文件

在Windows系统里文件存放在C:\Users\Administrator.ssh 文件夹下。

在Linux和mac里，文件存放在~/.ssh文件夹下。

### 复制公钥到GitHub中

在上述文件夹中有一个名叫id_rsa.pub的文件，用文本编辑器打开，复制其中的全部内容，记住一定是全部，落一个符号都不行！！！

打开你的GitHub，然后，在右上角个人账号信息里面，点击etting（设置），在设置里面，点击SSH and GPG keys，再点击 New SSH key。将刚才复制的公钥，直接复制进去，标题随便起。

![图片](https://github.com/Xisaname/Xisaname/assets/52352730/fad3ea4f-9c83-4cda-bcc0-c5000b6198f6)
![图片](https://github.com/Xisaname/Xisaname/assets/52352730/fa520e96-f7f8-4f5d-8546-9f2ca924be54)
![图片](https://github.com/Xisaname/Xisaname/assets/52352730/b0fd894f-1ce9-4a21-9967-f09afa07b271)

### 测试
终端运行以下命令进行测试
```
ssh -T git@github.com
```
要是出现你的GitHub名字，就成功啦！
