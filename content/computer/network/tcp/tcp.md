<https://blog.csdn.net/fuhanghang/article/details/114528098>

在tcp/ip协议中，tcp通过三次握手建立起一个tcp的链接，大致如下：

第一次握手：客户端尝试连接服务器，向服务器发送syn包，syn=j，客户端进入SYN_SEND状态等待服务器确认。

第二次握手：服务器接收客户端syn包并确认（ack=j+1），同时向客户端发送一个SYN包（syn=k），即SYN+ACK包，此时服务器进入SYN_RECV状态。

第三次握手：客户端收到服务器的SYN+ACK包，向服务器发送确认包ACK(ack=k+1），此包发送完毕，客户端和服务器进入ESTABLISHED状态，完成三次握手。

三次握手如下图：

![2024-04-08-13-23-32.png](assets/2024-04-08-13-23-32.png)

根据tcp的三次握手，socket也定义了三次握手，也许是参考tcp的三次握手，一些计算机大神们画出了socket的三次握手的模型图

模型图如下：