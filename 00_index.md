1. [Introduction](#_bookmark2) 1
   1. [Software and Modern Cars](#software-and-modern-cars) 1
   2. [History of Software in the Automotive Industry](#history-of-software-in-the-automotive-industry) 2
   3. [Trends Shaping Automotive Software Development](#trends-shaping-automotive-software-development) 5
   4. [Organization of Automotive Software Systems](#organization-of-automotive-software-systems) 8
   5. [Architecting as a Discipline](#architecting-as-a-discipline) 9
      1. [Architecting vs. Project Management](#architecting-vs.-project-management) 10
      2. [Architecting vs. Design](#architecting-vs.-design) 11
   6. [Content of This Book](#content-of-this-book) 12
      1. [Chapter 2: Software Architectures](#chapter-2-software-architectures) 13
      2. [Chapter 3: Modern Software Architectures: Federated and Centralized](#chapter-3-modern-software-architectures-federated-and-centralized) 13
2. [Chapter 4: Automotive Software Development](#chapter-4-automotive-software-development) 14
3. [Chapter 5: AUTOSAR Reference Model](#chapter-5-autosar-reference-model) 14
4. [Chapter 6: Detailed Design of Automotive Software](#chapter-6-detailed-design-of-automotive-software) 14
5. [Chapter 7: Machine Learning in Automotive Software](#chapter-7-machine-learning-in-automotive-software) 15
6. [Chapter 8: Evaluation of Automotive Software Architectures](#chapter-8-evaluation-of-automotive-software-architectures) 15
7. [Chapter 9: Metrics for Software Design and Architectures](#chapter-9-metrics-for-software-design-and-architectures) 15
8. [Chapter 10: Functional Safety of Automotive Software](#chapter-10-functional-safety-of-automotive-software) 16
9. [Chapter 11: Current Trends in Automotive Software Development](#chapter-11-current-trends-in-automotive-software-development) 16
10. [Motivating Examples in the Book](#motivating-examples-in-the-book) 16

<!-- -->

1. [Knowledge Prerequisites](#knowledge-prerequisites) 17
2. [Where to Go Next](#where-to-go-next) 17

[References](#_bookmark39) 18

1. [Software Architectures—Views and Documentation](#_bookmark54) 19
   1. [Introduction](#introduction-1) 19
   2. [Common View on Architecture in General and in the Automotive Industry in Particular](#common-view-on-architecture-in-general-and-in-the-automotive-industry-in-particular)
      20
2. [Definitions](#definitions) 21
3. [High-Level Structures](#high-level-structures) 22
4. [Architectural Principles](#architectural-principles) 24
5. [Architecture in the Development Process](#architecture-in-the-development-process) 26
6. [Architectural Views](#architectural-views) 27
   1. [Functional View](#functional-view) 27
   2. [Physical System View](#physical-system-view) 29
   3. [Logical View](#logical-view) 31
   4. [Relation to the 4+1 View Model](#relation-to-the-41-view-model) 31
7. [Architectural Styles](#architectural-styles) 33
   1. [Layered Architecture](#layered-architecture) 34
   2. [Component-Based](#component-based) 37
   3. [Monolithic](#monolithic) 38
   4. [Microkernel](#microkernel) 39
   5. [Pipes and Filters](#pipes-and-filters) 40
   6. [Client–Server](#clientserver) 41
   7. [Publisher–Subscriber](#publishersubscriber) 42
   8. [Event–Driven](#eventdriven) 43
   9. [Middleware](#middleware) 43
   10. [Service-Oriented](#service-oriented) 44
8. [Describing the Architectures](#describing-the-architectures) 46
   1. [SysML](#sysml) 46
   2. [EAST ADL](#east-adl) 48
9. [Next Steps](#next-steps) 50
10. [Further Reading](#further-reading) 50
11. [Summary](#summary) 50

[References](#_bookmark114) 51

1. [Contemporary Software Architectures: Federated and Centralized](#_bookmark154) 55
2. [Introduction](#introduction-2) 55
3. [Federated Software Architectures](#federated-software-architectures) 56
4. [Centralized Software Architectures](#centralized-software-architectures) 59
5. [Examples](#examples) 61
   1. [Federated Architecture of a Car](#federated-architecture-of-a-car) 62
   2. [Pipes and Filters in Autonomous Drive](#pipes-and-filters-in-autonomous-drive) 63
   3. [Infotainment Systems](#infotainment-systems) 64
6. [On Truck Architectures](#on-truck-architectures) 64
7. [Summary](#summary-1) 65

[References](#_bookmark172) 65

1. [Automotive Software Development](#_bookmark185) 67
   1. [Introduction](#introduction-3) 67
      1. [V-Model of Automotive Software Development](#v-model-of-automotive-software-development) 68
   2. [Requirements](#requirements) 69
      1. [Types of Requirements in Automotive Software Development](#types-of-requirements-in-automotive-software-development) 71
   3. [Variant Management](#variant-management) 75
      1. [Configuration](#configuration) 76
      2. [Compilation](#compilation) 76
      3. [Practical Variability Management](#practical-variability-management) 78
   4. [Integration Stages of Software Development](#integration-stages-of-software-development) 78
   5. [Testing Strategies](#testing-strategies) 79
      1. [Unit Testing](#unit-testing) 79
      2. [Component Testing](#component-testing) 81
      3. [System Testing](#system-testing) 83
      4. [Functional Testing](#functional-testing) 83
      5. [Pragmatics of Testing Large Software Systems: Iterative Testing](#pragmatics-of-testing-large-software-systems-iterative-testing) 84
2. [Construction Database and Its Role in Automotive Software Engineering](#construction-database-and-its-role-in-automotive-software-engineering) 85
3. [Further Reading](#further-reading-1) 89
   1. [Requirements Specification Languages](#requirements-specification-languages) 91
4. [Summary](#summary-2) 92

[References](#_bookmark225) 92

1. [AUTOSAR (AUTomotive Open System ARchitecture)](#_bookmark273) 97
   1. [Introduction](#introduction-4) 97
   2. [AUTOSAR Classic Platform](#autosar-classic-platform) 99
      1. [Reference Architecture](#reference-architecture) 101
      2. [Development Methodology](#development-methodology) 102
      3. [AUTOSAR Meta-Model](#autosar-meta-model) 108
      4. [AUTOSAR ECU Middleware](#autosar-ecu-middleware) 117
   3. [AUTOSAR Adaptive Platform](#autosar-adaptive-platform) 119
      1. [Reference Architecture](#reference-architecture-1) 122
      2. [Development Methodology](#development-methodology-1) 123
      3. [AUTOSAR Meta-Model](#autosar-meta-model-1) 125
      4. [AUTOSAR ECU Middleware](#autosar-ecu-middleware-1) 130
   4. [AUTOSAR Foundation](#autosar-foundation) 130
   5. [Further Reading](#further-reading-2) 131
   6. [Summary](#summary-3) 133

[References](#_bookmark315) 134

1. [Detailed Design of Automotive Software](#_bookmark368) 137
   1. [Introduction](#introduction-5) 137
   2. [Simulink Modelling](#simulink-modelling) 138
      1. [Basics of Simulink](#basics-of-simulink) 139
      2. [Sample Model of Digitalization of a Signal](#sample-model-of-digitalization-of-a-signal) 143
      3. [Translating Physical Processes to Simulink](#translating-physical-processes-to-simulink) 146
      4. [Sample Model of Car’s Interior Heater](#sample-model-of-cars-interior-heater) 149
   3. [Simulink Compared to SySML/UML](#simulink-compared-to-sysmluml) 155
   4. [Principles of Programming of Embedded Safety-Critical Systems](#principles-of-programming-of-embedded-safety-critical-systems) 157
2. [MISRA](#misra) 158
3. [NASA’s Ten Principles of Safety-Critical Code](#nasas-ten-principles-of-safety-critical-code) 160
4. [Detailed Design of Non-safety-Critical Functionality](#detailed-design-of-non-safety-critical-functionality) 161
   1. [Infotainment Applications](#infotainment-applications) 161
5. [Quality Assurance of Safety-Critical Software](#quality-assurance-of-safety-critical-software) 163
   1. [Formal Methods](#formal-methods) 163
   2. [Static Analysis](#static-analysis) 164
   3. [Testing](#testing) 166
6. [Further Reading](#further-reading-3) 166
7. [Summary](#summary-4) 168

[References](#_bookmark423) 168

1. [Machine Learning in Automotive Software](#_bookmark451) 171
   1. [Introduction](#introduction-6) 171
   2. [Fundamentals of Supervised Learning](#fundamentals-of-supervised-learning) 174
   3. [Neural Networks](#neural-networks) 176
   4. [Image Recognition Using Convolutional Neural Networks](#image-recognition-using-convolutional-neural-networks) 178
   5. [Object Detection](#object-detection) 180
   6. [Reinforced Learning and Parameter Optimization](#reinforced-learning-and-parameter-optimization) 181
   7. [On-Board and Off-Board Machine Learning Algorithms](#on-board-and-off-board-machine-learning-algorithms) 182
   8. [Challenges with Using Machine Learning in Automotive Software](#challenges-with-using-machine-learning-in-automotive-software) 185
2. [Summary](#summary-5) 186

[References](#_bookmark473) 187

1. [Evaluation of Automotive Software Architectures](#_bookmark493) 189
   1. [Introduction](#introduction-7) 189
   2. [ISO/IEC 25000 Quality Properties](#isoiec-25000-quality-properties) 190
      1. [Reliability](#reliability) 191
      2. [Fault Tolerance](#fault-tolerance) 193
      3. [Mechanisms to Achieve Reliability and Fault Tolerance](#mechanisms-to-achieve-reliability-and-fault-tolerance) 193
2. [Architecture Evaluation Methods](#architecture-evaluation-methods) 195
3. [ATAM](#atam) 197
   1. [Steps of ATAM](#steps-of-atam) 197
   2. [Scenarios Used in ATAM in Automotive](#scenarios-used-in-atam-in-automotive) 198
   3. [Templates Used in the ATAM Evaluation](#templates-used-in-the-atam-evaluation) 201
4. [Example of Applying ATAM](#example-of-applying-atam) 202
   1. [Presentation of Business Drivers](#presentation-of-business-drivers) 203
   2. [Presentation of the Architecture](#presentation-of-the-architecture) 203
   3. [Identification of Architectural Approaches](#identification-of-architectural-approaches) 205

<!--  -->

1. [Self-\*](#self-) 261
2. [Big Data](#big-data) 262
3. [New Software Development Paradigms](#new-software-development-paradigms) 264
   1. [Architecting in the Age of Agile > Software Development](#architecting-in-the-age-of-agile-software-development) 265
4. [Other Trends](#other-trends) 266
5. [Summary](#summary-8) 267

[References](#_bookmark698) 267
6. **[Summary](#_bookmark727)** 269

1. [Software Architectures in General and in the Automotive Software—A Short Recap](#software-architectures-in-general-and-in-the-automotive-softwarea-short-recap) 269
2. [Chapter 2—Software Architectures](#chapter-2software-architectures) 269
3. [Chapter 3—Contemporary Software > Architectures: Federated and Centralized](#chapter-3contemporary-software-architectures-federated-and-centralized) 270
4. [Chapter 4—Automotive Software Engineering](#chapter-4automotive-software-engineering) 271
5. [Chapter 5—AUTOSAR](#chapter-5autosar) 271
6. [Chapter 6—Detailed Design of Automotive Software](#chapter-6detailed-design-of-automotive-software) 272
7. [Chapter 7—Machine Learning in Automotive Software](#chapter-7machine-learning-in-automotive-software) 272
8. [Chapter 8—Evaluation of Automotive Software Architectures](#chapter-8evaluation-of-automotive-software-architectures) 272
9. [Chapter 9—Metrics for Software Designs and Architectures](#chapter-9metrics-for-software-designs-and-architectures) 273
10. [Chapter 10—Functional Safety of Automotive Software](#chapter-10functional-safety-of-automotive-software) 273
11. [Chapter 11—Current Trends](#chapter-11current-trends) 274
12. [Closing Remarks](#closing-remarks) 274
