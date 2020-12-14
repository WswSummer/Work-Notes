### Dubbo学习笔记

#### 1. RPC 远程过程调用 Remote Procedure Call

![image-20200710090643447](C:\Users\wangsongwen\AppData\Roaming\Typora\typora-user-images\image-20200710090643447.png)

 	远程过程调用是一个[分布式计算](https://zh.wikipedia.org/wiki/分布式计算)的[客户端-服务器](https://zh.wikipedia.org/wiki/客户端-服务器)（Client/Server）的例子，它简单而又广受欢迎。远程过程调用总是由[客户端](https://zh.wikipedia.org/wiki/客户端)对[服务器](https://zh.wikipedia.org/wiki/服务器)发出一个执行若干过程请求，并用客户端提供的参数。执行结果将返回给客户端。

![image-20200710091005778](C:\Users\wangsongwen\AppData\Roaming\Typora\typora-user-images\image-20200710091005778.png)

#### 2. Dubbo

![image](https://dubbo.apache.org/docs/zh-cn/user/sources/images/dubbo-architecture-roadmap.jpg)

![image-20200710091253465](C:\Users\wangsongwen\AppData\Roaming\Typora\typora-user-images\image-20200710091253465.png)

![image-20200710091305771](C:\Users\wangsongwen\AppData\Roaming\Typora\typora-user-images\image-20200710091305771.png)

Apache Dubbo是一款高性能、轻量级的开源Java RPC框架，它提供了三大核心能力：面向接口的远程方法调用，智能容错和负载均衡，以及服务自动注册和发现。

#### 3. 架构

![dubbo-architucture](https://dubbo.apache.org/docs/zh-cn/user/sources/images/dubbo-architecture.jpg)

![image-20200710094235493](C:\Users\wangsongwen\AppData\Roaming\Typora\typora-user-images\image-20200710094235493.png)

![image-20200710094359522](C:\Users\wangsongwen\AppData\Roaming\Typora\typora-user-images\image-20200710094359522.png)

#### 4. Zookeeper注册中心

