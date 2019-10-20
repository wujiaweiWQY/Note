#<center>Ubuntu</center>
## 一、修改默认root账户密码
&emsp;&emsp;&emsp;&emsp;安装成功Ubuntu后，使用一般账户成功进入系统之后，才能对root账户密码进行设置。<br />
&emsp;&emsp;&emsp;&emsp;开启命令行，在桌面单击右键。选择opin in Terminal打开命令窗。<br />
&emsp;&emsp;&emsp;&emsp;在终端中输入:
```
		sudo passwd root
```
&emsp;&emsp;&emsp;&emsp;输入当前用户密码。<br />
&emsp;&emsp;&emsp;&emsp;之后设置root账户密码后设置成功.<br />
## 二、Vmware中安装Ubuntu不能显示全像素的问题解决方案
## &emsp;&emsp;(1)安装Vmware Tools
&emsp;&emsp;&emsp;&emsp;在选项卡中[选项卡]->[安装Vmware Tools]<br />
## &emsp;&emsp;(2)在系统中安装Vmware Tools
&emsp;&emsp;&emsp;&emsp;在系统管理中会出现VMware Tools的虚拟光驱被加载到系统中，在文件管理中能看到，
之后把.gz文件复制到home目录下，后把文件提取到当前文件夹中。之后打开终端。
输入su root，之后输入密码，切换到root账户进行操作，之后输入:
```
		cd ../home/vmware-tools-distrib
```
&emsp;&emsp;&emsp;&emsp;进入vmware-tools-distrib文件夹中，在该文件夹下安装VMware Tools 输入命令：
```
		sudo ./vmare-tools-distrib
```
&emsp;&emsp;&emsp;&emsp;之后需要按若干次回车，需要输入很多次yes看到下图文字就代表VMware Tools已安装成功。<br />
&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB73359feb634af18e19d9885f7b51c290?method=download&shareKey=c8cdd6c47db840784807fe79a894a594)
## 三、切换用户
&emsp;&emsp;&emsp;&emsp;在操作系统中的终端界面中输入：
```
		su+用户名
		密码
```
&emsp;&emsp;&emsp;&emsp;切换用户。<br />
## 四、升级程序
&emsp;&emsp;&emsp;&emsp;在终端中输入以下命令：
```
		apt-get update
```
## 五、使用远程登录软件登录操作系统
### &emsp;&emsp;(1)输入命令，安装SSH服务
```
		sudo apt-get install openssh-server
```
### &emsp;&emsp;(2)在ubuntu下有时需要安装net-tools
&emsp;&emsp;&emsp;&emsp;输入以下命令：
```
		sudo apt-get install net-tools
```
&emsp;&emsp;&emsp;&emsp;安装工具，才能使用ifconfig命令。<br />
&emsp;&emsp;&emsp;&emsp;在终端中输入：
```
		ifconfig
```
&emsp;&emsp;&emsp;&emsp;获取本机IP地址。<br />
&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB84464a9dec07e85bdb2e6f0d6121d19d?method=download&shareKey=584ba3f5c4c000ae991bcdb6ddb8d6d8)<br />
&emsp;&emsp;&emsp;&emsp;图中划圈的部分为本机IP。<br />
### &emsp;&emsp;(3)之后进入Xshell软件，新建一个会话
&emsp;&emsp;&emsp;&emsp;名称自己取随意。<br />
&emsp;&emsp;&emsp;&emsp;主机是之前在Linux中查看的IP填进去。<br />
&emsp;&emsp;&emsp;&emsp;用户名就是你要用哪个用户登录，一般使用root用户登录，密码就是你所用用户的密码。<br />
&emsp;&emsp;&emsp;&emsp;出现一下画面为链接成功。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEBd2acb356ddd2ecc56194eb6dc15cd99d?method=download&shareKey=f826857f3f8fb9ba1028db3b0b5cf9f5)<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB1d8d0ca66e2b7fe9dec2d3719ca4d066?method=download&shareKey=453faa4308b641f9bb4b63b2b4812818)<br />
&emsp;&emsp;&emsp;&emsp;注意：安装过程中会出现一些问题，我遇到的不多，就只要到了一种。就是在使用Xshell连接系统的时候会出现问题。<br />
&emsp;&emsp;&emsp;&emsp;这种问题我在使用CentOS7的时候没有遇到，但是在使用Ubuntu时遇到了以下问题：<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;使用Xshell连接Ubuntu时SSH服务器拒绝了密码的问题。先查看SSH是否启动，输入ps –e|grep ssh,如果没有ssh-agent表示还没启动。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;需要输入命令：
```
			/etc/init.d/ssh start
```
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;如果没有解决问题可能是ssh-server的配置文件设置了拒绝以root用户的模式。<br />
```
			vim /ect/ssh/sshd_config
```
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB04c7179ee13d177d34f38732b669cc6d?method=download&shareKey=10756221b4b37e3a02eb052d4bb021a1)<br />
<br />&emsp;&emsp;&emsp;&emsp;将上图中圈出的属性，修改为下图的样子。<br /><br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB0e19da8533707a0cd8048289a4dd1849?method=download&shareKey=c04ecf012be123cfef0ca2e45ab90c0b)<br />
<br />&emsp;&emsp;&emsp;&emsp;修改成功后，需重启ssh-service服务，在终端中输入以下命令：<br />
```
		sudo /ect/init.d/ssh restart
```
&emsp;&emsp;&emsp;&emsp;如果成功了，应入下图所示：<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEBd4cf8b865445b1f2199d2a3719c73c2c?method=download&shareKey=5e663e9da28a7a750fdc39114028a43f)<br />
## 六、使用FileZilla连接Linux虚拟机
&emsp;&emsp;&emsp;&emsp;首先，需要在Linux中使用ifconfig查看虚拟机IP地址。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB5bfa19510f90d0e8d8f9862c3f61d6d5?method=download&shareKey=6ed4bcdc0faa9e44ac0f23262e5dd5eb)
![image](https://note.youdao.com/yws/api/personal/file/WEBa1897ebf65297df3642cc33be75ef2c0?method=download&shareKey=6e687a1088ffb4058f7d39bac4956462)<br />
&emsp;&emsp;&emsp;&emsp;协议使用SFTP协议，端口使用22或者不填，用户使用root，密码就是root的密码。<br />
&emsp;&emsp;&emsp;&emsp;注意：在使用FileZilla中可能会遇到防火墙的问题。<br />
&emsp;&emsp;&emsp;&emsp;分别输入命令：
```
		iptables -N RH-Firewall-1-INPUT      //添加政策
		service iptables save　　　　　　　 //保存
		vi /etc/sysconfig/iptables           //编辑
```
&emsp;&emsp;&emsp;&emsp;添加下面这段到里面：
```
		-ARH-Firewall-1-INPUT -m state --state NEW -m tcp -p tcp --dport 22 -j ACCEPT
		-A INPUT -m state --state NEW -m tcp -p tcp --dport 3306 -j ACCEPT
```
&emsp;&emsp;&emsp;&emsp;然后再重启22端口输入命令：
```
		service iptables restart
```
&emsp;&emsp;&emsp;&emsp;即可正常连接到Linux。
## 七、安装Java JDK
&emsp;&emsp;(1)下载jdk文件。<br />
&emsp;&emsp;&emsp;&emsp;在官网下载，Linux版本的，通过FileZilla把JDK上传到Linux中。<br />
&emsp;&emsp;(2)使用终端打开压缩包所在文件夹。<br />
&emsp;&emsp;(3)建议新建一个文件夹。<br />
&emsp;&emsp;&emsp;&emsp;输入以下命令：<br />
```
		sudo mkdir 文件名<br />
```
&emsp;&emsp;(4)将压缩包解压到新建文件夹中。<br />
&emsp;&emsp;&emsp;&emsp;输入以下命令：
```
		tar –zxvf 压缩包名
```
&emsp;&emsp;(5)解压后重新打开终端输入：<br />
```
		gedit ~/.bashrc
```
&emsp;&emsp;&emsp;&emsp;会出现文本界面，将以下的内容粘贴到文本末尾，之后保存。<br />
```
		export JAVA_HOME=/usr/lib/jvm/jdk-9.0.1
		export JRE_HOME=${JAVA_HOME}/jre
		export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
		export PATH=${JAVA_HOME}/bin:$PATH
```
![image](https://note.youdao.com/yws/api/personal/file/WEB088e75f41ad424a57fa705b579181dfe?method=download&shareKey=a5083cbb70633c18b3fad761432f20ac)<br />
&emsp;&emsp;(6)在终端中输入以下命令使之生效。<br />
```
		source ~/.bashrc
```
&emsp;&emsp;(7)在终端中输入命令查看JDK是否安装成功。<br />
&emsp;&emsp;&emsp;&emsp;在终端中输入以下命令：
```
		java –version
```
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB755238aefee1ec6148decc45d020ec55?method=download&shareKey=a57f63f2b56e8a8ba5eba189d02e9b34)<br />
&emsp;&emsp;&emsp;&emsp;可以看到JDK版本就说明安装成功。<br />
## 八、Ubuntu切换安装源
&emsp;&emsp;(1)修改文件sources.list<br />
&emsp;&emsp;&emsp;&emsp;修改文件sources.list前，先备份这个文件。使用命令如下：<br />
```
		sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
&emsp;&emsp;(2)编辑源列表文件<br />
&emsp;&emsp;&emsp;&emsp;使用命令如下：<br />
```
		sudo vim /etc/apt/sources.list
```
&emsp;&emsp;&emsp;&emsp;如果报错：sudo:vim:command not found    说明没装vim编辑器<br />
&emsp;&emsp;&emsp;&emsp;使用命令：<br />
```
		sudo apt-get install vim 安装即可
```
&emsp;&emsp;(3)添加以下内容<br />
```
		deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
		deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
		deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
		deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
		deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
		deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
		deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
		deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
		deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
		deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
```
&emsp;&emsp;(4)更新软件列表<br />
&emsp;&emsp;&emsp;&emsp;输入以下命令：<br />
```
		sudo apt-get update
```
&emsp;&emsp;(5)更新软件包<br />
&emsp;&emsp;&emsp;&emsp;运行如下命令<br />
```
		sudo apt-get upgrade
```
## 九、安装Mysql
&emsp;&emsp;(1)如果使用了上面的软件源下载mysql<br />
```
		sudo apt-get install mysql-server
```
&emsp;&emsp;(2)编辑配置文件<br />
&emsp;&emsp;&emsp;&emsp;输入以下命令：<br />
```
		sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf。<br />
```
&emsp;&emsp;&emsp;&emsp;找到“bind-address:127.0.0.1”，将这行注释掉，然后重启mysql。<br />
&emsp;&emsp;&emsp;&emsp;启动mysql：<br />
```
		方式一：sudo /etc/init.d/mysql start 
		方式二：sudo service mysql start
 ```
&emsp;&emsp;&emsp;&emsp;停止mysql：<br />
```
		方式一：sudo /etc/init.d/mysql stop 
		方式二：sudo service mysql stop


&emsp;&emsp;&emsp;&emsp;重启mysql：

```
		方式一：sudo/etc/init.d/mysql restart
		方式二：sudo service mysql restart
```
&emsp;&emsp;(3)登录进入mysql使用的命令。<br />
&emsp;&emsp;&emsp;&emsp;在Windows中使用的命令是是一样的。<br />
```
		mysql –uroot –p
```
## 十、安装tomcat
&emsp;&emsp;(1)下载安装包<br />
&emsp;&emsp;&emsp;&emsp;现在Tomcat官网下载Tomcat安装包https://tomcat.apache.org/download-80.cgi。<br />
&emsp;&emsp;&emsp;&emsp;通过FileZilla将Tomcat安装包上传到Linux指定文件夹里面。<br />
&emsp;&emsp;(2)解压Tomcat<br />
&emsp;&emsp;&emsp;&emsp;通过终端到达Tomcat安装包所在的文件中，并解压压缩包输入如下命令：<br />
```
		Tar –zxvf apache-tomcat-8.5.43.tar.gz
```
&emsp;&emsp;(3)测试Tomcat<br />
&emsp;&emsp;&emsp;&emsp;进入tomcat中的bin目录下找到startuo.sh，并运行该文件，输入如下命令:<br />
```
		./startup.sh
```
&emsp;&emsp;&emsp;&emsp;在浏览器中输入IP+:8080测试<br />
&emsp;&emsp;(4)配置Tomcat后台账号<br />
&emsp;&emsp;&emsp;&emsp;找到tomcat目录下的conf文件夹中的tomcat-users.xml文件<br />
&emsp;&emsp;&emsp;&emsp;编辑这个文件输入以下命令：<br />
```
		vim tomcat-users.xml
```
&emsp;&emsp;&emsp;&emsp;在文件中加入下面的两行<br />
```
		<user username=”用户名” password=”用户密码”roles=”manager-gui”/>
		<role rolename="manager-gui"/>
```
&emsp;&emsp;(5)修改tomcat端口号<br />
&emsp;&emsp;&emsp;&emsp;找到tomcat下server.xml，输入如下命令：<br />
```
		vim server.xml
```
&emsp;&emsp;&emsp;&emsp;在文档的<Connector>标签的port属性中修改端口号，一般设置为80即可。<br />
&emsp;&emsp;&emsp;&emsp;注意：如果在安装过程中遇到tomcat权限不足的问题时，先查看自己是否处于root用户，使用root用户进行安装。<br />
&emsp;&emsp;&emsp;&emsp;如果是root的话，对*.sh赋可执行权限输入以下命令。<br >
```
		chmod +x *.sh
```
&emsp;&emsp;&emsp;&emsp;之后重启tomcat就行了在tomcat的bin目录下输入以下命令关闭tomcat。<br />
```
		./shutdown.sh
```
## 十一、安装eclipse
&emsp;&emsp;就在终端使用root用户执行一下下面的命令，如果是ubuntu在命令前面添加sudo即可：<br />
```
		update-alternatives --install /usr/bin/java java /usr/local/jdk1.8.0_151/bin/java 1100  
		update-alternatives --install /usr/bin/javac javac /usr/local/jdk1.8.0_151/bin/javac 1100 
```
&emsp;&emsp;其中将/usr/local/jdk1.8.0_151/换成你自己的jdk的路径
## 十二、固定IP地址
&emsp;&emsp;在通过Xeshell和FileZilla连接时需要虚拟机锁定IP地址。<br />
&emsp;&emsp;(1)编辑interfaces<br />
&emsp;&emsp;&emsp;&emsp;输入以下命令：<br />
```
		vim /etc/network/interface 
```
&emsp;&emsp;&emsp;&emsp;将原有内容使用#注释，并计入以下内容：<br />
```
		auto eth0
		iface eth0 inet static
		address 192.168.1.10    #要固定的IP地址
		netmask 255.255.255.0   #ifconf可以查看的子网掩码
		gateway 192.168.1.1     #默认网关dns-nameserver 114.114.114.114 8.8.8.8  #静态DNS码
```
&emsp;&emsp;(2)配置DNS文件<br />
&emsp;&emsp;&emsp;&emsp;找到resolv/conf.d/base文件并编辑，输入以下命令：<br />
```
		vim /etc/resolvconf/resolv.conf.d/base
```
&emsp;&emsp;&emsp;&emsp;将原有信息注释，后加入默认网关和静态DNS码。<br />
&emsp;&emsp;&emsp;&emsp;采用nameserver:***.***.***.***的形式书写。<br />
&emsp;&emsp;(3)保证保存同步<br />
&emsp;&emsp;&emsp;&emsp;需要编辑/etc/resolv.conf内的nameserver。<br />
&emsp;&emsp;&emsp;&emsp;加入默认网关和静态DNS码。<br />
&emsp;&emsp;(4)重启网络服务和网络配置。<br />
## 十三、安装Maven
&emsp;&emsp;(1)安装Maven<br />
```
		sudo apt-get install maven
```
&emsp;&emsp;(2)修改全局文件<br />
&emsp;&emsp;&emsp;&emsp;添加环境变量，输入以下命令：<br />
```
		sudo vi /etc/profile
```
&emsp;&emsp;在文件中添加以下内容<br />
```
		export M2_HOME=安装Maven目录
		export PATH=${M2_HOME}/bin:$PATH
```
## 十四、安装redis
&emsp;&emsp;1.获取redis资源<br />
```
		wget http://download.redis.io/releases/redis-4.0.8.tar.gz
```
&emsp;&emsp;2.解压<br />
```
		tar -xzvf redis-4.0.8.tar.gz
```
&emsp;&emsp;3.安装<br />
&emsp;&emsp;&emsp;&emsp;输入以下命令：<br />
```
		cd redis-4.0.8
		make
		cd src
		make install PREFIX=/usr/local/redis
```
&emsp;&emsp;4.移动配置文件到安装目录下<br />
&emsp;&emsp;&emsp;&emsp;输入以下命令：<br />
```
		cd ../
		mkdir /usr/local/redis/etc
		mv redis.conf /usr/local/redis/etc
```
&emsp;&emsp;5.配置redis为后台启动<br />
```
		vim /usr/local/redis/etc/redis.conf //将daemonize no 改成daemonize yes
```
&emsp;&emsp;6.将redis加入到开机启动<br />
```
		vim /etc/rc.local //在里面添加内容：/usr/local/redis/bin/redis-server /usr/local/redis/etc/redis.conf (意思就是开机调用这段开启redis的命令)
```
&emsp;&emsp;7.开启redis<br />
```
		/usr/local/redis/bin/redis-server /usr/local/redis/etc/redis.conf 
```
&emsp;&emsp;&emsp;&emsp;常用命令：　　
```
		redis-server /usr/local/redis/etc/redis.conf //启动redis
		pkill redis  //停止redis
```
&emsp;&emsp;&emsp;&emsp;卸载redis：<br />
```
		rm -rf /usr/local/redis //删除安装目录
		rm -rf /usr/bin/redis-* //删除所有redis相关命令脚本
		rm -rf /root/download/redis-4.0.4 //删除redis解压文件夹
```
## 十五、安装zookeeper
&emsp;&emsp;(1)从apache官网下载zookeeper的压缩包，zookeeper<br />
&emsp;&emsp;&emsp;&emsp;这里我使用的是zookeeper-3.4.6版本比较低，也可以使用更高的版本<br />
&emsp;&emsp;(2)将zookeeper的压缩包上传到Linux中<br />
&emsp;&emsp;&emsp;&emsp;一般上传到虚拟机的/usr/local/zookeeper目录下<br />
&emsp;&emsp;(3)解压压缩包,输入以下命令：<br />
```
		Tar-zxvf 压缩包名
```
&emsp;&emsp;&emsp;&emsp;(4)设置环境变量<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(1)编辑环境变量文件<br />
```
		vim /etc/profile
```
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(2)在文件中加入以下内容<br />
&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB3c257a5c26a3f3ad361d092b2865b2cc?method=download&shareKey=5e8266bffddd5ba99b37c6a9dccbe864)<br />
ZOOKEEPER_HOME后面跟的是zookeeper的安装路径。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(3)更新环境变量<br />
source /etc/profile
&emsp;&emsp;(5)修改配置文件<br />
&emsp;&emsp;&emsp;&emsp;(1)备份配置文件<br />
```
		cp –zoo_sample.cfg zoo.cfg
```
&emsp;&emsp;&emsp;&emsp;(2)修改配置文件zoo.cfg<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;将配置文件修改成以下的样子：<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB69185d8dcbd0419397c1d5061cec9cef?method=download&shareKey=5f1bc9b7e353b9698c92dbca44fa68f2)<br />
&emsp;&emsp;(6)启动zookeeper,输入以下命令：<vr />
```
		sudo bin/zkServer.sh start
```
&emsp;&emsp;&emsp;&emsp;或在zookeeper安装目录的bin目录下执行zkServer.sh脚本启动<br />
&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB0c5491aaec20d8831c0015505e9fb78a?method=download&shareKey=834deba1e8190c380820783d3816a7e4)<br />
&emsp;&emsp;&emsp;&emsp;启动CLI，执行zkCli.sh脚本。<br />
![image](https://note.youdao.com/yws/api/personal/file/WEBe34f650fcd7f4a0faf7bd41886c7cff2?method=download&shareKey=9514e7eae5e17872e3cf40aa23597c93)<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;如果出现上面的画面，则zookeeper单机安装完成。<br />
## 十六、安装RocketMQ
&emsp;&emsp;(1)下载RocketMQ<br />
&emsp;&emsp;&emsp;&emsp;从官网下载RocketMQ。[RocketMQ](https://github.com/apache/rocketmq/)<br />
&emsp;&emsp;(2)解压RocketMQ的源码包<br />
```
		unzip 压缩文件名
```
&emsp;&emsp;&emsp;&emsp;(3)	进入文件夹<br />
```
		mvn -Prelease-all -DskipTests clean install –U
```
&emsp;&emsp;(4)	查看mq的启动文件<br />
```
		cd distribution/target/apache-rocketmq/bin
```
&emsp;&emsp;(5)	修改jvm内存分配<br />
&emsp;&emsp;&emsp;&emsp;修改runbroker.sh和runserver.sh文件中关于内存的配置<br />
```
		JAVA_OPT="${JAVA_OPT} -server -Xms4g -Xmx8g -Xmn8g"
```
&emsp;&emsp;&emsp;&emsp;改成
```
		JAVA_OPT="${JAVA_OPT} -server -Xms128m -Xmx256m -Xmn256m"
```
&emsp;&emsp;(6)启动nameserver<br />
&emsp;&emsp;&emsp;&emsp;在安装目录的输入一下命令<br />
```
		> nohup sh mqnamesrv &
		> tail -f ~/logs/rocketmqlogs/namesrv.log
```
&emsp;&emsp;(7)启动broker<br />
&emsp;&emsp;&emsp;&emsp;在安装目录下输入以下命令<br />
```
		> nohup sh mqbroker -n localhost:9876 &
		> tail -f ~/logs/rocketmqlogs/broker.log
```
&emsp;&emsp;(8)关闭相关服务<br />
```
		> sh mqshutdown broker
		> sh mqshutdown namesrv
```
## 十七、查看CPU、内存命令
&emsp;&emsp;输入以下命令：<br />
```
		cat /proc/cpuinfo
```
&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB1e4ba1b50d0b5b1bb97891ccbd38eea5?method=download&shareKey=6b93107789bc188edf1752ad9097df9c)<br />
