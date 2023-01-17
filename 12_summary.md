# Summary

**Abstract** In this book we have introduced the concept of `software architecture` in automotive software and overviewed different architectural styles that can be encountered in modern automotive software. In this chapter we present the summary of the main points of the book and pinpoint additional reading in the area.

> **摘要**在本书中，我们介绍了汽车软件中 `软件架构` 的概念，并概述了现代汽车软件中可能遇到的不同架构风格。在本章中，我们总结了本书的要点，并指出了该领域的其他阅读内容。

## Software Architectures in General and in the Automotive Software—A Short Recap(通用和汽车软件中的软件体系结构——简要回顾)

Software architecture is a high level design and organization of the software system. It provides guidelines for the detailed design of the software, its components and their deployment. It is usual that software architecture documentation contains a number of different viewpoints, such as the functional viewpoint, the logical viewpoints, or the deployment one.

> 软件体系结构是软件系统的高级设计和组织。它为软件，其组件及其部署的详细设计提供了指南。通常，软件体系结构文档包含许多不同的观点，例如功能观点，逻辑观点或部署。

As the software architecture also provides the principles of the high-level organization of the software system, they often include different architectural styles. In general, we could observe over 20 different styles which are often accompanies by over 20 different patterns. However, in the automotive software design only some of these styles and patterns are applicable.

> 由于软件体系结构还提供了软件系统高级组织的原理，因此它们通常包括不同的建筑风格。通常，我们可以观察到 20 多种不同的样式，这些样式通常伴随 20 多种不同的模式。但是，在汽车软件设计中，仅适用其中一些样式和图案。

In this book we collected the most important methods and tools for the design of automotive software—both at the architectural level and at a detailed design level. In this chapter we provide a short summary of each chapter and briefly outline why this knowledge is important for the future of the automotive software engineering.

> 在本书中，我们收集了用于设计汽车软件设计的最重要的方法和工具，即在建筑层面和详细的设计层面上。在本章中，我们提供了每章的简短摘要，并简要概述了为什么此知识对于汽车软件工程的未来很重要。

## Chapter [2](#_bookmark54)—Software Architectures

In the second chapter of this book we introduced the notion of software architecture as `high level structures of a software system, the discipline of creating such structures, and the documentation of these structures`. We have introduced the notion of software component and discussed a set of architectural viewpoints which are common in the design of the automotive software systems, such as:

> 在本书的第二章中，我们介绍了软件体系结构的概念，即 `软件系统的高级结构、创建此类结构的原则以及这些结构的文档` 。我们已经介绍了软件组件的概念，并讨论了汽车软件系统设计中常见的一组架构观点，例如：

- Functional view—describing the architecture of the functions of the vehicle and the dependency between them
- Physical view—describing the physical nodes (ECUs) and their connections
- Logical view—describing the software components and their organization, and
- Deployment view—describing the deployment of software components onto the ECUs

> - 功能视图 - 描述车辆功能的架构以及它们之间的依赖关系
> - 物理视图 - 描述物理节点(ECU)及其连接
> - 逻辑视图 - 描述软件组件及其组织，以及
> - 部署视图 - 描述 将软件组件部署到 ECU

We have also exemplified the main architectural styles present in the automotive sector:

> 我们还举例说明了汽车领域中存在的主要建筑风格：

- Layered architecture
- Component-based architecture
- Monolithic architecture
- Microkernel architecture
- Pipes and filters architecture
- Event-driven architecture, and
- Middleware architecture with message brokers

> - 分层架构
> - 基于组件的架构
> - 单体架构 >
> - 微内核架构
> - 管道和过滤器架构
> - 事件驱动架构
> - **具有消息代理的中间件架构**

The knowledge contained in Chap. [2](#_bookmark54) prepares us to start designing software systems at a very high level. In order to be effective we need to understand how the automotive software development is done, and therefore we describe it in the next chapter.

> Chap 中包含的知识。[2](#_bookmark54) 我们准备开始以很高的水平设计软件系统。为了有效，我们需要了解如何进行汽车软件开发，因此我们在下一章中进行了描述。

## Chapter [3](#_bookmark154)—Contemporary Software Architectures: Federated and Centralized(当代软件架构：联合和集中)

When describing the architectural styles, we focus on the principle governing each architectural style. However, a modern software system combines several styles. In this chapter, we look at the principles of designing the entire system and how the modern automotive software is organized.

> 在描述建筑风格时，我们专注于管理每种建筑风格的原则。但是，现代软件系统结合了几种样式。在本章中，我们研究了设计整个系统以及如何组织现代汽车软件的原理。

In Chap. [3](#_bookmark154), we explore examples of two architectural styles used in contemporary automotive software—federated and centralized software architectures. The federated architectures are organized into domains where each domain is independent from each other and contains a dedicated domain controller—a larger coordinating node. The centralized architectures are characterized by a large node at the center of the architecture. This node uses redundancy mechanisms and virtualization to ensure that the software is safe and reliable. It is also complemented with coordinating nodes to reduce the communication buses with ECUs on the edge of the vehicle’s network.

> 在第一章 [3](#_bookmark154)，我们探索了当代汽车软件中使用的两种架构风格的示例——联合和集中式软件架构。联合架构被组织成域，其中每个域彼此独立并包含一个专用域控制器——一个更大的协调节点。集中式架构的特点是架构中心有一个大节点。该节点使用冗余机制和虚拟化来确保软件安全可靠。它还辅以协调节点，以减少与车辆网络边缘 ECU 的通信总线。

We show examples of how systems are designed according to these styles and how they evolve. Towards the end of the chapter, we provide an example of design of an automated parking function, which is based on a real design, simplified for the purpose of this book.

> 我们展示了如何根据这些样式设计系统以及它们如何发展的示例。在本章结束时，我们提供了一个自动停车功能设计的示例，该设计基于真实的设计，简化了本书的目的。

## Chapter [4](#_bookmark185)—Automotive Software Engineering(汽车软件工程)

When describing the automotive software engineering practices, we start with the description of requirements, which are a bit specific for the automotive software. We discuss the following types of requirements:

> 在描述汽车软件工程实践时，我们从对需求的描述开始，这对于汽车软件有点特定。我们讨论以下要求：

- Textual requirements—specifications which are done in form of free text or tables
- Use case requirements—specifications which are based on UML Use cases and the corresponding sequence diagrams
- Model-based requirements—specifications which are done in form of models that should be implemented by suppliers
- 文本需求——以自由文本或表格形式完成的规格说明
- 用例需求——基于 UML 用例和相应序列图的规格说明
- 基于模型的需求——以模型形式完成的规格说明 由供应商实施

We need to understand the way in which requirements are done so that we understand the way in which software verification and validation is done. This verification and validation, done in form of testing, is discussed in the remaining of that chapter, where we introduce:

> 我们需要了解完成要求的方式，以便我们了解完成软件验证和验证的方式。该章节的其余部分讨论了以测试形式进行的验证和验证，我们介绍了：

- Unit testing—verification of the functionality of individual software modules
- Component testing—verification of groups of software modules—components
- System testing—verification of the complete system (both of its complete functionality and partial functionality during the course of the development), and
- Functional testing—validation of the end user functions against their specifications
- 单元测试——验证单个软件模块的功能
- 组件测试——验证软件模块组——组件
- 系统测试——验证整个系统(开发过程中的完整功能和部分功能)，
- 功能测试——根据最终用户的规范验证其功能

> [!note]
> 这个感觉就是对整个系统的验证，目前正缺少的

Once we introduce the different testing techniques, and the stages of integration of the software of a car, we discuss how these elements are stored in the so-called product databases.

> 一旦我们介绍了不同的测试技术以及汽车软件集成的阶段，我们就会讨论这些元素如何存储在所谓的产品数据库中。

## Chapter [5](#_bookmark273)—AUTOSAR

One of the major trends in today’s automotive software is the introduction of the AUTOSAR standard. The standard specifies how the automotive software is to be organized and how it should communicate with each other.

> 当今汽车软件的主要趋势之一是引入 Autosar 标准。该标准**指定如何组织汽车软件以及如何相互通信**。

This chapter has been written by Darko Durisic, who is one of the representatives of one of the Swedish OEMs in the AUTOSAR consortium. His research and expertise in the area resulted in a good introduction to the standard from the perspective of a software designer. The focus on the chapter is on the reference architecture provided by AUTOSAR and its implications.

> 本章是由 Darko Durisic 撰写的，Darko Durisic 是 Autosar 财团中瑞典 OEM 之一的代表之一。从软件设计师的角度来看，他在该领域的研究和专业知识使该标准很好地介绍了标准。对本章的重点是 Autosar 提供的参考体系结构及其含义。

## Chapter [6](#_bookmark368)—Detailed Design of Automotive Software

The discussion about automotive architectures would not be complete if we did not discuss the methods for detailed design of this software. In Chap. [5](#_bookmark273) we introduce a number of methods:

> 如果我们不讨论该软件详细设计的方法，那么关于汽车架构的讨论将无法完成。在第一章中。[5](#_bookmark273) 我们介绍了许多方法：

- Simulink modelling—probably the most widely used method for detailed design of algorithms in the automotive software, usually used in such domains as Powertrain and Active Safety or Chassi development.
- SysML—a UML based method for specifying the software focused on the concepts of the programming languages.
- EAST-ADL—another UML based method for designing the automotive software, combining the problem domain concepts with the programming/system level concepts.
- GENIVI—a standard for programming infotainment systems, which is currently gaining increasingly more popularity in the market.

> - Simulink 建模——可能是汽车软件中算法详细设计使用最广泛的方法，通常用于动力总成和主动安全或底盘开发等领域。
> - **SysML**——一种基于 UML 的方法，用于指定专注于编程语言概念的软件。
> - **EAST-ADL**——另一种基于 UML 的汽车软件设计方法，将问题域概念与编程/系统级概念相结合。
> - GENIVI——信息娱乐系统编程标准，目前在市场上越来越受欢迎。

> [!note]
> 这里给出了两种关于软件 UML 的，可以好好看一下

Knowing the notation is one thing, understanding the principles of the design of safety-critical systems is another. Therefore we introduce the principles of designing of safety critical systems based on the research from NASA and its space program.

> 知道符号是一件事，了解安全 - 关键系统设计的原理是另一回事。因此，我们根据 NASA 及其太空计划的研究介绍了设计安全关键系统的原理。

## Chapter [7](#_bookmark451)—Machine Learning in Automotive Software

Modern software systems contain an increasing amount of new technologies. One of these technologies is machine learning, which brings the power of artificial intelligence to the automotive software. In this chapter, we outline the main principles behind machine learning and how these non-deterministic algorithms can be integrated with the rest of the software components.

> 现代软件系统包含越来越多的新技术。这些技术之一是机器学习，它将人工智能的力量带入了汽车软件。在本章中，我们概述了机器学习背后的主要原理以及如何将这些非确定性算法与其他软件组件集成在一起。

In particular, we explore the supervised learning technology for image recognition and outline reinforced learning used for optimizations. We also discuss the principles behind on-board and off-board training.

> 特别是，我们探索了用于图像识别的监督学习技术，并用于优化的大纲增强学习。我们还讨论了车载和板外培训背后的原则。

## Chapter [8](#_bookmark493)—Evaluation of Automotive Software Architectures(汽车软件架构评估)

Once we introduce the detailed design we also discuss methods for evaluating software architectures. In Chap. [8](#_bookmark493) we focus on presenting methods based on qualitative evaluations—we focus on Architecture Trade-Off Analysis Method (ATAM).

> 介绍详细的设计后，我们还会讨论评估软件体系结构的方法。在第一章中。[8](#_bookmark493) 我们专注于基于定性评估的呈现方法 - 我们专注于建筑权衡分析方法(ATAM)。

12.10 Chapter [10](#_bookmark642)—Functional Safety of Automotive Software 273

> 12.10 第 [10](#_bookmark642) - 汽车软件的功能安全 273

We start the chapter by introducing the rationale for the evaluation of the architectures anchored in the international standard ISO/IEC 25000. We then describe the ATAM and provide a number of typical scenarios for evaluating safety critical systems.

> 我们通过介绍锚定在国际标准 ISO/IEC 25000 中的架构的理由来开始本章。然后，我们描述 ATAM 并提供许多用于评估安全关键系统的典型情况。

Finally we present an example evaluation of a simple architectural design.

> 最后，我们介绍了简单建筑设计的示例评估。

## Chapter [9](#_bookmark558)—Metrics for Software Designs and Architectures

To complement the methods presented in Chap. [6](#_bookmark368), we focus on methods based on quantitative measurements of software design. We introduce the international standard ISO/IEC 15939 for software measurement processes and we discuss abstraction levels of different metrics.

> 补充第一章中提出的方法。[6](#_bookmark368)，我们专注于基于软件设计定量测量的方法。我们介绍了用于软件测量过程的国际标准 ISO/IEC 15939，并讨论了不同指标的抽象水平。

We provide a set of measures used by software architects—an architect portfolio—and their visualizations. We also present a set of metrics for the detailed designs of the automotive software.

> 我们提供了软件架构师(建筑师投资组合)及其可视化的一组措施。我们还为汽车软件的详细设计提供了一组指标。

As an example in this chapter we present measurement results of publicly available industrial data set from one of the modern cars. Based on this open data we discuss the properties of the software such as its size or cyclomatic complexity. We reason what that means for the validation of software and its safety.

> 作为本章的一个例子，我们介绍了一辆现代汽车的公共工业数据集的测量结果。基于此开放数据，我们讨论了软件的属性，例如其大小或循环复杂性。我们认为这对于验证软件及其安全意味着什么。

This chapter is co-authored with Wilhelm Meding from Ericsson, who is a senior measurement program and team leader and has been working in this domain for more than 10 year.

> 本章与爱立信的威廉·梅丁(Wilhelm Meding)合着，他是一项高级测量计划和团队负责人，在这个领域工作了 10 年以上。

## Chapter [10](#_bookmark642)—Functional Safety of Automotive Software

Once we outlined the risks of not being able to fully validate the software once it becomes too complex, we move on and introduce one of the major standard in the automotive software today—ISO 26262 (functional safety).

> 一旦我们概述了一旦软件变得太复杂就无法完全验证该软件的风险，我们就继续前进并介绍当今汽车软件中的主要标准之一，即 ISO 26262(功能安全)。

This chapter was authored by Per Johannessen who was part of the introduction of the ISO 26262 standard to one of the OEMs of the passenger vehicles and is currently working on the same topic for heavy vehicles and buses.

> 本章是由 Johannessen 撰写的，他是 ISO 26262 标准的一部分，该标准是乘用车的 OEM 之一，目前正在为重型车辆和公共汽车进行同一主题。

As an example in this chapter we present an architecture of a microcontroller where the different ASILs are demonstrated.

> 作为本章的一个例子，我们介绍了一个微控制器的体系结构，其中展示了不同的 ASIL。

## Chapter [11](#_bookmark687)—Current Trends

Finally we close this book by outlining the current trends in the automotive software development. We outline the following trends:

> 最后，我们通过概述了汽车软件开发的当前趋势来结束这本书。我们概述了以下趋势：

- Autonomous driving—a trend which requires more complex software and higher degree of connectivity.
- Self-healing, self-adaptive, self-organizing systems—a trend which enables more reliable and smarter software, but is challenging in terms of safety assessment over time.
- Big data—a trend which enables the cars’ software to make smarter decisions based on the availability of information from external sources, at the same time putting requirements on the processing power, storage and other characteristics of the software system.
- New trends in software development—for example the trend of continuous integration of software which enables constant improvements of the software, but at the same time putting a lot of requirements on safety assessment and validation of the software on-the-fly.

> - 自动驾驶——一种需要更复杂的软件和更高程度的连接性的趋势。
> - 自我修复、自适应、自组织系统——这一趋势使软件更可靠、更智能，但随着时间的推移，在安全评估方面具有挑战性。
> - 大数据——一种使汽车软件能够根据外部来源信息的可用性做出更明智决策的趋势，同时对软件系统的处理能力、存储和其他特性提出要求。
> - 软件开发的新趋势——例如软件持续集成的趋势使软件能够不断改进，但同时对软件的安全评估和实时验证提出了很多要求。

## Closing Remarks

At this point we finish our journey through the automotive software development of the second decade of the second millennium. We see that we live in very dynamic times where the field of software engineering in the automotive sector just starts to grow and expand rapidly.

> 在这一点上，我们完成了第二个千年第二个十年的汽车软件开发的旅程。我们看到我们生活在非常动态的时期，在汽车领域的软件工程领域刚刚开始增长和扩展。

We hope that this book will help You, the reader to become a better software engineer and will help the cars to be smarter, better, more fun and above all—safer!

> 我们希望这本书能帮助您，读者成为一名更好的软件工程师，并帮助汽车变得更聪明，更好，更有趣，最重要的是！
