# 项目架构
## 架构图
![谷粒商城-微服务架构图](https://user-images.githubusercontent.com/47976649/115681436-1bf6be80-a387-11eb-99bd-6b472a9d9d81.jpg)
## 微服务划分图
![image](https://user-images.githubusercontent.com/47976649/115681892-8a3b8100-a387-11eb-95fe-b066ca6ce27f.png)
# 技术总和
# 开发准备
## Linux环境准备
* visualBox进行安装需要cpu开启虚拟化，在开机启动的时候设置主板，CPU configuration，然后点击Intel Vitualization Technology。重启电脑
普通安装linux虚拟机太麻烦，可以利用vagrant可以帮助我们快速地创建一个虚拟机。主要装了vitualbox，vagrant可以帮助我们快速创建出一个虚拟机。他有一个镜像仓库。
去https://www.vagrantup.com/ 下载vagrant安装，安装后重启系统。cmd中输入vagrant有版本代表成功了。
输入vagrant init centos/7，即可初始化一个centos7系统。（注意这个命令在哪个目录下执行的，他的Vagrantfile就生成在哪里）
vagrant up启动虚拟机环境。
启动后出现default folder:/cygdrive/c/User/… =>/vagrant。然后ctrl+c退出
前面的页面中有ssh账号信息。vagrant ssh 就会连上虚拟机。可以使用exit退出
> 下次使用也可以直接vagrant up直接启动，但要确保当前目录在C:/用户/ 文件夹下，他下面有一个Vagrantfile，不过我们也可以配置环境变量。
> 启动后再次vagrant ssh连上即可
* 不过他使用的网络方式是网络地址转换NAT（端口转发），如果其他主机要访问虚拟机，必须由windows端口如3333断发给虚拟机端口如3306。这样每在linux里安一个软件都要进行端口映射，不方便，（也可以在virualBox里挨个设置）。我们想要给虚拟机一个固定的ip地址，windows和虚拟机可以互相ping通。
* 方式1是在虚拟机中配置静态ip。
* 也可以更改Vagrantfile更改虚拟机ip，修改其中的config.vm.network "private_network",ip:"192.168.56.10"，这个ip需要在windows的ipconfig中查到vitualbox的虚拟网卡ip，然后更改下最后一个数字就行（不能是1，1是我们的主机）。配置完后vagrant reload重启虚拟机。在虚拟机中ip addr就可以查看到地址了。互相ping也能ping通。
* 关掉防火墙，VirualBox中第一个网卡设置NAT，第二个网卡设置仅主机
* 如果ping不了baidu<br>
  * cd /etc/sysconfig/network-scripts
  * ls 一般有ifcfg-eth0 1
  * ip addr 看哪个网格是192.168.56网段，然后vim他
  * vim ifcfg-eth1 加入
    ```java
    GATEWAY=192.168.56.1
    DNS1=114.114.114.114
    DNS2=8.8.8.8
    ```
  * service network restart
默认只允许ssh登录方式，为了后来操作方便，文件上传等，我们可以配置允许账号密码登录
```java
vim /etc/ssh/sshd_config
修改
PasswordAuthentication yes
重启
service sshd restart
账号root
密码vagrant
```
 
