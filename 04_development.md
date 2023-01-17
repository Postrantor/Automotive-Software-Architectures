# Automotive Software Development(汽车软件开发)

**Abstract** In this chapter we describe and elaborate on software development pro- cesses in the automotive industry. We introduce the V-model for the entire vehicle development and we continue to introduce modern, agile software development methods for describing the ways of working of software development teams. We start by describing the beginning of all software development—requirements engineering—and we describe how requirements are perceived in automotive software development using text and different types of models. We discuss the specifics of automotive software development such as variant management, different integration stages of software development, testing strategies and the methods used for these. We review methods used in practice and explain how they should be used. We conclude the chapter with discussion on the need for standardization as the automotive software development is based on client-supplier relationships between the OEMs and the suppliers developing components of vehicles.

> **摘要**在本章中，我们描述并详细介绍了汽车行业的软件开发过程。我们介绍了整个车辆开发的 V 模型，并继续介绍现代，敏捷的软件开发方法，以描述软件开发团队的工作方式。我们首先描述所有软件开发(要求工程学)的开始，并描述使用文本和不同类型的模型在汽车软件开发中如何看待需求。我们讨论了汽车软件开发的细节，例如变体管理，软件开发的不同集成阶段，测试策略以及用于这些的方法。我们回顾实践中使用的方法，并解释应如何使用它们。我们在本章中讨论了对标准化的必要性，因为汽车软件开发是基于 OEM 与开发车辆组件的供应商之间的客户供应商关系。

## Introduction

Software development processes are at the heart of software engineering as they provide _structure and rigor_to the practices of developing software [[C+90](#_bookmark230)]. Soft- ware development processes consist of phases, activities and tasks which prescribe what actors should do. The actors can have different roles in software development such as software construction designers, software architects, project managers and quality managers.

> 软件开发过程是软件工程的核心，因为它们为开发软件的实践提供了*结构和严格*[[C90](#_bookmark230)]。软件开发过程包括规定演员应该做什么的阶段，活动和任务。参与者在软件开发中可以发挥不同的作用，例如软件架构设计师，软件架构师，项目经理和质量经理。

The software development processes are organized in phases where the focus is on a specific part of software development. Historically these phases include:

> 软件开发过程是在重点放在软件开发的特定部分的阶段中组织的。从历史上看，这些阶段包括：

1. requirements engineering—the phase where ideas about the functions of the software are created and broken down into requirements (atomic pieces of information about what should be implemented)
2. software analysis—the phase where the system analysis is conducted and high- level decisions about the allocation of functionality to the logical part of the system are made

> 1. 需求工程 - 创建有关软件功能并将其分解为要求的阶段(原子有关应实施的信息)
> 2. 软件分析 - 进行系统分析的阶段以及有关功能分配到系统逻辑部分的高级决策

<img src=`./media/image88.png` style=`width:4.4969in;height:2.1in` />
<**Fig. 4.1** > V-shaped model of software development process in automotive software development

1. software architecting—the phase where the software architects describe the high- level design of the software including its components and allocate them to computational nodes (ECUs)
2. software design—the phase where each of the components is designed in detail
3. implementation—the phase where the design for each component is imple- mented in programming languages relevant for the design.
4. testing—the phase where the software is tested in a number of different ways, for example through unit and component tests.

> 1. 软件架构 - 软件架构师描述软件包括其组件的高级设计的阶段，并将其分配给计算节点(ECUS)
> 2. 软件设计 - 每个组件详细设计的阶段
> 3. 实施 - 以与设计相关的编程语言中实现每个组件的设计的阶段。
> 4. 测试 - 以多种不同方式测试软件的阶段，例如通过单位和组件测试。

These phases are often done in parallel as modern software development paradigms postulate that it is best to design, implement and test software iteratively. However, the prevalent software development model in the automotive industry is the so-called V-model where these phases are aligned to a V-shaped curve, where the design phases are on the left-hand side of the V and the testing phases are on the right-hand side of the V.

> 这些阶段通常是同时完成的，因为现代软件开发范式假设最好是设计，实施和测试软件。但是，汽车行业中普遍的软件开发模型是所谓的 V 模型，其中这些阶段与 V 形曲线保持一致，其中设计阶段位于 V 的左侧，测试阶段是在 V 的右侧。

### _V-Model of Automotive Software Development_

The V-model is illustrated in Fig. [4.1](#_bookmark187). This model is prescribed by international industry standards for development of safety-critical systems, like the ISO/IEC 26262 [[Org11](#_bookmark253)].

> V 模型如图 [4.1](#_bookmark187) 所示。该模型由国际行业的安全关键系统制定标准规定，例如 ISO/IEC 26262 [org11](#_bookmark253)]。

In the figure, we also make a distinction between the responsibilities of OEMs (vehicle manufactures) and those of their suppliers. This distinction is important as it is often the phase where the handshaking between the suppliers and OEMs takes place, and therefore the requirements are used during the contract negotiations. In this context a detailed, unambiguous and correct requirements specification prevents potentially unnecessary costs related to the changes in requirements caused by misunderstandings between the OEMs and suppliers.

> 在该图中，我们还区分了 OEM(车辆制造商)的责任及其供应商的责任。这种区别很重要，因为它通常是供应商和 OEM 之间发生握手的阶段，因此在合同谈判期间使用了要求。在这种情况下，详细，明确和正确的要求规范可阻止与 OEM 和供应商之间误解有关的要求变化有关的潜在不必要的成本。

In the remainder of this chapter we go through the requirements engineering phase and the testing phase. The analysis and architecture phase are included in the next chapter while the detailed design phase is included in the latter part of the book.

> 在本章的其余部分中，我们将遵循需求工程阶段和测试阶段。分析和体系结构阶段包括在下一章中，而详细的设计阶段则包括在本书的后半部分中。

## Requirements

Requirements engineering is a discipline of vehicle development on the one hand and on the other hand a subdomain of software engineering and an initial phase of the software development lifecycle. It deals with the methods, tools and techniques for eliciting, specifying, documenting, prioritizing and quality assuring the require- ments. The requirements themselves are very important for the quality of software in multiple senses as the quality is defined as `The degree to which software fulfills the user requirements, implicit expectations and professional standards.` [[C90](#_bookmark230)].

> 需求工程是一方面的一项纪律，另一方面是软件工程的子域和软件开发生命周期的初始阶段。它处理用于启发，指定，记录，优先级和质量的方法，工具和技术，以确保需求。需求本身对于多种感觉的软件质量非常重要，因为质量被定义为 `软件满足用户需求，隐性期望和专业标准的程度` 。[C 90](#_bookmark230)]。

Requirements engineering in the automotive sector is increasingly about the software since the software is the source of the innovations. According to Houdek [[Hou13](#_bookmark241)] and a report about the innovation in the car industry [[DB15](#_bookmark233)], the number of functions in an average car grows much faster than the number of devices, with the number of systematic innovations growing faster than the individual innovations. The systematic innovations are systems of software functions rather than individual functions.

> 汽车领域的需求工程越来越多地关注该软件，因为该软件是创新的来源。根据 houdek [hou13](#_bookmark241)]和关于汽车行业创新的报告 [db15](#_bookmark233)]，平均汽车中的功能数量比该数量的数量快得多。设备，系统创新的数量比单个创新更快。系统的创新是软件功能的系统，而不是单个功能。

Therefore the discipline of requirements engineering is more about engineering than it is about innovation.

> 因此，需求工程的纪律更多是工程学，而不是创新。

The length of an automotive requirements specification is in the range of 100,000 pages for a new car model according to Houdek, based on his study at MercedesBenz [[Hou13](#_bookmark241)], with ca. 400 documents of 250 pages each at the lowest specification level (component specifications), which are sent over to a large number of suppliers (usually over 100 suppliers, one for each ECU in the car).

> 根据 Houdek 的研究，根据 Houdek 的研究，汽车需求规范的长度在 100,000 页的范围内，根据他在 Mercedes- Benz [Hou13](#_bookmark241)]的研究，并在 CA 中进行。在最低规范级别(组件规格)中，每张 250 页的 400 个文档被发送给大量供应商(通常超过 100 个供应商，一个为汽车中的每个 ECU)。

Weber and Weisbrod [[WW02](#_bookmark272)] showed the complexity and size of requirements specifications in the automotive domain based on their experiences at Daimler- Chrysler. Their large software development projects can have as many as 160 engineers working on a single requirement specification and producing over 3 GB of requirements data. Weber and Weisbrod describe the process of requirements engineering in the following way: `Textual requirements are only part of the game— automotive development is too complex for text alone to manage.` This quote reflects the state-of-the-practice of requirements engineering—that the requirements form only one part of the construction database. However, let’s look at how the requirements are specified in the automotive domain. Similar challenges of linking requirements to other parts of the construction database can be also found in our previous studies in [[MS08](#_bookmark247)].

> Weber 和 Weisbrod [WW02](#_bookmark272)]根据戴姆勒·克莱斯勒(Daimler-Chrysler)的经验，显示了汽车域中需求规格的复杂性和大小。他们的大型软件开发项目可以拥有多达 160 位从事单个需求规范的工程师，并生产超过 3 GB 的需求数据。Weber 和 Weisbrod 用以下方式描述了需求工程的过程： `文本需求只是游戏的一部分 - 汽车开发太复杂了，无法单独管理。` 该报价反映了需求工程的最新实践，即要求仅构成施工数据库的一部分。但是，让我们看一下如何在汽车域中指定的需求。将要求与施工数据库的其他部分联系起来的类似挑战也可以在我们先前在 [MS08](#_bookmark247)]的研究中找到。

The requirements are often defined as (1) A condition or capability needed by a user to solve a problem or achieve an objective. (2) A condition or capability that must be met or possessed by a system or system component to satisfy a contract, standard, specification, or other formally imposed documents. (3) A documented representation of a condition or capability as in (1) or (2)_[[C+90](#_bookmark230)]. This definition stresses the link between the user of the system and the system itself, which is important for a number of reasons:

> 这些要求通常定义为_(1)用户解决问题或实现目标所需的条件或能力。(2)条件或能力必须由系统或系统组件满足或拥有，以满足合同，标准，规格或其他正式强加的文档。(3)如(1)或(2)_[C 90](#_bookmark230)]中的条件或能力的记录表示形式。该定义强调了系统用户与系统本身之间的联系，这很重要，原因有很多：

- Testability of the system—it should be clear how a requirement should be tested, e.g. what is the usage scenario realized by the requirement?
- Traceability of the functionality to design—it should be possible to trace which parts of the software realize the requirement in order to provide safety argumentation and enable impact/change management
- Traceability of the project progress—it should be possible to get an overview of which requirements have already been implemented and which are still to be implemented in the project

> - 系统的可检验性 - 应该清楚应如何测试需求，例如该要求实现了什么用法方案？
> - 设计功能的可追溯性 - 应该追踪软件的哪一部分实现要求，以提供安全论证并启用影响/变更管理
> - 项目进度的可追溯性 - 应该概述已经实施了哪些要求，并且在项目中仍将实施哪些要求

It is a very technical definition for something that is intuitively well known— a requirement is a way of communicating what we, the users, want in our dream car. In this sense it seems that the discipline of requirements engineering is simple. In practice, working with requirements is very complex as the ideas which we, users, have need to be translated to one of the millions of components of the car and its software. So, let’s look at how the automotive companies work with our requirements or dreams.

> 对于直觉上知名的事物来说，这是一个非常技术的定义 - 一种要求是一种传达我们梦 dream 以求的用户想要的东西的方式。从这个意义上讲，需求工程的学科似乎很简单。实际上，使用需求非常复杂，因为我们的用户需要将其转换为汽车及其软件的数百万组件之一。因此，让我们看一下汽车公司如何满足我们的要求或梦想。

We talk about software requirements engineering because the automotive indus- try has recognized the need to move innovation from the mechanical parts of the car to the electronics and software. The majority of us, the customers, buy cars today because they are fast (sporty), safe or comfortable. In many cases these properties are realized by adjusting the software that steers the parts of modern cars. For example we can have the same car with a software package that makes it extremely sporty—look at Tesla’s `Insane` acceleration package or Volvo’s Polestar performance package. These represent just two challenges which lead to two very important trends in automotive software requirements engineering:

> 我们谈论软件需求工程，因为汽车行业已经意识到有必要将创新从汽车的机械零件转移到电子和软件。我们大多数客户，客户今天购买汽车，因为它们快速(运动型)，安全或舒适。在许多情况下，这些属性是通过调整引导现代汽车部分的软件来实现的。例如，我们可以使用相同的汽车，其中具有使其非常运动的软件包 - 看特斯拉的 `疯狂` 加速套件或沃尔沃的 Polestar Performance 套件。这些仅代表了两个挑战，这导致了汽车软件需求工程的两个非常重要的趋势：

1. Growing amount of software in contemporary cars—as the innovation is driven by software, the amount of software and its complexity grow exponentially. For example the amount of software in the 1990s was a few megabytes of binary code (e.g. Volvo S80) and today reaches over one gigabyte, excluding maps and other user data (e.g. Volvo XC90 of 2016).
2. Safety requirements posed by such standards as ISO 26262—as software steers more parts of the car, there is a larger probability that it can interfere with our driving and cause accidents and therefore it has to be safety-assured just like the software in airplanes and trains. The contemporary standard for functional safety (ISO/IEC 26262, Road vehicles—Functional safety) prescribes methods and processes to specify, design and verify/validate the software.

> 1. 当代汽车中的软件量增加 - 由于创新是由软件，软件及其复杂性呈指数增长的驱动的。例如，1990 年代的软件数量是二进制代码的一些兆字节(例如沃尔沃 S80)，今天到达一千千兆字节，不包括地图和其他用户数据(例如，2016 年的沃尔沃 XC90)。
> 2. 由 ISO 26262 等标准提出的安全要求 - 作为软件引导汽车的更多部分，它可能会干扰我们的驾驶并引起事故，因此必须像软件一样安全地确保安全性。飞机和火车。当代功能安全标准(ISO/IEC 26262，道路车辆(功能安全))规定了指定，设计和验证/验证软件的方法和过程。

Automotive software requirements engineering therefore requires rigid processes for handling the construction of software for a car and therefore is very different from other types of software requirements engineering, such as for telecom or web design.

> 因此，汽车软件需求工程需要严格的流程来处理汽车的软件构建，因此与其他类型的软件需求工程(例如电信或网络设计)大不相同。

This chapter takes us through the theory of requirements engineering in automo- tive development by looking into two types of requirements—textual specifications and models used as requirements. It also helps us to explore the evolution of requirements engineering in automotive software development to finally draw on current trends and challenges for the future.

> 本章通过研究两种类型的要求(文本规范和模型用作要求)，将我们通过自动开发中的需求工程理论。它还有助于我们探索汽车软件开发中需求工程的演变，以最终利用未来的当前趋势和挑战。

### Types of Requirements in Automotive Software_Development(汽车软件开发中的要求类型)

When designing software for a car, the designers (who are often referred to as constructors) gradually break down the requirements from car level to component level. They also gradually refine them from textual requirements to models of behaviour of the software. This gradual refinement is due to the fact that the requirements have to be sent to Tier 1 suppliers for development and therefore should be as detailed as possible to enable their validation. In the automotive domain we have a number of tiers of suppliers:

> 在为汽车设计软件时，设计师(通常称为构造函数)逐渐破坏了从汽车级别到组件级别的需求。他们还逐渐将它们从文本需求改进到软件的行为模型。这种逐步的完善是由于必须将要求发送给第 1 级供应商进行开发，因此应尽可能详细地进行验证。在汽车领域，我们有许多供应商：

- Tier 1—suppliers working directly with OEMs, usually delivering complete software and hardware subsystems and ECUs to the OEMs
- Tier 2—suppliers working with Tier 1 suppliers, delivering parts of the sub- products which are then delivered by Tier 1 suppliers to the OEMs; Tier 2 suppliers usually do not work directly with OEMs, which makes it even more important for the requirements to be detailed so that they can be correctly broken down by Tier 1 suppliers for Tier 2.
- Tier 3—suppliers working with Tier 2 suppliers, similarly to Tier 2 suppliers working with Tier 1 suppliers. Usually silicon vendors who deliver the hardware together with the drivers.

In this section we describe these different types of requirements, which can be found in these phases.

> -1 级 - 直接与 OEM 合作，通常将完整的软件和硬件子系统和 ECU 交付给 OEMS
> -2 级 - 与 1 级供应商一起工作的供应商，将部分产品交付，然后由 1 级供应商交付给 OEM；第 2 级供应商通常不直接与 OEM 合作，这使得对要求的要求更为重要，以便可以将其正确分解为第 2 层的第 1 层供应商。
>
> - 第 3 层 - 与第 2 级供应商合作的供应商，类似于与第 1 级供应商一起工作的第 2 级供应商。通常，硅供应商与驾驶员一起运送硬件。

> 在本节中，我们描述了这些不同类型的要求，可以在这些阶段中找到。

###### Textual Requirements(文本要求)

AUTOSAR is a great source of inspiration for research in automotive software development, and therefore let us look at the requirements in this standard—they are mostly textual. We use the same template as AUTOSAR for specifying requirements to provide an example of a requirement for keyless entry to the vehicle, as presented in Fig. [4.2](#_bookmark191).

> Autosar 是汽车软件开发研究的重要灵感来源，因此让我们查看此标准中的要求 - 它们主要是文本的。我们使用与 Autosar 相同的模板来指定要求，以提供对车辆无钥匙进入的示例，如图 [4.2](#_bookmark191) 所示。

The structure of the requirement is quite typical for requirements in general— it contains the description, the rationale and the use cases. So far we do not see anything specific. Nevertheless, if we look at the sheer size of such a specification— over 1000 pages—we can see that we might confront issues; so let’s discuss the kind of issues we can discover.

> 总体上，需求的结构非常典型 - 它包含描述，原理和用例。到目前为止，我们还没有看到任何具体的东西。但是，如果我们看一下这种规范的巨大规模(超过 1000 页)，我们可以看到我们可能会面对问题；因此，让我们讨论一下我们可以发现的问题。

<**Fig. 4.2** > An example AUTOSAR requirement

**Rationale** The textual requirements are used when describing high-level prop- erties of cars. These types of requirements are mostly used in two phases—the requirements phase, when the specification of the car’s functionality at a high level takes place, and at the component design phase, where large software requirements specification documents are sent to suppliers for development (although the textual requirements are often complemented by model-based requirements).

> **理由**在描述汽车的高级支撑物时，使用文本要求。这些类型的需求主要在两个阶段中使用 - 要求阶段，当汽车在高级别的情况下的规范时，在组件设计阶段，将大型软件需求规范文档发送给供应商进行开发(尽管文本要求通常由基于模型的要求补充)。

**Method** Specifying this kind of requirement rarely happens from scratch. Textual requirements are often specified based on models (e.g. UML domain models) and are intended to describe details of the inner workings of software systems. They are often linked to verification methods describing how the requirements should be verified—e.g. describing the test procedure for validating that the requirement is implemented correctly. Quite often it is the suppliers who do the verification, as many requirements demand specific test equipment to test their implementation. If this is the case, the OEMs choose a subset of requirements and verify them to check the correctness of the verification procedure on their side.

> **方法**指定这种要求很少发生。通常根据模型(例如 UML 域模型)指定文本要求，并旨在描述软件系统内部工作的详细信息。它们通常与验证方法链接，描述应如何验证要求(例如)。描述验证要求正确实施的测试程序。经常是供应商进行验证，因为许多需求要求特定的测试设备来测试其实施。如果是这种情况，OEM 会选择一部分要求，并验证它们以检查验证过程的正确性。

**Format** The text for the requirement is specified in the format which we can see in Fig. [4.2](#_bookmark191)—tables with text. This format is very good if we can specify the details, but they are not very good when we want to communicate overviews and provide the context for the requirements. For that we need other types of requirements—use cases or models.

> **格式**要求的文本以我们可以在图 [4.2](#_bookmark191) 中看到的格式指定，并带有文本。如果我们可以指定详细信息，则这种格式非常好，但是当我们想交流概述并为要求提供背景时，它们不是很好。为此，我们需要其他类型的要求 - 使用案例或模型。

![](./media/image89.png)
<**Fig. 4.3** > An example use case specification with one use case

<img src=`./media/image91.png` style=`width:0.16012in;height:0.39153in` />
<**Fig. 4.4** > An example specification of a use case using the message sequence charts/sequence diagrams

###### Use Cases

In software engineering the golden standard for specifying requirements is using use cases as defined by Jacobson, together with his Objectory methodology, in the 1990s [[JBR97](#_bookmark242)]. The use cases describe a course of interaction between an actor and the system under specification, for example as shown in Fig. [4.3](#_bookmark192), where the actor interacts with the car in the use case `Keyless start-up` . The corresponding diagram (called the use case diagram in UML) is used to present which interactions (use cases) exist and how many actors are included in these interactions.

> 在软件工程中，用于指定要求的黄金标准是使用 Jacobson 定义的用例，以及他的对象方法，在 1990 年代 [JBR97](#_bookmark242)]。用例描述了演员与规范下的系统之间的相互作用，例如，如图 [4.3](#_bookmark192) 所示，在其中，演员在用例 `无钥匙启动` 中与汽车交互。相应的图(称为 UML 中的用例图)用于介绍存在哪些相互作用(用例)以及这些相互作用中包含多少个参与者。

In the automotive industry this kind of requirements specification is the most common when describing the functions of the vehicles and their dependencies. It is used to describe how the actors (drivers or other cars) interact with the designed vehicle (the system) in order to realize a specific use case. This kind of specification is often described using the sequence diagrams of UML and we can see an example of such a specification in Fig. [4.4](#_bookmark193).

> 在汽车行业中，这种要求规范在描述车辆及其依赖性时最常见。它用于描述演员(驾驶员或其他汽车)如何与设计的车辆(系统)相互作用，以实现特定的用例。通常使用 UML 的序列图来描述这种规范，我们可以在图 [4.4](#_bookmark193) 中看到此类规范的示例。

<img src=`./media/image92.jpeg` style=`width:4.33636in;height:2.385in` />
<**Fig. 4.5** > An example Simulink model which can be used as a requirement to describe how to implement the ABS system

**Rationale** The use case specifications provide a high-level overview of the func- tionality of the designed system, such as a car, and therefore are very useful in the early phases of vehicle development. Usually these early phases are the functional design (use case diagrams) and the beginning of the system design (use case specifications).

> **理由**用例规范提供了设计系统(例如汽车)功能的高级概述，因此在车辆开发的早期阶段非常有用。通常，这些早期阶段是功能设计(用例图)和系统设计的开始(用例规范)。

**Method** Using the high-level descriptions of product properties, the functional designers break down these properties into usage scenarios. These usage scenarios provide a way to identify which of the functions (use cases) are of value to the customers and which are too cumbersome.

> **方法**使用产品属性的高级描述，功能设计师将这些属性分解为使用情况。这些用法方案提供了一种识别哪些功能(用例)对客户有价值且哪些太麻烦的方法。

**Format** These kinds of specifications consist of three parts—(1) the use case diagram, (2) the use case specification using a sequence diagram, and (3) the textual specification of a use case detailing the steps of the interaction using somewhat structured natural language.

> **格式**这些类型的规格由三个部分组成：(1)用例图，(2)使用序列图的用例规范，以及(3)用例的文本规范详细介绍了该步骤使用某种结构化的自然语言进行互动。

###### Model-Based Requirements(基于模型的要求)

One method to provide more context to the requirements is to express them as models. This kind of representation can be done in two types of formalisms—UML- like models and Simulink models. In Fig. [4.5](#_bookmark194) we present an excerpt of a Simulink model for an ABS system from [[Dem12](#_bookmark234)] and [[RSB+13b](#_bookmark260)].

> 为要求提供更多背景的一种方法是将其表示为模型。这种表示可以用两种类型的形式主义来完成：uml-like Models 和 Simulink 模型。在图。[4.5](#_bookmark194) 中，我们提出了 [dem12](#_bookmark234)] ]和 13b](#_Bookmark260)]。

The model shows how to implement the ABS system, but the most important property is that the model shows how the algorithm should behave and therefore how it should be verified.

> 该模型显示了如何实现 ABS 系统，但是最重要的属性是该模型显示了算法应如何行为以及如何验证该算法。

**Rationale** Using models as requirements has been recognized by practitioners, and in an automotive software project up to 23% of models are used as requirements according to our previous studies [[MS10b](#_bookmark250)] and [[MS10a](#_bookmark249)]. According to the same studies, up to 13% of effort is spent in the software project to design these kinds of requirements.

> **基本原理**使用模型已被从业人员确认，并且根据我们以前的研究，最多 23％的模型被用作要求的 23％的模型 [ms10b](#_bookmark250)]和 [ms10a](#_bookmark249)]。根据相同的研究，在软件项目中花费了多达 13％的精力来设计这类要求。

**Method** The simulation models used for requirements engineering are often used as part of the process of system design and function design, where the software and system designers develop algorithms that describe how functions in modern cars are to be realized. These models can be automatically translated to C/C++ code using code generation, but it is rather uncommon. The reason is that these models describe entire functions which are often partitioned into different domains and spread over multiple components. Quite often these kinds of requirements are translated into textual specifications, shown in the previous subsection.

> **方法**用于需求工程的仿真模型通常被用作系统设计和功能设计过程的一部分，在该过程中，软件和系统设计人员开发了描述现代汽车功能如何实现的算法。这些模型可以使用代码生成自动转换为 C/C ++ 代码，但这并不常见。原因是这些模型描述了整个功能，这些功能通常被分配到不同的域并分布在多个组件上。这些要求经常被转化为文本规格，如先前的小节所示。

**Format** The models are expressed using Simulink or a variation of statechart such as Statemate or Petri nets. These simulation models detail the functions described in the use cases by adding the system view of the interaction—the blocks and signals. The blocks and signals represent the realization of the functionality in the car and are focused on one function only. These models are often used as specifications which are then detailed and often used to generate the source code automatically.

> **格式**模型是使用 simulink 或 statechart 的变体(例如司令或培养皿网)表示的。这些仿真模型通过添加交互的系统视图(块和信号)详细说明了用例中描述的功能。块和信号表示汽车中功能的实现，仅专注于一个函数。这些模型通常用作规格，然后将其详细介绍，并通常用于自动生成源代码。

## Variant Management(变体管理)

Having a good database of requirements and construction elements is key to success in automotive software engineering. This is dictated by the fact that the automotive market is based on _variability_—i.e. the locations in the product (software) where it can be configured. As customers we expect the ability to configure our car with the latest and greatest features of hardware, electronics and software.

> 拥有良好的需求数据库和施工元素是汽车软件工程成功的关键。这是由汽车市场基于 *variability*-i.e 的事实决定了这一事实。产品(软件)中的位置可以配置。作为客户，我们希望能够使用硬件，电子和软件的最新和最大功能配置我们的汽车。

There are two basic kinds of variability mechanisms in automotive software:

- Configuration—when we configure parameters of the software without modify- ing its internal structure. This kind of variability is often seen in the non-safety critical functions such as engine calibration or in configuring the availability of functions (e.g. rain sensors).
- Compilation—when we change the internal structure of the software, compile it and then deploy on the target ECU. This kind of variability is used when we need to ensure that the software always behaves in the same way, for example the availability of the function for collision avoidance by breaking.

> 汽车软件中有两种基本的可变性机制：
>
> - 配置 - 当我们配置软件的参数而无需修改其内部结构时。这种可变性通常在非安全关键功能(例如发动机校准或配置功能的可用性(例如雨传感器))中看到。
> - 汇编 - 当我们更改软件的内部结构时，将其编译，然后在目标 ECU 上部署。当我们需要确保软件始终以相同的方式行事(例如，通过破坏碰撞避免碰撞的功能可用性)时，使用这种可变性。

In this section we explain the basics of these two mechanisms.

> 在本节中，我们解释了这两种机制的基础。

<img src=`./media/image93.png` style=`width:1.67807in;height:0.11687in` />
<img src=`./media/image94.png` style=`width:1.76756in;height:0.1174in` />
<**Fig. 4.6** > Variability through configuration

### _Configuration_(配置)

Configuration is often referred to as runtime variability as changing the software can be done after the software is compiled. Figure [4.6](#_bookmark196) presents the conceptual view of this kind of variability.

> 配置通常称为运行时可变性，因为在编译软件后可以完成该软件。图 [4.6](#_bookmark196) 介绍了这种可变性的概念视图。

In Fig. [4.6](#_bookmark196) we can see that we have one variant of the software component (rectangle) with one variability point (the dotted line triangle) which can be configured using two different configurations—without the rain sensor and with the rain sensor. This means that we compile the code for the software component once and then use two different configuration files when deploying the software.

> 在图。[4.6](#_bookmark196) 中，我们可以看到我们有一个具有一个可变性点(虚线三角形)的软件组件(矩形)的变体，可以使用两种不同的配置进行配置，而没有雨传感器和带有雨水传感器和雨传感器。这意味着我们一次编译软件组件的代码，然后在部署软件时使用两个不同的配置文件。

The configuration as a variability mechanism has important implications for the designers of the software. The main implication is that the software has to be tested using multiple scenarios—i.e. the software designers need to be able to prevent use of the software component with invalid configurations.

> 作为可变性机制的配置对软件的设计人员具有重要意义。主要的含义是必须使用多种方案进行测试软件。软件设计人员需要能够防止使用无效配置使用软件组件。

### _Compilation_

The compilation as a variability mechanism is fundamentally different as it results in a software component which cannot be modified (configured) after its compilation, during runtime. Therefore it is an example of so-called _design time variability_as the designers must decide during design which variant is being developed. This is conceptually shown in Fig. [4.7](#_bookmark199) where we can see two different versions of the same component—with and without the rain sensor.

> 该汇编作为可变性机制在根本上有所不同，因为它导致软件组件在运行时无法修改(配置)后无法修改(配置)。因此，这是所谓的 *design 时间变异性*的一个示例，因为设计师在设计过程中必须确定正在开发哪种变体。这在图 [4.7](#_bookmark199) 中显示在概念上，我们可以在其中看到两个不同版本的同一组件(没有雨传感器)。

<**Fig. 4.7** > Variability through compilation

As Fig. [4.7](#_bookmark199) suggests, there are two different code bases for the software component—one with and one without the rain sensor. This means that the development of these two variants can be decoupled from each other, but that also means that the designers have to maintain two different code bases at the same time. This parallel maintenance means that if there are defects in the common code then both code bases need to be updated and tested.

> 如图 [4.7](#_bookmark199) 建议，该软件组件有两个不同的代码库 - 一个与雨传感器一起使用。这意味着这两个变体的开发可以彼此解耦，但这也意味着设计人员必须同时维护两个不同的代码库。此并行维护意味着，如果通用代码中存在缺陷，则需要对两个代码库进行更新和测试。

The main advantage of this kind of variability mechanism is the assurance that the code is not tampered with in any way after the compilation. The code can be tested, and once deployed there is no way that an incorrect configuration can break the quality of the component. However, the main disadvantage of this type of variability management mechanism is the high cost of maintenance of the code base—parallel maintenance.

> 这种可变性机制的主要优点是保证该代码在编译后不会以任何方式篡改。可以测试代码，一旦部署，不正确的配置就无法破坏组件的质量。但是，这种可变性管理机制的主要缺点是代码基础维护的高成本 - 并行维护。

### _Practical Variability Management_

Both of the above variability management mechanisms are used in practice. Compile time variability is used when the software is an integral part of an ECU whereas configuration is used when the software can be calibrated to different types of configurations during deployment (e.g. configuration on the assembly line, calibration of the engine and gearbox depending on the powertrain performance settings).

> 上述两种变异性管理机制均在实践中使用。当软件是 ECU 不可或缺的一部分时，使用编译时间可变性，而在部署过程中可以将软件校准为不同类型的配置时(例如，在装配线上的配置，发动机和变速箱的校准，取决于电源，则使用配置性能设置)。

## Integration Stages of Software Development(软件开发的集成阶段)

On the left-hand side of the V-model the main type of activity is refinement of requirements in multiple ways. On the right-hand side of the model the main activity type is integration followed by testing.

> 在 V 模型的左侧，主要活动类型是通过多种方式改进需求。在模型的右侧，主要活动类型是集成，然后进行测试。

In short, integration is the activity where software construction engineers inte- grate their code with the code of other components and with the hardware. In the first integration stages the hardware is usually simulated hardware in order to allow for unit and component testing (described in Sect. [4.5](#testing-strategies)). In the later integration phases the software code is integrated together with the target hardware, which is then integrated into a complete electrical/electronic system of the car (Table [4.1](#_bookmark202)).

> 简而言之，集成是软件构建工程师将其代码与其他组件和硬件的代码进行整体的活动。在第一个集成阶段，通常会模拟硬件，以便进行单元和组件测试(在各节中进行了描述。[4.5](#testing-trategies))。在后来的集成阶段中，软件代码与目标硬件集成在一起，然后将其集成到汽车的完整电气/电子系统中(表 [4.1](#_bookmark202))。

Figure [4.8](#_bookmark203) shows an example software integration of software modules and components into an electrical system. What is important to notice is the fact that the integration steps (vertical solid black lines) are not synchronized as the development of different software modules is done at different pace.

> 图 [4.8](#_bookmark203) 显示了软件模块和组件中的软件集成到电气系统中。重要的是要注意的是，由于不同的软件模块的开发是在不同的节奏下完成的，因此不同步集成步骤(垂直实心黑线)。

**Table 4.1** Types of integration
![](./media/image95.png)
<**Fig. 4.8** > Software integration with integration steps

In practice this figure is even more complicated, as the integration plan is often a document with several dimensions. Each integration cycle (which is what we show in Fig. [4.8](#_bookmark203)) is done several times during the project. First, the so-called basic software is integrated (functionality like the boot code, and communication) and then higher level functionality is added, according to the functional architecture as described in Chap. [2](#_bookmark54).

> 实际上，这个数字更加复杂，因为集成计划通常是具有多个维度的文档。在项目期间，每个集成周期(这是我们在图 [4.8](#_bookmark203) 中显示的内容)是多次完成的。首先，所谓的基本软件是集成的(例如引导代码和通信等功能)，然后根据 CHAP 中所述的功能架构添加更高的级别功能。[2](#_bookmark54)。

## Testing Strategies(测试策略)

Requirements engineering progresses from higher abstraction levels towards more detailed, lower abstraction levels. Testing is the opposite. When the testers test the software they start from the most atomic type of testing—unit testing—where they test each function and each line of code. Then they gradually progress by testing entire components (i.e. multiple units linked together), then the entire system and finally each function. Figure [4.9](#_bookmark206) shows the right-hand side of the V-model with a focus on the testing phases.

> 需求工程从较高的抽象水平发展到更详细的，较低的抽象水平。测试是相反的。当测试仪测试软件时，它们从最原子类型的测试(单位测试)开始，它们在其中测试每个功能和每个代码。然后，它们通过测试整个组件(即将多个单位链接在一起)，然后是整个系统，最后每个功能逐渐进展。图 [4.9](#_bookmark206) 显示了 V 模型的右侧，重点是测试阶段。

In the coming subsections we look deeper into the testing phases of the automotive software.

> 在即将到来的小节中，我们更深入地研究了汽车软件的测试阶段。

### _Unit Testing_

Unit test is the basic test, which is performed on individual entities of software such as classes, source code modules and functions. The goal of unit testing is to find defects related to the implementation of atomic functions/methods in the source code.

> 单位测试是基本测试，它是对类软件实体(例如类，源代码模块和功能)执行的。单位测试的目的是找到与源代码中原子函数/方法实现有关的缺陷。

![](./media/image100.png)
<**Fig. 4.9** > Testing phases in automotive software development

The basic scheme of unit testing is the creation of automated test cases which combine individual methods with the data that is needed to achieve the needed quality. The result is then compared to the expected result, usually with the help of assertions. An example of a unit test is presented in Fig. [4.10](#_bookmark207).

> 单元测试的基本方案是创建自动测试用例，这些测试用例将单个方法与实现所需质量所需的数据结合在一起。然后将结果与预期的结果进行比较，通常在断言的帮助下。图 [4.10](#_bookmark207) 显示了单元测试的示例。

The unit test presented in Fig. [4.10](#_bookmark207) is a test for correctness of the creation of object `WindshieldWiper` —a unit under test (UUT). This particular test code is written in C# and in practice the test code can be written in almost any programming language. The principles, however, are the same for all unit tests.

> 图 [4.10](#_bookmark207) 中介绍的单元测试是对对象 `挡风玻璃吹动器` 的正确性的测试 - 正在测试的单元(UUT)。该特定的测试代码用 C#编写，实际上，测试代码几乎可以用任何编程语言编写。但是，对于所有单位测试，原理都是相同的。

Of interest for our chapter are lines 14–23, as they contain the actual test code. Line 15 is the arrangement line which prepares (sets up) the test case—in our example it declares a variable which will be assigned to the object of the class WindshieldWiper. Line 18 is the actuation line which executes the actual test code— in our example creates the object of the WindshieldWiper class.

> 我们章节感兴趣的是第 14-23 行，因为它们包含实际的测试代码。第 15 行是准备(设置)测试案例的布置行 - 在我们的示例中，它声明了一个变量，该变量将分配给类 WindshieldWiper 的对象。第 18 行是执行实际测试代码的驱动线 - 在我们的示例中，创建了挡风玻璃泽类类的对象。

The most interesting are lines 21–23 since they contain the so-called assertion. The assertion is a condition which should be fulfilled after the execution of the test code. In our example the assertion is that the status of the newly created object (line 21) is `closed` (line 22). If it is not the case, then the error message is logged in the testing environment (line 32) and the execution of the new test cases continues.

> 最有趣的是第 21-23 行，因为它们包含所谓的断言。断言是在执行测试代码后应实现的条件。在我们的示例中，断言是新创建的对象的状态(第 21 行)是 `封闭` (第 22 行)。如果不是这种情况，则错误消息将在测试环境(第 32 行)中记录，并且新测试用例的执行仍在继续。

Unit testing is often perceived as the simplest type of testing and is most often automated. Frameworks like CppUnit, JUnit or Google test framework can orchestrate the execution of unit tests, allowing us to quickly execute the entire set of tests (called test suites) without the need for manual intervention.

> 单位测试通常被认为是最简单的测试类型，并且通常是自动化的。诸如 CPPUNIT，JUNIT 或 Google 测试框架之类的框架可以协调单位测试的执行，从而使我们能够快速执行整个测试(称为测试套件)，而无需手动干预。

Automated unit tests are also reused in several ways, for example to create nightly regression test suites or to create the so-called `smoke testing` where testers randomly execute test cases to check whether the system exposes random behavior.

> 自动化的单元测试也以多种方式重复使用，例如创建夜间回归测试套件或创建所谓的 `烟雾测试` ，其中测试人员随机执行测试用例以检查系统是否暴露了随机行为。

<img src=`./media/image101.jpeg` style=`width:4.46275in;height:3.795in` />
<**Fig. 4.10** > Example unit test for testing the status of windshield wiper module

It is also important to notice that reuse of test cases needs to be accompanied by the methods to prioritize test cases, e.g. by identifying risky areas in source code [[ASM+14](#_bookmark226)] or focusing on code that was changed since the last test run [[KSM+15](#_bookmark244),

> 同样重要的是要注意，重用测试用例需要伴随着优先级测试用例的方法，例如通过识别源代码中的风险区域 [ASM + 14](#_bookmark226)]或专注于自上次测试运行以来已更改的代码 [KSM ++ 15](#_bookmark244)，

[SHF](#_bookmark262)]. It is also important to trace the test process in the context of software reliability growth [[RSM](#_bookmark261), [RSBa](#_bookmark259)].

> [SHF ](#_bookmark262)]。在软件可靠性增长的背景下追踪测试过程也很重要，[[RSM ](#_bookmark261)，[rsb a](#_kbookmark259)]。

We can also see that if the test case finds a problem (fails), then troubleshooting is relatively simple—we know which code was executed and under which conditions. This knowledge allows the testers to quickly describe where the defect is or even suggest how to fix it.

> 我们还可以看到，如果测试案例发现问题(失败)，那么故障排除相对简单 - 我们知道执行了哪些代码以及在哪些条件下。这些知识使测试人员可以快速描述缺陷在哪里，甚至建议如何修复缺陷。

### _Component Testing_

This is sometimes also called _integration testing_, as the goal of this type of testing is to test the integrations, i.e. links, between units of code within one of many components. The main characteristic which differentiates component tests from unit tests is that in component testing we use stubs to simulate the environment of the tested component or the group of the components. This is illustrated in Fig. [4.11](#_bookmark209).

> 这有时也称为 *Integration Testing*，因为这种类型的测试的目的是测试集成，即链接，在许多组件之一中的代码单位之间。将组件测试与单位测试区分开的主要特征是，在组件测试中，我们使用存根来模拟已测试组件或组件组的环境。这在图 [4.11](#_bookmark209) 中说明。

![](./media/image102.png)
<**Fig. 4.11** > Component under test with the simulated environment

In contrast to unit tests, component tests focus on the interaction between the stubs and the component under test. The goal of this type of testing is to verify that the structure and behavior of the interfaces is implemented correctly.

> 与单位测试相反，组件测试集中于存根和正在测试的组件之间的相互作用。这种类型的测试的目的是验证接口的结构和行为是否正确实现。

We should also mention that the number of stubs in the system decreases as the development project progresses. With the progress of the development, new components are designed and they replace the stubs. Hence the nickname of this type of testing— `integration testing` .

> 我们还应该提到，随着开发项目的进行，系统中的存根数量减少。随着开发的进展，设计了新的组件，并取代了存根。因此，这种类型的测试的昵称 - `集成测试` 。

In automotive systems this type of testing is often done by simulating the environment using either models (the so-called Model-In-the-Loop or MIL testing) or hardware simulators (the so-called Hardware-In-the-Loop or HIL testing). An example of equipment for HIL testing is presented in Fig. [4.12](#_bookmark210).

> 在汽车系统中，这种类型的测试通常是通过使用型号(所谓的型号或 MIL 测试)或硬件模拟器(所谓的硬件或 HIL 的型号来完成环境来完成的测试)。图 [4.12](#_bookmark210) 提供了 HIL 测试设备的示例。

<img src=`./media/image103.jpeg` style=`width:1.07917in;height:2.3715in` /><**Fig. 4.12** > HIL testing rig—Image source: dSPACE GmbH. Copyright 2015 dSPACE GmbH—reprinted with permission

Figure [4.12](#_bookmark210) shows a testing rig from dSpace, which is widely used in the automotive industry to test components by simulating the external environment.

> 图 [4.12](#_bookmark210) 显示了 DSPACE 的测试钻机，该测试钻机在汽车行业中广泛用于通过模拟外部环境来测试组件。

Since the environment of the components is simulated, the non-functional prop- erties of the components are often hard to test or require very detailed simulations. The very detailed simulations, however, also tend to be very costly.

> 由于模拟了组件的环境，因此组件的非功能支持通常很难测试或需要非常详细的模拟。但是，非常详细的模拟也往往非常昂贵。

### _System Testing_

System testing is the phase of testing when the entire system is assembled and tested as a whole. The focus of system testing is on checking whether the system fulfills its specifications in a number of ways. The system testing focuses on verifying the following aspects:

> 系统测试是整个系统组装和整体测试时测试的阶段。系统测试的重点是检查系统是否以多种方式符合其规格。系统测试的重点是验证以下方面：

1. functionality—testing whether the system has the functionality as specified in the requirements specification
2. interoperability—testing whether the system can connect to the other systems which are designed to interact with the system under test
3. performance—testing whether the system under test performs within the speci- fied limits (e.g. timing limits, capacity limits)
4. scalability—testing whether the system’s operation scales up and down (e.g. whether the communication buses operate with 80 and 120 ECUs connected)
5. stress—testing whether the system operates correctly under high load (e.g. when the maximum capacity of the communication buses is reached)
6. reliability—testing whether the system operates correctly during a specific period of time
7. regulatory and compliance—testing whether the system fulfills legal and regula- tory requirements (e.g. carbon dioxide emissions)

> 1. 功能 - 测试系统是否具有需求规范中指定的功能
> 2. 互操作性 - 测试系统是否可以连接到旨在与正在测试的系统交互的其他系统
> 3. 性能 - 测试正在测试的系统是否在指定限制范围内执行(例如，时间限制，容量限制)
> 4. 可伸缩性 - 测试系统的操作是否上下缩放(例如，连接 80 和 120 ECU 的通信总线是否运行)
> 5. 压力 - 测试系统是否在高负载下正确运行(例如，达到通信总线的最大容量)
> 6. 可靠性 - 测试系统是否在特定时间段内正确运行
> 7. 监管和合规性 - 测试系统是否满足法律和规范要求(例如二氧化碳排放)

System testing is usually the first testing phase when the above aspects can be tested and therefore it is usually the most effective way of testing. However, it is also very costly way of testing and very inefficient, as fixing the defects found in this phase requires frequent changes in multiple components.

> 系统测试通常是可以测试上述方面的第一个测试阶段，因此通常是最有效的测试方法。但是，这也是非常昂贵的测试方式和非常低效的方法，因为在此阶段发现的缺陷需要经常改变多个组件。

In the automotive software this type of testing is often done using the so-called `box cars` —the entire electrical system being set up on tables without the chassi and the hardware components.

> 在汽车软件中，这种类型的测试通常是使用所谓的 `盒子` 进行的，这是在没有底盘和硬件组件的桌子上设置的整个电气系统。

### _Functional Testing_

The functional testing phase focuses on verifying that the functions of the system work according to their specification. They correspond to the functional require- ments in the form of use cases and are quite often specified according to the use cases. Figure [4.13](#_bookmark213) presents an example of a functional test—specified as a table.

> 功能测试阶段的重点是验证系统的功能是否根据其规范工作。它们对应于用例形式的功能要求，并且经常根据用例指定。图 [4.13](#_bookmark213) 提出了一个功能测试的示例，称为表。

What is important in this example is the specification, which is similar to the specification of a use case—the description of the action (step) on the left-hand side together with the expected outcome on the right-hand side. We can also observe that the functional test does not require the knowledge of the actual construction of the system under test (SUT), which led to the nickname of these tests as `black-box testing` .

> 在此示例中重要的是规范，该规范类似于用例的规范 - 左侧的动作(步骤)的描述以及右侧的预期结果。我们还可以观察到，功能测试不需要了解正在测试的系统的实际结构(SUT)的知识，这导致这些测试的昵称是 `黑盒测试` 。

![](./media/image104.png)
<**Fig. 4.13** > Example of a functional test

We should not focus on the simplicity of the example because functional testing is often the most effort-intensive type of testing. It is often done in a manual manner and requires sophisticated equipment to conduct.

> 我们不应该关注示例的简单性，因为功能测试通常是最努力的测试类型。它通常是手动进行的，需要进行复杂的设备进行操作。

Examples of sophisticated functional test cases are safety test cases where OEMs test their safety systems. To be able to test such a function, car manufacturers need to recreate the situation where the system could be activated and check whether it was activated. They also need to recreate the situation when it should not be activated and test that it was not activated.

> 复杂功能测试案例的示例是 OEM 测试其安全系统的安全测试用例。为了能够测试此类功能，汽车制造商需要重新创建可以激活系统的情况并检查是否被激活。当不应激活并测试未被激活时，他们还需要重新创建情况。

When the functional test fails, it is rather difficult to find the defect, as the number of construction elements which take part in the interaction can be quite large—in our example the failure of the functional test case could be caused by anything from mechanical failure of the battery to design defect in the software. Therefore functional testing is often used after the other tests are conducted to validate functionality rather than to verify the design.

> 当功能测试失败时，很难找到缺陷，因为参与互动的施工元素的数量可能很大 - 在我们的示例中电池以设计软件中的缺陷。因此，在进行其他测试以验证功能而不是验证设计之后，通常使用功能测试。

### Pragmatics of Testing Large Software Systems: Iterative_Testing

As the electrical system of contemporary cars is very complex, OEMs often apply concepts of iterative testing to their development. Concept of iterative testing means that the functionality of the software is divided into levels (as prescribed by the functional architecture described in Chap. [2](#_bookmark54)) and the functions are tested using unit, component, system and functional testing per layer. This means that the basic functionality such as booting up of the electronics, starting up of the communication protocols, running diagnostics, etc. are tested first and the more advanced functions such as lighting, steering, and braking are tested later, followed by more advanced functions such as driver alerts.

> 由于当代汽车的电气系统非常复杂，因此 OEM 经常将迭代测试的概念应用于其开发中。迭代测试的概念意味着软件的功能分为级别(如第 [2](#_bookmark54) 中描述的功能体系结构所规定)，并使用单元，组件，系统和每层功能测试对功能进行测试。这意味着首先测试了诸如启动电子设备，启动通信协议，运行诊断等的基本功能，并在稍后测试更高级的功能，例如，稍后进行更高级的测试功能，例如驱动程序警报。

## Construction Database and Its Role in Automotive Software Engineering

All these types of requirements need to come together somehow and that’s why we have the process and the infrastructure for requirements engineering. Let us start with the infrastructure—usually named the design or construction database. In the light of work of Weber and Weisbrod [[WW02](#_bookmark272)] it is called the common information model. Figure [4.14](#_bookmark216) shows how this design database is used. The construction database contains all elements of the design of the electrical system of the vehicle— components, electronic control units, systems, controllers, etc. The structure of such a database is hierarchical and reflects the structure of the vehicle. Each of the elements in the database has a set of requirements linked to it. The requirements are also linked to one another to show how they are broken down. Such a database grows over time and is version-controlled as different versions of the same elements can be used in different vehicles (e.g. different year models of the same car or different cars).

> 所有这些类型的要求都需要以某种方式结合在一起，这就是为什么我们拥有需求工程的流程和基础架构的原因。让我们从基础架构开始 - 通常命名设计或构造数据库。鉴于 Weber 和 Weisbrod [WW02](#_bookmark272)]的工作称为常见信息模型。图 [4.14](#_bookmark216) 显示了如何使用此设计数据库。构造数据库包含车辆电气系统设计的所有元素 - 组件，电子控制单元，系统，控制器等。此类数据库的结构是分层的，并反映了车辆的结构。数据库中的每个元素都有一组链接到它的要求。这些要求还相互链接，以显示它们如何被分解。这样的数据库随着时间的推移而增长，并且由版本控制，因为相同元素的不同版本可以在不同的车辆中使用(例如，同一汽车或不同汽车的不同年度型号)。

An example of such a system is described by Chen et al. [[CTS+06](#_bookmark232)] and has been developed by the company Systemite, which specializes in databases for vehicle construction. Such a database structures all the elements of the construction of the electronics of the vehicle and links all artifacts to the construction elements. An example of a construction element is the engine’s electronic control unit, and all the functions that use this control unit are linked to it.

> Chen 等人描述了这种系统的一个例子。[CTS + 06](#_bookmark232)]已由公司 Systemite 开发，该公司专门研究车辆构建数据库。这样的数据库结构了车辆电子设备构建的所有元素，并将所有伪像链接到构造元素。构造元素的一个示例是发动机的电子控制单元，使用此控制单元的所有功能都链接到它。

Such a database usually has a number of views which show the required set of details—functional view, architectural view, topological view and software components’ view. Each view provides the corresponding entry point and shows the relevant elements, but the database is always in a consistent state where all the links are valid.

> 这样的数据库通常具有许多视图，这些视图显示了所需的细节集 - 功能视图，架构视图，拓扑视图和软件组件的视图。每个视图提供相应的入口点并显示相关元素，但是数据库始终处于所有链接有效的一致状态。

The database is used to generate construction specifications for different actors. For each supplier that delivers an ECU, the database generate the set of all requirements which are linked to the ECU and all models which describe the behaviour of the ECU. Sometimes, depending on the situation, the documentation contains even the simulation models for the functions which are to be included in the ECU.

> 该数据库用于为不同参与者生成施工规范。对于每个提供 ECU 的供应商，数据库生成了与 ECU 链接的所有要求以及描述 ECU 行为的所有模型。有时，根据情况，文档甚至包含将包含在 ECU 中的功能的模拟模型。

One of the commercial tools available on the market which is used as a construction database is the tool SystemWeaver provided by Systemite. The main strength of such a tool is the ability to link all elements together. In Fig. [4.15](#_bookmark217) we can see > how the requirements are linked to the software architecture model. On the left-hand side we can see that the requirements are part of an element (e.g. `Adjust speed` as part of the `Adaptive cruise control` ), and on the right-hand side another requirement visualized as a diagram.

> 市场上可用的商业工具之一用作施工数据库，是 SystemIte 提供的工具系统 Weaver。这种工具的主要优势在于能够将所有元素联系在一起。在图。[4.15](#_bookmark217) 我们可以看到 <span ID = ` _bookmark216`  class = `锚` > </span>如何链接到软件体系结构模型。在左侧，我们可以看到需求是元素的一部分(例如，作为 `自适应巡航控制` 的一部分，`调整速度` )，在右侧，另一项可视化为图表的要求。

<img src=`./media/image116.png` style=`width:4.13453in;height:3.21in` />
<**Fig. 4.14** Design database

Such tools provide specific views, for example listing all requirements linked to a specific function as shown in Fig. [4.16](#_bookmark218). As part of that view we can see that the text is complemented with figures which allow the analysts to be more specific when specifying requirements and allow the designers to understand the requirements better.

> 这样的工具提供了特定的视图，例如列出链接到特定功能的所有要求，如图 [4.16](#_bookmark218) 所示。作为该观点的一部分，我们可以看到文本与数字相辅相成，这些数字使分析师在指定要求时可以更具体，并允许设计师更好地理解要求。

The ability to link the elements from different views (e.g. requirements and components) and provide a graphical overview of these elements allows the architects to quickly perform change impact analyses and reason about their architectural choices. Such a dynamic creation of views is very important when assessing architectures (e.g. during ATAM assessments). An example of such a view is one showing a set of architectural components used in realization of a specific user function, as shown in Fig. [4.17](#_bookmark219).

> 从不同视图(例如需求和组件)链接元素并提供这些元素的图形概述的能力使架构师能够快速执行变更影响分析和有关其体系结构选择的理由。在评估体系结构(例如，在 ATAM 评估期间)，这种动态的观点创造非常重要。这种视图的一个示例是显示一组用于实现特定用户功能的体系结构组件，如图 [4.17](#_bookmark219) 所示。

The system construction database can also help us in linking requirements to test cases during the test planning phase—as shown in Fig. [4.18](#_bookmark220).

> 系统构建数据库还可以帮助我们在测试计划阶段将需求与测试用例联系起来，如图 [4.18](#_bookmark220) 所示。

It can also assist us in tracking the progress of testing—Fig. [4.19](#_bookmark221). Since the number of requirements is so large in automotive systems, tracking the progress of whether they are tested is also not trivial. Therefore a unified view is needed where the project can track the test cases that are planned to cover certain requirements, as well as those that they were executed and what the result of the execution was.

> 它还可以帮助我们跟踪测试的进度-FIG。[4.19](#_bookmark221)。由于汽车系统中的需求数量如此之大，因此跟踪是否测试的进度也不是微不足道的。因此，需要一个统一的视图，该项目可以跟踪计划涵盖某些要求的测试案例，以及执行它们的要求以及执行的结果是什么。

<img src=`./media/image117.jpeg` style=`width:4.50332in;height:3.2in` />
Fig. 4.15Design database linking requirements to architectural elements. Copyright 2016, Systemite—reprinted with permission
<img src=`./media/image118.jpeg` style=`width:4.49939in;height:2.755in` />
Fig. 4.16** Design database listing requirements for a specific function. Copyright 2016, Systemite> —reprinted with permission
<img src=`./media/image119.jpeg` style=`width:4.49736in;height:2.84in` />
Fig. 4.17Design database showing architectural components used when designing a specific function. Copyright 2016, Systemite—reprinted with permission
<img src=`./media/image120.jpeg` style=`width:4.49667in;height:3.045in` />
Fig. 4.18** Linking test cases to requirements. Copyright 2016, Systemite—reprinted with permis- sion
<img src=`./media/image121.jpeg` style=`width:4.49667in;height:3.045in` />
Fig. 4.19Tracking test progress. Copyright 2016, Systemite—reprinted with permission

The construction database and modelling tool provide the project teams with a consistent view on their software system. In the case of software architectures this tool allows us to link together all the views presented in Chap. [2](#_bookmark54) (such as physical, logical, and deployment) and therefore avoid unnecessary work to keep documents in a steady and consistent state. Most of the tools available for this purpose provide the possibility to handle multiple parallel versions and baselines, which is essential in the development of automotive software.

> 构建数据库和建模工具为项目团队提供了对其软件系统的一致性视图。在软件体系结构的情况下，此工具使我们能够将 CHAP 中显示的所有视图链接在一起。[2](#_bookmark54)(例如物理，逻辑和部署)，因此避免了不必要的工作以使文档保持稳定和一致的状态。用于此目的的大多数工具提供了处理多个并行版本和基线的可能性，这对于汽车软件的开发至关重要。

## Further Reading

In this chapter we outlined the practical aspects of automotive software development from a bird’s eye perspective. Interested readers can turn to more literature in the area to dive deeper into details.

> 在本章中，我们从鸟类的角度概述了汽车软件开发的实际方面。有兴趣的读者可以转向该领域的更多文献，以深入研究细节。

For the automotive software processes we recommend the book by Schäuffele and Zurawka [[SZ05](#_bookmark268)], which presents a classical view on automotive software development, starting from low-level processor programming and moving on to advanced functionality development.

> 对于汽车软件流程，我们推荐 Schäuffele 和 Zurawka [SZ05](#_bookmark268)]的这本书，该书从低级处理器程序开始，并继续进行高级功能开发。

The classical paper by Broy [[Bro06](#_bookmark229)] describing the challenges in automotive software engineering is the next step to understanding the dynamics of automotive

> BROY [BRO06](#_bookmark229)]的古典论文描述汽车软件工程的挑战是了解汽车动态的下一步

software engineering in general. This reading can be complemented by the paper by Pretschner et al. [[PBKS07](#_bookmark256)], where the focus is on the future of automotive software development.

> 一般软件工程。Pretschner 等人的论文可以补充该读物。[PBKS07](#_bookmark256)]，其中重点是汽车软件开发的未来。

Readers interested in the management of variability in general should explore the work of Bosch et al. [[VGBS01](#_bookmark271), [SVGB05](#_bookmark267)] or [[BFG+01](#_bookmark228)]. The work is based on software product lines, but applies very well to the automotive sector. This can be complemented with more recent developments in this area—software ecosystems and their realization in the automotive sector [[EG13](#_bookmark238), [EB14](#_bookmark237)].

> 一般对可变性管理感兴趣的读者应该探索 Bosch 等人的工作。[[VGBS01](#_bookmark271)、[SVGB05](#_bookmark267)] 或 [[BFG+01](#_bookmark228)]。这项工作基于软件产品线，但非常适用于汽车行业。这可以与该领域最近的发展相辅相成——软件生态系统及其在汽车领域的实现 [[EG13](#_bookmark238), [EB14](#_bookmark237)]。

Otto et al. [[Ott12](#_bookmark254)] and [[Ott13](#_bookmark255)] presents a study on requirements engineering at Mercedes-Benz, where they classified over 5800 requirement review protocols to their quality model. Their results showed that textual requirements (or natural language requirements as they are called in the publication) are prone to such problems as inconsistency, incompleteness and ambiguity—with about 70% of defects in requirements falling into these categories. In the light of this article we can see the need for complementing the textual requirements with more context, provided by use case models, user stories and use cases.

> 奥托等人。[[Ott12](#_bookmark254)] 和 [[Ott13](#_bookmark255)] 介绍了梅赛德斯-奔驰的需求工程研究，他们将 5800 多个需求审查协议分类到他们的质量模型中。他们的结果表明，文本需求(或在出版物中称为自然语言需求)容易出现不一致、不完整和歧义等问题——大约 70% 的需求缺陷属于这些类别。根据本文，我们可以看到用用例模型、用户故事和用例提供的更多上下文来补充文本需求的必要性。

Törner et al. [[TIPÖ06](#_bookmark269)] presented a similar study but of the requirements at Volvo Car Group. In contrast to the study of Otto et al. [[Ott12](#_bookmark254)], these authors studied the use case specifications and not the textual requirements. The results, however, are similar, as the main types of defects are missing elements (correctness in Otto et al.’s model) and incorrect linguistics (ambiguity in Otto et al.’s model).

> Törner 等。[tipö06](#_bookmark269)]提出了类似的研究，但沃尔沃汽车组的要求。与 Otto 等人的研究相反。[OTT12](#_bookmark254)]这些作者研究了用例规范，而不是文本要求。但是，结果是相似的，因为缺陷的主要类型是缺失的元素(Otto 等人的模型中的正确性)和不正确的语言学(Otto 等人的模型中的模棱两可)。

Eliasson et al. [[EHKP15](#_bookmark239)] described further experiences from Volvo Car Group where they explored challenges with requirements engineering at large in a mecha- tronics development organization. Their findings showed that there is a lot of communication in parallel to the requirements specification. The stakeholders in the requirements specification frequently mentioned the need to have a good network in order to specify the requirements correctly. This indicates the challenges described previously in this chapter that the requirements need more context than is usually provided in just the specification (especially the textual specification).

> Eliasson 等。[EHKP15](#_bookmark239)]描述了沃尔沃汽车集团的进一步经验，他们在 Mecha-Tronics Development Homchany 中探索了大型需求工程的挑战。他们的发现表明，与需求规范并行的交流很多。需求规范中的利益相关者经常提到需要一个良好的网络才能正确指定要求。这表明本章前面描述的挑战是，要求需要比仅规范中通常提供的上下文(尤其是文本规范)。

Mahally et al. [[MMSB15](#_bookmark246)] identified requirements to be the main barriers and enablers in moving towards Agile mechatronics organizations. Although today OEMs try to move towards fast development of mechatronics and reduce the cycle time by using Agile software development approaches, the challenges are that we do not know upfront whether a requirement requires the development of electronics or is only a software requirement. According to Mahally et al. that kind of problem needs to be solved, and based on the prediction of Houdek [[Hou13](#_bookmark241)] this kind of issue might be coming to an end as device development flattens out and most of the requirements become software requirements. Similar challenges were presented by Pernstål et al. [[PGFF13](#_bookmark258)] who found that requirements engineering is one of the top improvement areas for automotive OEMs. The ability to communicate via requirements was also an important part.

> Mahally 等。[MMSB15](#_bookmark246)]确定要求是朝着敏捷机电组织组织发展的主要障碍和推动力。尽管今天 OEM 试图通过使用敏捷软件开发方法来快速开发机电一体化并减少周期时间，但挑战是我们不知道需求是否需要电子设备开发或仅是软件需求。根据 Mahally 等人的说法。需要解决这种问题，并基于 Houdek [Hou13](#_bookmark241)]的预测，随着设备开发的变平，大多数要求成为软件要求，这种问题可能会结束。Pernstål 等人提出了类似的挑战。[PGFF13](#_bookmark258)]发现需求工程是汽车 OEM 的主要改进领域之一。通过要求进行交流的能力也是重要的部分。

At Audi, Allmann et al. [[AWK+06](#_bookmark227)] presented the challenges in the requirements communication on the boundary between the OEMs and their suppliers. They identified the need for better communication and the challenges of communicating through textual representations. They recognized the need for tighter partnerships as there is an inherent deficiency in communicating through requirements— transferring knowledge through an intermediate medium. Therefore they recom- mended integrating systems to minimize knowledge loss via transfer of documents. Siegl et al. [[SRH15](#_bookmark266)] presented a method for formalizing requirements specifica- tions using the Time Usage Model and applied it successfully to a requirements specification from one of the German OEMs. The evaluation study showed an increase in test coverage and increased quality of the requirements specification.

> 在奥迪，Allmann 等。[AWK + 06](#_bookmark227)]在 OEMS 及其供应商之间边界的需求通信中提出了挑战。他们确定了进行更好的沟通和通过文本表示进行沟通的挑战的必要性。他们认识到需要更紧密的合作伙伴关系，因为通过需求进行交流存在固有的缺陷 - 通过中间媒介传输知识。因此，他们推荐整合系统，以通过文档传输来最大程度地减少知识损失。Siegl 等。[SRH15](#_bookmark266)]提出了一种使用时间使用模型进行正式要求特定要求的方法，并将其成功应用于德国 OEM 之一的要求规范。评估研究表明，测试覆盖范围和需求规范质量的提高。

At BMW, Hardt et al. [[HMB02](#_bookmark240)] demonstrated the use of formalized domain engineering models in order to reason about the dependencies between requirements in the presence of variants. Their approach provided a simplistic, yet powerful, formalism and its strength was industrial applicability.

> 在宝马，Hardt 等。[HMB02](#_bookmark240)]演示了使用形式化的域工程模型，以便在存在变体的存在下对需求之间的依赖关系进行推理。他们的方法提供了一种简单而强大的形式主义，其力量是工业的适用性。

A study of the functional architecture of a car project at BMW and the requirements linked to the functions by Vogelsang and Fuhrmann [[VF13](#_bookmark270)] showed that 85% of functions are dependent on one another and that these dependencies cause a significant number of problems in software projects. This study shows the complexity of the functional decomposition of the vehicle’s design and the complexity of its description.

> 对宝马汽车项目的功能架构的研究以及 Vogelsang 和 Fuhrmann [VF13](#_bookmark270)]与功能相关的要求，**表明 85％的功能彼此依赖，并且这些依赖性彼此造成软件项目中有很多问题**。这项研究显示了车辆设计功能分解的复杂性及其描述的复杂性。

At Bosch, the longitudinal study of a 5-year project by Langenfeld et al. [[LPP16](#_bookmark245)] showed that 61% of defects in requirements come from the incompleteness or incorrectness of the requirements specifications.

> 在 Bosch，Langenfeld 等人对 5 年项目的纵向研究。[LPP16](#_bookmark245)]表明，需求中有 61％的缺陷来自需求规格的不完整或不正确。

One of interesting trends in requirements engineering is the automatization of tasks of requirements engineers. One of such tasks is the discovery of non-functional requirements. This task is based on reading the specifications of functional require- ments and identifying phrases which should transform into non-functional require- ments. A study on the automation of this task has been conducted by Cleland- Huang et al. [[CHSZS07](#_bookmark231)]. The study showed that the automated classification of requirements could be as good as 90%, but at this stage cannot replace the manual classifiers.

> 需求工程的有趣趋势之一是需求工程师任务的自动化。这样的任务之一是发现非功能要求。此任务是基于阅读功能要求的规格，并识别应转换为非功能要求的短语。Cleland-Huang 等人已经进行了有关此任务自动化的研究。[CHSZS07](#_bookmark231)]。研究表明，需求的自动分类可能高达 90％，但在此阶段无法替代手动分类器。

### _Requirements Specification Languages_

A model for requirements traceability [[DPFL10](#_bookmark235)] DARWIN4Req has been proposed to address the challenges related to the ability to follow the requirements’ lifecycle. The model allows us to link requirements expressed in different formalities (e.g. UML, SySML) and connect them to one another. However, to the best of our knowledge, the model and the tool have not been adopted on a wider scale yet.

> 已提出了一种需求可追溯性的模型 [DPFL10](#_bookmark235)] darwin4req 已提出，以解决与遵循需求的生命周期能力相关的挑战。该模型允许我们链接以不同手续(例如 UML，sysml)表示的要求，并将其连接到彼此。但是，据我们所知，该模型和工具尚未按更广泛的规模采用。

EAST-ADL [[DSLT05](#_bookmark236)] is an architecture specification language which contains elements to capture requirements and link them to the architectural design. The approach is similar to that of SySML but with the difference that there is no dedicated requirements specification diagram. EAST-ADL has been demonstrated to work in industry; however, it is not a standard for automotive OEMs yet. Mahmud [[MSL15](#_bookmark252)] presented a language ReSA that complements the EAST-ADL modelling language with the possibility to analyze and validate requirements (e.g. basic consistency checks).

> East-Adl [DSLT05](#_bookmark236)]是一种体系结构规范语言，其中包含以捕获需求并将其链接到架构设计的元素。该方法类似于 SYSML 的方法，但区别没有专用的要求规范图。East-Adl 已被证明在工业中工作。但是，这还不是汽车 OEM 的标准。mahmud [MSL15](#_bookmark252)]提出了一种语言 RESA，该语言补充了 East-ADL 建模语言，具有分析和验证要求的可能性(例如，基本的一致性检查)。

For non-functional requirements in the domain of safety, Peraldi [[PFA10](#_bookmark257)] has proposed another extension of the EAST-ADL language which allows for increased traceability of requirements and their linking to non-functional properties of the designed embedded software (e.g. Safety).

> 对于安全领域中的非功能要求，Peraldi [PFA10](#_bookmark257)]提出了 East-ADL 语言的另一种扩展，使需求的透气性及其与它们与非功能性属性的联系增加设计的嵌入式软件(例如安全性)。

Mellegård and Staron [[MS09](#_bookmark248)] and [[MS10c](#_bookmark251)] conducted an empirical study on the impact of using hierarchical graphical requirements specification on the quality of change impact assessment. For this purpose they designed a requirements’ specification language based on the existing formalism—Requirements Abstraction Model. The results showed that the graphical overview of the dependencies between requirements introduces significant improvement [[KS02](#_bookmark243)].

> Mellegård 和 Staron [MS09](#_bookmark248)] ]和 [ms10c](#_bookmark251)]进行了一项关于使用层次图形要求规范对变化影响质量影响评估的层次图形要求规范的影响的经验研究。为此，他们根据现有的形式主义设计了需求的规范语言 - 要求抽象模型。结果表明，需求之间的依赖关系的图形概述引入了显着的改进 [KS02](#_bookmark243)]。

Finally, the use of models as core artifacts in software development in the automotive domain has been studied in the context of MDA (Model-Driven Architecture) [[SKW04a](#_bookmark263), [SKW04b](#_bookmark264), [SKW04c](#_bookmark265)]. The important aspect is the evolution of models throughout the lifecycle.

> 最后，在 MDA(模型驱动的体系结构)的背景下，研究了模型作为软件开发中的核心工件 [SKW04A](#_bookmark263)，[skw04b](#_kw04b](#_bookmark264)，[SKW04C](#_bookmark265)]。重要方面是模型在整个生命周期中的演变。

## Summary

Correct, unambiguous and consistent requirements specifications are foundations for high-quality software in general and in the automotive embedded systems in particular. In this chapter we introduced the most common types of requirements used in this domain and provided their main strengths.

> 正确，明确和一致的需求规格是一般，尤其是汽车嵌入式系统的高质量软件的基础。在本章中，我们介绍了该域中使用的最常见的要求类型，并提供了其主要优势。

Based on the current state of evolution of automotive software we could observe three trends in requirements engineering for automotive embedded systems—

> 基于汽车软件的当前发展状态，我们可以观察到汽车嵌入式系统需求工程的**三个趋势** -

\(1\) agility in requirements specification, (2) increased focus on non-functional requirements and (3) increased focus on security as a domain for requirements. Towards the end of the chapter we also provided an overview of the requirements practices at some of the vehicle manufacturers (Mercedes Benz, Audi, BMW and Volvo) based on documented experiences at these companies. We have also pointed out a number of directions for further reading for the interested.

> \(1 \)在需求规范中，(2)增加对非功能要求的关注，以及(3)增加对安全性作为需求领域的关注。在本章结束时，我们还根据这些公司的经验经验，概述了一些车辆制造商(梅赛德斯·奔驰，奥迪，宝马和沃尔沃)的需求实践。我们还指出了许多指示，以进一步阅读感兴趣的人。

In our future work we plan to review the requirements engineering practices in the main automotive OEMs and identify their differences and commonalities.

> 在未来的工作中，我们计划在主要汽车 OEM 中审查需求工程实践，并确定它们的差异和共同点。

## References

> </span>ASM+14. Vard Antinyan, Miroslaw Staron, Wilhelm Meding, Per Österström, Erik Wikstrom, Johan Wranker, Anders Henriksson, and Jörgen Hansson. Identifying risky areas of software code in agile/lean software development: An industrial experience report. In _Software Maintenance, Reengineering and Reverse Engineering (CSMR-WCRE), 2014 Software Evolution Week-IEEE Conference on_, pages 154–163. IEEE, 2014.

> AWK+06. Christian Allmann, Lydia Winkler, Thorsten Kölzow, et al. The requirements engi- neering gap in the OEM-supplier relationship. _Journal of Universal Knowledge Management_, 1(2):103–111, 2006.

> BFG+ 01. Jan Bosch, Gert Florijn, Danny Greefhorst, Juha Kuusela, J Henk Obbink, and Klaus Pohl. Variability issues in software product lines. In _International Workshop on Software Product-Family Engineering_, pages 13–21. Springer, 2001.

> Bro06. Manfred Broy. Challenges in automotive software engineering. In _Proceedings of the 28th international conference on Software engineering_, pages 33–42. ACM, 2006.

> C+ 90. IEEE Standards Coordinating Committee et al. IEEE Standard glossary of software engineering terminology (IEEE Std 610.12–1990). Los Alamitos. _CA: IEEE Computer Society_, 1990.

> CHSZS07. Jane Cleland-Huang, Raffaella Settimi, Xuchang Zou, and Peter Solc. Automated classification of non-functional requirements. _Requirements Engineering_, 12(2):103– 120, 2007.

> CTS+ 06. DeJiu Chen, Martin Törngren, Jianlin Shi, Sebastien Gerard, Henrik Lönn, David Servat, Mikael Strömberg, and Karl-Erik Årzen. Model integration in the development of embedded control systems-a characterization of current research efforts. In _Computer Aided Control System Design, 2006 IEEE International Conference on Control Applications, 2006 IEEE International Symposium on Intelligent Control, 2006 IEEE_, pages 1187–1193. IEEE, 2006.

> DB15. Jan Dannenberg and Jan Burgard. 2015 car innovation: A comprehensive study on innovation in the automotive industry. 2015.

> Dem12. Simulink Demo. Modeling an anti-lock braking system. _Copyright 2005–2010 The MathWorks, Inc_, 2012.

> DPFL10. Hubert Dubois, Marie-Agnès Peraldi-Frati, and Fadoi Lakhal. A model for require- ments traceability in a heterogeneous model-based design process: Application to automotive embedded systems. In _Engineering of Complex Computer Systems (ICECCS), 2010 15th IEEE International Conference on_, pages 233–242. IEEE, 2010.

> DSLT05. Vincent Debruyne, Françoise Simonot-Lion, and Yvon Trinquet. EAST–ADL – An architecture description language. In _Architecture Description Languages_, pages 181– 195\. Springer, 2005.

> EB14. Ulrik Eklund and Jan Bosch. Architecture for embedded open software ecosystems. _Journal of Systems and Software_, 92:128–142, 2014.

> EG13. Ulrik Eklund and Håkan Gustavsson. Architecting automotive product lines: Industrial practice. _Science of Computer Programming_, 78(12):2347–2359, 2013.

> EHKP15. Ulf Eliasson, Rogardt Heldal, Eric Knauss, and Patrizio Pelliccione. The need of complementing plan-driven requirements engineering with emerging communication: Experiences from Volvo Car Group. In _Requirements Engineering Conference (RE), 2015 IEEE 23rd International_, pages 372–381. IEEE, 2015.

> HMB02. Markus Hardt, Rainer Mackenthun, and Jürgen Bielefeld. Integrating ECUs in vehicles- requirements engineering in series development. In _Requirements Engineering, 2002. Proceedings. IEEE Joint International Conference on_, pages 227–236. IEEE, 2002.

> Hou13. Frank Houdek. Managing large scale specification projects. In _Requirements Engineering foundations for software quality, REFSQ_, 2013.

> JBR97. Ivar Jacobson, Grady Booch, and Jim Rumbaugh. The objectory software development process. _ISBN: 0-201-57169-2, Addison Wesley_, 1997.

> KS02. Ludwik Kuzniarz and Miroslaw Staron. On practical usage of stereotypes in UML- based software development. _the Proceedings of Forum on Design and Specification Languages, Marseille_, 2002.

> KSM+15. Eric Knauss, Miroslaw Staron, Wilhelm Meding, Ola Söder, Agneta Nilsson, and Magnus Castell. Supporting continuous integration by code-churn based test selection. In _Proceedings of the Second International Workshop on Rapid Continuous Software Engineering_, pages 19–25. IEEE Press, 2015.

> LPP16. Vincent Langenfeld, Amalinda Post, and Andreas Podelski. Requirements Defects over a Project Lifetime: An Empirical Analysis of Defect Data from a 5-Year Automotive Project at Bosch. In _Requirements Engineering: Foundation for Software Quality_, pages 145–160. Springer, 2016.

> MMSB15. Mahshad M Mahally, Miroslaw Staron, and Jan Bosch. Barriers and enablers for shortening software development lead-time in mechatronics organizations: A case study. In _Proceedings of the 2015 10th Joint Meeting on Foundations of Software Engineering_, pages 1006–1009. ACM, 2015.

> MS08. Niklas Mellegård and Miroslaw Staron. Methodology for requirements engineering in model-based projects for reactive automotive software. In _18th ECOOP Doctoral Symposium and PhD Student Workshop_, page 23, 2008.

> MS09. Niklas Mellegård and Miroslaw Staron. A domain specific modelling language for specifying and visualizing requirements. In _The First International Workshop on Domain Engineering, DE@mailto:DE@ CAiSE, Amsterdam_, 2009.

> MS10a. Niklas Mellegård and Miroslaw Staron. Characterizing model usage in embedded software engineering: a case study. In _Proceedings of the Fourth European Conference on Software Architecture: Companion Volume_, pages 245–252. ACM, 2010.

> MS10b. Niklas Mellegård and Miroslaw Staron. Distribution of effort among software development artefacts: An initial case study. In _Enterprise, Business-Process and Information Systems Modeling_, pages 234–246. Springer, 2010.

> MS10c. Niklas Mellegård and Miroslaw Staron. Improving efficiency of change impact assessment using graphical requirement specifications: An experiment. In _Product- focused software process improvement_, pages 336–350. Springer, 2010.

> MSL15. Nesredin Mahmud, Cristina Seceleanu, and Oscar Ljungkrantz. ReSA: An ontology- based requirement specification language tailored to automotive systems. In _Industrial Embedded Systems (SIES), 2015 10th IEEE International Symposium on_, pages 1–10. IEEE, 2015.

> Org11. International Standards Organization. 26262–road vehicles-functional safety. _Interna- tional Standard ISO_, 26262, 2011.

> Ott12. Daniel Ott. Defects in natural language requirement specifications at Mercedes- Benz: An investigation using a combination of legacy data and expert opinion. In _Requirements Engineering Conference (RE), 2012 20th IEEE International_, pages 291– 296\. IEEE, 2012.

> Ott13. Daniel Ott. Automatic requirement categorization of large natural language specifi- cations at Mercedes-Benz for review improvements. In _Requirements Engineering: Foundation for Software Quality_, pages 50–64. Springer, 2013.

> PBKS07. Alexander Pretschner, Manfred Broy, Ingolf H Kruger, and Thomas Stauner. Software engineering for automotive systems: A roadmap. In _2007 Future of Software Engineer- ing_, pages 55–71. IEEE Computer Society, 2007.

> PFA10. Marie-Agnès Peraldi-Frati and Arnaud Albinet. Requirement traceability in safety crit- ical systems. In _Proceedings of the 1st Workshop on Critical Automotive applications: Robustness & Safety_, pages 11–14. ACM, 2010.

> PGFF13. Joakim Pernstål, Tony Gorschek, Robert Feldt, and Dan Florén. Software process improvement in inter-departmental development of software-intensive automotive systems – A case study. In _Product-Focused Software Process Improvement_, pages 93–107. Springer, 2013.

> RSB+13a. Rakesh Rana, Miroslaw Staron, Christian Berger, Jörgen Hansson, Martin Nilsson, and Fredrik Torner. Evaluating long-term predictive power of standard reliability growth models on automotive systems. In _Software Reliability Engineering (ISSRE), 2013 IEEE 24th International Symposium on_, pages 228–237. IEEE, 2013.

> RSB+13b. Rakesh Rana, Miroslaw Staron, Christian Berger, Jörgen Hansson, Martin Nilsson, and Fredrik Törner. Improving fault injection in automotive model based development using fault bypass modeling. In _GI-Jahrestagung_, pages 2577–2591, 2013.

> RSM+13. Rakesh Rana, Miroslaw Staron, Niklas Mellegård, Christian Berger, Jörgen Hansson, Martin Nilsson, and Fredrik Törner. Evaluation of standard reliability growth models in the context of automotive software systems. In _Product-Focused Software Process Improvement_, pages 324–329. Springer, 2013.

> SHF+ 13. Miroslaw Staron, Jorgen Hansson, Robert Feldt, Anders Henriksson, Wilhelm Meding, Sven Nilsson, and Christoffer Hoglund. Measuring and visualizing code stability – A case study at three companies. In _Software Measurement and the 2013 Eighth International Conference on Software Process and Product Measurement (IWSM- MENSURA), 2013 Joint Conference of the 23rd International Workshop on_, pages 191–200. IEEE, 2013.

> SKW04a. Miroslaw Staron, Ludwik Kuzniarz, and Ludwik Wallin. Case study on a process of industrial MDA realization: Determinants of effectiveness. _Nordic Journal of Computing_, 11(3):254–278, 2004.

> SKW04b. Miroslaw Staron, Ludwik Kuzniarz, and Ludwik Wallin. A case study on industrial MDA realization – Determinants of effectiveness. _Nordic Journal of Computing_, 11(3):254–278, 2004.

> SKW04c. Miroslaw Staron, Ludwik Kuzniarz, and Ludwik Wallin. Factors determining effective realization of MDA in industry. In K. Koskimies, L. Kuzniarz, Johan Lilius, and Ivan Porres, editors, _2nd Nordic Workshop on the Unified Modeling Language_, volume 35, pages 79–91. Abo Akademi, 2004.

> SRH15. Sebastian Siegl, Martin Russer, and Kai-Steffen Hielscher. Partitioning the require- ments of embedded systems by input/output dependency analysis for compositional creation of parallel test models. In _Systems Conference (SysCon), 2015 9th Annual IEEE International_, pages 96–102. IEEE, 2015.

> SVGB05. Mikael Svahnberg, Jilles Van Gurp, and Jan Bosch. A taxonomy of variability realization techniques. _Software: Practice and Experience_, 35(8):705–754, 2005.

> SZ05. Jörg Schäuffele and Thomas Zurawka. _Automotive software engineering – Principles, processes, methods and tools_. 2005.

> TIPÖ06. Fredrik Törner, Martin Ivarsson, Fredrik Pettersson, and Peter Öhman. Defects in automotive use cases. In _Proceedings of the 2006 ACM/IEEE international symposium on Empirical software engineering_, pages 115–123. ACM, 2006.

> VF13. Andreas Vogelsanag and Steffen Fuhrmann. Why feature dependencies challenge the requirements engineering of automotive systems: An empirical study. In _Requirements Engineering Conference (RE), 2013 21st IEEE International_, pages 267–272. IEEE, 2013.

> VGBS01. Jilles Van Gurp, Jan Bosch, and Mikael Svahnberg. On the notion of variability in software product lines. In _Software Architecture, 2001. Proceedings. Working IEEE/IFIP Conference on_, pages 45–54. IEEE, 2001.

> WW02. Matthias Weber and Joachim Weisbrod. Requirements engineering in automotive development-experiences and challenges. In _Requirements Engineering, 2002. Pro- ceedings. IEEE Joint International Conference on_, pages 331–340. IEEE, 2002.
