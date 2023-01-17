# Foreword

`The fear of error is the error itself.` Famous philosopher G.F.W. Hegel, whose 250th birthday we currently commemorate, underlined the very necessity of inno- vation and thinking out of the box. Innovation needs guidance but must not be overconstrained. As engineers, we should follow critical rules but also allow error and learn from it—in order to move forward and not administrate the past. This book will provide guidance toward innovative automotive architectures and services— along the lines of Hegel.

> `对错误的恐惧是错误本`。著名哲学家 G.F.W.黑格尔目前纪念他的 250 岁生日，他强调了创新和思考的必要性。创新需要指导，但不能过度限制。作为工程师，我们应该遵循关键规则，但也允许错误并从中学习 - 为了前进而不是管理过去。这本书将在黑格尔的线路上为创新的汽车架构和服务提供指导。

Software and IT are the major drivers of modern cars—both literally and from a marketing perspective. Modern vehicles have more than 70 electronic control units (ECUs), with premium cars having more than 100 such embedded computer systems. Some functions, such as engine control or dynamics, are hard real-time functions, with reaction times going down to a few milliseconds. Practically all other functions, such as infotainment, demand at least soft real-time behaviors.

> 软件及其是现代汽车的主要驱动力 - 从字面上看，也是营销的角度。现代车辆拥有 70 多个电子控制单元(ECU)，高级汽车具有 100 多种此类嵌入式计算机系统。某些功能，例如发动机控制或动力学，是硬实时功能，反应时间降低到几毫秒。实际上，所有其他功能，例如信息娱乐，至少需要软实时行为。

The complexity of automotive systems and services is growing fast. Each auto- motive area has its own requirements for computation speed, reliability, security, safety, flexibility, and extensibility. Automotive electronic systems map functions such as braking, powertrain, or lighting controls to individual software systems and physical hardware. The resulting complexity has reached a limit that demands an architectural restart (Fig. [1](#_bookmark0)). At the same time, innovative functions such as connectivity with external infrastructures and vehicle-to-vehicle communication demand IT backbone and cloud solutions with service-oriented architectures (SOA). Software and IT in vehicles and their environments are evolving at a fast pace. Multimodal mobility will connect previously separated domains like cars and public transportation. Mobility-oriented services such as car sharing create completely new ecosystems and business models far away from the classic `buy- your-own-car` approach. Autonomous driving demands highly interactive services with multisensor fusion, vastly different from the currently deployed functionally isolated control units. Connectivity and infotainment have transformed the car into a distributed IT system with cloud access, over-the-air functional upgrades, and high- bandwidth access to map services, media content, other vehicles, and surrounding infrastructure. Energy efficiency evolves the classic powertrain toward high-voltage hybrid and electric engines.

> 汽车系统和服务的复杂性正在迅速增长。每个自动区域对计算速度，可靠性，安全性，灵活性和可扩展性都有其自身的要求。汽车电子系统映射诸如制动，动力总成或照明控件之类的功能，可用于单个软件系统和物理硬件。最终的复杂性已达到需要架构重新启动的极限(图 [1](#_bookmark0))。同时，诸如与外部基础架构的连通性以及车辆到车辆通信的连接性需要骨干和云解决方案，并使用面向服务的体系结构(SOA)。软件及其在车辆及其环境中正在以快速发展。多模式移动性将连接先前分开的域，例如汽车和公共交通工具。诸如汽车共享等面向移动性的服务创造了全新的生态系统和业务模型，远离经典的 `购买 - 您拥有的汽车` 方法。自动驾驶要求具有多传感器融合的高度交互式服务，与当前部署的功能隔离控制单元有很大不同。连接性和信息娱乐已将汽车转变为具有云访问，空中功能升级以及高度带宽访问地图服务，媒体内容，其他车辆以及周围环境的分布式 IT 系统基础设施。能源效率将经典动力总成朝高压混合动力和电动发动机发展。

Fig. 1 The convergence of IT and EE fuels automotive technology

The major driver in the 2020s is convergence. We face a fast integration of the previously separated concepts of IT and E/E. Software engineering for automotive systems encompasses modern embedded and cloud technologies, distributed com- puting, real-time systems, mixed safety and security systems, and, not least, the connection of all that to long-term sustainable business models.

> 2020 年代的主要驱动力是融合。我们面临着先前分开的 IT 和 E/E 的快速整合。汽车系统的软件工程包括现代嵌入式技术和云技术，分布式组合，实时系统，混合安全和安全系统，以及所有这些与长期可持续业务模型的联系。

Automotive engineers must master both domains, paired with functional safety and cybersecurity. Today automotive software is spearheading IT innovation. The everyday relevance of automotive software to today’s software engineers is high, and it is the focus of this book to bring this message to practitioners.

> 汽车工程师必须掌握两个领域，并配对功能安全性和网络安全性。如今，汽车软件正在率领 IT 创新。汽车软件与当今软件工程师的日常相关性很高，这是本书将此信息带给从业者的重点。

Technology trends are converging across industries (Fig. [2](#_bookmark1)). What used to be a clear-cut differentiation can be summarized today by the quest for ACES, i.e., autonomous systems, convergence, ecology, and services. Business trends are similar in developed and emerging economies. Ten years ago, only 2 out of 10 most valuable public companies by market capitalization were tech companies. Today, almost all are highly driving, and driven by, software technology. Failures to recognize future trends and challenges would be like entering the next decade with all senses closed.

> 技术趋势正在跨行业融合(图 [2](#_bookmark1))。过去可以通过对 ACE(即自主系统，融合，生态和服务)的探索来概括过去的明确差异化。发达和新兴经济体的业务趋势相似。十年前，根据市值，只有 10 个最有价值的上市公司中只有 2 个是科技公司。如今，几乎所有人都高度驾驶，并且由软件技术驱动。未能识别未来趋势和挑战的失败就像进入接下来的十年，所有感官都关闭了。

While converging to the new normal, priorities are shifting heavily. Autonomy, until recently still a number one shooting star, has started its slowdown along the hype cycle. At the same time, ecology gets to speed with a high focus especially of the young generation on our future and the sustainability of our earth. Convergence levers the two forces of competitiveness and innovation toward a sustainable business prospective for technology companies. Services are the major driver. Services are very appealing and we have been talking about them for many years. It follows the Kano model at its best because a good service for a mediocre product can create real excitement. Provide 24/7 online support and you earn a big `wow` if you deliver.

> 在收敛到新的正常状态时，优先事项正在大大转移。直到最近仍然是头号射击恒星，自主权一直在炒作周期开始放缓。同时，生态学以很高的重点加速，尤其是年轻一代对我们的未来和地球的可持续性。融合杠杆竞争力和创新的两种力量朝着技术公司的可持续业务前景。服务是主要驱动力。服务非常吸引人，我们已经谈论了很多年了。它遵循 Kano 模型的最佳状态，因为平庸产品的优质服务可以引起真正的兴奋。提供 24/7 的在线支持，如果您交付的话，您将获得大量的 `哇` 。

<Fig. 2 Prepare for the future: ACES makes digital winners

To master this fast-growing complexity, automotive software needs a clear architecture. Architecture evolution today is the major focus across companies, and thus the book arrives just at the right time. The impacts of architecture are manifold, such as systems modeling, testing, and simulation with models in the loop; the combination of several quality requirements such as safety; service- oriented advanced operating systems with secure communication platforms, such as adaptive AUTOSAR (Automotive Open System Architecture); multisensor fusion and picture recognition for ADAS (advanced driver-assistance systems) and autonomous driving; distributed end-to-end security for flexible remote software updates directly into the car’s firmware; and connectivity of cloud technologies and IT backbones with billions of cars and their onboard devices for infotainment, online apps, remote diagnosis, and emergency call processing.

> 为了掌握这种快速增长的复杂性，汽车软件需要清晰的体系结构。当今的架构演变是整个公司的主要重点，因此该书就到了正确的时间。体系结构的影响是多种多样的，例如循环中模型的系统建模，测试和模拟。结合了几种质量要求，例如安全；具有安全通信平台的面向服务的高级操作系统，例如自适应汽车(汽车开放系统体系结构)；ADA(高级驾驶员辅助系统)和自动驾驶的多传感器融合和图片识别；为灵活的远程软件更新的端到端分布式安全性直接在汽车的固件中分布；以及云技术和 IT 骨架的连通性，具有数十亿辆汽车及其在线娱乐，在线应用程序，远程诊断和紧急通话处理的机上设备。

This second edition of the already classic primer on Automotive Software comprehensively introduces to automotive software architecture. Authored by renowned expert Miroslaw Staron, this book provides a guided tour through the methodology and usage of automotive software architecture. Starting with a brief introduction to software architecture paradigms, it quickly moves to current application domains, such as AUTOSAR. Architecture analysis with methods such as ATAM (Architecture Trade-off Analysis Method) of the Software Engineering Institute provides hands-on guidance, keeping in mind the current paradigm shift from classic networking controllers toward the three-tier model of future automotive IT.

> 第二版的《汽车软件》中已经经典的底漆全面介绍了汽车软件体系结构。这本书由著名的专家 Miroslaw Staron 撰写，通过汽车软件体系结构的方法和使用提供了指导之旅。从简要介绍软件体系结构范例开始，它迅速转移到当前的应用程序域，例如 AutoSar。软件工程学院的 ATAM(架构权衡分析方法)等方法的架构分析提供了动手指导，请记住当前从经典网络控制器向未来汽车 IT 的三层模型的范式转移。

Miroslaw Staron with his coauthors target with this book both engineers and decision-makers in the automotive electronics and IT domain. They guide engineers, developers, and managers along the convergence of the two worlds of IT and embedded systems. Education however has only in rare cases dedicated programs for engineering these converging IT and embedded systems. Business models will evolve toward flexible service-oriented architectures and ecosystems. Reference points based on industry standards such as three-tier cloud architectures, adaptive AUTOSAR, and Ethernet connectivity facilitate reuse across companies and indus- tries. The classicctional split is replaced by a more service-oriented architecture and delivery model. Development in the future will be a continuous process that will fully decouple the rather stable hardware of the car from its functionality driven by software upgrades. Hierarchic modeling of business processes, functionality, and architecture from a systems perspective allows early simulation while ensuring robustness and security. Agile service delivery models combining DevOps, micro- services, and cloud solutions will allow functional changes far beyond the traditional V approach.

> Miroslaw Staron 与他的合着者瞄准了这本书，该书在汽车电子和 IT 领域中既有工程师和决策者。他们指导工程师，开发人员和管理人员沿着 IT 和嵌入式系统的两个世界的融合。然而，教育仅在极少数情况下专门用于工程的计划，以将其融合并嵌入式系统。业务模型将发展为灵活的面向服务的体系结构和生态系统。参考基于三层云体系结构，自适应汽车和以太网连接等行业标准的积分有助于整个公司和工业之间的再利用。经典的功能拆分被更面向服务的架构和交付模型所取代。未来的开发将是一个连续的过程，它将完全将汽车的相当稳定的硬件与软件升级驱动的功能相结合。从系统角度来看，业务流程，功能和体系结构的层次结构建模允许早期模拟，同时确保稳健性和安全性。将 DevOps，Micro-Services 和 Cloud Solutions 结合在一起的敏捷服务交付模型将允许功能更改远远超出传统 V 方法。

The techniques presented in this book are not supposed to be the ultimate truth. Yet they provide direction in this fast-evolving field. It will help you as well as your organization to grow your maturity. Our society and each of us depend on seamless mobility, and so we need to also trust these underlying systems of infrastructure and vehicles. Let us evolve the necessary technology, methods, and competencies in a positive direction to stay in control of automotive software and avoid the many pitfalls of classic IT systems. For this matter, I wish you all the best and success.

> 本书中提出的技术不应该是最终的真理。然而，它们在这个快速发展的领域提供了方向。它将帮助您以及组织的成熟度。我们的社会和我们每个人都取决于无缝的流动性，因此我们还需要信任这些基础设施和车辆的基础系统。让我们以积极的方向发展必要的技术，方法和能力，以控制汽车软件，并避免经典 IT 系统的许多陷阱。为此，祝您一切顺利。

As with all architecture independent of application domain, do not forget to deliver value and results to your markets. Your future is based on your competitiveness—both corporate and personal. It is not those to succeed who now shrink engineering and IT innovation, but those who navigate well in the magic triangle of quality, competitiveness, and innovation. Thinker, politician, and novelist Goethe got it straight: `Knowing is not enough; we must apply. Willing is not enough; we must do.` This is the wake-up call to use innovation and guts to stay competitive amidst a meager economic outlook. Business history is littered with the skeletons of those who take neither ownership nor risks.

> 与所有独立于应用领域的架构一样，请不要忘记为您的市场提供价值和结果。您的未来基于您的竞争力 - 包括公司和个人。现在，成功的人现在缩水了工程及其创新，而是那些在质量，竞争力和创新方面很好地导航的人。思想家，政治家和小说家歌德(歌德)直截了当： `知道还不够；我们必须申请。愿意不够；我们必须做。` 这是使用创新和胆量在微薄的经济前景中保持竞争力的警钟。商业历史上散布着那些既没有拥有所有权也没有风险的人的骨骼。

Software is omnipresent in our society. It controls everything from the backbone of electrical infrastructure, to telecommunication equipment to our watches. Cars are no exception, and the amount of software in modern cars is more than in any other consumer product. I was once asked by a colleague at a conference whether the car would still run if we kill the electronic components. The answer was `no` as basically all elements of modern cars are controlled by software—engine, brakes, windshield wipers, blinkers, radio, you name it.

> 软件在我们的社会中无所不在。它控制着从电气基础设施的骨干到电信设备到我们的手表的所有内容。汽车也不例外，现代汽车中的软件量比任何其他消费产品中都要多。同事在一次会议上曾经问我，如果我们杀死电子组件，这辆车是否仍会运行。答案是 `否` 的，因为现代汽车的所有元素都由软件控制 - 发动机，制动器，挡风玻璃刮水器，眨眼，广播，您可以命名。

In the last few years, the amount of software in cars has increased as electrifi- cation, connectivity, and autonomous drive became more prevalent in all segments. The complexity of scenarios for autonomous driving is so large that cars cannot drive autonomously all the time. Yet, they can drive in various scenarios without changing lanes, and they can change lanes in certain scenarios or even park themselves without anyone in the driver’s seat.

> 在过去的几年中，随着电气，连通性和自动驱动器在所有细分市场的普遍性，汽车中的软件量增加了。自动驾驶的场景的复杂性是如此之大，以至于汽车无法始终自动驾驶。但是，他们可以在各种情况下开车而无需更换车道，并且可以在某些情况下更换车道，甚至可以在没有任何人座位的情况下停放自己。

When this complexity grows, we face new challenges in the design of automotive software—more functions become safety critical, more functions interact and communication busses get overcrowded. We need to design the software with that in mind and we need to do it in a new way.

> 当这种复杂性增长时，我们在汽车软件的设计中面临着新的挑战 - 更多的功能变得至关重要，更多的功能相互作用，通信总线变得过度拥挤。我们需要考虑一下该软件，我们需要以新的方式进行。

In 2017, we published the first edition of this book, which became popular among students and practitioners alike. Many readers connected with me and asked for certain elements, pointed out to important new developments, and asked questions. I’ve taken these suggestions into consideration and I, once again, managed to convince my colleagues—Dr. Darko Durisic and Dr. Per Johannessen—to help in revising the book.

> 2017 年，我们出版了本书的第一版，该书在学生和从业者中都很流行。许多读者与我联系，并索要某些要素，并指出了重要的新发展，并提出了问题。我已经考虑了这些建议，我再次设法说服了我的同事。Darko Durisic 和 Per Johannessen 博士 - 帮助修改这本书。

The purpose of the book is to introduce the concept of software architecture as one of the cornerstones of software in modern cars. The book is a result of my work in the area of software engineering, with a particular focus on safety systems and software measurement. Throughout my research, I have worked with multiple companies in the automotive and telecom domains and I have noticed that over time these domains became increasingly similar. The processes and tools for developing software in modern cars became very similar to those used in the development of telecommunication systems. The same is true about software architectures—initially very different, today they are increasingly similar in terms of architectural styles, programming paradigms, and architectural patterns.

> 本书的目的是将软件体系结构的概念介绍为现代汽车中软件的基石之一。这本书是我在软件工程领域工作的结果，特别关注安全系统和软件测量。在整个研究中，我曾与汽车和电信域中的多家公司合作，我注意到随着时间的流逝，这些域变得越来越相似。在现代汽车中开发软件的过程和工具与在电信系统开发中使用的工具非常相似。软件架构也是如此 - 在截然不同的情况下，今天它们在架构样式，编程范式和架构模式方面越来越相似。

The book starts with a historical overview of the evolution of software in modern cars and the description of the main challenges which drive the evolution. Chapter [2](#_bookmark54) describes the main architectural styles of automotive software and their use in cars’ software. Chapter [3](#_bookmark154) is a new addition, where we learn about the modern software architectures—federated and centralized ones. In Chap. [4](#_bookmark185), the reader can find a description of software development processes used to develop software on the car manufacturer’s side. Chapter [5](#_bookmark273) introduces AUTOSAR—an important standard in automotive software. In this edition, this chapter discusses both the classic and adaptive AUTOSAR. Chapter [6](#_bookmark368) goes beyond simple architecture and describes the process of detailed design of automotive software with the use of Simulink, which helps us understand how the detailed design links to the high-level design. Chapter [7](#_bookmark451) is a new one and focuses on machine learning in automotive software development. Chapter [8](#_bookmark493) presents a method for assessing the quality of the architecture—ATAM (Architecture Trade-off Analysis Method)—and provides an example assessment. Chapter [9](#_bookmark558) presents an alternative way of assessing the architecture, namely, by using quantitative measures and indicators. In Chap. [10](#_bookmark642), we dive deeper into one of the specific properties discussed in Chap. [11](#_bookmark687)—safety—and can read about the important standard in that area—ISO/IEC 26262. This time, this chapter contains more information about the hardware than in the first edition of the book. Finally, Chap. [12](#_bookmark727) presents a set of future trends that seem to emerge today that have the potential to shape automotive software engineering in the coming years.

> 这本书从现代汽车中软件演变的历史概述开始，以及对推动进化的主要挑战的描述。[第[2]章](#_bookmark54)描述了汽车软件的主要体系结构风格及其在汽车软件中的使用。[第[3]章](#_bookmark154)是一个新的补充，我们在其中了解现代软件体系结构 - 填充和集中式体系。在第一章中。[4](#_bookmark185)，读者可以找到用于在汽车制造商方面开发软件的软件开发过程的描述。[第[5]章](#_bookmark273)介绍了 Autosar，这是汽车软件的重要标准。在此版本中，本章讨论了经典和自适应汽车。[第[6]章](#_bookmark368)超越了简单的体系结构，并使用 Simulink 使用 Simulink 描述了汽车软件的详细设计过程，这有助于我们了解如何详细的设计链接到高级设计。[第[7]章](#_bookmark451)是一个新的，专注于汽车软件开发中的机器学习。[第[8]章](#_bookmark493)提出了一种评估体系结构质量的方法 - ATAM(架构权衡分析方法)，并提供了一个示例评估。[第[9]章](#_bookmark558)提出了一种评估体系结构的替代方法，即使用定量措施和指标。在第一章中。[10](#_bookmark642)，我们更深入地研究了第一章中讨论的特定属性之一。[11](#_bookmark687) - 安全 - 可以阅读有关该领域的重要标准-ISO/IEC 26262。这次，本章包含有关硬件的更多信息，而不是本书的第一版。最后，小伙子。[12](#_bookmark727) 提出了一系列未来的趋势，这些趋势如今似乎有可能在未来几年内塑造汽车软件工程。

First and foremost, I would like to thank the coauthors of some of the chapters in this book—Darko Durisic, Per Johannessen, and Wilhelm Meding. I have had the privilege of working with them for a number of years and I am deeply thankful for their insights into the car and telecom industries.

> 首先，我要感谢本书中一些章节的合着者-Darko Durisic，Johannessen 和 Wilhelm Meding。我有多年的特权与他们合作，我深表感谢他们对汽车和电信行业的见解。

I am greatly indebted to my family—Sylwia, Alexander, Viktoria, and Cornelia—who support me in taking on challenges and see to it that I am successful. They are the most fantastic family one could imagine.

> 我非常感谢我的家人 - Sylwia，Alexander，Viktoria 和 Cornelia，他们支持我承担挑战，并看到我成功。他们是一个可以想象的最棒的家庭。

I would also like to thank my publisher—Ralf Gerstner from Springer—who has proposed the idea of the book and helped me throughout the process. Without his encouragement and practical pointers, this book would have never happened. After so many years, he still believes in me and provides me with precious advice. I hope that more authors have a chance to be taken care of by such a competent and dedicated publisher.

> 我还要感谢我的出版商 - Springer 的 Ralf Gerstner，他提出了这本书的想法，并在整个过程中为我提供了帮助。没有他的鼓励和实用的指针，这本书将永远不会发生。这么多年后，他仍然相信我，并为我提供宝贵的建议。我希望更多的作者有机会受到这样一个有能力和专门的出版商的照顾。

Many thanks to dSpace GmbH for permitting me to use images of their equipment as part of the book. I also thank Jan Söderberg from Systemite for providing me with figures and explanations on how the SystemWeaver tool keeps the different construction artifacts together. Many thanks go to Volvo Cars, who provided me with several figures in the book.

> 非常感谢 DSPACE GMBH 允许我将其设备图像作为书的一部分。我还要感谢 Systemite 的 JanSöderberg 为我提供有关 SystemWeaver 工具如何将不同的构造工具融合在一起的数字和解释。非常感谢沃尔沃汽车(Volvo Cars)为我提供了书中的几个数字。

I am grateful to my colleagues from Volvo Cars who have taught me about practicalities of the automotive industry. I have met many persons from the fantastic team of Volvo Cars and had many great discussions about how cars are designed today, but in particular I am indebted to Kent Niesel, Martin Nilsson, Niklas Baumann, Anders Svensson, Hans Alminger, Ilker Dogan, Lars Rosqvist, Sajed Miremari, Mikael Sjöstrand, and Peter Dahlslund. I would also like to thank Mark Hirche and Malin Folke for their comments on the draft of the book.

> 我感谢沃尔沃汽车的同事，他们教会了我有关汽车行业的实用性。我遇到了沃尔沃(Volvo Cars)的出色团队中的许多人，并就今天的设计设计进行了许多精彩的讨论，但尤其是我感谢肯特·尼泽尔(Kent Niesel)，马丁·尼尔斯森(Martin Nilsson)，尼克拉斯·鲍曼(Niklas Baumann)，安德斯·斯文森(Niklas Baumann)，安德斯·斯文森(Anders Svensson)，汉斯·阿尔明(Hans Alminger)，汉斯·阿尔明格(Hans Alminger)，伊尔克·多甘(Ilker Dogan)，拉尔斯(Lars Lars)，拉尔斯(Lars Lars)，拉尔斯(Lars Lars)，拉尔斯(Lars Lars)，拉尔斯(Lars)Rosqvist，Sajed Miremari，MikaelSjöstrand 和 Peter Dahlslund。我还要感谢 Mark Hirche 和 Malin Folke 对本书草案的评论。

I would also like to thank my colleagues from the research community for their help and support in both writing this book and in my research activities leading to this book. In particular, I would like to thank Imed Hammouda for his feedback and comments on the ATAM evaluation chapter.

> 我还要感谢研究界的同事在撰写本书和我的研究活动中的帮助和支持。特别是，我要感谢 Imed Hammouda 对 ATAM 评估章节的反馈和评论。

Finally, I would like to thank the Software Center, Swedish Innovation Agency Vinnova, the Swedish Strategic Research Foundation (SSF), and the Software Center for providing me with research funding that allowed me to pursue my research interests in the area of this book.

> 最后，我要感谢软件中心，瑞典创新机构 Vinnova，瑞典战略研究基金会(SSF)和软件中心为我提供研究资金，使我能够在本书的领域追求我的研究兴趣。
