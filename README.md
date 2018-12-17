Redis问题集合

Windows下解决redis连接服务器报错：
[7320] 18 Nov 16:03:21.522 # Creating Server TCP listening socket 127.0.0.1:6379: bind: No error

在cmd里按顺序依次输入以下命令：
redis-cli.exe
shutdown
exit
进入redis根目录下输入redis-server.exe redis.windows.conf


redis连接池

为什么使用连接池:假设Redis服务器与客户端分处在异地，虽然基于内存的Redis数据库有着超高的性能，但是底层的网络通信却占用了一次数据请求的大量时间，因为每次数据交互都需要先建立连接，假设一次数据交互总共用时30ms，超高性能的Redis数据库处理数据所花的时间可能不到1ms，也即是说前期的连接占用了29ms，连接池则可以实现在客户端建立多个链接并且不释放，当需要使用连接的时候通过一定的算法获取已经建立的连接，使用完了以后则还给连接池，这就免去了数据库连接所占用的时间。

import redis    # 导入redis模块，通过python操作redis 也可以直接在redis主机的服务端操作缓存数据库    
pool = redis.ConnectionPool(host='localhost', port=6379, decode_responses=True)   # host是redis主机，需要redis服务端和客户端都起着 redis默认端口是6379
r = redis.Redis(connection_pool=pool)
r.set('gender', 'male')     # key是"gender" value是"male" 将键值对存入redis缓存
print(r.get('gender'))      # gender 取出键male对应的值
   



 

 

 

 

 
