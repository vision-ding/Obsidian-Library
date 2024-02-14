sds常用方法：
sdsempty()
sdscat()
sdstrim()  -- 删除sds中的指定字符
sdssplitargs    -- todo

###### 监听socket:
1.设置属性
	reuseAddress --一个端口可以监听多个网卡
	nonblock

2.将fd加到epoll中，等待可读事件，回调函数是acceptTcpHandler

###### beforeSleep
	unblocked fd： 在read的时候，不能阻塞，即加入了epoll，待有数据读的时候再read
	 blocked fd: 没有加入epoll

###### client_fd ：
	- 映射为一个redisClient对象
	- tcp属性设置nonblock, tcp_no_delay
	 - epoll注册为read，回调函数是readQueryFromClient

###### 解析client的请求命令：
	执行函数是：processMultibulkBuffer;
	redisClient的缩写是c;
	读出的数据存在c->querybuf中;
	解析的字段存放在c->argv中;
	例如："*3\r\n$5\r\nhmget\r\n$4\r\nhfoo\r\n$6\r\nfield1\r\n"
	解析结果是: 
	argv[0] = "hmget", 
	argv[1] = "hfoo", 
	argv[2] = "field1", 

###### 执行命令
	根据argv[0]找到对应的redisCommand；
	调用call函数；
	执行redisCommand的proc；
	数据都存在不同的数据结构里，proc实际上是处理对应的数据结构；
	
###### 将命令加到multi_state中

	根据argv[0]找到对应的redisCommand；
	由argv、argc和redisCommand构成一个multiCmd；
	将multiCmd加到c->mstate.commands数组里；


