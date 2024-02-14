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




