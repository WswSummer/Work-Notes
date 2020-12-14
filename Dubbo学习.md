### Dubbo学习笔记

#### 1. RPC 远程过程调用 Remote Procedure Call

![image](https://user-images.githubusercontent.com/34562805/102066014-3e565980-3e34-11eb-8ce1-d22e9e49277c.png)

 	远程过程调用是一个[分布式计算](https://zh.wikipedia.org/wiki/分布式计算)的[客户端-服务器](https://zh.wikipedia.org/wiki/客户端-服务器)（Client/Server）的例子，它简单而又广受欢迎。远程过程调用总是由[客户端](https://zh.wikipedia.org/wiki/客户端)对[服务器](https://zh.wikipedia.org/wiki/服务器)发出一个执行若干过程请求，并用客户端提供的参数。执行结果将返回给客户端。

![image](https://user-images.githubusercontent.com/34562805/102066048-50d09300-3e34-11eb-8196-0be58b3110f6.png)

#### 2. Dubbo

![image](https://user-images.githubusercontent.com/34562805/102066119-66de5380-3e34-11eb-9476-df160990b44c.png)

Apache Dubbo是一款高性能、轻量级的开源Java RPC框架，它提供了三大核心能力：面向接口的远程方法调用，智能容错和负载均衡，以及服务自动注册和发现。

#### 3. 架构

![image](https://user-images.githubusercontent.com/34562805/102066183-7c537d80-3e34-11eb-9d19-22bd46150f5f.png)

#### 4. Zookeeper注册中心

