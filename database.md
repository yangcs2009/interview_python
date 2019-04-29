
<!-- vim-markdown-toc GFM -->

* [数据库](#数据库)
    * [1 事务](#1-事务)
        * [事务的四个特性](#事务的四个特性)
        * [数据库隔离级别](#数据库隔离级别)
        * [事务的四个隔离级别](#事务的四个隔离级别)
        * [隔离级别的选择](#隔离级别的选择)
    * [2 数据库索引](#2-数据库索引)
    * [3 缓存那些事，兼论redis和memcached](#3-缓存那些事兼论redis和memcached)
        * [memcached](#memcached)
        * [Redis](#redis)
            * [Redis数据模型图](#redis数据模型图)
            * [6种的数据淘汰策略](#6种的数据淘汰策略)
            * [应用场景](#应用场景)
    * [4 乐观锁和悲观锁](#4-乐观锁和悲观锁)
    * [5 MVCC](#5-mvcc)
    * [6 MyISAM和InnoDB](#6-myisam和innodb)
    * [7 范式](#7-范式)

<!-- vim-markdown-toc -->

# 数据库

## 1 事务

**数据库事务(Database Transaction)** ，是指作为单个逻辑工作单元执行的一系列操作，要么完全地执行，要么完全地不执行。
一方面，当多个应用程序并发访问数据库时，事务可以在应用程序间提供一个隔离方法，防止互相干扰。另一方面，事务为数据库操作序列提供了一个从失败恢复正常的方法。

### 事务的四个特性

事务具有四个特性：原子性（Atomicity）、一致性（Consistency）、隔离型（Isolation）、持久性（Durability），简称ACID。

**原子性（Atomicity）** 事务的原子性是指事务中的操作不可拆分，只允许全部执行或者全部不执行。

**一致性（Consistency）** 事务的一致性是指事务的执行不能破坏数据库的一致性，一致性也称为完整性。一个事务在执行后，数据库必须从一个一致性状态转变为另一个一致性状态。

**隔离型（Isolation）** 事务的隔离型是指并发的事务相互隔离，不能互相干扰。

**持久性（Durability）** 事务的持久性是指事务一旦提交，对数据的状态变更应该被永久保存。

### 数据库隔离级别

对于同时运行的多个事务,当这些事务访问数据库中相同的数据时,如果没有采取必要的隔离机制,就会导致各种并发问题:

**脏读**：对于两个事务T1，T2，T1读取了已经被T2更新但还没有提交的字段，之后，若T2回滚，T1读取到的内容就是临时无效的内容。

**不可重复读**：对于事务T1，T2，T1需要读取一个字段两次，在第一次和第二次读取之间，T2更新或删除了该字段，导致T1第二次读取到的内容值不同。

**幻读**： 事务A读取与搜索条件相匹配的若干行。事务B以插入方式来修改事务A的结果集，然后再提交。  
**幻读与不可重复读之间的区别是幻读强调的是新增insert,而不可重复读强调的是修改update和删除delete**。  
比如Mary两次查工资，中间有人update或delete过工资，则两次结果不一样，这就是不可重复读。Mary要查工资一千的人数，第一次查到了10个，中间有人增加了一条工资为一千的人，下次查的时候就变成了11个，好像第一次查询的是幻觉一样。

### 事务的四个隔离级别 
实际工作中事务几乎都是并发的，完全做到互相之间不干扰会严重牺牲性能，为了平衡隔离型和性能，SQL92规范定义了四个事务隔离级别：读未提交（Read Uncommitted）、读已提交（Read Committed）、可重复读（Repeatable Read）、串行化（Serializable）。四个级别逐渐增强，每个级别解决上个级别的一个问题。

**读未提交（Read Uncommitted）** 另一个事务修改了数据，但尚未提交，而本事务中的SELECT会读到这些未被提交的数据（脏读）。 脏读是指另一个事务修改了数据，但尚未提交，而本事务中的SELECT会读到这些未被提交的数据。

**读已提交（Read Committed）** 本事务读取到的是最新的数据（其他事务提交后的）。问题是，在同一个事务里，前后两次相同的SELECT会读到不同的结果（不可重复读）。

**可重复读（Repeatable Read）** 在同一个事务里，SELECT的结果是事务开始时间点的状态，同样的SELECT操作读到的结果会是一致的。但是，会有幻读现象。
可重复读保证了同一个事务里，查询的结果都是事务开始时的状态（一致性）。但是，如果另一个事务同时提交了新数据，本事务再更新时，就会发现了这些新数据，貌似之前读到的数据是幻觉，这就是幻读。

**串行化（Serializable）** 所有事务只能一个接一个串行执行，不能并发。

![事务隔离级别](img/transaction_isolation.png)

### 隔离级别的选择

事务隔离级别越高，越能保证数据的一致性，但对并发性能影响越大，一致性和高性能必须有所取舍或折中。
一般情况下，多数应用程序可以选择将数据库的隔离级别设置为读已提交，这样可以避免脏读，也可以得到不错的并发性能。尽管这个隔离级别会导致不可重复度、幻读，但这种个别场合应用程序可以通过主动加锁进行并发控制。

Oracle支持两种隔离级别，READ COMMITED和SERIALIZABLE默认的事务隔离级别是READ COMMITED

MYSQL支持4中隔离界别，默认的是`REPEATED READ`

## 2 数据库索引

推荐:
 [MySQL索引原理及慢查询优化](http://tech.meituan.com/mysql-index.html)

[MySQL索引背后的数据结构及算法原理](http://blog.codinglabs.org/articles/theory-of-mysql-index.html)

聚集索引,非聚集索引,B-Tree,B+Tree,最左前缀原理

**建立数据库索引的作用**

数据库索引是将数据库表中的`某一列或几列`以特定的数据结构存起来，比如B-Tree，Hash等，这样查找的时候就可以不用从头插到尾要O(n)，
这样可以缩短到O(log)级别甚至O(1)。
建立索引之后查找和修改，排序等操作可以省很多时间。
索引是对数据库表中一个或多个列（例如，employee 表的姓名 (name) 列）的值进行排序的结构。如果想按特定职员的姓来查找他或她，
则与在表中搜索所有的行相比，索引有助于更快地获取信息。
例如这样一个查询：select * from table1 where id=10000。如果没有索引，必须遍历整个表，直到ID等于10000的这一行被找到为止；
有了索引之后(必须是在ID这一列上建立的索引)，即可在索引中查找。由于索引是经过某种算法优化过的，因而查找次数要少的多。可见，索引是用来定位的。
数据库索引好比是一本书前面的目录，能加快数据库的查询速度。

**聚簇索引与非聚簇索引**

索引分为聚簇索引和非聚簇索引两种，聚簇索引是按照数据存放的物理位置为顺序的，就像书中的目录，内容是按照页码顺序排列的，
而非聚簇索引就不一样了；聚簇索引能提高多行检索的速度，而非聚簇索引对于单行的检索很快。
注意一个表只能有一个聚集索引，但是可以由多个非聚集索引。

**唯一索引 主键索引 聚集索引**

接下来说以下三种不同的索引： 根据数据库的功能，可以在数据库设计器中创建三种索引：唯一索引、主键索引和聚集索引。 
提示：尽管唯一索引有助于定位信息，但为获得最佳性能结果，建议改用主键或唯一约束。

* 唯一索引
**唯一索引是不允许其中任何两行具有相同索引值的索引**。不是只能建一个索引。 当现有数据中存在重复的键值时，
大多数数据库不允许将新创建的唯一索引与表一起保存。数据库还可能防止添加将在表中创建重复键值的新数据。
例如，如果在employee表中职员的姓(lname)上创建了唯一索引，则任何两个员工都不能同姓。

* 主键索引
数据库表经常有一列或多列组合，其值唯一标识表中的每一行。该列称为表的主键。在数据库关系图中为表定义主键将自动创建主键索引，
**主键索引是唯一索引的特定类型**。该索引要求主键中的每个值都唯一。当在查询中使用主键索引时，它还允许对数据的快速访问。

* 聚集索引
在聚集索引中，表中行的物理顺序与键值的逻辑（索引）顺序相同。一个表只能包含一个聚集索引。如果某索引不是聚集索引，
则表中行的物理顺序与键值的逻辑顺序不匹配。与非聚集索引相比，聚集索引通常提供更快的数据访问速度。

* 索引列 可以基于数据库表中的单列或多列创建索引。多列索引可以区分其中一列可能有相同值的行。

* 如果经常同时搜索两列或多列或按两列或多列排序时，索引也很有帮助。例如，如果经常在同一查询中为姓和名两列设置判据，
那么在这两列上创建多列索引将很有意义。

## 3 缓存那些事，兼论redis和memcached
[缓存那些事](https://tech.meituan.com/cache_about.html)  
[memcached完全剖析系列](https://charlee.li/memcached-001.html)

### memcached
memcached本身不提供分布式解决方案。在服务端，memcached集群环境实际就是一个个memcached服务器的堆积，环境搭建较为简单；cache的分布式主要是在客户端
实现，通过客户端的路由处理来达到分布式解决方案的目的。
![memcached客户端路由图](img/database/memcache路由图.png)

![memcached一致性hash](img/database/memcache一致性hash.png)
memcached客户端采用一致性hash算法作为路由策略

memcached的内存管理机制
![memcached内存结构图](img/database/memcache内存结构图.png)
**slab**是一个内存块，它是memcached一次申请内存的 **最小单位**。在启动memcached的时候一般会使用参数-m指定其可用内存，但是并不是在启动的那一刻所有的
内存就全部分配出去了，只有在需要的时候才会去申请，而且每次申请一定是一个slab。Slab的大小固定为 **1M**（1048576 Byte），一个slab由若干个大小相等的
**chunk**组成。每个chunk中都保存了一个item结构体、一对key和value。  
虽然在同一个slab中chunk的大小相等的，但是在不同的slab中chunk的大小并不一定相等，在memcached中按照chunk的大小不同，可以把slab分为很多
种类（class），默认情况下memcached把slab分为41类（class1～class40），在class 1中，chunk的大小为80字节，由于一个slab的大小是固定的
1048576字节（1M），因此在class1中最多可以有13107个chunk（也就是这个slab能存最多13107个小于80字节的key-value数据）。
memcached内存管理采取 **预分配、分组管理**的方式，分组管理就是我们上面提到的slab class，按照chunk的大小slab被分为很多种类。内存预分配过程是怎样的呢？
向memcached添加一个item时候，memcached首先会根据item的大小，来选择最合适的slab class：例如item的大小为190字节，默认情况下class 4的chunk
大小为160字节显然不合适，class 5的chunk大小为200字节，大于190字节，因此该item将放在class 5中（显然这里会有10字节的浪费是不可避免的），
计算好所要放入的chunk之后，memcached会去检查该类大小的chunk还有没有空闲的，如果没有，将会申请1M（1个slab）的空间并划分为该种类chunk。
例如我们第一次向memcached中放入一个190字节的item时，memcached会产生一个slab class 2（也叫一个page），并会用去一个chunk，剩余5241个
chunk供下次有适合大小item时使用，当我们用完这所有的5242个chunk之后，下次再有一个在160～200字节之间的item添加进来时，memcached会再次产生
一个class 5的slab（这样就存在了2个pages）。  

**总结**来看，memcached内存管理需要注意的几个方面：  
* chunk是在page里面划分的，而page固定为1m，所以chunk最大不能超过1m。  
* chunk实际占用内存要加48B，因为chunk数据结构本身需要占用48B。  
* 如果用户数据大于1m，则memcached会将其切割，放到多个chunk内。  
* 已分配出去的page不能回收。  
* 数据没有持久化，集群故障重启数据无法恢复  
对于key-value信息，最好不要超过1m的大小；同时信息长度最好相对是比较均衡稳定的，这样能够保障最大限度的使用内存；同时，memcached采用的LRU清理策略，合理甚至过期时间，提高命中率。

### Redis
[redis设计与实现笔记](https://blog.csdn.net/yangcs2009/article/details/50637165)
#### Redis数据模型图
![Redis数据模型图](img/database/encoding.png)  
字符串可以被编码为embstr(小于39字节）、raw（一般字符串）或int（为了节约内存，Redis会将字符串表示的64位有符号整数编码为整数来进行储存）；  
列表可以被编码为ziplist或linkedlist，ziplist是为节约大小较小的列表空间而作的特殊表示；  
集合可以被编码为intset或者hashtable，intset是只储存数字的小集合的特殊表示；  
hash表可以编码为ziplist或者hashtable，zipmap是小hash表的特殊表示；  
有序集合可以被编码为ziplist或者skiplist格式，ziplist用于表示小的有序集合，而skiplist则用于表示任何大小的有序集合。  

#### 6种的数据淘汰策略
1. volatile-lru：从已设置过期时间的数据集（server.db[i].expires）中挑选最近最少使用的数据淘汰；
2. volatile-ttl：从已设置过期时间的数据集（server.db[i].expires）中挑选将要过期的数据淘汰；
3. volatile-random：从已设置过期时间的数据集（server.db[i].expires）中任意选择数据淘汰 ；
4. allkeys-lru：从数据集（server.db[i].dict）中挑选最近最少使用的数据淘汰；
5. allkeys-random：从数据集（server.db[i].dict）中任意选择数据淘汰；
6. no-enviction（驱逐）：禁止驱逐数据。

#### 应用场景
* 在主页中显示最新的项目列表：Redis使用的是常驻内存的缓存，速度非常快。LPUSH用来插入一个内容ID，作为关键字存储在列表头部。LTRIM用来限制列表中
的项目数最多为5000。如果用户需要的检索的数据量超越这个缓存容量，这时才需要把请求发送到数据库。  
* 删除和过滤：如果一篇文章被删除，可以使用LREM从缓存中彻底清除掉。  
* 排行榜及相关问题：排行榜（leader board）按照得分进行排序。ZADD命令可以直接实现这个功能，而ZREVRANGE命令可以用来按照得分来获取前100名的用户，
ZRANK可以用来获取用户排名，非常直接而且操作容易。  
* 按照用户投票和时间排序：排行榜，得分会随着时间变化。LPUSH和LTRIM命令结合运用，把文章添加到一个列表中。一项后台任务用来获取列表，并重新计算列表的排序，
ZADD命令用来按照新的顺序填充生成列表。列表可以实现非常快速的检索，即使是负载很重的站点。  
* 过期项目处理：使用Unix时间作为关键字，用来保持列表能够按时间排序。对current_time和time_to_live进行检索，完成查找过期项目的艰巨任务。
另一项后台任务使用ZRANGE…WITHSCORES进行查询，删除过期的条目。  
* 计数：进行各种数据统计的用途是非常广泛的，比如想知道什么时候封锁一个IP地址。INCRBY命令让这些变得很容易，通过原子递增保持计数；GETSET用来重置计数器；
过期属性用来确认一个关键字什么时候应该删除。  
* 特定时间内的特定项目：这是特定访问者的问题，可以通过给每次页面浏览使用SADD命令来解决。SADD不会将已经存在的成员添加到一个集合。
* Pub/Sub：在更新中保持用户对数据的映射是系统中的一个普遍任务。Redis的pub/sub功能使用了SUBSCRIBE、UNSUBSCRIBE和PUBLISH命令，让这个变得更加容易。
* 队列：在当前的编程中队列随处可见。除了push和pop类型的命令之外，Redis还有阻塞队列的命令，能够让一个程序在执行时被另一个程序添加到队列。
## 4 乐观锁和悲观锁

悲观锁：假定会发生并发冲突，屏蔽一切可能违反数据完整性的操作

乐观锁：假设不会发生并发冲突，只在提交操作时检查是否违反数据完整性。

## 5 MVCC


## 6 MyISAM和InnoDB

Myisam与InnoDB的区别：

最主要的一点是MyIsam不支持`事务操作，外键以及行级锁`，而InnoDB支持这些功能。MyIsam只支持表级锁，当多线程并发操作数据库时，
就会为整个表上锁，而InnoDB 则从行上锁。但这也是不一定的，如果一个SQL语句不能确定扫描范围的话，也会为整个表上锁，
比如： update table set num=1 where name like “%aaa%”

但是MyIsam的`读的速度`比InnoDB更加快一些，InnoDB不保存表的行数，比如要执行count(*)的话，它就会扫描整个表，但是如果是MyIsam的话，直接返回行数

InnoDB执行Drop from table 时，不会重新建表，而是一行一行删除。如果执行大量的select操作选择MyIsam，如果有大量的insert和update操作，选择InnoDB。

AUTO_INCREMENT 对于AUTO_INCREMENT类型的字段，InnoDB中必须包含只有该字段的索引，但是在MyISAM表中，可以和其他字段一起建立联合索引

表的存储方面：InnoDB的存储方式是一个表空间数据文件，一个日志文件，而MyIsam的存储方式是索引文件（.MYI（myindex）），
数据文件(.MYD(mydata))，表存储定义文件(.frm)

`MyISAM 适合于一些需要大量查询的应用，但其对于有大量写操作并不是很好`。甚至你只是需要update一个字段，整个表都会被锁起来，而别的进程，
就算是读进程都无法操作直到读操作完成。另外，MyISAM 对于 SELECT COUNT(*) 这类的计算是超快无比的。

InnoDB 的趋势会是一个非常复杂的存储引擎，对于一些小的应用，它会比 MyISAM 还慢。但是它支持“行锁” ，于是在写操作比较多的时候，会更优秀。
并且，他还支持更多的高级应用，比如：事务。

## 7 范式
◆ 第一范式（1NF）：强调的是 **列的原子性**，即列不能够再分成其他几列。 考虑这样一个表：【联系人】（姓名，性别，电话） 如果在实际场景中，
一个联系人有家庭电话和公司电话，那么这种表结构设计就没有达到 1NF。要符合 1NF 我们只需把列（电话）拆分，
即：【联系人】（姓名，性别，家庭电话，公司电话）。1NF 很好辨别，但是 2NF 和 3NF 就容易搞混淆。

◆ 第二范式（2NF）：首先是 1NF，另外包含两部分内容，一是表必须有一个主键；二是没有包含在主键中的列必须 **完全依赖于主键**，
而不能只依赖于主键的一部分。 考虑一个订单明细表：【OrderDetail】（OrderID，ProductID，UnitPrice，Discount，Quantity，ProductName）。 
因为我们知道在一个订单中可以订购多种产品，所以单单一个 OrderID 是不足以成为主键的，主键应该是（OrderID，ProductID）。
显而易见 Discount（折扣），Quantity（数量）完全依赖（取决）于主键（OderID，ProductID），而 UnitPrice，ProductName 只依赖于 ProductID。
所以 OrderDetail 表不符合 2NF。不符合 2NF 的设计容易产生冗余数据。 可以把【OrderDetail】表拆分为
【OrderDetail】（OrderID，ProductID，Discount，Quantity）和【Product】（ProductID，UnitPrice，ProductName）
来消除原订单表中UnitPrice，ProductName多次重复的情况。

◆ 第三范式（3NF）：首先是 2NF，另外非主键列必须直接依赖于主键， **不能存在传递依赖**。即不能存在：非主键列 A 依赖于非主键列 B，
非主键列 B 依赖于主键的情况。 考虑一个订单表【Order】（OrderID，OrderDate，CustomerID，CustomerName，CustomerAddr，CustomerCity）
主键是（OrderID）。 其中 OrderDate，CustomerID，CustomerName，CustomerAddr，CustomerCity 等非主键列都完全依赖于主键（OrderID），
所以符合 2NF。不过问题是 CustomerName，CustomerAddr，CustomerCity 直接依赖的是 CustomerID（非主键列），而不是直接依赖于主键，
它是通过传递才依赖于主键，所以不符合 3NF。 通过拆分【Order】为【Order】（OrderID，OrderDate，CustomerID）和
【Customer】（CustomerID，CustomerName，CustomerAddr，CustomerCity）从而达到3NF。 

第二范式（2NF）和第三范式（3NF）的概念很容易混淆，
区分它们的关键点在于，
**2NF：非主键列是否完全依赖于主键，还是依赖于主键的一部分；3NF：非主键列是直接依赖于主键，还是直接依赖于非主键列**。
