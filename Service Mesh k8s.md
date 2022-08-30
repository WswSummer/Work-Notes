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

![image](https://user-images.githubusercontent.com/34562805/187164294-0b1a7aaa-4757-4241-9ccd-a08fc7fbb4e0.png)

![image](https://user-images.githubusercontent.com/34562805/187166776-2ee2426d-9ede-4691-9550-8c1004ca0f54.png)

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

CRD

***

container (容器) 的本质是进程，而 pod 是管理这一组进程的资源

pod可以管理多个container

在生产环境中，我们基本上不会直接管理 pod，我们需要 kubernetes 来帮助我们来完成一些自动化操作，例如自动扩容或者自动升级版本，deployment，来帮助我们管理 pod

kubernetes提供了一种名叫 Service 的资源帮助解决这些问题，它为 pod 提供一个稳定的 Endpoint。Servie 位于 pod 的前面，负责接收请求并将它们传递给它后面的所有pod。一旦服务中的 Pod 集合发生更改，Endpoints 就会被更新，请求的重定向自然也会导向最新的 pod。

- kubeadm：用来初始化集群的指令
- kubelet：在集群中的每个节点上用来启动 Pod 和容器等
- kubectl：用来与集群通信的命令行工具

让 DevOps 这一角色变得更加清晰，每一个软件工程师都可以通过 Kubernetes 来定义服务之间的拓扑关系、线上的节点个数、资源使用量并且能够快速实现水平扩容、蓝绿部署等在过去复杂的运维操作。

- 主节点服务 - Master 架构

作为管理集群状态的 Master 节点，它主要负责接收客户端的请求，安排容器的执行并且运行控制循环，将集群的状态向目标状态进行迁移。Master 节点内部由下面三个组件构成：

API Server: 负责处理来自用户的请求，其主要作用就是对外提供 RESTful 的接口，包括用于查看集群状态的读请求以及改变集群状态的写请求，也是唯一一个与 etcd 集群通信的组件。

etcd: 是兼具一致性和高可用性的键值数据库，可以作为保存 Kubernetes 所有集群数据的后台数据库。

Scheduler: 主节点上的组件，该组件监视那些新创建的未指定运行节点的 Pod，并选择节点让 Pod 在上面运行。调度决策考虑的因素包括单个 Pod 和 Pod 集合的资源需求、硬件/软件/策略约束、亲和性和反亲和性规范、数据位置、工作负载间的干扰和最后时限。

controller-manager: 在主节点上运行控制器的组件，从逻辑上讲，每个控制器都是一个单独的进程，但是为了降低复杂性，它们都被编译到同一个可执行文件，并在一个进程中运行。这些控制器包括：节点控制器(负责在节点出现故障时进行通知和响应)、副本控制器(负责为系统中的每个副本控制器对象维护正确数量的 Pod)、端点控制器(填充端点 Endpoints 对象，即加入 Service 与 Pod))、服务帐户和令牌控制器(为新的命名空间创建默认帐户和 API 访问令牌)。

![image](https://user-images.githubusercontent.com/34562805/187166469-6b19198d-34a9-4941-bfad-6018edd48d0e.png)

- 工作节点 - Node 架构

其他的 Worker 节点实现就相对比较简单了，它主要由 kubelet 和 kube-proxy 两部分组成。

kubelet: 是工作节点执行操作的 agent，负责具体的容器生命周期管理，根据从数据库中获取的信息来管理容器，并上报 pod 运行状态等。

kube-proxy: 是一个简单的网络访问代理，同时也是一个 Load Balancer。它负责将访问到某个服务的请求具体分配给工作节点上同一类标签的 Pod。kube-proxy 实质就是通过操作防火墙规则(iptables或者ipvs)来实现 Pod 的映射。

Container Runtime: 容器运行环境是负责运行容器的软件，Kubernetes 支持多个容器运行环境: Docker、 containerd、cri-o、 rktlet 以及任何实现 Kubernetes CRI(容器运行环境接口)。

![image](https://user-images.githubusercontent.com/34562805/187166553-363f0742-ac9f-487a-9517-15dd9088651e.png)

主要核心组件：

- apiserver
  - 所有服务访问的唯一入口，提供认证、授权、访问控制、API 注册和发现等机制
- controller manager
  - 负责维护集群的状态，比如副本期望数量、故障检测、自动扩展、滚动更新等
- scheduler
  - 负责资源的调度，按照预定的调度策略将 Pod 调度到相应的机器上
- etcd
  - 键值对数据库，保存了整个集群的状态
- kubelet
  - 负责维护容器的生命周期，同时也负责 Volume 和网络的管理
- kube-proxy
  - 负责为 Service 提供 cluster 内部的服务发现和负载均衡
- Container runtime
  - 负责镜像管理以及 Pod 和容器的真正运行

除了核心组件，还有一些推荐的插件：

- CoreDNS
  - 可以为集群中的 SVC 创建一个域名 IP 的对应关系解析的 DNS 服务
- Dashboard
  - 给 K8s 集群提供了一个 B/S 架构的访问入口
- Ingress Controller
  - 官方只能够实现四层的网络代理，而 Ingress 可以实现七层的代理
- Prometheus
  - 给 K8s 集群提供资源监控的能力
- Federation
  - 提供一个可以跨集群中心多 K8s 的统一管理功能，提供跨可用区的集群

Pod、Service、Volume 和 Namespace 是 Kubernetes 集群中四大基本对象，它们能够表示系统中部署的应用、工作负载、网络和磁盘资源，共同定义了集群的状态。Kubernetes 中很多其他的资源其实只对这些基本的对象进行了组合。

- Pod -> 集群中的基本单元
- Service -> 解决如何访问 Pod 里面服务的问题
- Volume -> 集群中的存储卷
- Namespace -> 命名空间为集群提供虚拟的隔离作用

K8S 中所有的内容都抽象为了资源，资源实例化之后就叫做对象。

在 Kubernetes 系统中，Kubernetes对象是持久化的实体，Kubernetes使用这些实体去表示整个集群的状态。特别地，它们描述了如下信息：

- 哪些容器化应用在运行，以及在哪个 Node 上
- 可以被应用使用的资源
- 关于应用运行时表现的策略，比如重启策略、升级策略，以及容错策略

Kubernetes对象是 “目标性记录” —— 一旦创建对象，Kubernetes系统将持续工作以确保对象存在。通过创建对象，本质上是在告知 Kubernetes 系统，所需要的集群工作负载看起来是什么样子的，这就是 Kubernetes 集群的期望状态。

Kubernetes资源配额控制器确保了指定的资源对象始终不会超过配置的资源，能够有效的降低整个系统宕机的机率，增强系统的鲁棒性，对整个集群的稳定性有非常重要的作用。

kubectl 是 Kubernetes 自带的客户端，可以用它来直接操作Kubernetes集群，kubectl 最主要的工作就是执行 Kubernetes API 的 HTTP 请求。

k9s是基于终端的资源仪表板。它只有一个命令行界面。无论在Kubernetes仪表板Web UI上做什么，都可以在终端使用K9s仪表板工具进行相同的操作。k9s持续关注Kubernetes集群，并提供命令以使用集群上定义的资源。
