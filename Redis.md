# <center>Redis</center>
## 一、安装redis
##### &emsp;&emsp;1、源码编译方式安装redis<br />
&emsp;&emsp;&emsp;&emsp;通过阅读redis官方文档，得知输入以下命令直接把文件下载到你当前所在目录中<br />
```
		wget http://download.redis.io/releases/redis-5.0.5.tar.gz
		tar xzf redis-5.0.5.tar.gz
		cd redis-5.0.5
		make
```
&emsp;&emsp;&emsp;编译二进制文件。<br />
&emsp;&emsp;&emsp;对redis进行make编译之后会出现的。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEBcd6f4b1f0d83448367811ee3651ae308?method=download&shareKey=778ef1944b203460171617daefde650b)<br />
&emsp;&emsp;&emsp;之后输入以下命令进入src目录：<br />
```
		cd  src
```
&emsp;&emsp;&emsp;能看到以下图片中的文件。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB355e2e64a7eb2d8c848597e73bb0b36d?method=download&shareKey=f4e4d6baff90206bdd946dbed15da8bd)<br />
```
		redis-server：用于启动redis服务的脚本文件
		redis-cli：是终端控制脚本
		redis-benchmark：用来进行压力测试的脚本文件
		redis-check-aof、redis-check-dump：检测备份文件的脚本文件
```
##### &emsp;&emsp;2、将redis运行所需文件，拷贝到redis运行目录<br />
&emsp;&emsp;&emsp;在/usr/loacl目录下创建redis目录输入以下命令<br />
```
		mkdir  /usr/local/redis
```
#####&emsp;&emsp;3、将redis-server和redis-cli文件拷贝到刚刚创建的文件夹下<br />
&emsp;&emsp;&emsp;在 ../redis-5.0.5/src下输入以下命令<br />
```
		cp  redis-server redis-cli /usr/local/redis
```
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB33e40ed065b6df1c0cc58b87fc0115fa?method=download&shareKey=8b21e33c4372899d6711a48765153073)<br />
<br />
##### &emsp;&emsp;4、将redis的配置文件复制到/usr/local/redis中<br />
&emsp;&emsp;&emsp;&emsp;再redis安装目录下输入以下命令：<br />
```
		cp redis.conf /usr/local/redis
```
&emsp;&emsp;&emsp;&emsp;文件夹中就会存在三个文件。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEBde89b6622619f376b41b2d6db082e706?method=download&shareKey=5a544210901788abd336049ff0e2affa)<br />
##### &emsp;&emsp;5、完成上述操作之后就可以启动redis服务。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![imagr](https://note.youdao.com/yws/api/personal/file/WEB4199a50fbeb598660edbc6afca5722c0?method=download&shareKey=35b0284f1d3db52b2e44745b1ea5d559)<br />
&emsp;&emsp;&emsp;&emsp;但是当前启动是前台启动的方式。<br />
##### &emsp;&emsp;6.将启动方式修改为后台启动
&emsp;&emsp;&emsp;&emsp;需要使用后台打开配置文件。<br />
&emsp;&emsp;&emsp;&emsp;在刚刚创建的redis启动目录中打开编辑redis.conf文件，修改配置文件。<br />
&emsp;&emsp;&emsp;&emsp;将daemonize的选项改为yes，设置后台启动redis。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEBb5fafb688ca6a6930713d62387636686?method=download&shareKey=fb469cb2aefff604aac7d5ba7917ad20)<br />
&emsp;&emsp;&emsp;&emsp;再次启动redis服务，并使用刚刚编辑的配置文件，输入以下命令：<br />
```
		./redis-server redis.conf
```
&emsp;&emsp;&emsp;&emsp;便可完成。<br />
&emsp;&emsp;&emsp;&emsp;后台启动redis服务，可以输入ps -e|grep redis查看进程。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB83375f40a5c7995508ece13cafc7d0af?method=download&shareKey=243af1b95d96300ff713fe4c84358cb8)<br />
&emsp;&emsp;&emsp;&emsp;能看到redis-server服务开启了。<br />
&emsp;&emsp;&emsp;&emsp;在/usr/local/redis文件下输入以下命令，进入redis终端。<br />
```
		./redis-cli
```
&emsp;&emsp;&emsp;&emsp;可以进行简单的使用。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB537192c0350959b62a147389422d92f2?method=download&shareKey=fa83df50ba162d96f3e8a795197f85d3)<br />
## 二、具体使用
##### &emsp;&emsp;1.简单操作
&emsp;&emsp;在redis中，除了“\n”和空格不能作为名字的组成内容外，其他内容都可以作为key的名字部分，名字长度不做要求。<br />
&emsp;&emsp;keys键操作：
| key名 | 用法 |
| :-: | :-: | 
| existis key | 测试指定key是否存在 |
| del key1 key2 | 删除给定key |
| type key | 返回给定key的value类型 |
| keys pattern | 返回皮牌指定模式的所有key |
| rename aldkey newkey | 改名字 |
| dbsize | 返回当前数据库的key数量 |
| expire key seconds | key指定过期时间 |
| ttl key | 返回key的剩余过期秒数 |
| select db-index | 选择数据库 |
| move key db-index | 将key从当前数据库移动到指定数据库 |
| flushdb | 删除当前数据库中所有key |
| flushall | 删除所有数据库中的所有key |
&emsp;&emsp;Key：<br />
&emsp;&emsp;&emsp;给存储在redis内存zhong 的数据起的变量名字<br />
&emsp;&emsp;&emsp;&emsp;Values<br />
&emsp;&emsp;&emsp;&emsp;Strings<br />
&emsp;&emsp;&emsp;&emsp;List<br />
&emsp;&emsp;&emsp;&emsp;Sets<br />
&emsp;&emsp;&emsp;&emsp;Sirted sets<br />
&emsp;&emsp;&emsp;&emsp;Hash<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB04a9fa1a979a2284dcacba4a15b71b4a?method=download&shareKey=2a724cafa2eec1a354b2e28df25e0361)<br />
&emsp;&emsp;&emsp;&emsp;默认可以使用16个数据库。
##### &emsp;&emsp;2.string类型操作
| key |用法 |
| :-: | :-: |
| set key value | 设置key对应的值为string类型的value |
| mset key1 value 1 ---keyN valueN | 一次性设置多个key的值 |
| mget key1 key2 ---keyN | 一次性获取多个key的值 |
| incr key | 对key的值做加加操作，并返回新的值 |
| decr key | 同上，但是做的事减减操作 |
| incrby key integer | 同incr，加指定值 |
| decrby key integer | 同decr，减指定值 |
| substr key start end | 返回截取的key的字符串值 |
| incr | 该指令可以对与key进行累加操作 |
##### &emsp;&emsp; 3.简单命令	
| 命令名 | 作用 |
| :-: | :-: |
| dbsize | 查看当前所在数据库中有多少key |
| keys * | 查看当前所在数据库中所有key(在实际应用中最好不要使用) |
| flashall | 清楚所有数据库中的所有key-value |
| flashdb | 清除当前数据库中的所有key-value |
| exlsts | 查看是否存在这个key |
## 三、redis配置文件
##### &emsp;&emsp; 1. Redis默认不是以守护进程的方式运行
&emsp;&emsp;&emsp;&emsp;可以通过该配置项修改，使用yes启用守护进程，设置以下属性：
```
		daemonize no
```
##### &emsp;&emsp; 2. 当Redis以守护进程方式
&emsp;&emsp;&emsp;&emsp;运行时，Redis默认会把pid写入/var/run/redis.pid文件，可以通过pidfile指定：<br />
```
		pidfile /var/run/redis.pid
```
##### &emsp;&emsp; 3. 指定Redis监听端口
&emsp;&emsp;&emsp;&emsp;默认端口为6379，作者在自己的一篇博文中解释了为什么选用6379作为默认端口，因为6379在手机按键上MERZ对应的号码，而MERZ取自意大利歌女Alessia Merz的名字。<br />
```
		port 6379<br />
```
##### &emsp;&emsp; 4. 绑定的主机地址,输入以下命令：
```
		bind 127.0.0.1
```
##### &emsp;&emsp; 5.当客户端闲置多长时间后关闭连接
&emsp;&emsp;&emsp;&emsp;如果指定为0，表示关闭该功能。<br />
```
		timeout 300
```
##### &emsp;&emsp; 6. 指定日志记录级别
&emsp;&emsp;&emsp;&emsp;Redis总共支持四个级别：debug、verbose、notice、warning，默认为verbose。<br />
```
		loglevel verbose
```
##### &emsp;&emsp; 7. 日志记录方式
&emsp;&emsp;&emsp;&emsp;默认为标准输出，如果配置Redis为守护进程方式运行，而这里又配置为日志记录方式为标准输出，则日志将会发送给/dev/null<br />
```
		logfile stdout
```
##### &emsp;&emsp; 8. 设置数据库的数量
&emsp;&emsp;&emsp;&emsp;默认数据库为0，可以使用SELECT 命令在连接上指定数据库id<br />
```
		databases 16
```
##### &emsp;&emsp; 9. 指定在多长时间内，有多少次更新操作
&emsp;&emsp;&emsp;&emsp;就将数据同步到数据文件，可以多个条件配合<br />
```
		save
``` 
&emsp;&emsp;&emsp;&emsp;Redis默认配置文件中提供了三个条件：<br />
```
		save 900 1
		save 300 10
		save 60 10000
```
&emsp;&emsp;&emsp;&emsp;分别表示900秒（15分钟）内有1个更改，300秒（5分钟）内有10个更改以及60秒内有10000个更改。<br />
##### &emsp;&emsp; 10. 指定存储至本地数据库时是否压缩数据
&emsp;&emsp;&emsp;&emsp;默认为yes，Redis采用LZF压缩，如果为了节省CPU时间，可以关闭该选项，但会导致数据库文件变的巨大<br />
```
		rdbcompression yes
```
##### &emsp;&emsp; 11. 指定本地数据库文件名，默认值为dump.rdb,输入以下命令：
```
		dbfilename dump.rdb
```
##### &emsp;&emsp; 12. 指定本地数据库存放目录
```
		dir ./
```
##### &emsp;&emsp; 13. 设置当本机为slav服务时，设置master服务的IP地址及端口，在Redis启动时，它会自动从master进行数据同步
```
		slaveof 
```
##### &emsp;&emsp; 14. 当master服务设置了密码保护时，slav服务连接master的密码
```
		masterauth 
```
##### &emsp;&emsp; v15. 设置Redis连接密码
&emsp;&emsp;&emsp;&emsp;如果配置了连接密码，客户端在连接Redis时需要通过AUTH 命令提供密码，默认关闭。<br />
```
		requirepass foobared
```
##### &emsp;&emsp; 16. 设置同一时间最大客户端连接数
&emsp;&emsp;&emsp;&emsp;默认无限制，Redis可以同时打开的客户端连接数为Redis进程可以打开的最大文件描述符数，如果设置 maxclients 0，表示不作限制。当客户端连接数到达限制时，Redis会关闭新的连接并向客户端返回max number of clients reached错误信息。<br />
```
		maxclients 128
```
##### &emsp;&emsp; 17. 指定Redis最大内存限制
&emsp;&emsp;&emsp;&emsp;Redis在启动时会把数据加载到内存中，达到最大内存后，Redis会先尝试清除已到期或即将到期的Key，当此方法处理 后，仍然到达最大内存设置，将无法再进行写入操作，但仍然可以进行读取操作。Redis新的vm机制，会把Key存放内存，Value会存放在swap区。
```
		maxmemory
```
##### &emsp;&emsp; 18. 指定是否在每次更新操作后进行日志记录
&emsp;&emsp;&emsp;&emsp;Redis在默认情况下是异步的把数据写入磁盘，如果不开启，可能会在断电时导致一段时间内的数据丢失。因为 redis本身同步数据文件是按上面save条件来同步的，所以有的数据会在一段时间内只存在于内存中。默认为no。<br />
```
		appendonly no
```
##### &emsp;&emsp; 19. 指定更新日志文件名，默认为appendonly.aof
```
		appendfilename appendonly.aof
```
##### &emsp;&emsp; 20. 指定更新日志条件，共有3个可选值： 
```
		no：表示等操作系统进行数据缓存同步到磁盘（快） 
		always：表示每次更新操作后手动调用fsync()将数据写到磁盘（慢，安全） 
		everysec：表示每秒同步一次（折衷，默认值）
		appendfsync everysec
```
##### &emsp;&emsp; 21. 指定是否启用虚拟内存机制
&emsp;&emsp;&emsp;&emsp;默认值为no，简单的介绍一下，VM机制将数据分页存放，由Redis将访问量较少的页即冷数据swap到磁盘上，访问多的页面由磁盘自动换出到内存中（在后面的文章我会仔细分析Redis的VM机制）。<br />
```
		vm-enabled no
```
##### &emsp;&emsp; 22. 虚拟内存文件路径
&emsp;&emsp;&emsp;&emsp;默认值为/tmp/redis.swap，不可多个Redis实例共享。<br />
```
		vm-swap-file /tmp/redis.swap
```
##### &emsp;&emsp; 23. 将所有大于vm-max-memory的数据存入虚拟内存
&emsp;&emsp;&emsp;&emsp;无论vm-max-memory设置多小,所有索引数据都是内存存储的(Redis的索引数据 就是keys),也就是说,当vm-max-memory设置为0的时候,其实是所有value都存在于磁盘。默认值为0。<br />
```
		vm-max-memory 0
```
##### &emsp;&emsp; 24. Redis swap文件分成了很多的page
&emsp;&emsp;&emsp;&emsp;一个对象可以保存在多个page上面，但一个page上不能被多个对象共享，vm-page-size是要根据存储的 数据大小来设定的，作者建议如果存储很多小对象，page大小最好设置为32或者64bytes；如果存储很大大对象，则可以使用更大的page，如果不 确定，就使用默认值。<br />
```
		vm-page-size 32
```
##### &emsp;&emsp; 25. 设置swap文件中的page数量
&emsp;&emsp;&emsp;&emsp;由于页表（一种表示页面空闲或使用的bitmap）是在放在内存中的，，在磁盘上每8个pages将消耗1byte的内存。<br />
```
		vm-pages 134217728
```
##### &emsp;&emsp; 26. 设置访问swap文件的线程数
&emsp;&emsp;&emsp;&emsp;最好不要超过机器的核数,如果设置为0,那么所有对swap文件的操作都是串行的，可能会造成比较长时间的延迟。默认值为4。<br />
```
		vm-max-threads 4
```
##### &emsp;&emsp; 27. 设置在向客户端应答
&emsp;&emsp;&emsp;&emsp;是否把较小的包合并为一个包发送，默认为开启<br />
```
		glueoutputbuf yes
```
##### &emsp;&emsp; 28. 指定在超过一定的数量或者最大的元素超过某一临界值
&emsp;&emsp;&emsp;&emsp;采用一种特殊的哈希算法。<br />
```
		hash-max-zipmap-entries 64
		hash-max-zipmap-value 512
```
##### &emsp;&emsp; 29. 指定是否激活重置哈希
&emsp;&emsp;&emsp;&emsp;默认为开启（后面在介绍Redis的哈希算法时具体介绍）
```
		activerehashing yes
```
##### &emsp;&emsp; 30. 指定包含其它的配置文件
&emsp;&emsp;&emsp;&emsp;可以在同一主机上多个Redis实例之间使用同一份配置文件，而同时各个实例又拥有自己的特定配置文件
```
		include /path/to/local.conf
```
## 四、基础知识
#### &emsp;&emsp; 1.默认索引
&emsp;&emsp;&emsp;&emsp;redis默认索引开始从0开始<br />
#### &emsp;&emsp; 2.五大数据类型
##### &emsp;&emsp;&emsp;&emsp; 4.2.1.String（字符串）
&emsp;&emsp;&emsp;&emsp;string是redis最基本的类型，你可以理解成与Memcached一模一样的类型，一个key对应一个value。<br />
&emsp;&emsp;&emsp;&emsp;string类型是二进制安全的。意思是redis的string可以包含任何数据。比如jpg图片或者序列化的对象 。<br />
&emsp;&emsp;&emsp;&emsp;string类型是Redis最基本的数据类型，一个redis中字符串value最多可以是512M。<br />
##### &emsp;&emsp;&emsp;&emsp; 4.2.2	hash(哈希，与java中map相似)
&emsp;&emsp;&emsp;&emsp;Redis hash 是一个键值对集合。<br />
&emsp;&emsp;&emsp;&emsp;Redis hash 是一个String类型的field和value的映射表，hash特别适合用于存储对象。<br />
##### &emsp;&emsp;&emsp;&emsp; 4.2.3List(列表)
&emsp;&emsp;&emsp;&emsp;Redis List是简单的字符串列表，按照插入顺序排序，可以添加一个元素到列表的头部(左边)或者尾部(右边)。<br />
&emsp;&emsp;底层通过链表实现。<br />
##### &emsp;&emsp;&emsp;&emsp; 4.2.4set(集合)
&emsp;&emsp;&emsp;&emsp;Redis的set是string类型的无序集合。通过hash table实现。<br />
##### &emsp;&emsp;&emsp;&emsp; 4.2.5 zset(有序集合)
&emsp;&emsp;&emsp;&emsp;Redis zset和set一样是string类型元素的集合，且不允许重复的成员。<br />
&emsp;&emsp;&emsp;&emsp;不同的是每个元素都回关联一个double类型的分数。<br />
&emsp;&emsp;&emsp;&emsp;Redis正是通过分数为集合中的成员进行从大到小的排序。Zset的成员是唯一的，但是分数是可以重复的。<br />
#### &emsp;&emsp; 3.Redis键(key)
##### &emsp;&emsp;&emsp;&emsp; 4.3.1key *
##### &emsp;&emsp;&emsp;&emsp; 4.3.2exists
&emsp;&emsp;&emsp;&emsp;Exists key的名字，判断某个key是否存在。<br />
##### &emsp;&emsp;&emsp;&emsp; 4.3.3move key db
&emsp;&emsp;&emsp;&emsp;将当前所在数据库移除。<br />
##### &emsp;&emsp;&emsp;&emsp; 4.3.4expire key	
&emsp;&emsp;&emsp;&emsp;expire key 秒表 为给定的key设置过期时间。<br />
&emsp;&emsp; &emsp;&emsp; &emsp;&emsp; &emsp;&emsp; ![image](https://note.youdao.com/yws/api/personal/file/WEB9bea9e088d5df1012606ab231ae7b84a?method=download&shareKey=f5509f0831a912eae26c9dd0d0071e3b)<br />		
##### &emsp;&emsp;&emsp;&emsp; 4.3.5 ttl key
&emsp;&emsp;&emsp;&emsp;查看你所指定的key还有多少秒过期。<br />
##### &emsp;&emsp;&emsp;&emsp; 4.3.6type key	
&emsp;&emsp;&emsp;&emsp;Type key查看你的key是什么类型的。<br />
#### &emsp;&emsp; 4.Redis字符串(String)
##### &emsp;&emsp;&emsp;&emsp; 4.4.1set/get/del/append/strlen
&emsp;&emsp;(1)get key<br />
&emsp;&emsp;&emsp;&emsp;get key获取key的值<br />
&emsp;&emsp;(2)set key<br />
&emsp;&emsp;&emsp;&emsp;set key 设置key的值<br />
&emsp;&emsp;(3)del key<br />
&emsp;&emsp;&emsp;&emsp;del key 删除key的值<br />
&emsp;&emsp;(4)append<br />
&emsp;&emsp;&emsp;&emsp;在尾部追加值 <br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Append key值 追加的值<br />
&emsp;&emsp;(5)strlen<br />
&emsp;&emsp;&emsp;&emsp;strlen 返回键值的长度<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;strlen key值<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB4205898029dc53ce9657ee5e9c55d052?method=download&shareKey=b5a1041ce850718c7875c71a9ca8b5e9)<br />
##### &emsp;&emsp;&emsp;&emsp; 4.4.2Incr/decr/incrby/decrby
&emsp;&emsp;(1)	incr<br />
&emsp;&emsp;&emsp;&emsp;incrby 递增整数值<br />
&emsp;&emsp;&emsp;&emsp;格式：incr key值 <br />
&emsp;&emsp;(2)	decr<br />
&emsp;&emsp;&emsp;&emsp;decr 递减整数值<br />
&emsp;&emsp;&emsp;&emsp;格式：decr key值<br />
&emsp;&emsp;(3)	incrby<br />
&emsp;&emsp;&emsp;&emsp;incrby递增整数值，可指定增减的数值<br />
&emsp;&emsp;&emsp;&emsp;格式：incrby key值 正负数<br />
&emsp;&emsp;(4)	decrby<br />
&emsp;&emsp;&emsp;&emsp;decrby递减整数值，可指定增减的数值<br />
&emsp;&emsp;&emsp;&emsp;格式：decrby key值 正负数<br />
##### &emsp;&emsp;&emsp;&emsp; 4.4.3getrange/setrange
&emsp;&emsp;(1)	getrange<br />
&emsp;&emsp;&emsp;&emsp;getrange获取指定索引范围内的值。<br />
&emsp;&emsp;&emsp;&emsp;格式：getrange key值 起始索引 结束索引。<br />
&emsp;&emsp;(2)	setrange<br />
&emsp;&emsp;&emsp;&emsp;setrange设置指定索引范围的值。<br />
&emsp;&emsp;&emsp;&emsp;格式：setrange key值 起始索引 结束索引。<br />
##### &emsp;&emsp;&emsp;&emsp;4.4.4	setex(set with expire)键秒值/setnx(set if not exist)
&emsp;&emsp;(1)	setex<br />
&emsp;&emsp;&emsp;&emsp;setex设置带过期时间的key，动态设置。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		setex键 秒值 真实值
```
&emsp;&emsp;(2)	setnx<br />
&emsp;&emsp;&emsp;&emsp;setnx只有在key不存在时设置key的值。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		setnx键 秒值 真实值<br />
```
##### &emsp;&emsp;&emsp;&emsp;4.4.5	mset/mget/msetnx
&emsp;&emsp;(1)	mset<br />
&emsp;&emsp;&emsp;&emsp;mset同时设置多个键的值。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		mset key值 value(key和value可以是多对)
```
&emsp;&emsp;(2)	mget<br />
&emsp;&emsp;&emsp;&emsp;mget同时获取多个键的值。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		mget 多个key值
```
&emsp;&emsp;(3)	msetnx<br />
&emsp;&emsp;&emsp;&emsp;msetnx同时设置一个或多个key-value对，当且仅当所有给定key都不存在。<br />
&emsp;&emsp;&emsp;&emsp;格式：
```
		msetnx 多个key-value键值对
```
##### &emsp;&emsp;&emsp;&emsp;4.4.6 getset
&emsp;&emsp;&emsp;&emsp;getset：原子的设置key的值，并返回key的旧值。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		getset key value+
```
#### &emsp;&emsp;5.Redis列表(List)
##### &emsp;&emsp;&emsp;&emsp; 4.5.1 lpush/rpush/lrange
&emsp;&emsp;(1) lpush<br />
&emsp;&emsp;&emsp;&emsp;lpush添加值<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		lpush list的key item项的值(值可能是多个)
```
&emsp;&emsp;(3)	rpush<br />
&emsp;&emsp;&emsp;&emsp;rpush添加值<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		rpush list的key item项的值(值可能是多个)
```
&emsp;&emsp;(4)	lrange<br />
&emsp;&emsp;&emsp;&emsp;lrange按索引范围获取值<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		lrange list的key 其实索引 终止索引(-1表示最后一个索引)
```
##### &emsp;&emsp;&emsp;&emsp; 4.5.2 lpop/rpop
&emsp;&emsp;(1) lpop<br />
&emsp;&emsp;&emsp;&emsp;lpop弹出值<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		lpop list的key
```
&emsp;&emsp;(2)rpop<br />
&emsp;&emsp;&emsp;&emsp;rpop弹出值<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		rpop list的key
```
##### &emsp;&emsp;&emsp;&emsp;4.5.3 lindex
&emsp;&emsp;&emsp;&emsp;lindex获取指定索引的值<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		lindex list的key 索引号
```
##### &emsp;&emsp;&emsp;&emsp;4.5.4 llen
&emsp;&emsp;&emsp;&emsp;llen获取list中元素的个数<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		llen list的key
```
##### &emsp;&emsp;&emsp;&emsp;4.5.5. lrem key
&emsp;&emsp;&emsp;&emsp;lrem key删除N个value<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		lrem list的key 数量 item项的值
```
##### &emsp;&emsp;&emsp;&emsp;4.5.6 ltrim key
&emsp;&emsp;&emsp;&emsp;ltrim key截取指定范围的值后再复制给key<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		ltrim key 开始index 结束index，截取指定范围的值后再复制给key
```
##### &emsp;&emsp;&emsp;&emsp;4.5.7 rpoplpush
&emsp;&emsp;&emsp;&emsp;rpoplpush移除列表的最后一个元素，并将该元素添加到另一个列表并返回<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		rpoplpush 源列表 目的列表
```
##### &emsp;&emsp;&emsp;&emsp;4.5.8 lset
&emsp;&emsp;&emsp;&emsp;lset设置指定索引的值<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		lset list的key 索引 新值
```
##### &emsp;&emsp;&emsp;&emsp;4.5.9 linsert 
&emsp;&emsp;&emsp;&emsp;Linsert插入元素<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		linsert list的key before|after 定位查找的值 添加的值
```
##### &emsp;&emsp;&emsp;&emsp;4.5.10 性能总结
&emsp;&emsp;&emsp;&emsp;它是一个字符串链表，left、right都可以插入添加；<br />
&emsp;&emsp;&emsp;&emsp;如果键不存在，创建新的链表；<br />
&emsp;&emsp;&emsp;&emsp;如果键已存在，新增内容；<br />
&emsp;&emsp;&emsp;&emsp;如果值全移除，对应的键也就消失了。<br />
&emsp;&emsp;&emsp;&emsp;链表的操作无论是头和尾效率都极高，但假如是对中间元素进行操作，效率就很惨淡了。<br />
#### &emsp;&emsp;6.Redis集合(Set)
##### &emsp;&emsp;&emsp;&emsp;4.6.1sadd/smembers/sismember
&emsp;&emsp;(1)sadd<br />
&emsp;&emsp;&emsp;&emsp;sadd添加元素。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		sadd set的key item的项值，item项可以又多个
```
&emsp;&emsp;(2)smembers<br />
&emsp;&emsp;&emsp;&emsp;Smembers：获取集合中所有元素。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		smembers set的key
```
&emsp;&emsp;(3)sismember<br />
&emsp;&emsp;&emsp;&emsp;Sismember：判断元素是否所在集合中。<br />
##### &emsp;&emsp;&emsp;&emsp;4.6.2 scard
&emsp;&emsp;&emsp;&emsp;Scard获取集合中元素的个数。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		scard set的key
```
##### &emsp;&emsp;&emsp;&emsp;4.6.3 srem
&emsp;&emsp;&emsp;&emsp;Srem删除元素。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		srem set的key item项的值
```
##### &emsp;&emsp;&emsp;&emsp;4.6.4 srandmember
&emsp;&emsp;&emsp;&emsp;Srandmember随机获取集合的元素。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		srandmember set的key[数量]。（数量为正数时，会随机获取这么多个不重复的元素；如果数量大于集合元素个数，返回全部；如果数量为负，会随机获取这么多个元素，可能有重复。）
```
##### &emsp;&emsp;&emsp;&emsp;4.6.5 spop
&emsp;&emsp;&emsp;&emsp;Spop：弹出元素。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		spop set的key
```
#### &emsp;&emsp;4.6.6 smove
&emsp;&emsp;&emsp;&emsp;Smvoe：将一个key值赋值给另一个key。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		smove key1 key2
```
#### &emsp;&emsp;7.	Redis哈希(Hash)
#### &emsp;&emsp;(1)hset/hget/hmset/hmget/hgetall/hdel
&emsp;&emsp;(1)	hset<br />
&emsp;&emsp;&emsp;&emsp;hset:设置值。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		hset hash的key项的key项的值
```
&emsp;&emsp;(2)	hget<br />
&emsp;&emsp;&emsp;&emsp;hget:获取值。<br />
&emsp;&emsp;&emsp;&emsp;格式： <br />
```
		hget hash的key项的key
```
&emsp;&emsp;(3)	hmet<br />
&emsp;&emsp;&emsp;&emsp;hmet::同时设置多对值。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		hmet hash的key项的key项的值(项的key和项的值可以是多对)
```
&emsp;&emsp;(4)	hgetall<br />
&emsp;&emsp;&emsp;&emsp;hgetall：获取该key下所有的值。<br />
&emsp;&emsp;&emsp;&emsp;格式: <br />
```
		hgetall hash的key
```
&emsp;&emsp;(5)	hdel<br />
&emsp;&emsp;&emsp;&emsp;hdel:删除某个项。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		hdel hash的key项的key
```
#### &emsp;&emsp;(2)hlen
&emsp;&emsp;&emsp;&emsp;hlen:获取key里面的键值对数量。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		hlen hash的key
```
#### &emsp;&emsp;(3)hexists key
&emsp;&emsp;&emsp;&emsp;hexists key：判断键值对是够存在。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		hexists hash的key项的key
```
#### &emsp;&emsp;(4)hkeys/hvals
&emsp;&emsp;(1)	hkeys<br />
&emsp;&emsp;&emsp;&emsp;hkeys:获取所有的item的key。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		hkey hash的key
```
&emsp;&emsp;(2)	hvals<br />
&emsp;&emsp;&emsp;&emsp;hvals：获取所有的item的值。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		hvals hash的key
```
#### &emsp;&emsp;(5)hincrby/hincrbyfloat
&emsp;&emsp;(1)	hincrby<br />
&emsp;&emsp;&emsp;&emsp;hincrby：增减整数数字。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		hincrby Hash的key项的key正负数
```
&emsp;&emsp;&emsp;&emsp;(2)	hincrbyfloat<br />
&emsp;&emsp;&emsp;&emsp;hincrbyfloat: 增减float数值。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		hincrbyfloat Hash的key项的key正负float
```
&emsp;&emsp;(3)	hsetnx<br />
&emsp;&emsp;&emsp;&emsp;hsetnx：如果不存在则复制，存在时什么都不做。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		hsetnx Hash的key项的key项的值
```
#### &emsp;&emsp;8.Redis有序集合Zset(sorted set)
#### &emsp;&emsp; (1)zadd/zrange
&emsp;&emsp;&emsp;(1)zadd<br />
&emsp;&emsp;&emsp;&emsp;zadd：添加元素。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
	zadd zset的key score值项的值，Source和项可以是多对，score可以是整数，也可以是浮点数，还可以是+inf表示无限大，-inf表示负无穷大
```
&emsp;&emsp;&emsp;&emsp;(2)zrange<br />
&emsp;&emsp;&emsp;&emsp;zrange:获取索引区间内的元素。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		zrange zset的key其实索引 终止索引(withscore)
```
#### &emsp;&emsp; (2)zrangebyscore 
&emsp;&emsp;&emsp;&emsp;zrangebyscore :获取分数区间内的元素。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		zrangebyscore zset的key 起始score 终止score (withscore),默认是包含端点值的，如果加上"("表示不包含，后面还可以加上limit来限制。
```
#### &emsp;&emsp;(3)zrem
&emsp;&emsp;&emsp;&emsp;zrem:删除元素。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		zrem zset的key项的值，项的值可以是多个
```
#### &emsp;&emsp;(4)zcard/zcount
&emsp;&emsp;&emsp;(1)zcard<br />
&emsp;&emsp;&emsp;&emsp;zcard：获取集合中元素个数。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		zcard zset的key
```
&emsp;&emsp;&emsp;&emsp;(2)zcount<br />
&emsp;&emsp;&emsp;&emsp;zcount：获取分数区间内元素个数。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		zcount zset的key起始score终止score
```
#### &emsp;&emsp; (5)zrevrank
&emsp;&emsp;&emsp;&emsp;zrevrank：获取项在zset中倒序的索引。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		zrevrank zset的key项的值
```
#### &emsp;&emsp; (6)zrevrange
&emsp;&emsp;&emsp;&emsp;zrevrange：获取索引区间内的元素。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		zrevrange zset的key其实索引 终止索引 (withscores)
```
#### &emsp;&emsp;(7)zrevrangebyscore
&emsp;&emsp;&emsp;&emsp;zrevrangebyscore：获取分数区间内的元素。<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		zrevrangebyscore zset的key 终止scroe 起始score(withscores)
```
## 五、Redis的持久化
#### &emsp;&emsp; 1、RDB(Redis DataBase)
#### &emsp;&emsp; (1)是什么
&emsp;&emsp;1)定义<br />
&emsp;&emsp;&emsp;&emsp;在指定的时间间隔内将内存中的数据集快照写入磁盘，也就是行话将的Snapshot快照，它恢复时时将快照文件直接读到内存里。<br />
&emsp;&emsp;2)具体<br />
&emsp;&emsp;&emsp;&emsp;Redis会单独创建(fork)一个子线程类进行持久化，会先将数据写入到一个临时文件中，待持久化过程结束了，再将这个临时文件替换上次持久化好的文件。整个过程中，主进程时不进行任何IO操作的，这就确保了极高的性能，如果需要进行大规模数据的恢复，且对于数据恢复的完整性不是非常敏感，那RDB方式要比AOF方式更加的高效。RDB的缺点是最后一次持久化后的数据可能丢失。<br />
#### &emsp;&emsp; (2)Fork<br />
&emsp;&emsp;&emsp;&emsp;Fork的作用就是复制一个与当前线程一样的线程。新线程的所有数据(变量、环境变量、程序计数器等)，数值都和原进程一致，但是是一个全新的进程，并作为原进程的子进程。<br />
#### &emsp;&emsp; (3)rdb保存的是dump.rdb文件<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB8496c5059b9b647f2320e48cae2d51d8?method=download&shareKey=38c3c39522d91047c7a8beef45c14615)<br />
#### &emsp;&emsp; (4)如何出发PDB快照<br />
&emsp;&emsp;(1)	配置文件中默认的快照配置<br />
&emsp;&emsp;&emsp;&emsp;冷拷贝后重新使用，可以cp dump.rdb dump_new.rdb<br />
&emsp;&emsp;(2)	命令save或者bgsave<br />
&emsp;&emsp;&emsp;1)Save<br />
&emsp;&emsp;&emsp;&emsp;Save时只保管保存，其他不管，全部阻塞<br />
&emsp;&emsp;&emsp;2)bgsave<br />
&emsp;&emsp;&emsp;&emsp;Redis会在后台异步进行快照操作，快照同时还可以响应客户端请求。可以通过lastsave命令获取最后一次成功执行快照的时间。<br />
&emsp;&emsp;(3)	执行flushall命令，也会产生dump.rdb文件，但是里面时空的，无意义。<br />
#### &emsp;&emsp; (5)如何恢复
&emsp;&emsp;&emsp;&emsp;将备份文件(dump.rdb)移动到redis安装目录并启动服务即可。<br />
&emsp;&emsp;&emsp;&emsp;Config get dir获取目录。<br />
#### &emsp;&emsp;(6)优势
&emsp;&emsp;&emsp;&emsp;(1)适合大规模的数据恢复。<br />
&emsp;&emsp;&emsp;&emsp;(2)对数据完整性和一致性要求不高。<br />
#### &emsp;&emsp;(7)劣势
&emsp;&emsp;&emsp;&emsp;(1)在一定间隔时间做一次备份，所以如果redis以为down掉的话，就会丢失最后一次快照后的所有修改。<br />
&emsp;&emsp;&emsp;&emsp;(2)fork的时候，内存中的数据被克隆了一份，大致2倍的膨胀性需要考虑。<br />
#### &emsp;&emsp;(8)如何停止
&emsp;&emsp;&emsp;&emsp;动态所有停止RDB保存规则的方法：redis-cli config set save " "。<br />
#### &emsp;&emsp;2、AOF(Append Only File)
#### &emsp;&emsp; (1)是什么
&emsp;&emsp;&emsp;&emsp;以日志的形式来记录每个操作，将Redis执行过的所有写指令记录下来(读操作不记录)，只许最近文件但不可以改写文件，redis启动之初会读取该文件重新构建数据，换言之，redis重启的话就会根据日志文件的内容将写入指令从前到后执行一次以完成数据的恢复工作。<br />
#### &emsp;&emsp; (2)AOF保存的是appendonly.aof文件
#### &emsp;&emsp; (3)配置位置
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image](https://note.youdao.com/yws/api/personal/file/WEB79c2173a7d2e826bef3ef0c6b4cef3fe?method=download&shareKey=91218a1578775978a3c3b542bb7c93ce)<br />
#### &emsp;&emsp;(4)AOF启动/恢复/修复
&emsp;&emsp;1)正常恢复<br />
&emsp;&emsp;&emsp;A、启动<br />
&emsp;&emsp;&emsp;&emsp;设置为Yes，修改appendonly no为yes<br />
&emsp;&emsp;&emsp;B、保存<br />
&emsp;&emsp;&emsp;&emsp;将所有的aof文件复制一份保存到对应目录(config get dir)<br />
&emsp;&emsp;&emsp;C、恢复<br />
&emsp;&emsp;&emsp;&emsp;重启redis然后重新加载<br />
&emsp;&emsp;2)异常恢复<br />
&emsp;&emsp;&emsp;A、启动<br />
&emsp;&emsp;&emsp;&emsp;设置为Yes，修改appendonly no为yes<br />
&emsp;&emsp;&emsp;B、备份被写坏的AOF文件<br />
&emsp;&emsp;&emsp;C、修复<br />
&emsp;&emsp;&emsp;&emsp;Redis-check-aof –fix进行修复<br />
&emsp;&emsp;&emsp;D、恢复<br />
&emsp;&emsp;&emsp;&emsp;重启redis然后重新加载<br />
#### &emsp;&emsp; (5)rewrite<br />
&emsp;&emsp;1)是什么<br />
&emsp;&emsp;&emsp;&emsp;AOF采用文件追加方式，文件会越来越大为避免出现此种情况，新增了重写机制，当AOF文件的大小超过所设定的阈值时，Redis就会启动AOF文件的内容压缩，只保留可以恢复数据的最小指令集.可以使用命令bgrewriteaof。<br />
&emsp;&emsp;2)重写原理<br />
&emsp;&emsp;&emsp;&emsp;AOF文件持续增长而过大时，会fork出一条新进程来将文件重写(也是先写临时文件最后再rename)，遍历新进程的内存中数据，每条记录有一条的Set语句。重写aof文件的操作，并没有读取旧的aof文件，而是将整个内存中的数据库内容用命令的方式重写了一个新的aof文件，这点和快照有点类似。<br />
&emsp;&emsp;3)触发机制<br />
&emsp;&emsp;&emsp;&emsp;Redis会记录上次重写时的AOF大小，默认配置是当AOF文件大小是上次rewrite后大小的一倍且文件大于64M时触发。<br />
#### &emsp;&emsp; (6)优势
&emsp;&emsp;(1)每修改同步<br />
&emsp;&emsp;&emsp;&emsp;appendfsync always   同步持久化 每次发生数据变更会被立即记录到磁盘  性能较差但数据完整性比较好<br />
&emsp;&emsp;(2)每秒同步<br />
&emsp;&emsp;&emsp;&emsp;appendfsync everysec    异步操作，每秒记录   如果一秒内宕机，有数据丢失<br />
&emsp;&emsp;(3)不同步<br />
&emsp;&emsp;&emsp;&emsp;appendfsync no   从不同步<br />
#### &emsp;&emsp;(7)劣势
&emsp;&emsp;(1)相同数据集的数据而言aof文件要远大于rdb文件，恢复速度慢于rdb。<br />
&emsp;&emsp;(2)aof运行效率要慢于rdb,每秒同步策略效率较好，不同步效率和rdb相同。<br />
## 六、Redis事务
#### &emsp;&emsp; 1、是什么
&emsp;&emsp;&emsp;&emsp;可以一次执行多个命令，本质一组命令的集合，一个事务中的所有命令都会序列化，按顺序地串行执行而不会被其他命令插入，不许加塞。<br />
#### &emsp;&emsp; 2、能干嘛
&emsp;&emsp;&emsp;&emsp;一个队列中，一次性、顺序性、排他性地执行一系列命令。<br />
#### &emsp;&emsp;3、怎么玩
&emsp;&emsp;(1)取消事务<br />
&emsp;&emsp;&emsp;&emsp;格式：<br />
```
		redis 本地IP:端口号 DISCARD
```
&emsp;&emsp;(2)执行所有事务块内地命令<br />
```
	Exec
```
&emsp;&emsp;(3)取消watch事务块内的命令<br />
```
		Unwatch
```
&emsp;&emsp;(4)	监视一个(或多个) key ，如果在事务执行之前这个(或这些) key 被其他命令所改动，那么事务将被打断。
```
		Wach key[key……]
```
&emsp;&emsp;(5)	watch监控<br />
&emsp;&emsp;&emsp;1)乐观锁/悲观锁/CAS<br />
&emsp;&emsp;&emsp;&emsp;(1)悲观锁<br />
&emsp;&emsp;&emsp;&emsp;悲观锁(Pessimistic Lock), 顾名思义，就是很悲观，每次去拿数据的时候都认为别人会修改，所以每次在拿数据的时候都会上锁，这样别人想拿这个数据就会block直到它拿到锁。传统的关系型数据库里边就用到了很多这种锁机制，比如行锁，表锁等，读锁，写锁等，都是在做操作之前先上锁。<br />
&emsp;&emsp;&emsp;&emsp;(2)	乐观锁<br />
&emsp;&emsp;&emsp;&emsp;乐观锁(Optimistic Lock), 顾名思义，就是很乐观，每次去拿数据的时候都认为别人不会修改，所以不会上锁，但是在更新的时候会判断一下在此期间别人有没有去更新这个数据，可以使用版本号等机制。乐观锁适用于多读的应用类型，这样可以提高吞吐量。<br />
&emsp;&emsp;&emsp;&emsp;乐观锁策略:提交版本必须大于记录当前版本才能执行更新。<br />
&emsp;&emsp;&emsp;2)有加塞篡改<br />
&emsp;&emsp;&emsp;&emsp;监控了key，如果key被修改了，后面一个事务的执行失效。<br />
&emsp;&emsp;&emsp;3)小结<br />
&emsp;&emsp;&emsp;&emsp;(1)Watch指令，类似乐观锁，事务提交时，如果Key的值已被别的客户端改变，比如某个list已被别的客户端push/pop过了，整个事务队列都不会被执行。<br />
&emsp;&emsp;&emsp;&emsp;(2)通过WATCH命令在事务执行之前监控了多个Keys，倘若在WATCH之后有任何Key的值发生了变化，EXEC命令执行的事务都将被放弃，同时返回Nullmulti-bulk应答以通知调用者事务执行失败。<br />
#### &emsp;&emsp; 4、3阶段
&emsp;&emsp;(1)开启<br />
&emsp;&emsp;&emsp;&emsp;以MULTI开始一个事务。<br />
&emsp;&emsp;(2)入队<br />
&emsp;&emsp;&emsp;&emsp;将多个命令入队到事务中，接到这些命令并不会立即执行，而是放到等待执行的事务队列里面。<br />
&emsp;&emsp;(3)执行<br />
&emsp;&emsp;&emsp;&emsp;由EXEC命令触发事务。<br />
#### &emsp;&emsp; 5、3特性
&emsp;&emsp;(1)单独地隔离操作<br />
&emsp;&emsp;&emsp;&emsp;事务中的所有命令都会序列化、按顺序地执行。事务在执行的过程中，不会被其他客户端发送来的命令请求所打断。<br />
&emsp;&emsp;(2)没有隔离级别的概念<br />
&emsp;&emsp;&emsp;&emsp;队列中的命令没有提交之前都不会实际的被执行，因为事务提交前任何指令都不会被实际执行，也就不存在”事务内的查询要看到事务里的更新，在事务外查询不能看到”这个让人万分头痛的问题。<br />
&emsp;&emsp;(3)不保证原子性<br />
&emsp;&emsp;&emsp;&emsp;redis同一个事务中如果有一条命令执行失败，其后的命令仍然会被执行，没有回滚。<br />
## 七、Redis地发布订阅
#### &emsp;&emsp; (1)是什么
&emsp;&emsp;&emsp;&emsp;进程间的一种消息通信模式：发送者(pub)发送消息，订阅者(sub)接收消息。<br />
#### &emsp;&emsp; 2)案例
&emsp;&emsp;&emsp;先订阅后发布后才能收到消息，<br />
&emsp;&emsp;&emsp;&emsp;1 可以一次性订阅多个，SUBSCRIBE c1 c2 c3。<br />
&emsp;&emsp;&emsp;&emsp;2 消息发布，PUBLISH c2 hello-redis。<br />
&emsp;&emsp;&emsp;&emsp;3 订阅多个，通配符*， PSUBSCRIBE new*。<br />
&emsp;&emsp;&emsp;&emsp;4 收取消息， PUBLISH new1 redis2015。<br />
## 八、Redis地Java客户端Jedis
#### &emsp;&emsp; (1)是什么
&emsp;&emsp;&emsp;&emsp;行话：也就是我们所说的主从复制，主机数据更新后根据配置和策略，自动同步到备机的master/slaver机制，Master以写为主，Slave以读为主。<br />
#### &emsp;&emsp; (2)能干啥
&emsp;&emsp;&emsp;&emsp;(1)读写分离<br />
&emsp;&emsp;&emsp;&emsp;(2)容灾恢复<br />
#### &emsp;&emsp; (3)怎么玩
&emsp;&emsp;&emsp;(1)配从(库)不配主(库)<br />
&emsp;&emsp;&emsp;(2)从库配置<br />
&emsp;&emsp;&emsp;&emsp;每次与master断开之后，都需要重新连接，除非你配置进redis.conf文件。<br />
&emsp;&emsp;&emsp;&emsp;info replication<br />
&emsp;&emsp;&emsp;(3)修改配置文件细节操作<br />
&emsp;&emsp;&emsp;&emsp;1)拷贝redis.conf文件<br />
&emsp;&emsp;&emsp;&emsp;2)开启daemonize yes<br />
&emsp;&emsp;&emsp;&emsp;3)pid文件名字<br />
&emsp;&emsp;&emsp;&emsp;4)指定端口<br />
&emsp;&emsp;&emsp;&emsp;5)log文件名字<br />
&emsp;&emsp;&emsp;&emsp;6)dump.rdb名字<br />
&emsp;&emsp;&emsp;(4)常用3招<br />
&emsp;&emsp;&emsp;&emsp;1)一仆二主<br />
&emsp;&emsp;&emsp;&emsp;&emsp;A．Init<br />
&emsp;&emsp;&emsp;&emsp;&emsp;B．一个Master两个Slave<br />
&emsp;&emsp;&emsp;&emsp;&emsp;C．日志查看<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(1)主机日志<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(2)备机日志<br />
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(3)info replication<br />
&emsp;&emsp;&emsp;&emsp;&emsp;D．主从问题<br />
&emsp;&emsp;&emsp;&emsp;2)薪火相传<br />
&emsp;&emsp;&emsp;&emsp;&emsp;A．上一个Slave可以是下一个slave的Master，Slave同样可以接收其他slaves的连接和同步请求，那么该slave作为了链条中下一个的master，可以有效减轻master的写压力。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;B．中途变更转向<br />
&emsp;&emsp;&emsp;&emsp;会清除之前的数据，重新建立拷贝最新的。<br />
&emsp;&emsp;&emsp;&emsp;&emsp;C．slaveof 新主库IP 新主库端口<br />
&emsp;&emsp;&emsp;&emsp;3)反客为主<br />
&emsp;&emsp;&emsp;&emsp;SLAVEOF no one：使当前数据库停止与其他数据库的同步，转成主数据库<br />
#### &emsp;&emsp; (4)复制原理
&emsp;&emsp;&emsp;(1) slave启动成功连接到master后会发送一个sync命令。<br />
&emsp;&emsp;&emsp;(2) Master接到命令启动后台的存盘进程，同时收集所有接收到的用于修改数据集命令，在后台进程执行完毕之后，master将传送整个数据文件到slave,以完成一次完全同步。<br />
&emsp;&emsp;&emsp;(3)全量复制<br />
&emsp;&emsp;&emsp;&emsp;而slave服务在接收到数据库文件数据后，将其存盘并加载到内存中。<br />
&emsp;&emsp;&emsp;(4)增量复制<br />
&emsp;&emsp;&emsp;&emsp;Master继续将新的所有收集到地修改命令一次传给clave，完成同步。<br />
&emsp;&emsp;&emsp;(5)但是只要是重新连接master,一次完全同步（全量复制)将被自动执行。<br />
#### &emsp;&emsp; (5)哨兵模式
&emsp;&emsp;&emsp;(1)是什么<br />
&emsp;&emsp;&emsp;&emsp;反客为主的自动版，能够后台监控主机是否故障，如果故障了根据投票数自动将从库转换为主库。<br />
&emsp;&emsp;&emsp;(2)怎么玩(使用步骤)<br />
&emsp;&emsp;&emsp;&emsp;(1)调整结构，6379带着80、81<br />
&emsp;&emsp;&emsp;&emsp;(2)自定义的/myredis目录下新建sentinel.conf文件，名字绝不能错<br />
&emsp;&emsp;&emsp;&emsp;(3)配置哨兵,填写内容<br />
&emsp;&emsp;&emsp;(1)sentinel monitor被疾控数据库名字(自己起名字)127.0.0.1:6379 1<br />
&emsp;&emsp;&emsp;(2)上面最后一个数字1，表示主机挂掉后salve投票看让谁集体成为主机，得票数多少后成为主机<br />
&emsp;&emsp;&emsp;&emsp;(4)启动哨兵<br />
&emsp;&emsp;&emsp;&emsp;&emsp;(1)redis-sentinel/myredis/sentinel.conf<br />
&emsp;&emsp;&emsp;&emsp;&emsp;(2)上述目录依照各自地实际情况配置，可能目录<br />
&emsp;&emsp;&emsp;&emsp;(5)正常主从演示<br />
&emsp;&emsp;&emsp;&emsp;(6)原有的master挂了<br />
&emsp;&emsp;&emsp;&emsp;(7)投票新选<br />
&emsp;&emsp;&emsp;&emsp;(8)重新主从继续开工，info replication查查看<br />
&emsp;&emsp;&emsp;&emsp;(9)问题：如果之前的master重启回来，会不会双master冲突？<br />
&emsp;&emsp;&emsp;(3)一组sentinel能同时监控多个Master<br />
