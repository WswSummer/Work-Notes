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



# K8S

![1642572038655_35B19CC6-5017-449e-A3C7-2F0305BDA1B8](https://user-images.githubusercontent.com/34562805/150077306-bee88399-e9ed-4c88-a1f6-f83b5746658b.png)

![image](https://user-images.githubusercontent.com/34562805/150077366-c01ad82d-aada-41cb-8b3a-8c78fb42c98a.png)

![image](https://user-images.githubusercontent.com/34562805/150077435-f08a6b53-af22-4ea9-bcea-60ea0edd06d0.png)

![image](https://user-images.githubusercontent.com/34562805/150078368-565af5c6-d2ac-4eda-aeed-8cfb2d59ca85.png)

![image](https://user-images.githubusercontent.com/34562805/150087315-f249deea-1fa7-4a95-98b2-128f4a5fa667.png)

![image](https://user-images.githubusercontent.com/34562805/150263894-5aeba6cd-0a05-48fe-b0e7-9331d94350ce.png)

​	![image](https://user-images.githubusercontent.com/34562805/150265094-2204e2db-9c83-4dfe-9f77-b4233db0b343.png)

![image](https://user-images.githubusercontent.com/34562805/150265610-37828a73-e3b0-4a70-b8e5-155cd543958b.png)

![image](https://user-images.githubusercontent.com/34562805/150283186-6cd88ebb-c6fc-45d5-89b2-71e43907ef1b.png)

![image](https://user-images.githubusercontent.com/34562805/150289463-cff708d9-5a8d-48f2-b5f6-bb05f310a795.png)

![image](https://user-images.githubusercontent.com/34562805/150290037-0f1797cb-fbcf-4940-bca2-8fa50be381f7.png)



# k8s学习实践

k8s minikube

![1661741932171_760F5928-BAB0-4e1b-A5DD-B6306D16FD78](https://user-images.githubusercontent.com/34562805/187133831-ee61ad24-cd04-40b1-972c-bac09d4c7f00.png)

![1661742272458_71570B04-B747-49fa-A788-F185F284C351](https://user-images.githubusercontent.com/34562805/187133867-f72cdd25-6350-49c5-8d31-2d26cda714ae.png)

![1661751179104_98DC2AC7-35B3-415b-BE82-52FD4F29595A](https://user-images.githubusercontent.com/34562805/187133928-a3d9caab-eb57-4bd4-a24d-e72eac62f780.png)

![1661751371411_6B577327-CA29-4c76-98CE-59ED8C56CB3A](https://user-images.githubusercontent.com/34562805/187134011-10af8c0d-2c03-48a8-a132-9872f467a165.png)

![1661751466424_71D09DA3-1E80-4604-929D-471079C4AC47](https://user-images.githubusercontent.com/34562805/187134087-8c9e422a-93b2-4fda-b57f-dd241106d6b7.png)

![1661751616278_12425AB5-E38B-471b-8DDE-1C19FAAFEA75](https://user-images.githubusercontent.com/34562805/187134160-57d09450-9c51-4d12-98b3-f02470b82f94.png)

***

application

container 

pod

deployment

service

ingress

namespace

configmap

secret

job

cornjob

Rolling Update(滚动更新)

存活探针 (livenessProb)

就绪探针 (readiness)

helm

dashboard

***

container (容器) 的本质是进程，而 pod 是管理这一组进程的资源

pod可以管理多个container

在生产环境中，我们基本上不会直接管理 pod，我们需要 kubernetes 来帮助我们来完成一些自动化操作，例如自动扩容或者自动升级版本，deployment，来帮助我们管理 pod

kubernetes提供了一种名叫 Service 的资源帮助解决这些问题，它为 pod 提供一个稳定的 Endpoint。Servie 位于 pod 的前面，负责接收请求并将它们传递给它后面的所有pod。一旦服务中的 Pod 集合发生更改，Endpoints 就会被更新，请求的重定向自然也会导向最新的 pod。
