# <center>CentOS<center/>
## 一、解决不能重启network<br />
&emsp;&emsp;为什么是打开 有线连接_1 接口而不是 enp1s0f0 ,不管怎样我们配置的是enp1s0f0，所以我们希望他打开enp1s0f0，所以我尝试将有线连接_1 配置注释。<br />
```
		[root@localhost network-scripts]/etc/sysconfig/network-scripts
		[root@localhost network-scripts]/mv ifcfg-有线连接_1  backup-ifcfg-有线连接_1
```
再次重启网络服务就成功了。<br />
```
		[root@localhost network-scripts]# service network restart<br />
		Restarting network (via systemctl):  
```
## 二、关闭防火墙并关闭开机启动<br />
&emsp;&emsp;查看防火墙状态<br />
```
		Firewall-cmd –state
```
&emsp;&emsp;停止firewall<br />
```
		Systemctl stop firewalld.service
```
&emsp;&emsp;禁止firewall开机启动<br />
```
		Systemctl disable firewalld.service
```
## 三、安装C语言编译环境<br />
&emsp;&emsp;从yum源下载C语言编译环境<br />
```
		yum install gcc
```
![image](https://note.youdao.com/yws/api/personal/file/85C092CF032C4E48A6C49C9C8C7687ED?method=download&shareKey=602b6ceba08951a4f17083842ed25c78)<br />
## 四、Java编译环境<br />
&emsp;&emsp;&emsp;&emsp;(1)先使用FileZila把Java JDK安装到Linux中一般存放再/usr/local/中。<br />
&emsp;&emsp;&emsp;&emsp;(2)现在当前Linux系统上是否安装有JDK。<br />
```
		rpm –qa|grep java
```
&emsp;&emsp;&emsp;&emsp;其中带有openjdk的都是可以卸载的，需要删除。<br />
```
		rpm –e –nodeps +系统自带JDK名
```
&emsp;&emsp;&emsp;&emsp;(3)新建/usr/local/java：<br />
```
		mkdir /usr/local/java
```
&emsp;&emsp;&emsp;&emsp;(4)把jdk解压到这个目录下命令<br />
```
		–zxvf /usr/local/下载JDK的名字 –C /usr/local/java
```
&emsp;&emsp;&emsp;&emsp;(5)编辑CLASSPATH，设置环境变量<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;输入命令:<br />
```
		vim /etc/profile
```
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/15CDE7E1E0A14BD5AA36582E96384A45?method=download&shareKey=6394ef70cb8db0afc4a1e780198e362a)
<br />&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;在该文件最后加入以下的东西
```
		export JAVA_HOME=/usr/local/java/jdk1.8.0_162
		export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
		export PATH=$PATH:$JAVA_HOME/bin
```
&emsp;&emsp;&emsp;&emsp;其中JAVA_HOME等号后面的是解压jdk的目录，CLASSPATH和PATH都是基于JAVA_HOME来确定的，都是一模一样的。原理与Windows中的classpath和path同理。
使环境变量生效：<br />
```
		Source /etc/profile
```
&emsp;&emsp;&emsp;&emsp;(6)测试Java测试Jdk的安装情况<br /><br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/3507384C9F9145349C08846CCF25EC53?method=download&shareKey=5b8ba5d83e6ca509a591132caf1fac0f)<br /><br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;使用java-version查看当前的jdk的版本
![image](https://note.youdao.com/yws/api/personal/file/B1530DCFA7A047898FF8C9D3F2B3FCBD?method=download&shareKey=bcd85beb044c5f56c6c354f66ca571a7)<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;到此，安装配置成功。<br />
## 五、安装Mysql<br />
&emsp;&emsp;&emsp;&emsp;(1)通过FileZila把上传Mysql得安装文件。<br />
&emsp;&emsp;&emsp;&emsp;(2)解压Mysql得压缩文件。<br />
&emsp;&emsp;&emsp;&emsp;(3)切换到mysql的安装目录，并创建data文件夹。<br />
```
				mkdir data
```
&emsp;&emsp;&emsp;&emsp;(4)在mysql安装目录外创建一个组msyql。<br />
```
				groupadd mysql
```
&emsp;&emsp;&emsp;&emsp;(5)创建一个用户 。<br />
```
				useradd –r – q mysql mysql –s /sbin/nologin
```
&emsp;&emsp;&emsp;&emsp;(6)将该目录所有权限全部改为mysql用户的权限。<br />
```
				chown –R mysql:mysql mysql
```
&emsp;&emsp;&emsp;&emsp;(7)初始化mysql脚本。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;先到达mysql安装目录中的bin目录下 找到mysql-install.db初始化脚本。<br />
```
				./mysql_install_db –user=mysql -–basedir=安装目录 –datadir=data目录
```
&emsp;&emsp;&emsp;&emsp;(8)获取初始密码。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;输入：<br />
```
				cat /root/.mysql_secret
```
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;便可获得初始密码。<br />
&emsp;&emsp;&emsp;&emsp;(9)修改配置文件。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;在support-files文件夹下载把my-default.cnf拷贝到/etc目录下替换my.cnf。<br />
```
				cp my-default.cnf /etc/my.cnf
```
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;编辑my.cnf，输入以下命令：<br />
```
				vim my.cnf	
```
&emsp;&emsp;&emsp;&emsp;(10)安装服务。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;在support-files目录下：<br />
```
				cp –a mysql.server /etc/init.d/mysqld
```
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;启动mysql服务，输入以下命令：<br />
```
				Service mysqld start
```
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;关闭防火墙，输入以下命令：<br />
```
				Systemctl stop firewalld
				Systemctl disable firewalld
```
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;将bin目录加入path环境变量中，进行以下操作：<br />
```
				vim /etc/profile
				source /etc/profile
```
&emsp;&emsp;&emsp;&emsp;(11)第一次进入mysql。<br />
```
				Msyql –uroot –p
				Set password=password(‘所要设置的密码’)
```