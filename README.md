# 项目架构
## 架构图
![谷粒商城-微服务架构图](https://user-images.githubusercontent.com/47976649/115681436-1bf6be80-a387-11eb-99bd-6b472a9d9d81.jpg)
## 微服务划分图
![image](https://user-images.githubusercontent.com/47976649/115681892-8a3b8100-a387-11eb-95fe-b066ca6ce27f.png)
# 技术总和
# 开发准备
## Linux环境准备
visualBox进行安装需要cpu开启虚拟化，在开机启动的时候设置主板，CPU configuration，然后点击Intel Vitualization Technology。重启电脑
普通安装linux虚拟机太麻烦，可以利用vagrant可以帮助我们快速地创建一个虚拟机。主要装了vitualbox，vagrant可以帮助我们快速创建出一个虚拟机。他有一个镜像仓库。
去https://www.vagrantup.com/ 下载vagrant安装，安装后重启系统。cmd中输入vagrant有版本代表成功了。
输入vagrant init centos/7，即可初始化一个centos7系统。（注意这个命令在哪个目录下执行的，他的Vagrantfile就生成在哪里）
vagrant up启动虚拟机环境。
启动后出现default folder:/cygdrive/c/User/… =>/vagrant。然后ctrl+c退出
前面的页面中有ssh账号信息。vagrant ssh 就会连上虚拟机。可以使用exit退出
> 下次使用也可以直接vagrant up直接启动，但要确保当前目录在C:/用户/ 文件夹下，他下面有一个Vagrantfile，不过我们也可以配置环境变量。
> 启动后再次vagrant ssh连上即可`
