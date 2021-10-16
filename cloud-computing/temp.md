# 并行计算 分布式计算（技术）
`并行计算` ：hpc server， 使用一个强大的机器或者infiniband万兆网络连接，分派给系统中的多个运算单元；共享memory（可以直接访问所有内存）
`分布式计算` ：cluster上运行，百兆网络等，将计算任务分派给多个机器，再merge；分布式memory，message passing
　
快速🔜的分布式　
map/reduce
Hadoop 
spark

# 网格计算，云计算系统

`网格计算`  `教育网格` （信息中心）计算队列：将空闲的服务器通过教育网共享
服务器一般不断电：软件configuration，路径，环境变量；逻辑上一起，初期没有虚拟化
需要提供自己的计算资源，限制成员

`云计算` anyone, anytime, anywhere
共享软硬件 shared licenses 按需易拓展 autoscaling
计算模式
数据量大增
 
jp摩根

公司：灵活性不足
云️服务：Amazon，黑五 增加服务器，平时浪费

# 基本思想 universal

基本能力都可通过网络获得
云应对用户硬件友好
不需要用户安装复杂软件，数据保证安全（备份）

# 安全：云的安全，第三方

threat model：假设平台是安全的



密码学

`同态加密` ：云上加密
对加密数据直接进行计算
limitation：花销很大，算法限制

supercomputing
　　Keynote： DreamWorks
　　雪花❄️动画（图形学）电影动画渲染 $\rightarrow$  渲染时间久 由高性能完成精细的场景渲染
　　
> 大数据是云计算的motivation
隐私

# 大数据？

大数据的特征：

- 价值密度低（需要挖掘数据，数据清洗：重复、无用、噪声数据、缺失值处理）
- 数据量大（volume） 
　　- 每天产生大量数据，PB级别
- 产生速度快，数据处理需要高效率
　　- `streaming processing` 
　　- 丢包：如果处理速率不够快，会丢包
　　- zoom 多方会议，带宽受限，数据传输调度？$\rightarrow$ 用户体验↑
- 多样性 variety
　　- 结构性/非结构性/半结构性数据，语音
　　- 搜索喜马拉雅：只能搜索`metadata` （文件名/小说名/属性），无法根据内容讲某个细节搜索$\rightarrow$ 非结构化数据索引
　　- 复杂性 分析和处理的难度大
　　

$$G=f(x), f云计算, x大数据$$

各种云服务：请求使用专有服务器等等

云：不对用户有要求，数据可靠不会被泄露，

三备份，仍旧可能会丢失

salesforce，VMware虚拟化技术，MapReduce模型

搜索引擎：输入keyword，爬虫机器人🤖（cache），**分布式**索引查询$\rightarrow$ 汇总$\rightarrow$ **分布式**排序

分布式化：
MapReduce框架 map$\rightarrow$ shuffle（交换）$\rightarrow$ reduce；写到memory：spark；数据恢复？
S3 `Simple Storage Service`  
EC2 
>Amazon Elastic Compute Cloud（Amazon EC2 云服务器）是一种 Web 云服务，能在云中提供安全且可调整大小的计算能力. 该服务旨在让开发人员能够更轻松地进行 Web 规模的云计算. Amazon EC2 云服务器的 Web 云服务接口非常简单，您可以最小的阻力轻松获取容量，随之配置容量. 使用该服务，您将能完全控制您的计算资源，并能在亚马逊成熟且行之有效的计算环境中运行. 
Amazon EC2 云服务器提供最广泛、最深入的计算平台，可选择处理器、存储、联网、操作系统和购买模式. 我们提供最快的云处理器，是唯一的 400 Gbps 以太网网络云. 我们拥有最强大的针对机器学习培训和图形工作负载的 GPU 云服务器实例，以及云中每次推理成本最低的云服务器实例. 与任何其它云相比，AWS 均运行更多的 SAP、HPC、机器学习和 Windows 工作负载. 单击此处了解 Amazon EC2 云服务器的最新功能. 

机器，使用时长（小时$\rightarrow$ 分钟$\rightarrow$ 秒）等数据模型变化

serverless 无服务器
> 开发者再也不用过多考虑服务器的问题，计算资源作为服务而不是服务器的概念出现. Serverless是一种构建和管理基于微服务架构的完整流程，

> AWS Lambda はサーバーレスコンピューティングサービスで、サーバーのプロビジョニングや管理、ワークロード対応のクラスタースケーリングロジックの作成、イベント統合の維持、ランタイムの管理を行わずにコードを実行できます. Lambda を使用すれば、実質どのようなタイプのアプリケーションやバックエンドサービスでも管理を必要とせずに実行できます. コードを ZIP ファイルまたはコンテナイメージとしてアップロードするだけで、Lambda はあらゆる規模のトラフィックに対して、自動的かつ正確にコンピューティング実行能力を割り当て、受信リクエストやイベントに基づいてコードを実行します. コードは、200 種類を超える AWS のサービスおよび SaaS アプリケーションから自動的にトリガーするよう設定することも、ウェブやモバイルアプリケーションから直接呼び出すよう設定することもできます. Lambda 関数をお気に入りの言語 (Node.js、Python、Go、Java など) で記述し、サーバーレスツールと AWS SAM や Docker CLI などのコンテナツールの両方を使用して、関数をビルド、テスト、デプロイできます. 

> 云函数
简单易用
用户只需编写最重要的“核心代码”，不再需要关心周边组件，极大地降低了服务架构搭建的复杂性. 无需任何手动配置，云函数即可根据请求量自动横向扩缩. 不管您的应用每天的请求数处于波峰还是波谷，云函数均可自动安排合理的计算资源满足业务需求. 
高效
云函数不要求特定框架，开发者可专注于核心代码的开发. 单个模块的开发无需了解代码细节. 您可以使用云函数编写一些目的单一、逻辑独立的业务模块. 每个函数都是单独运行、单独部署、单独伸缩的，用户上传代码后即可自动部署，提升了独立开发和迭代的速度. 
稳定可靠
如果某个可用区因灾害或电力故障等导致瘫痪，云函数会自动地选择其他可用区的基础设施来运行，免除单可用区运行的故障风险. 由事件触发的工作负载可以使用云函数来实现，利用不同云服务满足不同的业务场景和业务需求，使得您的服务架构更加健壮. 
简化管理
用户不再需要对 OS 入侵、登录风险、文件系统安全、网络安全和端口监听做复杂的配置和管理，一切交由平台处理，平台通过定制化的容器保证每个用户的隔离性. 用户无需复杂的配置文件即可一键部署和测试云函数. 
降低开销
云函数在未执行时不产生任何费用，所以对一些无需常驻的业务进程来说，开销将大幅降低. 云函数执行时按请求数和计算资源的运行时间收费，价格优势明显，对初创期的开发者十分友好. 

容器 （轻量级虚拟机），没有OS层$\rightarrow$ 层很薄，可以快速部署 iaas
docker 
Google cloud（TensorFlow←data flow服务），azure，IBM cloud
⭐做系统级的工作难以被取代：工程师$\rightarrow$ 架构师*
中层压力大

## 云：网络的发展

物联网 IoT 万物互联
传感器数据量$\rightarrow$ 网络传输带宽有限
传感器电量小 power consumption

边缘计算$\rightarrow$ 减少带宽，数据预处理$\rightarrow$ 减少了耗电量

## HoloLens

ar增强现实 
虚拟地图导航
终端设备，定位？（室内，三维建模，构建场景地图）

## 提供不同的定位
amazom-便宜，提供infrastructure
Google - platform，自带系统
azure -license 软件，程序托管

阿里云（淘宝所提出的需求） 腾讯云（） 华为云（政府云，云桌面）

gfs BigTable Google APP engine

P（platform）aaS， S（software）aaS， i（infrastructure）aas

技术$\rightarrow$ 产品$\rightarrow$ *落地应用*
对于用户来说最少的管理，最少地与供应商互动

## 云服务特点　
　按需自助 无处不在 弹性
　　资源池（公有云）服务可度量（以分钟/GB/...计算）
　　
## 服务模式

iaas PaaS SaaS

iaas 将硬件设备等基础设施封装成服务，需手动设置管理机器通信等

kvm，ceph（文件管理，OpenStack（私有云）等

GitHub gitlab kubernates docker
PaaS 提供用户应用程序**运行环境**
SaaS 软件

Verizon， cloudblue ，cloud scripting
SaaS 直接提供软件

## 部署模式

公有云 私有云 混合云 社区云

| 种类 | 缺点 | 优点 |
|:----:|:----:|:----:|
|   公有云   |   对外部用户，安全性较低，功能拓展较低，数据风险较高   |  弹性扩容强    |
|  私有云    |   （与公有云相反）   |   扩容性差（私有云多用户之间服务隔离性会差一些$\rightarrow$ 云性能不稳定性，用户多时共享性能会差）   |
|   混合云（用户少时私有云，其他公有云）   |    管理成本很高，任务迁移、数据移动以及用户体验稳定问题  |      |

## 影响

中型公司自建数据中心，管理费用太高
️上成本降低，数据丢失风险下降
量贩式KTV 超市 量多单价下降

电费 不同地区电费差异，地震️，主要用于冷却费用
高峰电费，低峰电费，全球调度

云南贵州内蒙古

## 云服务商大数据中心

华为，阿里（第一梯队）

百度，短视频  实时推荐系统：快手/抖音，字节跳动

Oregon州免税 1.8GW
>  我们的冷却塔
>  俄勒冈州达尔斯数据中心冷却塔顶端升腾的蒸汽. 缕缕蒸汽形成薄雾，安静地漂浮在黄昏之中. 

## 云的好处

云使得使用计算服务价格下降，资源利用率上升，节约成本

# Amazon开启虚拟机

选择ami（guest OS image）：支持的virtualization type (paravirtual 半虚拟化$\rightarrow$ 性能不一致)

Windows不支持HVM

> HVM (known as Hardware Virtual Machine) is the type of instance that mimics bare-metal server setup which provides better hardware isolation. With this instance type, the OS can run directly on top of the Virtual Machine without additional configuration making it to look like it is running on a real physical server. For more information about this instance type and the other one that is most commonly used, you may refer to the resource link below.

base镜像
full container
SQL……

研究方向：云计算虚拟化，如live migration（实时虚拟机迁移：无感迁移？）

# 服务器虚拟化（服务器硬件资源的虚拟化）

## CPU虚拟化

一个core$\rightarrow$ 一个虚拟机

if 单核？
应该也是支持
一个虚拟机：可以视为一个application，模拟多CPU并发运行$\rightarrow$ 允许一个平台同时运行多个虚拟机操作系统


`concurrent 并行` ：同时进行
`（分时）并发` 2个任务同时发生，看似同时运行，但未必同时进行

图：虚拟机调度

virtual CPUs （与硬件无关）
monitor
core （locigal CPU，逻辑处理器）

超线程：一个核变2个核（某些硬件存在2份，如registers，加快运算单元运算，一个线程block时执行另一线程）

### 虚拟CPU性能取决于2级调度的效率
guest application$\rightarrow$ 虚拟CPU调度
虚拟CPU发出指令$\rightarrow$ vmm调度$\rightarrow$ 物理核
物理核：任务队列

### *调度*：不同任务之间、不同io/网络等

MapReduce$\rightarrow$ Hadoop /，spark *spark的调度*

### CPU全虚拟化

ring：特权等级

ring 0 monitor
ring 1 guest OS
ring 3 application


`ring compression` ，`二进制代码翻译` （假如指令不支持虚拟化时）

guest OS下发指令$\rightarrow$ monitor捕捉、模拟、转换

此等级机制避免直接下达命令到CPU

### CPU半虚拟化

修改过guest OS支持hypercall直接调用CPU指令

### CPU硬件辅助（全）虚拟化

Intel VT-X，

区分root模式
monitor运行在root模式运行，虚拟机支持非root的ring0，硬件区分来自guest OS指令和host OS指令，核心指令可以直接发送给CPU而无需vmm捕捉

## 内存虚拟化

真实物理内存$\rightarrow$ 其他存储，️超过物理内存时performance下降

$\rightarrow$ 虚拟地址空间，分配虚拟地址

$虚拟地址↔^{translation}实际地址$

每个进程看到独立的地址内存空间
假如超过内存空间，需等待其他程序释放

虚拟地址↔real memory address（虚拟机所看到的虚拟地址）↔physical（物理机看到的虚拟地址）

使用page table进行翻译

产生：源于vmm与guest OS所看到的内存空间不一致

### 全虚拟化

 page table：虚拟地址$\rightarrow$ 物理地址；有相关技术加速检索

shadow 页表（客户机页表）：维护进程的虚拟地址$\rightarrow$ guest os地址（guest physical address，如虚拟机申请的）
p2m页表/哈希函数 GPA地址$\rightarrow$ 机器地址……填充到在硬件上起作用的影子页表

### 半虚拟化

guest os直接向vmm注册

vmm跨层维护页表 virtual address直接翻译成physical address

### 内存硬件辅助虚拟化

ept 拓展页表 vmm将ept设置到CPU中，加速GPA$\rightarrow$ ma过程，再加速va$\rightarrow$ ma过程

## 常见的虚拟化产品

Hyperv
docker
xen
kvm
VMware

# 容器，docker，kubernates

**轻量级**的容器，可以只含有一个APP及其依赖

⭐管理容器？k8s：管理+调度

`镜像` 可执行的软件包
`容器` 将应用打包到一个可移植的**轻量级**镜像

base image包含OS等，APP image在base image之上

$\rightarrow$ serverless依赖于轻量级容器技术，执行毫秒级高性能要求任务，重量级容器启动慢，轻量级只包含minimal set，deploy快

docker是容器引擎的解决方案 封装Cgroup、namespace等，提供了接口和api，支持生成、发布、部署等

将程序和dependency包含在一个image中，使得对于全局配置的依赖解耦（应用和运行环境打包）

docker：

秒级的交付和部署，
eg 搜索服务
不定时的服务需求，需要尽快返回结果$\rightarrow$ 尽快部署

集群：基础运行收费（：只有运行时才能autoscale）+用户request多收费$\rightarrow$ 适用于中小企业
10tasks：查询的数据库、代码等需先存入️中
当有新请求时，️自动部署新容器

由k8s管理，效率高

有弹性

live migration成本低

### docker结果

client
server
docker host
daemon
base image←image registry选择基础组件
my containers


client/server架构 deamon（server）接受请求，创建、分发容器
部署到server上

动态迁移

# 虚拟机，虚拟化技术

virtual box
VMware

封装过的软件

| HEADER | HEADER | HEADER |
|:----:|:----:|:----:|
|   虚拟机   |   将一台物理计算机虚拟化为多个逻辑计算机，之间相互隔离，应用程序在相互独立空间中运行   |      |
|      |      |      |
|      |      |      |

层级结构：通过每层之间接口实现计算机系统
应用程序
操作系统（管理调度底层硬件）
硬件 x86


（虚拟机系统，与实体机的结构类似，虚拟化出一些硬件）
假如一个核分给2个虚拟机，则平台，OS需要分时切换
虚拟化平台 virtualization layer
——
（操作系统）
硬件

️网络的虚拟化隔离难以实现，因此虚拟化机网络性能不稳定
虚拟机的网络转发到物理机的网络中

Application
Guest os
Virtual machine
Hypervisor (virtual machine monitor)
Host os
host machine(hardware)

特点：分区（逻辑上的分区） 隔离（同一主机上的虚拟机之间相互隔离） 封装（整个系统保存在文件中）

虚拟机上读取数据？ 硬件磁盘挂载在硬件上 guest OS转换请求到hypervisor$\rightarrow$ OS$\rightarrow$ 硬件 以隔离不同虚拟机，overhead大

## 划分

软件辅助的虚拟化技术 （软件产生异常$\rightarrow$ 宿主机陷入异常$\rightarrow$ 触发虚拟化）hyperv

> Hyper-V specifically provides hardware virtualization. That means each virtual machine runs on virtual hardware. Hyper-V lets you create virtual hard drives, virtual switches, and a number of other virtual devices all of which can be added to virtual machines

硬件辅助的虚拟化技术 硬件支持的直接虚拟化 AMD-V

全虚拟化 完全隔离，由hypervisor层转换 VMware workstation：速度减慢，性能瓶颈，隔离更好
半虚拟化 在虚拟机OS加入特殊虚拟化指令  hypervisor可以直接调用硬件资源

> Unified Management for Containers and VMs
Manage complex, modern apps as easily as traditional apps and VMs on modern vSphere infrastructure that supports container-based application development. Rearchitected with native Kubernetes, you can now modernize the 70+ million workloads running on vSphere. And now, you can run modern, containerized applications alongside existing enterprise applications on existing infrastructure with vSphere with Tanzu

基于操作系统的虚拟化：2层OS，易于实现，开销较大，需要管理层OS层转换请求 VMware
基于硬件的虚拟化：省略OS层 如xen，依赖虚拟化层进行管理，不依赖于主机OS，可直接调用硬件 缺点：依赖于虚拟化层，需要对虚拟化层进行开发， VMware ESXi, ⭐XEN

> VMware ESXi: The Purpose-Built Bare Metal Hypervisor
Discover a robust, bare-metal hypervisor that installs directly onto your physical server. With direct access to and control of underlying resources, VMware ESXi effectively partitions hardware to consolidate applications and cut costs. It's the industry leader for efficient architecture, setting the standard for reliability, performance, and support

> the xen project is focused on advancing virtualization in a number of different commercial and open source applications, including server virtualization, infrastructure as a services (iaas), desktop virtualization, security applications, embedded and hardware appliances, and automotive/aviation

服务器虚拟化：一台服务器$\rightarrow$ 多台服务器
存储：
　　对资源池的巨大文件系统管理 
　　存储资源统一整合管理：目录树🌲管理
　　🔀底层实现高效组织，保持隔离，
多‍‍‍读写同一台机器性能瓶颈（用户行为特征：经常读的用户，经常写的用户，调度）

应用程序虚拟化：应用程序和硬件解耦
平台虚拟化：消息平台，监控平台
桌面虚拟化：桌面和terminal解耦

请求🔀管理层🔀多台机器

# 虚拟化技术

## 完全虚拟化

host OS之上有guest OS，通用性更好

kvm

> KVM (for Kernel-based Virtual Machine) is a full virtualization solution for Linux on x86 hardware containing virtualization extensions (Intel VT or AMD-V). It consists of a loadable kernel module, kvm.ko, that provides the core virtualization infrastructure and a processor specific module, kvm-intel.ko or kvm-amd.ko

使得OS无需修改可以安装到系统中，可能不知道正处于虚拟化环境中，但是缺点 处理器密集型

## 准虚拟化

使得OS和虚拟化层协同工作，减轻2层OS的负担，但是需对OS进行改动，OS知道正处于虚拟化环境中，开销减小

xen（也逐渐支持全虚拟化，以提升通用性）

The Xen Project community develops an open-source type-1 or bare-metal hypervisor, which makes it possible to run many instances of an operating system or indeed different operating systems in parallel on a single machine (or host). The project develops the only type-1 hypervisor that is available as open source. The hypervisor is used as the basis for a number of different commercial and open source applications, such as server virtualization, Infrastructure as a Service (IaaS), desktop virtualization, security applications, embedded and hardware appliances, and automotive. It enables users to increase server utilization, consolidate server farms, reduce complexity, and decrease total cost of ownership.

使用Linux开源系统，修改系统以支持内核
性能高

CPU虚拟化
内存虚拟化
io虚拟化

# 容器技术

容器的威胁模型（外部容器的攻击）$\rightarrow$ 云的安全性研究


# MapReduce

是一个并行编程模型

由mapper reducer过程

`Hadoop` ：系统实现；自动实现map/reduce过程

~类比 runtime visual studio 
点击️自动完成编译、执行的步骤，Hadoop简化底层操作

资源管理（不同的优化目标进行最好的调度）

## 分布式并行编程

背景1：“摩尔定律”，CPU性能不断发展：单核、单核多核心、

`软硬协同` ：软件硬件不断发展，硬件发展$\rightarrow$ 需要有相应软件充分利用计算资源
；TensorFlow 单精度浮点计算（对精度要求不高）$\rightarrow$ 专门设计AI芯片，专门加速单精度浮点数

double/float计算效率不同，double速度可能变慢

背景2：分布式程序运行在大规模计算机集群cluster上，通过网络运行

### 网络 

1 2 3 4并行 （flat）1$\rightarrow$ 2 local路由很快

1 2 （上一级网关1）3 4 （上一级网关2）…… （fat-tree：路由层次少，减少出局域网时损耗）

1$\rightarrow$ 3会变慢，通过很多路由器

当flat上挂载太多机器，需要级联（层次型）

infiniteband（贵） 以太网$\rightarrow$ 万兆以太网，速度可以接近infiniband

考虑计算任务应分配到哪些机器，平衡计算资源（如计算任务对于某些部件经常读写）

### 设计通用编程模型的需求

eg 快排

4g数据快排设分配到4台机器排序有序

归并？$\rightarrow$ 算法设计？考虑到网络通信实现数据合并（`并行编程` ），如何使得效率较高、减少慢速通信带来损耗

每次需要针对问题设计分布式算法带来问题：算法设计者不一定对系统底层很了解，需要多次与工程师沟通

map reduce提供了封装框架：提供抽象之后，底层即可并行运行

> MapReduce is a programming model and an associated implementation for processing and generating big data sets with a parallel, distributed algorithm on a cluster.[1][2][3]
A MapReduce program is composed of a map procedure, which performs filtering and sorting (such as sorting students by first name into queues, one queue for each name), and a reduce method, which perf