# Kubernetes

## 基本架构

kubernetes集群是由一个master来负责对各个节点进行管理的，其中被管理的各个node节点可能会是一些虚拟机或者小型机器。在每个node节点上都会运作有各种各样的pod，而pod通常会是各种各样的docker容器。

master => nodes => pods(docker containers)

​											master

​												|

​										/				\

​								node1			node2

​							  |	|	|		 |	|	|

​							p1   p2  p3      p1  p2  p3

### Master模块

kubectl主要的作用是对kubernetes发送命令，通过使用apiserver来调用kubernets对内部的各个node节点进行部署和控制。

**ApiServer**的主要工作就是对各个node节点进行增删改查。etcd主要是存储一些节点的数据信息，并且每次kubectl发送过来的指令都会被apiserver先存储到etcd中。

**Controller manager** 的作用主要是监控各个容器的情况。Controller manager会通过监听Api Server里面的提供的一个List Watch接口来监控各个集群资源的数据，从而调整资源的状态。在成百上千的微服务系统中，假设说某个节点出现了crash，那么这个时候Controller manager就会自动地进行节点的修复，故障转移，这样就能很好地减轻了运维人员的压力。

**Scheduler** 调度容器部署到指定的机器上，决定每个pod要放置再哪个node上，并且命令kubelet进行容器的部署



### Node模块

Node是k8s的工作节点，Node 一般是一个虚拟机或者物理机，每个 node 上都运行三个服务，分别是**Container runtime，kubelet，kube-proxy**三类。

kubelet 主要是负责接收master的命令，并且执行，同时还要维护容器的生命周期。
kube-proxy 主要的作用就是负责负载均衡，处理流量的转发问题。

Container runtime 是负责镜像管理以及pod和容器的真正运行。





## Principles

### kubernetes 对象

* 对象spec: 是必需的， 描述了对象的 *期望状态（Desired State）* —— 希望对象所具有的特征

* 对象status: *实际状态（Actual State）* ，它是由 Kubernetes 系统提供和更新的

#### 描述对象

**大多数情况下，需要在 .yaml 文件中为 `kubectl` 提供这些信息**。 `kubectl` 在发起 API 请求时，将这些信息转换成 JSON 格式。

Example yaml:

```yaml
apiVersion: apps/v1 # for versions before 1.9.0 use apps/v1beta2
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  selector:
    matchLabels:
      app: nginx
  replicas: 2 # tells deployment to run 2 pods matching the template
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```





## Kubectl commands

**Create kubernetes cluster**

```shell
minikube start
```

**View Cluester details**:

```shell
kubectl cluster-info
```

**View the nodes in the cluster**

```shell
kubectl get nodes
```

**Deploy app**

```
kubectl create deployment [deployment name] --image=[full repository url for images hosted outside Docker hub]
```

