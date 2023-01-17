# Contemporary Software Architectures: Federated and Centralized(当代软件体系结构：联合和集中的)

**Abstract** Automotive software architectures evolve together with the evolution of the electronics in vehicles. The distributed electronics of the cars of the 2000s and 2010s have started to reach the limit of their potential, and new electronic architectures are being introduced. In this chapter, we explore and discuss two of such new developments – federated architectures and centralized ones. These two architectural styles are a response to the challenges of distributed architectures with over 100 ECUs. Signaling, coordination, and integration drive the development of vehicles’ electronics to use fewer, more powerful ECUs with redundancy and virtualization. In this chapter, we explore these techniques and show how they are, and can be, used in vehicles’ software.

> **摘要**汽车软件体系结构随车辆中电子产品的发展而发展。2000 年代和 2010 年代汽车的分布式电子设备已经开始达到其潜力极限，并且正在引入新的电子体系结构。在本章中，我们探索并讨论了这两个新发展 - 联合体系结构和集中式架构。这两种架构风格是对具有 100 多个 ECU 的分布式体系结构的挑战的回应。信号传导，协调和集成推动了车辆电子产品的开发，以使用冗余和虚拟化更少，更强大的 ECU。在本章中，我们探讨了这些技术，并展示了它们在车辆软件中的使用方式，并且可以使用。

## Introduction

Automotive software architectures can follow a number of architectural styles. As Chap. [2](#_bookmark54) shows, there are a number of these. Although it seems that software architects can choose whichever style they want, each style has its particular pros and cons. It is also the case that the hardware architecture of the vehicles dictates certain principles [[Sta16](#_bookmark183), [Für10](#_bookmark175)]. For example, a distributed electronic system with over 100 ECUs must be supported by component-based architectural style and cannot be designed as one, large, monolithic application.

> 汽车软件体系结构可以遵循多种架构样式。作为第 [2](#_bookmark54) 章表明，有许多。尽管似乎软件架构师可以选择他们想要的任何样式，但每种样式都有其特定的优点和缺点。同样，车辆的硬件体系结构决定了某些原理[[sta16](#_bookmark183)，[für10](#_bookmark175)]。例如，必须由基于组件的架构样式支持具有 100 多个 ECU 的分布式电子系统，并且不能设计为一个大型，单片的应用。

In the recent decade, vehicle manufacturers found that their software cannot be based on the principle of distribution any more. Distribution works well until the communication overhead becomes a problem. In safety critical systems, where we need to validate that the software is safe, highly distributed systems can be hard to validate because of the emergent properties of the systems (e.g., high variability of communication latency over time, over traffic situations) and because of the need for coordination. One of the ways to address these challenges is to construct software according to the principles of federated software architectures, where highly dependent components are grouped into moderately dependent subsystems, connected by the federal information highways [[FZW03](#_bookmark176)].

> 近十年来，汽车制造商发现他们的软件不能再基于分发的原则。分发工作良好，直到通信开销成为问题。在安全关键系统中，我们需要验证软件是否安全，高度分布式系统可能难以验证，因为系统的突发特性(例如，通信延迟随时间、交通情况的高度可变性)以及由于 协调的需要。应对这些挑战的方法之一是根据联邦软件架构的原则构建软件，其中高度依赖的组件被分组为中度依赖的子系统，由联邦信息高速公路 [[FZW03](#_bookmark176)] 连接。

Federated architectures served their purpose, but over time, they also evolved towards centralized architectures [[OESHK09](#_bookmark179)]. These centralized architectures use a redundant pair of large computing nodes with virtualization to execute as many processes as possible. This reduces the need for communication overhead over networks and the low-level coordination but also increases challenges in terms of connecting boundary nodes (e.g., sensors and actuators) as well as brings in challenges of combining components of different criticality. In this chapter, we explore examples of federated and centralized software architectures. The examples are based on real vehicle architectures, largely simplified for the purpose of this book. In these examples, we explore how different architectural styles can be combined and make educated guesses or speculations about how the future of architecture may look like.

> 联合体系结构达到了目的，但随着时间的流逝，它们也发展为集中式体系结构[[Oeshk09](#_bookmark179)]。这些集中式体系结构使用冗余的大型计算节点和虚拟化来执行尽可能多的进程。这减少了网络上的通信开销和低级协调的需求，但在连接边界节点(例如传感器和执行器)方面，还增加了挑战，并带来了结合不同批判性的组成部分的挑战。在本章中，我们探讨了联合和集中式软件体系结构的示例。这些示例基于真实的车辆体系结构，在很大程度上简化了本书的目的。在这些示例中，我们探讨了如何将不同的架构风格组合在一起，并对架构未来的外观进行有根据的猜测或猜测。

## Federated Software Architectures(联合软件体系结构)

The concept of federated software comes essentially from the field of enterprise computing, where the enterprise system architecture reflects the organization’s structure. In the automotive field, the federation reflects the domains of the vehicle’s system rather than the organization. The most common domains are:

> 联合软件的概念基本上来自企业计算领域，企业系统体系结构反映了组织的结构。在汽车领域，联邦反映了车辆系统的域而不是组织的域。最常见的域是：

- Active safety – responsible for such functions as collision avoidance or emer- gency braking
- Infotainment – responsible for displays or connections to mobile phones
- Powertrain – responsible for the engine and gearbox’s software

> - 主动安全性 - 负责避免碰撞或出现制动等功能
> - 信息娱乐 - 负责显示或连接手机
> - 动力总成 - 负责发动机和变速箱的软件

The ECUs and thus the software components are tightly connected to each other within the domain, and the domains are connected to each other by high-speed connection busses. Figure [3.1](#_bookmark157) shows an example of such an architecture.

> ECU 和软件组件在域内紧密连接，并且域通过高速连接总线相互连接。图 [3.1](#_Bookmark157) 显示了此类架构的示例。

Figure [3.1](#_bookmark157) contains three domains, with one domain controller each. One of the domains is sparse, with five ECUs. These ECUs are connected to each other via a dedicated intra-domain bus. There is a lot of communication and coordination between these ECUs. In such domains, the ECUs are often larger in terms of computational power and the size of the software. An example could be a domain of infotainment which contains a few nodes (e.g., GPS, display) that require a lot of coordination and dedicated bandwidth to communicate with low latency.

> 图 [3.1](#_bookmark157) 包含三个域，每个域控制器一个。其中一个域是稀疏的，有五个 ECU。这些 ECU 通过专用的内域总线相互连接。这些 ECU 之间有很多沟通和协调。在这样的域中，ECU 在计算能力和软件大小方面通常更大。一个示例可能是一个信息娱乐域，其中包含一些节点(例如 GPS，显示)，这些节点需要大量协调和专用带宽才能与低延迟通信。

The second domain, in the middle, has nine ECUs. This domain coordinates more nodes, which means that the domain controller is larger in terms of computational power and bandwidth than in the first domain. The size of the ECUs is most probably smaller than in the first domain, but the communication and coordination are higher. An example of such a domain can be the active safety domain where there are a lot of actuators and sensors.

> 第二个领域中间有 9 个 ECU。该域协调更多的节点，这意味着域控制器在计算功率和带宽方面比第一个域更大。ECU 的大小可能比第一个域中的大小要小，但是通信和协调较高。这样的域的一个例子可以是有很多执行器和传感器的主动安全域。

The last domain contains five ECUs and two ECUs connected to other ECUs, and not directly to the intra-domain bus. The ECUs that are connected directly are often the ones that need to communicate with each other, but only one of them communicates with the domain controllers. These sub-ECUs are often actuators and sensors that include computational resources/processors.

> 最后一个域包含 5 个 ECU 和两个与其他 ECU 相连的 ECU，而不是直接与内域总线有关。直接连接的 ECU 通常是需要相互通信的 ECU，但其中只有一个与域控制器进行通信。这些子 ECU 通常是包括计算资源/处理器在内的执行器和传感器。

![](./media/image63.png)
<**Fig. 3.1** <span id=`_bookmark157` class=`anchor`></span>Federated software architecture

This figure illustrates that each domain is independent from others in terms of how it is organized. The software components that are executed on the domain controllers are mostly responsible for coordination, bus governance, and commu- nication between the domains. The software components executed on the ECUs provide the functionality that is related to the ECUs’ purpose and that is needed by specific functions. The specific functions are processes that are controlled either by the domain controllers or by dedicated, larger ECUs within the domain.

> 该图说明，每个领域在组织方式方面都是独立的。在域控制器上执行的软件组件主要负责域之间的协调，总线治理和通讯。在 ECUS 上执行的软件组件提供了与 ECUS 目的相关的功能，并且是特定功能所需的。特定功能是由域控制器或域内专用，更大的 ECU 控制的过程。

Figure [3.2](#_bookmark159)[<sup>1</sup>](#_bookmark158) presents how one function, in this case the automated parking, is distributed over different domains. The boxes represent the software components, the connections between them abstract the communication channels, and the colored backgrounds show the different domains.

> 图 [3.2](#_bookmark159)[](#_bookmark158)提出一个功能，在这种情况下，自动停车位是如何在不同域中分发的。框表示软件组件，它们之间的连接抽象到通信通道，而彩色背景显示了不同的域。

The algorithm for automated parking needs to control the vehicle’s speed and position by interacting with the brakes, engine, gearbox, and steering wheel. This means that the algorithm sends signals to the domain controller of the powertrain domain and the ECUs in that domain. The algorithm also needs to interact with the driver by displaying messages and potentially receive a cancellation command. This is done by communicating with the infotainment domain. Finally, the algorithm itself is executed on one of the ECUs in the active safety domain – the Driver Support Manager. It interacts with the components responsible for the camera (for image recognition) and the parking sensors/radars.

> 自动停车的算法需要通过与制动器，发动机，变速箱和方向盘进行交互来控制车辆的速度和位置。这意味着该算法将信号发送到该域中动力总成域和 ECU 的域控制器。该算法还需要通过显示消息并可能接收取消命令来与驱动程序进行交互。这是通过与信息娱乐域进行通信来完成的。最后，该算法本身是在 Active Safety 域中的一个 ECU 上执行的 - 驾驶员支持经理。它与负责相机(图像识别)和停车传感器/雷达的组件相互作用。

<img src=`./media/image8.png` style=`width:1.41833in` />
<span id=`_bookmark158` class=`anchor`></span>1Brake, steering wheel icons: Freepik, camera: Kirahshastry, engine: monkik, display: phatplus on flaticon.com.

<img src=`./media/image65.png` style=`width:0.30048in` />
<img src=`./media/image66.png` style=`width:0.23556in;height:0.13021in` />
![](./media/image67.png)
<img src=`./media/image72.png` style=`width:0.18491in` />
<img src=`./media/image73.png` style=`width:0.15373in` />
<**Fig. 3.2** <span id=`_bookmark159` class=`anchor`></span>Example of a software function with components distributed over different domains (colored background)

The algorithm also delegates certain calculations to the supporting components – signal processing. These supporting components off-load the main computer by calculating information about the vehicle speed, position, and obstacle detection.

> 该算法还将某些计算委托给支持组件 - 信号处理。这些支持组件通过计算有关车辆速度，位置和障碍物检测的信息来卸载主计算机。

This diagram illustrates two important aspects. The first is the separation of concerns – algorithms, controllers, and handlers are grouped into domains based on the combination of logical and physical allocation. The second is the principle of communication – the components that communicate with each other heavily are grouped together in the same domain.

> 该图说明了两个重要方面。首先是关注点的分离 - 根据逻辑和物理分配的组合将算法，控制器和处理程序分为域。第二个是交流的原则 - 彼此之间相互通信的组成部分分组在一起。

The separation of concerns is important as all software components related to a specific hardware component (e.g., engine) often realize functions related to these components. An engine controller increases/decreases throttle, shifts gear, etc. Therefore, it is important that these software functions are located close to the hardware and that these are not distributed – for example, one engine controller can ensure that none of the sequences of function invocations can damage the engine. The separation of concerns also means that realizing one function does not affect other, unrelated functions. When using the parking assistance function, we can still control the radio and open windows. When we, however, intervene with one of the components used in the function, the main algorithm is notified, and it reacts accordingly. For example, when we press a button to cancel the parking assistance, the algorithm suspends that function.

> 关注点的分离很重要，因为与特定硬件组件(例如，引擎)相关的所有软件组件通常会实现与这些组件相关的功能。发动机控制器增加/减小油门，移动齿轮等。因此，重要的是，这些软件功能靠近硬件，并且没有分布，例如，一个发动机控制器可以确保函数序列没有任何功能序列调用会损坏发动机。关注点的分离还意味着实现一个函数不会影响另一个无关的函数。使用停车援助功能时，我们仍然可以控制收音机和打开的窗户。但是，当我们干预功能中使用的一个组件之一时，将通知主算法，并做出相应的反应。例如，当我们按下按钮取消停车援助时，该算法会暂停该功能。

The communication within the same domain is more intensive than within different domains. For example, the supporting components for calculating the distance or detecting objects communicate very often with the main algorithm. They need to process live feed from cameras and radars and therefore need to send

> 在同一域内的通信比不同域中的通信更密集。例如，用于计算距离或检测对象的支持组件与主算法经常通信。他们需要处理来自相机和雷达的实时饲料，因此需要发送

1. Centralized Software Architectures 59 signals very often. However, the components that steer the engine and gearbox have latencies related to the physical processes in the engine and the gearbox – increasing the throttle does not happen as fast as capturing the frame of the video feed. Therefore, the communication overhead introduced by the inter-domain communication does not influence the parking assistance function noticeably. The above-mentioned advantages of the federated software architectures made them very popular in the automotive industry. They also resulted in the design principles which we see in modern cars – separation of concerns, reuse, and carry-overs between car generations. One of the notable examples of this is the GENIVI framework for passenger cars’ infotainment. It is a generic framework, which is developed in collaboration with several companies, and it is used by several car manufacturers. It can be extended with brand-specific extensions without jeopardizing the intellectual property rights of other brands, similar to the Android operating system.

> 1.集中式软件体系结构经常经常使用 59 个信号。但是，引导发动机和变速箱的组件具有与发动机和变速箱中物理过程相关的潜伏期 - 增加油门的速度不像捕获视频馈电框架那样快。因此，域间通信引入的通信开销不会明显影响停车援助的功能。联合软件架构的上述优势使它们在汽车行业非常受欢迎。它们还产生了我们在现代汽车中看到的设计原则 - 千代人之间的关注，再利用和携带。其中一个值得注意的例子之一是乘用车信息娱乐的 Genivi 框架。它是一个通用框架，与多家公司合作开发，并由几家汽车制造商使用。它可以通过特定于品牌的扩展来扩展，而不会危害其他品牌的知识产权，类似于 Android 操作系统。

However, there are certain limitations to federated architectures. The main limitation becomes evident in the cars that use machine learning or many advanced functions. As a rule of thumb, the more advanced the function, the more commu- nication it needs. The increased communication means increased speed or even additional communication busses. These extra busses and increased speed both have limitations and require more calculations, redundancy, coordination, and security. Increased number of hardware components decreases reliability as more elements can break and thus affect the overall performance of the entire system. This is where centralized software architectures enter the picture – with reduced number of ECUs but with larger computational power.

> 但是，联合体系结构有一定的局限性。在使用机器学习或许多高级功能的汽车中，主要限制变得明显。根据经验，功能越先进，其所需的通知就越多。增加的通信意味着提高速度甚至其他通信总线。这些额外的公共汽车和提高的速度都有局限性，需要更多的计算，冗余，协调和安全性。增加的硬件组件数量会降低可靠性，因为更多的元素可能会破裂，从而影响整个系统的整体性能。这是集中式软件体系结构进入图片的地方 - ECU 数量减少，但具有较大的计算能力。

## Centralized Software Architectures(集中软件体系结构)

The concept of centralized software architectures is well known and has been used in different domains before – it is also known as the  `star architecture`  as the topology is often drawn as a star.

> 集中式软件体系结构的概念是众所周知的，并且以前曾在不同的领域中使用过 - 它也被称为 `恒星体系结构` ，因为拓扑通常被绘制为恒星。

In automotive electronics, this architecture has been developed further. The central node has been designed so that it can be redundant. As this is the node which makes almost all calculations, it needs to be secure from hardware and software problems. Hardware redundancy helps to keep the hardware reliability high.

> 在汽车电子产品中，该体系结构已进一步开发。中央节点已经设计为可以多余。由于这是几乎所有计算的节点，因此需要从硬件和软件问题中安全。硬件冗余有助于保持硬件可靠性高。

Figure [3.3](#_bookmark161) shows the schematic of a centralized architecture. It illustrates the core concepts of a central computing unit, which is redundant. There is also an edge node, which is often a coordination unit to help reduce the number of busses in the system. These edge units have limited computing power and perform no calculations and control no algorithms, but they provide relaying functions between multiple sensors and the central unit.

> 图 [3.3](#_bookmark161) 显示了集中式体系结构的示意图。它说明了中央计算单元的核心概念，这是多余的。还有一个边缘节点，该节点通常是一个协调单元，可帮助减少系统中的公共汽车数量。这些边缘单元具有有限的计算能力，没有执行不计算和控制算法，但是它们在多个传感器和中央单元之间提供了中继功能。

In the centralized architecture, software is often executed in a redundant way – using the mechanism of virtualization and containerization [[SKF](#_bookmark181), [NDB](#_bookmark178)]. Virtualization is a mechanism that allows to divide physical computing resources into several virtual machines. These virtual machines are seen by the software components as physical machines. The software that controls and governs this virtualization process is called a hypervisor. This model of sharing resources and separating processes from each other is the foundation of cloud computing [[PJZ18](#_bookmark180)]. Figure [3.4](#_bookmark162) shows virtual machines running in a central computer node. A central computing node has hardware resource and an operating system that executes the hypervisor. The hypervisor virtualizes the resources and ensures that both virtual machines have access to the resources that they need for the processes they execute. The dotted lines in Fig. [3.4](#_bookmark162) show that the virtual machines can access/ communicate with different sensors. However, the sensors are all connected to the central computing node’s hardware resources. It is the hypervisor that manages the physical connections of sensors and their logical connections to the virtual machines.

> 在集中式架构中，软件通常以冗余方式执行——使用虚拟化和容器化机制 [[SKF](#_bookmark181), [NDB](#_bookmark178)]。虚拟化是一种允许将物理计算资源划分为多个虚拟机的机制。这些虚拟机被软件组件视为物理机。控制和管理此虚拟化过程的软件称为管理程序。这种资源共享和进程分离的模型是云计算的基础[[PJZ18](#_bookmark180)]。图 [3.4](#_bookmark162) 显示了在中央计算机节点中运行的虚拟机。中央计算节点具有硬件资源和执行管理程序的操作系统。管理程序将资源虚拟化并确保两个虚拟机都可以访问它们执行进程所需的资源。图 [3.4](#_bookmark162) 中的虚线显示虚拟机可以访问/与不同的传感器通信。但是，传感器都连接到中央计算节点的硬件资源。管理程序管理传感器的物理连接及其与虚拟机的逻辑连接。

![](./media/image74.png)
<**Fig. 3.3** <span id=`_bookmark161` class=`anchor`></span>Centralized software architecture

![](./media/image78.png)
<**Fig. 3.4** <span id=`_bookmark162` class=`anchor`></span>Centralized software architecture with a hypervisor

When distributing software components to virtual machines, we can use similar design principles as for the separation of domains. Those components that commu- nicate often with each other, or need a higher bandwidth, should be placed in the same virtual machine. There, they can share memory or disk space and therefore communicate without the use of network resources.

> 当将软件组件分配到虚拟机时，我们可以使用与域分离相似的设计原理。那些经常相互交流或需要更高带宽的组件应放在同一虚拟机中。在那里，他们可以共享内存或磁盘空间，因此可以在不使用网络资源的情况下进行通信。

Since virtual machines are seen by the components as separate computers/ECUs, the components from different virtual machines communicate with each other using network mechanisms or by using shared directories (mounting shared directories).

> 由于组件将虚拟机视为单独的计算机/ECU，因此来自不同虚拟机的组件使用网络机制或使用共享目录(安装共享目录)相互通信。

This centralized architecture with hypervisors is more flexible than the federated architecture. The number of virtual machines is limited only by the hardware resources. The hypervisor can also start/stop/restart virtual machines, which allows to save or prioritize resources. Virtual machines can be frozen, serialized, and started on the redundancy node if needed.

> 与联合体系结构相比，这种具有虚拟机管理程序的集中式体系结构更灵活。虚拟机的数量仅受硬件资源的限制。管理程序还可以启动/停止/重新启动虚拟机，从而可以保存或优先考虑资源。如果需要，可以将虚拟机冷冻，序列化并在冗余节点上启动。

There are, however, some disadvantages in this architecture. The software components need to be provided for a specific operating system and setup of the virtual machine, which makes the reuse different. Instead of reusing an entire ECU, we only reuse parts of the software, which need to be tested on new types of virtual machines. The virtual machines, and thus the software components executed on them, do not have all the rights to hardware resources as an ECU has. Therefore, testing for non-functional properties needs to be done when all virtual machines are in place.

> 但是，此架构中有一些缺点。需要为特定的操作系统和虚拟机设置提供软件组件，这使重复使用不同。我们只能重复使用整个 ECU，而仅重用软件的一部分，这些部分需要在新型的虚拟机上进行测试。虚拟机，因此在其上执行的软件组件，没有 ECU 拥有的所有硬件资源权利。因此，当所有虚拟机都到位时，需要对非功能性属性进行测试。

Naturally, when drawing these diagrams, I use only a few components. The reality is, however, very different. There can be hundreds of components running in parallel in a vehicle’s software system – at least one process per ECU. So, when changing the architecture from federated or distributed to centralized, these processes need to be moved to the few virtual machines that exist. From the perspec- tive of vehicle manufacturers, the number of virtual machines should be as small as possible to reduce hardware costs and complexity in the coordination between processes – both within each virtual machine and between virtual machines.

> 自然，当绘制这些图表时，我只使用几个组件。但是，现实是非常不同的。在车辆的软件系统中可以并行运行数百个组件 - 每个 ECU 至少一个过程。因此，当将体系结构从联合或分配到集中式更改时，需要将这些过程移至存在的少数虚拟机。从车辆制造商的透视图中，虚拟机的数量应尽可能少，以降低过程之间的硬件成本和复杂性 - 无论是在每个虚拟机和虚拟机之间。

The deployment of software components can be visualized in the same way as in federated architectures ([3.2](#_bookmark159)), but we can use colors to show the distribution of processes/components on virtual machines.

> 可以以与联合架构([3.2](#_bookmark159))相同的方式来可视化软件组件的部署，但是我们可以使用颜色来显示虚拟机上过程/组件的分布。

## Examples

So far we looked at the architectural styles and explained their principles. Now, let us explore examples of how this is realized in practice. Here, we discuss two examples – a federated architecture and its domain controllers and pipes and filters in autonomous drive.

> 到目前为止，我们研究了架构风格，并解释了他们的原则。现在，让我们探讨如何在实践中实现这一目标的例子。在这里，我们讨论了两个示例 - 一个联合体系结构及其域控制器，管道和自动驱动器中的过滤器。

### _Federated Architecture of a Car_(汽车联合架构)

In this chapter, I mentioned that most cars are moving towards centralized architec- ture. This is mostly driven by the fact that software gets so complex that it cannot be developed in the same way anymore. In the preface to the first edition of this book, Christof Ebert provided a diagram showing that the size of the software in a car grows and is expected to grow further [[Sta17](#_bookmark184)].

> 在本章中，我提到大多数汽车正在朝着集中的架构迈进。这主要是由于软件变得如此复杂，以至于不能再以相同的方式开发它。在本书的第一版的序言中，克里斯托夫·埃伯特(Christof Ebert)提供了一个图表，显示汽车中该软件的大小会增长，并有望进一步生长[[sta17](#_bookmark184)]。

However, discussing this development in software engineering conferences often leads to the conclusion that this development is still a few years away. The limiting factors are the computing power of today and the need to change the programming paradigms to overcome it. We also need to focus on new aspects, which are increasingly difficult in a distributed environment, e.g., security [[Ebe17](#_bookmark173)]. With the first example, I want to illustrate two aspects: (1) how automotive software architectures are presented at a high level and (2) how different views on the same architecture help us communicate and understand the architectural design of the system.

> 但是，讨论软件工程会议中的这种发展通常会得出这样的结论：这种发展还有几年的时间。限制因素是当今的计算能力以及改变编程范例以克服它的需要。我们还需要关注新方面，这些方面在分布式环境中越来越困难，例如安全性[[EBE17](#_bookmark173)]。在第一个示例中，我想说明两个方面：(1)如何在高级呈现汽车软件体系结构以及(2)相同体系结构上的不同视图如何帮助我们进行交流和理解系统的架构设计。

Figure [3.5](#_bookmark165) presents an example of the nodes in a modern car. It presents software subsystems drawn according to their physical location in the car or to emphasize their role.

> 图 [3.5](#_bookmark165) 介绍了现代汽车中节点的示例。它介绍了软件子系统根据其在汽车中的实际位置或强调其角色。

<img src=`./media/image84.jpeg` style=`width:4.33999in;height:1.475in` />
<**Fig. 3.5** <span id=`_bookmark165` class=`anchor`></span>Example of a car’s architecture from [[Eea21](#_bookmark174)], used with permission from the author

The example shows two central nodes (Central Gateway and Connectivity Gateway) as well as a number of domain controllers – e.g., Powertrain DC (Domain Controller) and Body DC. It also contains a number of nodes connected directly to the central nodes – Instrument Cluster or Head Unit.

> 该示例显示了两个中央节点(中央门户和连接网关)以及许多域控制器 - 例如动力总成 DC(域控制器)和身体 DC。它还包含许多直接连接到中央节点的节点 - 仪表盘或头部单元。

Figure [3.6](#_bookmark166) shows the same architecture as layered architectural style. This shows that the architectural style, to some degree, depends on how we visualize the architecture.

> 图 [3.6](#_bookmark166) 显示与分层体系结构样式相同的架构。这表明在某种程度上，架构风格取决于我们如何可视化体系结构。

The figure is structured differently, but it emphasizes the important aspects of the design, which are less evident in Fig. [3.5](#_bookmark165). The Connectivity Gateway is not really a central node, but it is a gateway which is used for high-speed communication with certain components (e.g., Infotainment Cluster). The distinction between these two nodes is clear when we name the layers – high-performance layer vs. connectivity layer.

> 该图的结构不同，但它强调了设计的重要方面，这在图 [3.5](#_bookmark165) 中不太明显。连接网关并不是真正的中央节点，而是一个网关，用于与某些组件(例如信息娱乐集群)的高速通信。当我们命名图层时，这两个节点之间的区别很明显 - 高性能层与连接层。

<img src=`./media/image85.jpeg` style=`width:4.60422in;height:3.13in` />
<**Fig. 3.6** <span id=`_bookmark166` class=`anchor`></span>Layered view of the software architecture in Fig. [3.5](#_bookmark165), from [[Eea21](#_bookmark174)], used with permission from the author

### _Pipes and Filters in Autonomous Drive_

One of the interesting new developments in automotive software is the introduction of functions in the area of autonomous drive. This is a function that allows drivers to release their hands from the steering wheel and let the car’s software drive autonomously.

> 汽车软件中有趣的新发展之一是在自动驱动器领域引入功能。这是一个允许驾驶员从方向盘释放手并让汽车的软件自动驾驶的功能。

The real architectures are proprietary, but the work of Serban et al. [[SPV18](#_bookmark182)] presents an example of how this architecture can be realized. The software compo- nents are organized into a pipe-and-filter architecture (as discussed in Chap. [2](#_bookmark54)).

> 真正的体系结构是专有的，但是 Serban 等人的工作。[[SPV18](#_bookmark182)]介绍了如何实现此架构的示例。软件组合被组织成管道和过滤器架构(如第 [2](#_bookmark54) 中所述)。

The advantage of this type of architectural style is the ability to process data continuously and take over the control of the car without the need to coordinate many software components outside of the pipe. However, the challenge is that this becomes a single point of failure and therefore needs to be software redundant. An example of how this can be realized can be found in the work of Luo et al.

> 这种类型的架构样式的优点是能够连续处理数据并接管汽车的控制，而无需协调管道外许多软件组件。但是，挑战在于，这成为单个故障点，因此需要成为软件冗余。可以在 Luo 等人的工作中找到如何实现这一目标的一个例子。

> [[LSB<sup>+</sup>17](#_bookmark177)]. Figure [3.7](#_bookmark168) shows a simplified version of the redundant channel.

The figure contains two separate channels of communication, with the redundancy channel monitoring all components in the main channel. When an error is detected, the redundant channel has components that execute algorithms for safe stop of the vehicle.

> 该图包含两个单独的通信通道，冗余通道监视主通道中的所有组件。当检测到错误时，冗余通道具有执行算法以安全停止车辆的组件。

The redundancy channel seems to be straightforward, but it cannot address all reliability challenges. For example, the actuator and the sensors are not redundant in this example. Neither are they in real life – the cost of introducing redundant sensors for all safety-critical functions is not justifiable from the customer perspective. Therefore, instead of redundancy, we often use sensor fusion and two different sensors that provide similar data, e.g., video feed and radar/lidar feed.

> 冗余渠道似乎很简单，但无法应对所有可靠性挑战。例如，在此示例中，执行器和传感器不是冗余。它们也不是现实生活 - 从客户的角度来看，为所有安全 - 关键功能引入冗余传感器的成本并不合理。因此，我们经常使用传感器融合和两个提供相似数据的不同传感器，例如视频饲料和雷达/激光雷达进料。

![](./media/image86.png)
<**Fig. 3.7** <span id=`_bookmark168` class=`anchor`></span>Channel redundancy in pipes and filters for autonomous drive

### _Infotainment Systems_

In the book, we focus mostly on the design of the overall system, but I recommend to explore some of the open-source components a bit further. These are especially important for understanding how we construct software systems for modern cars.

> 在这本书中，我们主要关注整体系统的设计，但我建议您进一步探索一些开源组件。这些对于了解我们如何为现代汽车构建软件系统尤其重要。

One of these open-source systems is the GENIVI platform for the infotainment system [https://genivi.github.io/](https://genivi.github.io/). This is a repository of all source codes for the GENIVI platform, including both architectural and detailed design diagrams of the source code.

> 这些开源系统之一是信息娱乐系统的节奏平台[[https://genivi.github.io/](https://genivi.github.io/)]([[https://genivi.github.io/](https://genivi.github.io/)](%5B[https://genivi.github.io/%5D(https://genivi.github.io/)](https://genivi.github.io/%5D(https://genivi.github.io/))))。这是 Genivi 平台的所有源代码的存储库，包括源代码的体系结构和详细的设计图。

## On Truck Architectures

In this book, I discuss mostly passenger cars. This is mainly because the automotive market develops very rapidly in that context. The market is very dynamic, and customers are drawn to cars that have increasingly advanced features. This is also the market where the requirements for using the software are relatively lower than for other types of vehicles. Truck drivers, construction machine operators, or special vehicle operators receive additional training. The training is often specific for the types of machinery that they operate.

> 在这本书中，我主要讨论乘用车。这主要是因为在这种情况下，汽车市场发展迅速。市场非常活跃，客户被越来越高级功能的汽车吸引。这也是使用该软件要求相对较低的市场，而不是其他类型的车辆。卡车司机，施工机器运营商或特殊车辆操作员会接受额外的培训。培训通常是针对其操作机械类型的特定特定的。

Autonomous trucks or construction vehicles have been demonstrated and used in designated areas, where the traffic is controlled and the operating conditions are monitored. Therefore, the architectures of modern trucks and other heavy vehicles differ from passenger cars to a certain degree, just as the requirements on these vehicles differ. Modern cars are supposed to be feature-rich, whereas heavy machines are supposed to be reliable and robust.

> 自动驾驶卡车或施工车辆已被证明并在指定区域，在该区域，在该区域控制并监控操作条件。因此，现代卡车和其他重型车辆的体系结构在一定程度上与乘用车不同，就像这些车辆的要求不同。现代汽车应该是功能丰富的，而重型机器应该是可靠和坚固的。

## Summary

Software is increasingly prevalent in modern cars. It is almost impossible to use any function of a car without software being involved in it. The principles of designing software evolve slowly; the architectural styles and patterns evolve slowly too.

> 在现代汽车中，软件越来越普遍。如果不参与软件，几乎不可能使用汽车的任何功能。设计软件的原理逐渐发展；架构风格和图案也会缓慢发展。

However, as automotive software gets increasingly complex and is required to be increasingly safe, the ways in which the components are integrated and organized change. In new cars, and in the cars of the future, the software gets more centralized and/or organized in domains. This enables machine learning, faster communication between components, and redundant hardware.

> 但是，随着汽车软件变得越来越复杂并且必须变得越来越安全，组件的集成和有组织的变化方式。在新车和未来的汽车中，该软件在域中变得更加集中和/或组织。这使机器学习，组件之间的通信更快以及冗余硬件。

In this chapter, we explored two architectural styles – federated and centralized. We learned the principles guiding the organization of the software components in these architectures. We also learned about modern architectures by studying two examples.

> 在本章中，我们探索了两种架构风格 - 联合和集中。我们了解了指导这些体系结构中软件组件的组织的原则。我们还通过研究两个例子来了解现代体系结构。

In the next chapter, we dive deeper into the standard that governs a lot of automotive software design today – AUTOSAR. We focus mostly on the new adaptive AUTOSAR platform, which is believed will change the face of automotive software architectures in the next decade.

> 在下一章中，我们更深入地了解了当今管理许多汽车软件设计的标准 - Autosar。我们主要关注新的自适应汽车平台，据信这将在未来十年内改变汽车软件体系结构的面貌。

## References

<span id=`_bookmark172` class=`anchor`><span id=`_bookmark173` class=`anchor`></span></span>Ebe17. Christof Ebert. Cyber security requirements engineering. In _Requirements Engineer- ing for Service and Cloud Computing_, pages 209–228. Springer, 2017.

<span id=`_bookmark174` class=`anchor`></span>Eea21. Christof Ebert and et. al. Technology trends converging to the new normal. _IEEE Software_, 38(2), 2021.

<span id=`_bookmark175` class=`anchor`></span>Für10. Simon Fürst. Challenges in the design of automotive software. In _Proceedings of the Conference on Design, Automation and Test in Europe_, pages 256–258. European Design and Automation Association, 2010.

<span id=`_bookmark176` class=`anchor`></span>FZW03. George Fernandez, Liping Zhao, and Inji Wijegunaratne. Patterns for federated architecture. _Journal of Object Technology_, 2(1):135–149, 2003.

<span id=`_bookmark177` class=`anchor`></span>LSB+ 17. Yaping Luo, Arash Khabbaz Saberi, Tjerk Bijlsma, Johan J Lukkien, and Markvan den Brand. An architecture pattern for safety critical automated driving appli- cations: Design and analysis. In _2017 Annual IEEE International Systems Conference (SysCon)_, pages 1–7. IEEE, 2017.

<span id=`_bookmark178` class=`anchor`></span>NDB+10. Nicolas Navet, Bertrand Delord, Markus Baumeister, et al. Virtualization in automotive embedded systems: an outlook. In _Seminar at RTS Embedded Systems_. Citeseer, 2010.

<span id=`_bookmark179` class=`anchor`></span>OESHK09. Roman Obermaisser, Christian El Salloum, Bernhard Huber, and Hermann Kopetz. From a federated to an integrated automotive architecture. _IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems_, 28(7):956–965, 2009.

<span id=`_bookmark180` class=`anchor`></span>PJZ18. Claus Pahl, Pooyan Jamshidi, and Olaf Zimmermann. Architectural principles for cloud software. _ACM Transactions on Internet Technology (TOIT)_, 18(2):1–23, 2018.

<span id=`_bookmark181` class=`anchor`></span>SKF+ 13. Marius Strobl, Markus Kucera, Andrei Foeldi, Thomas Waas, Norbert Balbierer, and Carolin Hilbert. Towards automotive virtualization. In _2013 International Conference on Applied Electronics_, pages 1–6. IEEE, 2013.

<span id=`_bookmark182` class=`anchor`></span>SPV18. Alexandru Constantin Serban, Erik Poll, and Joost Visser. A standard driven software architecture for fully autonomous vehicles. In _2018 IEEE International Conference on Software Architecture Companion (ICSA-C)_, pages 120–127. IEEE, 2018.

<span id=`_bookmark183` class=`anchor`></span>Sta16. Miroslaw Staron. Software complexity metrics in general and in the context of ISO 26262 software verification requirements. In _Scandinavian Conference on Systems Safety_. [http://gup.ub.gu.se/records/fulltext/233026/233026.pdf](http://gup.ub.gu.se/records/fulltext/233026/233026.pdf), 2016.

<span id=`_bookmark184` class=`anchor`></span>Sta17. Miroslaw Staron. _Automotive software architectures_. Springer, 2017.
