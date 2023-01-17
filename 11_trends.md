# Current Trends in Automotive Software Architectures

**Abstract** Cars have evolved a lot since their introduction and will evolve even more. Today’s cars would not work without the software that is embedded in their electronics. Although the physical processes are often the same as in the cars’ of the 1990s (combustion engines, servo steering), they become computer platforms and are able to `think` and drive autonomously. In this chapter we look into a few trends which shape automotive software engineering—autonomous driving, self-systems, big data and new software engineering paradigms. We look into how these trends can shape the future of automotive software engineering.

> **摘要**自推出以来，汽车已经发展了很多，而且还会进一步发展。今天的汽车如果没有嵌入在电子设备中的软件就无法工作。虽然物理过程通常与 20 世纪 90 年代的汽车相同(内燃机、伺服转向)，但它们成为计算机平台，能够 `思考` 和自主驾驶。在本章中，我们将探讨影响汽车软件工程自动驾驶、自我系统、大数据和新软件工程范式的几个趋势。我们研究这些趋势如何影响汽车软件工程的未来。

## Introduction

Automotive software evolves over time and requires changes to the methods used to develop it. The evolution of software means that we can use new functions which require more software, but also that we can use more advanced software development methods.

> 汽车软件随着时间的推移而发展，需要改变开发软件的方法。软件的发展意味着我们可以使用需要更多软件的新功能，但也意味着我们能够使用更先进的软件开发方法。

If we look at the history of electronics and software in cars, we can see that it is today that the big technological breakthroughs are happening. The cars of today have become sophisticated computer platforms which can be used in multiple ways. The powertrain technology has changed from traditional combustion engines to electrical or hybrid (e.g. hydrogen technology).

> 如果我们回顾汽车电子和软件的历史，我们可以看到，今天正在发生重大的技术突破。今天的汽车已经成为复杂的计算机平台，可以以多种方式使用。**动力总成技术已从传统的内燃机转向电动或混合动力(例如氢技术)**。

Living in these interesting times, software engineers and architects will see a lot of great possibilities and great potential. Let us then explore a few trends that seem to shape current automotive software engineering. In particular, let us explore the following trends:

> 在这些有趣的时期生活，软件工程师和架构师将看到许多巨大的可能性和巨大的潜力。然后，让我们探索一些似乎塑造当前汽车软件工程的趋势。特别是让我们探索以下趋势：

- Autonomous driving—how the introduction of autonomous driving shapes the automotive sector and the software needed to steer cars.
- Self-how the ability to develop self-healing and self-adaptive systems influences the way in which we can design software in modern cars.
- Big data—how the ability to communicate and process large quantities of data changes the way we think about decision making in cars.
- New software development paradigms—how new software engineering methods influence the way we develop software for automotive systems.

> - **自动驾驶**的引入如何塑造汽车行业和驾驶汽车所需的软件。
> - 开发**自我修复和自适应系统**的能力如何影响我们在现代汽车中设计软件的方式。
> - **大数据** - 沟通和处理大量数据的能力如何改变我们对汽车决策的思考方式。
> - 新的软件**开发范式**新的软件工程方法如何影响我们为汽车系统开发软件的方式。

In the remainder of this chapter we go through these trends.

## Autonomous Driving

Undoubtedly the main trend in modern software in cars’ is autonomous driving software. Autonomous driving software allows drivers to skip controlling the car or some of its functions. The NHSTA (National Highway Safety Traffic Administration) in the United States recognizes the following levels of autonomous functionality in cars [[A13](#_bookmark699)]:

> 毫无疑问，现代汽车软件的主要趋势是自动驾驶软件。自动驾驶软件允许驾驶员跳过控制汽车或其某些功能。美国国家公路安全交通管理局(NHSTA)承认汽车的自主功能级别如下[[A13](#_bookmark699)]：

> [!note]
> 自动驾驶分级

- Level 0, No automation—there are no functions in the car that can drive the car or support the driver.
- Level 1, Function-specific automation—according to the definition `automation at this level involves one or more specific control functions` , meaning that certain functions can be autonomous, e.g. adaptive cruise control.
- Level 2, Combined function automation—where a group of functions can be automated and be autonomous. The driver, however, is still responsible for the control of the vehicle and must be prepared to take control of the vehicle on very short notice. Example functions are self-driving on highways.
- Level 3, Limited self-driving automation—the vehicle is able to drive autonomously under certain conditions and monitor the conditions; the drivers might need to occasionally take control, but the transition time is comfortably longer than at Level 2.
- Level 4, Full self-driving automation—the vehicle is able to perform the entire trip autonomously; the driver is only expected to enter constraints and the destination for the trip. The level applies to both manned and unmanned vehicles.

> - 0 级，无自动化汽车中没有可以驱动汽车或支持驾驶员的功能。
> - 级别 1，根据定义 `此级别的自动化涉及**一个或多个特定控制功能**` 的功能特定自动化，这意味着某些功能可以是自主的，例如自适应巡航控制。
> - 第 2 级，组合功能自动化，**其中一组功能可以自动化和自主**。然而，**驾驶员仍然负责车辆的控制**，必须做好准备，以便在极短的时间内控制车辆。示例功能是高速公路上的自动驾驶。
> - 3 级，有限的自动驾驶自动化-车辆能够**在特定条件下自动驾驶并监控条件；驾驶员可能需要偶尔进行控制**，但过渡时间比 2 级时长得多。
> - 第 4 级，**全自动驾驶-车辆能够自主完成整个行程**；驾驶员**只需要输入行程的约束和目的地**。该级别适用于载人和无人驾驶车辆。

One can see that modern vehicles already provide functions for automation Level 2 (combined function automation) and some even for Level 3 (e.g. Tesla’s autopilot functionality, [[Pas14](#_bookmark716), [Kes15](#_bookmark709)]). This kind of functionality puts a lot of constraints on the automotive software.

> 我们可以看到，现代车辆已经提供了自动化 2 级(组合功能自动化)的功能，有些甚至提供了 3 级(例如特斯拉的自动驾驶功能，[[Pas14](#_bookmark716)，[Kes15](#_bbookmark709)])。这种功能给汽车软件带来了很多限制。

First of all, this drives the complexity of software and therefore the cost of its development, verification, validation and certification. As the self-driving functionality is safety-critical it requires specific validation. It also requires complex reasoning in traffic situations on a very abstract level—e.g. whether it is better to save lives of the car’s passengers or the lives of others in the accident.

> 首先，这驱动了软件的复杂性，因此驱动了其开发，验证，验证和认证的成本。由于自动驾驶功能是安全至关重要的，因此需要特定的验证。它还需要在非常抽象的层面上在流量情况下进行复杂的推理 - 例如。无论是在事故中挽救汽车乘客的生命还是其他人的生命。

Second of all, this kind of functionality drives the need for large quantities of data to process, which drives the need for processing power in modern cars. The processing power requires efficient CPUs and electronic buses of high throughput, which require more advanced infrastructure (e.g. cooling fans), that is often susceptible to environmental influences such as vibrations, humidity and temperature. This

> 其次，这种功能推动了对大量数据进行处理的需求，这驱动了现代汽车中处理能力的需求。处理能力需要有效的 CPU 和高通量的电子总线，这需要更先进的基础设施(例如冷却风扇)，这通常会受到环境影响，例如振动，湿度和温度。这个

1. Self-261 means that new components need to be develop especially for the cars, which drives costs.

> 1.Self-261 意味着需要开发新的部件，特别是汽车，这会增加成本。

Third of all, we need to understand that the quality of the sensors today is insufficient for advanced scenarios. Cameras are able to see clearly in specific conditions, but the human eye is still better synchronized with the human brain in all situations. Therefore cameras are not able to work effectively in low light or bad weather conditions [[KTI05](#_bookmark710)]. Using high-end cameras and sophisticated equipment would drive up the cost and still not guarantee the same quality as from human eyes and brains.

> 第三，我们需要了解，目前传感器的质量不足以满足高级场景。相机能够在特定条件下清晰地看到，但人眼在所有情况下都能更好地与人脑同步。因此，**相机无法在光线不足或恶劣天气条件下有效工作**[[KTI05](#_bookmark710)]。使用高端相机和精密设备会提高成本，**但仍不能保证与人眼和大脑相同的质量**。

And finally, this kind of autonomous functionality requires acting on higher abstraction levels. Information about distance to the nearest obstacle needs to be transformed to a worldview which can be compared to a map view to determine the best course of action in a specific situation [[BT16](#_bookmark703)]. This requires more advanced algorithms which can be based on heuristics. The heuristics, however, are very challenging to prove to work correctly in all kinds of traffic situations, thus posing problems for safety certification.

> 最后，这种自治功能需要在更高的抽象级别上进行操作。需要将有关到最近障碍物的距离的信息转换为世界视图，该世界视图可以与地图视图进行比较，以确定特定情况下的最佳行动方案[[BT16](#_bookmark703)]。这需要更先进的算法，这些算法可以基于启发式。然而，要证明启发式算法在各种交通情况下都能正确工作，这是非常具有挑战性的，因此给安全认证带来了问题。

## Self

Self-healing is the ability of the system to autonomously change its structure so that its behaviour stays the same. An example concept of self-healing can be seen in the work of Keromytis et al. [[Ker07](#_bookmark708)], who define the self-healing as the ability to autonomously recover from erroneous execution.

> 自我修复是系统**自主改变其结构，使其行为保持不变的能力**。Keromytis 等人[[Ker07](#_bookmark708)]的工作中可以看到自愈的示例概念，他们将自愈定义为从错误执行中自主恢复的能力。

One of the most prominent mechanisms used in self-healing systems is the MAPE-K (Measure, Analyse, Plan and Execute + Knowledge, [[MNS05](#_bookmark713)]). It is shown in Fig. [11.1](#_bookmark691) as an overwatch algorithm for an ECU realizing the adaptive cruise control functionality.

> 自愈系统中使用的最突出的机制之一是 MAPE-K(测量、分析、计划和执行 + 知识，[[MNS05](#_bookmark713)])。如图 [11.1](#_bookmark691) 所示，它是实现自适应巡航控制功能的 ECU 的监视算法。

The algorithm in short is based on monitoring the execution of the algorithm for correctness. In the example of adaptive cruise control, we can monitor the radar to confirm it provides reliable results (e.g. no distortion is present). The analysis component checks whether one of the failure conditions has been detected (e.g. too much noise in the radar readings) and sends a signal to the plan component which plans appropriate action based on the reading and analysis. One of the actions can be to disable the adaptive cruise control and inform the user. Once the component makes a decision about the recovery strategy it moves to the execution and executes the repair strategy (i.e. informs the user and disables the adaptive cruise control algorithm).

> 简而言之，该算法基于监视算法的正确性执行。在自适应巡航控制的示例中，我们可以监控雷达以确认它提供了可靠的结果(例如，不存在失真)。分析组件检查是否检测到故障条件之一(例如，雷达读数中的噪声太大)，并向计划组件发送信号。其中一个动作可以是禁用自适应巡航控制并通知用户。一旦组件做出关于恢复策略的决定，它就转到执行并执行修复策略(即通知用户并禁用自适应巡航控制算法)。

This trend of using self-adaptation is used increasingly in safety-critical systems as it allows us to change the operation of a component in the presence of errors and failures. It can provide the ability to the system to self-degrade the functionality (e.g. temporarily change the operation of the engine, as discussed in Chap. [6](#_bookmark368)).

> 这种使用自适应的趋势越来越多地用于安全关键系统，因为它允许我们在出现错误和故障时改变组件的操作。它可以为系统提供自我降级功能的能力(例如，如第[6]章(#_bookmark368)所述，暂时改变发动机的操作)。

However, there are still challenges which need to be addressed in order to make self-adaptation even more applicable to automotive systems. One of the major challenges is the ability to prove that the system is `safe` (in the sense of ISO/IEC 26262) during self-adaptation. Another is the fact that self-adaptation algorithms can be complex and need to be validated, but in many situations the failure modes cannot be replicated in real life. For example, it is difficult to safely replicate the situation where a radar in adaptive cruise control is broken when a vehicle drives at 150 km/h.

> 然而，为了使自适应更适用于汽车系统，仍有一些挑战需要解决。主要挑战之一是证明系统在自适应过程中是 `安全的` (在 ISO/IEC 26262 的意义上)的能力。另一个事实是，自适应算法可能很复杂，需要验证，但在许多情况下，故障模式无法在现实生活中复制。例如，当车辆以 150 公里/小时的速度行驶时，很难安全地复制自适应巡航控制中的雷达损坏的情况。

<**Fig. 11.1** Realization of MAPE-K for ECU software

Nevertheless, we can perceive more self-algorithms entering automotive systems as they need to monitor the increasingly complex decision algorithms in modern cars (e.g. related to autonomous driving).

> 然而，我们可以看到更多的自算法进入汽车系统，因为它们需要监控现代汽车中日益复杂的决策算法(例如，与自动驾驶相关)。

## Big Data

With the ability of modern cars to communicate with each other and the ability to use their own sensors in decision making, the amount to data used in modern cars has increased exponentially. At the same time, the field of computer science has evolved and started to tackle challenges related to storing, analysing and processing large quantities of data [[MCB11](#_bookmark711), [MSC13](#_bookmark715)].

> 随着现代汽车相互通信的能力以及在决策中使用自己的传感器的能力，现代汽车中使用的数据量呈指数级增长。与此同时，计算机科学领域已经发展并开始应对与存储、分析和处理大量数据相关的挑战[[MCB11](#_bookmark711)，[MSC13](#_bbookmark715)]。

Big Data systems are often characterized by the so-called five Vs:

> 大数据系统通常以所谓的五个 Vs 为特征：

- Volume—big data systems have large amounts of data (e.g. teraor petabytes), which makes storage and processing a challenging task requiring new types of algorithms.

1. Big Data 263

- Variety—the data comes from heterogeneous sources, has different formats, and has multiple semantic models, which require preprocessing before the data can be fed to analysis algorithms.

> - 多样性 - 数据来自异质来源，具有不同的格式，并且具有多种语义模型，这些模型需要进行预处理，然后才能将数据馈送到分析算法。

- Velocity—the data is provided at high speeds and requires processing realtime (e.g. from multiple sensors in the car and needs to be used to make safetycritical decisions). The speed requires large processing power, which might not be available in such systems as the automotive software.

> - 速度 - 数据以高速提供，需要实时处理(例如，来自汽车中的多个传感器，需要用于做出安全 - 关键决策)。速度需要大型处理能力，在汽车软件等系统中可能无法使用。

- Value—the data collected has some business value (e.g. data about the driving routines of cars) which makes the storage, privacy and security issues challenging, especially in combination with the velocity of processing and the next V—veracity.

> - 价值 - 收集的数据具有一些业务价值(例如，有关汽车驾驶程序的数据)，这使存储，隐私和安全问题 CHALENGING，尤其是与处理速度和下一个 V-栅极性相结合。

- Veracity—the data has varying degree of quality, e.g., in terms of accuracy and trustworthiness. This varying degree of accuracy makes it challenging for the systems to use.

> - 真实性 - 数据具有不同程度的质量，例如，就准确性和可信度而言。这种不同程度的准确性使系统使用挑战。

The challenges of using big data in automotive systems are related to all of the above V’s. The large volume of data which comes from the car’s own sensors needs to be processed and often stored, which puts requirements on storage in cars. Before the popularization of the SSD (Solid State Disk) technology it was rather challenging to use hard disks to store data (durability problems due to vibrations). Now, it is possible to store more data and also to process more data.

> 在汽车系统中使用大数据的挑战与上述所有 V 有关。需要处理和经常存储来自汽车自身传感器的大量数据，这使汽车存储要求。在普及 SSD(固态磁盘)技术之前，使用硬盘存储数据(由于振动引起的耐用性问题)是非常具有挑战性的。现在，可以存储更多数据并处理更多数据。

The high speed of processing requires more processing power, more efficient processors which take power and more connectivity. This drives the cost of automotive hardware since the more efficient processors require more infrastructure (stability, cooling), which is prone to problems in the automotive environment (humidity, vibrations). The hardware price is so important in the automotive domain (as opposed to other domains, where hardware is considered cheap) that one usually takes a calculation (a rule of thumb) that one dollar more expensive hardware per ECU can lead to 100 dollars more expensive cars.

> 高速处理需要更多的处理能力、更高效的处理器，这些处理器需要更多的功率和更多的连接。这提高了汽车硬件的成本，因为更高效的处理器需要更多的基础设施(稳定性、冷却)，这在汽车环境中容易出现问题(湿度、振动)。硬件价格在汽车领域非常重要(与其他领域相比，硬件被认为是廉价的)，因此人们通常需要计算(经验法则)，每个 ECU 一美元的昂贵硬件可以导致 100 美元的昂贵汽车。

The veracity of the data is a challenge as in many cases the `true` values cannot be measured but computed. For example, the slippage of the road in winter conditions cannot be measured but are derived either from ABS usage or the steering wheel friction. In some cases the data is obfuscated in order to secure privacy (e.g. triangulation algorithms to hide the true position of a car), which prevent the algorithms from `knowing` the true value of the data point [[SS16](#_bookmark725)].

> 数据的准确性是一个挑战，因为在许多情况下，`真实` 值无法测量，只能计算。例如，无法测量冬季条件下的路面滑移，而是由 ABS 使用情况或方向盘摩擦得出的。在某些情况下，为了保护隐私，数据被混淆(例如，隐藏汽车真实位置的三角测量算法)，这防止算法 `知道` 数据点的真实值[[SS16](#_bookmark725)]。

In the future we will see more of big data, as large quantities of data are needed for autonomous driving and for advanced algorithms for collision prevention and avoidance.

> 在未来，我们将看到更多的大数据，因为自动驾驶和先进的碰撞预防和避免算法需要大量数据。

## New Software Development Paradigms

Software engineering for automotive systems has evolved the pace of the automotive domain. So, let us look into a few of the trends which shape the field today and will potentially shape the field in the future.

> 汽车系统的软件工程已经发展了汽车域的步伐。因此，让我们研究一些趋势，这些趋势塑造了当今的领域，并有可能在未来塑造该领域。

**Agility in Specification Development** Agile software development has been used in many domains outside of the automotive and now there is evidence that it is used increasingly in the automotive domain. In particular, at the lower part of the Vmodel suppliers work more agilely with their requirements engineering and software development [[MS04](#_bookmark714)]. We can also observe these trends scaling up to complete vehicle development [[EHLB14](#_bookmark706)] and [[MMSB15](#_bookmark712)]. With this increased adoption of Agile principles we can foresee the increased ability to specify requirements alongside software development, especially as the trends in automotive electronics increasingly contain more commodity (or off-the-shelf) components. AUTOSAR also prescribes a standardized approach to development, which eases the use of iterative development principles as the development of electronics/hardware is decoupled from the development of functions/software.

> **规范开发中的敏捷性**敏捷软件开发已经在汽车领域之外的许多领域中使用，现在有证据表明，它在汽车领域中的应用越来越多。特别是，在 Vmodel 的较低部分，供应商更灵活地进行需求工程和软件开发[[MS04](#_bookmark714)]。我们还可以观察到这些趋势，并将其扩展到完整的车辆开发[[EHLB14](#_bookmark706)]和[[MMSB15](#_bookmark712)]。随着越来越多地采用敏捷原则，我们可以预见在软件开发的同时指定需求的能力也会增加，特别是随着汽车电子产品的趋势越来越多地包含更多的商品(或现成的)组件。AUTOSAR 还规定了一种标准化的开发方法，它简化了迭代开发原则的使用，因为电子/硬件的开发与功能/软件的开发是分离的。

**Increased Focus on Traceability** The increased amount of software in cars and their increased presence in safety systems leads to stricter processes for keeping track of requirements for safety-critical systems. ISO 26262 (Road vehicles— Functional Safety) is one example of this. In the automotive domain this means that the increased complexity of software modules [[SRH15](#_bookmark724)] leads to more fine-grained traceability management. One of the enablers of this increased traceability is the increased integration between the tools—tool chaining [[BDT10](#_bookmark701)] and [[ABB12](#_bookmark700)].

> **增加对可追溯性的关注**汽车中软件数量的增加及其在安全系统中的存在，**导致更严格的流程来跟踪安全关键系统的要求。ISO 26262(道路车辆-功能安全)就是一个例子**。在汽车领域，这意味着软件模块[[SRH15](#_bookmark724)]的复杂性增加导致了更细粒度的可追溯性管理。提高可追溯性的一个促成因素是工具工具链[[BDT10](#_bookmark701)]和[[ABB12](#_bbookmark700)]之间的集成度提高。

**Increased Focus on Non-functional Properties** The increased use of software for active safety systems calls for increased focus on non-functional properties of software. The increased traffic on communication buses within the car, and the increased capacity of the communication buses call for more synchronization and verification. Safety analyses such as control path monitoring, safety bits and data complexity control, are just a few examples [[Sin11](#_bookmark721)]. As the focus of requirements engineering research in the automotive domain was mainly (or implicitly) in the functional requirements, we foresee an increased growth of research and emphasis on the non-functional requirements.

> **增加对非功能性属性的关注**主动安全系统中软件的使用增加，需要增加对软件非功能性的关注。车内通信总线的流量增加，通信总线的容量增加，需要更多的同步和验证。安全分析(如控制路径监控、安全位和数据复杂性控制)只是几个例子[[Sin11](#_bookmark721)]。由于汽车领域的需求工程研究的重点主要(或隐含)在功能需求方面，我们预计研究的增长和对非功能需求的重视会增加。

**Increased Focus on Security Requirements** A dedicated group of requirements is the security requirements, as our cars are increasingly connected and therefore prone to hacker attacks [[SLS13](#_bookmark722)] and [[Wri11](#_bookmark726)]. The recent demonstration of the possibility of steering a Jeep Wrangler vehicle offroad showed that the threat is real and related to the safety of cars and transport systems. We therefore perceive that the ability to prevent attacks will the focus of the automotive software development increasingly more in the coming decade.

> **更加关注安全要求**一组专门的要求是安全要求，因为我们的汽车连接越来越紧密，因此容易受到黑客攻击[[SLS13](#_bookmark722)]和[[Wri11](#_bookmark726)]。最近的演示表明，驾驶吉普牧马人越野车的可能性表明，这种威胁是真实的，与汽车和运输系统的安全有关。因此，我们认为，在未来十年，防止攻击的能力将越来越成为汽车软件开发的重点。

1. New Software Development Paradigms 265

### _Architecting in the Age of Agile Software Development_

Architecture development in software development is usually conducted by experienced architects, and the larger the product, the more the experience required. As each type of system has its specific requirements, the architectural design requires attention to specific aspects like realtime properties or extensibility. For example, in the telecom domain the extensibility and performance are the main aspects, whereas in the automotive domain it is safety and performance that are of the utmost priority. The architecture development efforts are dependent to some extent on the software development process adopted by the company, e.g. the architecture development methods differ in the V-model and Agile methodologies. In the Vmodel the architecture work is mostly prescriptive and centralized around the architects whereas in the Agile methods the work can be more descriptive and distributed into multiple self-organized teams.

> 软件开发中的架构开发通常由经验丰富的架构师进行，产品越大，所需的经验就越多。由于每种类型的系统都有其特定的需求，所以体系结构设计需要关注特定的方面，如实时属性或可扩展性。例如，在电信领域，可扩展性和性能是主要方面，而在汽车领域，安全性和性能则是最重要的。体系结构开发工作在一定程度上取决于公司采用的软件开发过程，例如，体系结构开发方法在 V 模型和敏捷方法中有所不同。在 Vmodel 中，体系结构工作主要是规范性的，集中在架构师周围，而在敏捷方法中，工作可以更具描述性，并分布到多个自组织的团队中。

As Agile software development principles spread in industry, architecture development evolved. As Agile development teams became self-organized, architecture work became more distributed and harder to control centrally [[Ric11](#_bookmark718)]. The difficulties stem from the fact that Agile teams value independence and creativity

> 随着敏捷软件开发原则在行业中的传播，架构开发也随之发展。随着敏捷开发团队的自我组织，架构工作变得更加分散，难以集中控制[[Ric11](#_bookmark718)]。困难源于敏捷团队重视独立性和创造力

[[SBB09](#_bookmark720)] whereas architecture development requires stability, control, transparency and proactivity [[PW92](#_bookmark717)]. Figure [11.2](#_bookmark695) presents an overview of how the functional requirements (FR) and non-functional requirements (NFR) are packaged into work packages and developed as features by teams. Each team delivers code to the main branch. Each team has the possibility to deliver the code to any component of the product.

> [[SBB09](#_bookmark720)]而体系结构开发需要稳定性、控制力、透明度和主动性[[PW92](#_bbookmark717)]。图 [11.2](#_bookmark695) 概述了功能需求(FR)和非功能需求(NFR)如何打包成工作包，并由团队开发为功能。每个团队向主分支交付代码。每个团队都有可能将代码交付给产品的任何组件。

![](./media/image430.jpeg)
<**Fig. 11.2** Feature development in Lean/Agile methods

The requirements come from the customers and are prioritized and packaged into features by product management (PM), which communicates with system management (SM) on the technical aspects of how the features affect the architecture of the product. System management communicates with the teams (DM, Test) that design, implement and test (functional testing) the feature before delivering it to the main branch. The code in the main branch is tested thoroughly by dedicated test units before being release [[SM11](#_bookmark723)].

> 需求来自客户，由产品管理(PM)确定优先级并打包成功能，产品管理与系统管理(SM)就功能如何影响产品架构的技术方面进行沟通。系统管理与设计、实施和测试(功能测试)功能的团队(DM、测试)进行沟通，然后将其交付给主要分支。主分支中的代码在发布[[SM11](#_bookmark723)]之前由专用测试单元进行了彻底测试。

## Other Trends

Bosch has presented three trends which shaped software engineering in the mid2010s [[Bos16](#_bookmark702)]: speed of software development, ecosystems and data-driven development. He predicted that the companies which are the first ones on the market would be more successful than others as the innovation model is based on the shark’s tail rather than the traditional technology adoption curve. In particular, the majority of new, innovative software products are adopted by the market at a tremendous pace, and then companies need to be prepared to be ready for the market. Followers do not have the same ability to attract customers [[DN14](#_bookmark705)]. Ecosystem thinking (e.g. Apple’s App store or Google’s Play store) has been present in the automotive sector from way back in the hardware domain (e.g. customers of BMW are bound to buy spare parts from manufacturer) but not in the software domain. And finally we have data-driven development and the Lean innovation thinking [[Rie11](#_bookmark719)] where customers provide the companies with the data on how to develop their products. With connected cars and the ability to update the car software over the air we will probably see more data-driven development in the automotive industry in the coming decade.

> Bosch 在 2010 年代中期提出了三个影响软件工程的趋势[[Bos16](#_bookmark702)]：**软件开发速度、生态系统和数据驱动开发**。他预测，由于创新模式是基于鲨鱼尾巴而不是传统的技术采用曲线，市场上最早上市的公司将比其他公司更成功。特别是，大多数新的、创新的软件产品以惊人的速度被市场采用，然后公司需要为市场做好准备。
> 追随者不具备吸引客户的能力[[DN14](#_bookmark705)]。
> **生态系统思维**(例如，苹果的应用商店或谷歌的 Play 商店)早在硬件领域就已经出现在汽车行业(例如，宝马的客户必须从制造商那里购买零部件)，但在软件领域却没有。
> 最后，我们有数据驱动的开发和精益创新思维[[Rie11](#_bookmark719)]，客户向公司提供如何开发产品的数据。有了联网的汽车和通过无线更新汽车软件的能力，我们可能会在未来十年看到汽车行业更多的数据驱动发展。

Burton and Willis from Gartner identified five mega-trends which have the potential of shaping software engineering in the coming decades [[BW15](#_bookmark704)]. These mega-trends are:

> 来自 Gartner 的 Burton 和 Willis 确定了五个大型趋势，它们具有在未来几十年[[BW15](#_bookmark704)]中塑造软件工程的潜力。这些大型趋势是：

- Digital Business Moves Toward the Peak of Inflated Expectations
- IoT, Mobility and Smart Machines Rapidly Approach the Peak
- Digital Marketing and Digital Workplace Quickly Move Up
- Analytics Are at the Peak
- Big Data and Cloud Make Big Moves Toward the Trough of Disillusionment

> - 数字业务走向膨胀预期的顶峰
> - 物联网、移动和智能机器快速接近顶峰
> - 数字营销和数字工作场所快速上升
> - 分析处于顶峰
> - 大数据和云向幻灭低谷迈进

In short, these trends will drive the need for more advanced functionality of cars and the use of big data for decision making and even the development of the cars (finding out the requirements from the data rather than focus group interviews). However, they predict that the era of wearables (e.g. smartwatches) will reach the so-called `pit of disillusion` where they will probably reach the state where no more development is of interest to the customers.

> 简而言之，这些趋势将推动人们对汽车更先进功能的需求，并将大数据用于决策甚至汽车开发(从数据中找出需求，而不是焦点小组访谈)。然而，他们预测，可穿戴设备(如智能手表)的时代将达到所谓的 `幻灭之坑` ，届时他们可能会达到客户不再感兴趣的状态。

In their 2016 report, Gartner Associates provide even more focus on Artificial Intelligence, Machine Learning and autonomy. We perceive these technologies as new hype in automotive software engineering, especially when combined with different levels of autonomy and self-adaptation algorithms. This will mean even more complexity and software in future cars.

> 在 2016 年的报告中，Gartner Associates 更加关注**人工智能、机器学习和自主性**。我们将这些技术视为汽车软件工程中的新炒作，尤其是与不同级别的自主性和自适应算法相结合时。这将意味着未来汽车更加复杂和软件化。

## Summary

To conclude this chapter let us make a speculation that future cars will be more like computer platforms where different third party companies can build applications. We can see the self-driving car of Google as an example of such a move [[Gom16](#_bookmark707)].

> 总结本章，让我们猜测未来的汽车将更像是计算机平台，不同的第三方公司可以构建应用程序。我们可以看到 Google 的自动驾驶汽车，这是这样的举动[[GOM16](#_bookmark707)]。

The telecommunication domain has evolved from proprietary solutions in mobile phones of the 1990s to standardized platforms and ecosystems of the smartphones of the 2010s—Android and iOS leading the field in this direction. Customers buying a new mobile phone buy a device which they can load with apps of their own choice— some free and some paid. We can see that the ability to update car’s software will lead to similar trends (already visible in the infotainment domain).

> 电信领域已经从 20 世纪 90 年代的移动电话专有解决方案发展到 2010 年代 Android 和 iOS 智能手机的标准化平台和生态系统，在这一领域处于领先地位。购买新手机的客户购买的设备可以加载自己选择的应用程序，有些是免费的，有些是付费的。我们可以看到，更新汽车软件的能力将导致类似的趋势(在信息娱乐领域已经可见)。

These possibilities of opening up for third party software in cars is expected to change the face of the automotive industry in the future. Commoditizing platforms and portability between vendors on the application level can cause cars to become much safer and much more fun. We can expect the cars to become hubs for all kinds of devices and integrated with wearables to provide drivers and passengers with an even better driving experience than today’s. We need to live and see what the future of software in cars will bring.

> 这些为汽车中的第三方软件开放的可能性有望改变未来汽车行业的面貌。在应用程序级别上对平台进行商业化和供应商之间的可移植性可以使汽车变得更加安全和有趣。我们可以期待这些汽车成为各种设备的枢纽，并与可穿戴设备集成，为驾驶员和乘客提供比现在更好的驾驶体验。我们需要生活，看看汽车软件的未来会带来什么。

## References

A+13. National Highway Traffic Safety Administration et al. Preliminary statement of policy concerning automated vehicles. _Washington, DC_, pages 1–14, 2013.

ABB+ 12. Eric Armengaud, Matthias Biehl, Quentin Bourrouilh, Michael Breunig, Stefan Farfeleder, Christian Hein, Markus Oertel, Alfred Wallner, and Markus Zoier. Integrated tool chain for improving traceability during the development of automotive systems. In _Proceedings of the 2012 Embedded Real Time Software and Systems Conference_, 2012.

BDT10. Matthias Biehl, Chen DeJiu, and Martin Törngren. Integrating safety analysis into the model-based development toolchain of automotive embedded systems. In _ACM Sigplan Notices_, volume 45, pages 125–132. ACM, 2010.

Bos16. Jan Bosch. Speed, data, and ecosystems: The future of software engineering. _IEEE Software_, 33(1):82–88, 2016.

BT16. Sagar Behere and Martin Törngren. A functional reference architecture for autonomous driving. _Information and Software Technology_, 73:136–150, 2016.

BW15. Betsy Burton and David A Willis. Gartners Hype Cycles for 2015: Five Megatrends Shift the Computing Landscape. _Recuperado de: [https:// www.gartner.com/ doc/](https://www.gartner.com/doc/3111522/gartners--hype--cycles--megatrends--shift) [3111522/ gartners--hype--cycles--megatrends shift](https://www.gartner.com/doc/3111522/gartners--hype--cycles--megatrends--shift)_, 2015.

DN14. Larry Downes and Paul Nunes. _Big Bang Disruption: Strategy in the Age of Devastating Innovation_. Penguin, 2014.

EHLB14. Ulf Eliasson, Rogardt Heldal, Jonn Lantz, and Christian Berger. Agile modeldriven engineering in mechatronic systems-an industrial case study. In _Model-Driven Engineering Languages and Systems_, pages 433–449. Springer, 2014.

Gom16. Lee Gomes. When will Google’s self-driving car really be ready? It depends on where you live and what you mean by `ready` [News]. _IEEE Spectrum_, 53(5):13–14, 2016.

Ker07. Angelos D Keromytis. Characterizing self-healing software systems. In _Proceedings of the 4th international conference on mathematical methods, models and architectures for computer networks security (MMM-ACNS)_, 2007.

Kes15. Aaron M Kessler. Elon Musk Says Self-Driving Tesla Cars Will Be in the US by Summer. _The New York Times_, page B1, 2015.

KTI+ 05. Hiroyuki Kurihata, Tomokazu Takahashi, Ichiro Ide, Yoshito Mekada, Hiroshi Murase, Yukimasa Tamatsu, and Takayuki Miyahara. Rainy weather recognition from invehicle camera images for driver assistance. In _IEEE Proceedings. Intelligent Vehicles Symposium, 2005._, pages 205–210. IEEE, 2005.

MCB+11. James Manyika, Michael Chui, Brad Brown, Jacques Bughin, Richard Dobbs, Charles Roxburgh, and Angela H Byers. Big data: The next frontier for innovation, competition, and productivity. 2011.

MMSB15. Mahshad M Mahally, Miroslaw Staron, and Jan Bosch. Barriers and enablers for shortening software development lead-time in mechatronics organizations: A case study. In _Proceedings of the 2015 10th Joint Meeting on Foundations of Software Engineering_, pages 1006–1009. ACM, 2015.

MNS+05. Edson Manoel, Morten Jul Nielsen, Abdi Salahshour, Sai Sampath K.V.L., and Sanjeev Sudarshanan. _Problem determination using self-managing autonomic technology_. IBM International Technical Support Organization, 2005.

MS04. Peter Manhart and Kurt Schneider. Breaking the ice for agile development of embedded software: An industry experience report. In _Proceedings of the 26th international Conference on Software Engineering_, pages 378–386. IEEE Computer Society, 2004.

MSC13. Viktor Mayer-Schönberger and Kenneth Cukier. _Big data: A revolution that will transform how we live, work, and think_. Houghton Mifflin Harcourt, 2013.

Pas14. A Pasztor. Tesla unveils all-wheel-drive, autopilot for electric cars. _The Wall Street Journal_, 2014.

PW92. Dewayne E Perry and Alexander L Wolf. Foundations for the study of software architecture. _ACM SIGSOFT Software Engineering Notes_, 17(4):40–52, 1992.

Ric11. Eric Richardson. What an agile architect can learn from a hurricane meteorologist. _IEEE software_, 28(6):9–12, 2011.

Rie11. Eric Ries. _The lean startup: How today’s entrepreneurs use continuous innovation to create radically successful businesses_. Random House LLC, 2011.

SBB+ 09. Helen Sharp, Nathan Baddoo, Sarah Beecham, Tracy Hall, and Hugh Robinson. Models of motivation in software engineering. _Information and Software Technology_, 51(1):219–233, 2009.

Sin11. Purnendu Sinha. Architectural design and reliability analysis of a fail-operational brake-by-wire system from ISO 26262 perspectives. _Reliability Engineering & System Safety_, 96(10):1349–1359, 2011.

SLS+ 13. Florian Sagstetter, Martin Lukasiewycz, Sebastian Steinhorst, Marko Wolf, Alexandre Bouard, William R Harris, Somesh Jha, Thomas Peyrin, Axel Poschmann, and Samarjit Chakraborty. Security challenges in automotive hardware/software architecture design. In _Proceedings of the Conference on Design, Automation and Test in Europe_, pages 458–463. EDA Consortium, 2013.

SM11. Miroslaw Staron and Wilhelm Meding. Monitoring Bottlenecks in Agile and Lean Software Development Projects–A Method and Its Industrial Use. _Product-Focused Software Process Improvement_, pages 3–16, 2011.

SRH15. Miroslaw Staron, Rakesh Rana, and Jörgen Hansson. Influence of software complexity on ISO/IEC 26262 software verification requirements. 2015.

SS16. Miroslaw Staron and Riccardo Scandariato. Data veracity in intelligent transportation systems: the slippery road warning scenario. In _Intelligent Vehicles Symposium_, 2016.

Wri11. Alex Wright. Hacking cars. _Communications of the ACM_, 54(11):18–19, 2011.
