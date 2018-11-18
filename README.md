Redis问题集合

Windows下解决redis连接服务器报错：
[7320] 18 Nov 16:03:21.522 # Creating Server TCP listening socket 127.0.0.1:6379: bind: No error

在cmd里按顺序依次输入以下命令：
redis-cli.exe
shutdown
exit
进入redis根目录下输入redis-server.exe redis.windows.conf
