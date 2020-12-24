## Service Mesh

服务网格

第一代Service Mesh，它将分布式服务的通信抽象为单独一层，在这一层中实现负载均衡、服务发现、认证授权、监控追踪、流量控制等分布式系统所需要的功能，作为一个和服务对等的代理服务，和服务部署在一起，接管服务的流量，通过代理之间的通信间接完成服务之间的通信请求。

![img](https://philcalcado.com/img/service-mesh/6-a.png)

![img](https://philcalcado.com/img/service-mesh/mesh1.png)

![img](https://philcalcado.com/img/service-mesh/mesh2.png)

它看起来确实就像是一个由若干服务代理所组成的错综复杂的网格。

第一代Service Mesh由一系列独立运行的单机代理服务构成，为了提供统一的上层运维入口，演化出了集中式的控制面板，所有的单机代理组件通过和控制面板交互进行网络拓扑策略的更新和单机数据的汇报，第二代Service Mesh。

![img](https://philcalcado.com/img/service-mesh/6-b.png)

![img](https://philcalcado.com/img/service-mesh/mesh3.png)

>服务网格是一个**基础设施层**，用于处理服务间通信。云原生应用有着复杂的服务拓扑，服务网格保证**请求在这些拓扑中可靠地穿梭**。在实际应用当中，服务网格通常是由一系列轻量级的**网络代理**组成的，它们与应用程序部署在一起，但**对应用程序透明**。

Service Mesh具有如下优点：

- 屏蔽分布式系统通信的复杂性(负载均衡、服务发现、认证授权、监控追踪、流量控制等等)，服务只用关注业务逻辑；
- 真正的语言无关，服务可以用任何语言编写，只需和Service Mesh通信即可；
- 对应用透明，Service Mesh组件可以单独升级；

Service Mesh目前也面临一些挑战：

- Service Mesh组件以代理模式计算并转发请求，一定程度上会降低通信系统性能，并增加系统资源开销；
- Service Mesh组件接管了网络流量，因此服务的整体稳定性依赖于Service Mesh，同时额外引入的大量Service Mesh服务实例的运维和管理也是一个挑战；





TIPS:

https://philcalcado.com/2017/08/03/pattern_service_mesh.html

https://buoyant.io/2020/10/12/what-is-a-service-mesh/

https://jimmysong.io/blog/what-is-a-service-mesh/

https://zhuanlan.zhihu.com/p/61901608



