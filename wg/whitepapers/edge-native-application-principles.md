# Edge Native Application Principles

Publish date: Jan 17, 2023 (first edition), October 24, 2022 (draft)

## Objective

The term "Edge Native" has been mentioned in many places including industry blogs, such as, [Gartner](https://blogs.gartner.com/thomas_bittman/2020/04/17/cloud-native-isnt-edge-native/), [Macrometa](https://www.macrometa.com/blog/edge-native-is-not-cloud-native), and [FutureCIO](https://futurecio.tech/cloud-native-versus-edge-native-know-the-difference/). Organizations such as the [State of the Edge](https://github.com/State-of-the-Edge/glossary/blob/master/edge-glossary.md#edge-native-application) and the [Linux Foundation](https://www.lfedge.org/wp-content/uploads/2020/07/LFedge_Whitepaper.pdf) (LF) have also discussed edge native applications, but there has not been a focus on edge native principles.

This white paper focuses on edge native applications and how the principles are defined.

## What is Edge?

Edge computing is a paradigm which brings data processing closer to the source, for example, robot control in a factory.
Over the next five years edge computing will become more ubiquitous as the industry is estimated to grow [38.9% from 2022 to 2030](https://www.grandviewresearch.com/industry-analysis/edge-computing-market). Companies are seeing the following benefits of having computing power at the edge:

- Reduced latency
- Bandwidth management
- Increased privacy for sensitive data
- Uninterrupted operations with unreliable networks

Various definitions of edge computing exist, but the one this paper will focus on is based on the geographical location of data processing resources. Geography-based edge is classified into multiple categories depending on the distance from the user. The diagram below shows the categories as defined by the [Linux Foundation Edge Whitepaper](https://www.lfedge.org/wp-content/uploads/2020/07/LFedge_Whitepaper.pdf).

![Summary of edge continuum](https://i.imgur.com/yhNbawO.png)

Edge native principles share a number of similarities with cloud native principals; however, there are also some key differences.

## Cloud Native vs Edge Native

Cloud native technologies, as defined by the [Cloud Native Computing Foundation (CNCF)](https://github.com/cncf/foundation/blob/main/charter.md), are:

>*“Cloud native technologies empower organizations to build and run scalable applications in modern, dynamic environments such as public, private, and hybrid clouds. Containers, service meshes, microservices, immutable infrastructure, and declarative APIs exemplify this approach.*
>
>*These techniques enable loosely coupled systems that are resilient, manageable, and observable. Combined with robust automation, they allow engineers to make high-impact changes frequently and predictably with minimal toil.”*

This broad mission remains applicable to edge applications as [The Open Glossary of Edge Computing](https://github.com/State-of-the-Edge/glossary/blob/master/edge-glossary.md#edge-native-application) states that “edge native applications” leverage cloud native principles:

>*“An application built natively to leverage edge computing capabilities, which would be impractical or undesirable to operate in a centralized data center. Edge-native applications leverage cloud-native principles while taking into account the unique characteristics of the edge in areas such as resource constraints, security, latency and autonomy. Edge native applications are developed in ways that leverage the cloud and work in concert with upstream resources. Edge applications that don’t comprehend centralized cloud compute resources, remote management and orchestration or leverage CI/CD aren’t truly “edge native”, rather they more closely resemble traditional on-premises applications.”*

As cloud native use cases venture out of traditional clouds to incorporate data and events at edge locations, new tools and techniques are evolving in keeping with the goal of delivering loosely coupled systems that are resilient, manageable, and observable while also managing the unique characteristics of the edge.

## Similarities in Edge Native compared to Cloud Native

Many cloud native principles apply to edge native. This section describes these similarities.

|                Attributes               |                                                                                                      Cloud Native & Edge Native                                                                                                     |
|:---------------------------------------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| Apps and services portability           | Applications and services abstract their coupling from the infrastructure. A well written app can’t tell where it is running and can be expected to be portable across platforms.                                                   |
| Observability                           | The platform is accompanied by a suite of well documented interfaces and tool options to enable detection of issues and collection of metrics. This allows developers to build systems that are resilient and efficiently managed. |
| Manageability                           | Interfaces and tooling options are provided to manage apps and resources at scale. The platform also has a plug-in mechanism to provide baseline network connectivity, services, and management features.                    |
| Agnostic language and framework support | Apps and services can be implemented and hosted using a variety of popular languages and frameworks.                                                                                                                               |

## Edge Native and Cloud Native Differences

The broad missions of edge native and cloud native share similarities, yet developers should be aware of the differences.

|              Attributes              |                                                                                    Cloud Native                                                                                   |                                                                                                                                         Edge Native                                                                                                                                        |
|:------------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| App Model                            | Mostly microservice components that are built stateless for load balanced horizontal scaling.                                                                                     | While a service provider edge app may be quite similar, user edge apps may be singleton “monolithic”; in both cases, the state may be colocated with the app.                                                                                                                              |
| Data Model                           | Centralized model backing stateless components is common.                                                                                                                         | Caching, streaming, real-time and distributed models are often utilized.                                                                                                                                                                                                                   |
| Elasticity                           | Rapid spin up and down; generally treating underlying resources as unlimited.                                                                                                     | Limited elasticity due to constrained hardware resources at the edge; if available, scaling might be “vertical” up to a connected cloud.                                                                                                                                                   |
| Resilience                           | Resilience outsourced to cloud providers using redundant nodes spread across failure domains.                                                                                     | Often relies on hardened infrastructure, with recovery architectures for stateful components; in many cases, resilience may be lower than in the cloud.                                                                                                                                    |
| Scale                                | Typically limited to a few locations, instances.                                                                                                                                  | May span a large number of locations (up to 10,000s) with support for a large number of external devices (up to 100,000s).                                                                                                                                                                 |
| Orchestration                        | Orchestration in large public or on prem cloud is designed to achieve efficiency and availability by running workloads on centrally pooled hosts — scheduled in a horizontal way. | Edge is decentralized with workloads deployed in a distributed way — often scheduled in a location-specific way.                                                                                                                                                                           |
| Management                           | While both cloud native and edge native are manageable, the mechanism varies; cloud native relies on central management and automation.                                           | Edge native requires a mix of remote and centralized management and zero touch provisioning of hardware and software. Staffing at the edge may be untrained, untrusted, minimal or even non-existent. “Brick” resistant “atomic” upgrades become desirable because of recovery challenges. |
| Networking                           | Apps can rely on high speed networks with rich capabilities.                                                                                                                      | Apps need to account for varied speeds (ranging from intermittent, poor to excellent) and capabilities. Includes mobile and radio based, integrating data and events from non-IP protocol networks.                                                                                          |
| Security                             | Trusted fabric within secure facilities.                                                                                                                                          | Zero trust in insecure environments.                                                                                                                                                                                                                                                       |
| Hardware awareness                   | Apps rarely have to concern themselves with hardware placement due to de facto uniformity of compute resources with flavors that cater to most apps.                                    | Apps may have greater real time requirements making hardware platform, location, and/or security awareness a requirement. Developers need to be aware of a wider variety of hardware and interfaces.                                                                                       |
| Interacting with external resources  | Applications rarely need to interact with local hardware resources.                                                                                                               | Services deployed at the edge often need to interact with the local environment: cameras, sensors, actuators, users, and more.                                                                                                                                                             |

## Edge Native Applications

Edge native applications are applications and services written for the edge. They are written in a way that accounts for the above similarities and differences. The core principles for these applications are listed below.

## Edge Native Principles

Edge native applications should follow the following principles to fulfill the mission of edge native mentioned earlier in the paper.

| Principle                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Hardware aware                                       | Rather than having homogenous hardware platforms, developers need to be aware of a wider variety of hardware and interfaces.与其拥有同质化的硬件平台，开发者需要了解更广泛的硬件和接口。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| External device connectivity                         | Applications must know how to connect to the devices in their environment and be aware of the capability changes at runtime. For example, they must respond to dis/connecting sensors to the edge server after initial configuration or new devices entering the network. Capability is not static; rather it includes the environment, so orchestrators should be able to reconcile capability changes to application state.   应用程序必须知道如何连接到其环境中的设备，并且在运行时意识到其能力的变化。例如，在初始配置后连接或断开边缘服务器上的传感器，或新设备进入网络时，应用程序必须响应这些变化。能力并不是静态的，而是包括环境因素，因此编排程序应能够将能力变化与应用程序状态协调一致。                                                                                                                                                                                                                                                                      |
| Aware of variable-connectivity                       | Applications must adapt to network connectivity that is unreliable or even unavailable (air gapped) by using mechanisms such as asynchronous communication, queueing and caches. “Pull” mechanisms may be required to overcome scale, network connectivity, and security issues where the edge pulls configuration from a central site. 应用程序必须通过使用异步通信、队列和缓存等机制来适应不可靠或甚至不可用的网络连接（例如空中隔离）。在边缘从中央站点获取配置时，可能需要使用“拉取”机制来解决规模、网络连接和安全问题。                                                                                                                                                                                                                                     |
| Centrally observable                                 | While both edge and cloud native applications need to be centrally observable, edge native apps have unique considerations. Edge native app instances may be deployed at a massive scale of instances and/or face constrained staff or field support. For these reasons, techniques such as distributed data collection and centralized aggregation, a combination of open loop (human observable / actionable) and closed loop automation (machine actionable) are required. Observability covers metrics, logs, digital twins, alerting (events and alarms) and health monitoring.   虽然边缘和云原生应用程序都需要集中观测，但边缘原生应用程序有其独特的考虑因素。边缘原生应用程序实例可能部署在大规模的实例和/或受限的人员或现场支持面临的环境中。出于这些原因，需要采用分布式数据收集和集中聚合技术，以及开环（人可观测/可操作）和闭环自动化（机器可操作）的组合技术。观测包括指标、日志、数字孪生、警报（事件和报警）和健康监测。                                                                                                              |
| Infrastructure and platform management at scale      | Infrastructure and platform management at scale is important for edge applications thus requiring declarative intent-based mechanisms. Furthermore, there might be unique requirements such as device onboarding, limitations on horizontal scaling, managing bare metal environments, and more. At a platform level, deploying or managing the Kubernetes or virtualization layers and various plugins is also a concern; all while keeping the platform layer as vendor neutral as possible to enable application portability.  对于边缘应用程序而言，规模化的基础设施和平台管理非常重要，因此需要采用声明性意图驱动的机制。此外，可能存在设备注册、水平扩展限制、裸机环境管理等独特要求。在平台层面，部署或管理 Kubernetes 或虚拟化层以及各种插件也是一个问题；同时，保持平台层面的中立性，尽可能支持应用程序可移植性。                                                                                                                                                                    |
| Application management at scale                      | The number of applications and the number of instances of these applications can be very large on the edge, requiring automation ranging from declarative placement and configuration intent, automated service assurance via closed loop automation, and aggregated management views across multiple application instances. Applications may also have realtime needs which means the linkage between applications and infrastructure/platform (e.g. use of GPUs, DPUs, FPGAs, CPU architectures, kernel optimizations, Kubernetes plugins) may be tighter than with cloud applications. In other words, application orchestration may trigger infrastructure/platform orchestration underneath. 边缘上的应用程序数量和实例数量可能非常大，需要自动化，包括声明性部署和配置意图、通过闭环自动化实现自动化服务保障，以及跨多个应用程序实例的聚合管理视图。应用程序可能还需要实时处理，这意味着应用程序和基础设施/平台之间的联系（例如使用 GPU、DPU、FPGA、CPU 架构、内核优化、Kubernetes 插件）可能比云应用程序更紧密。换句话说，应用程序编排可能会触发基础设施/平台编排。|
| Spanning                                             | Applications do not exist at one location; tiers can straddle geographic, latency, and failure domain boundaries. In fact, edge apps may span public or centralized private clouds as well.   应用程序不仅存在于一个位置；应用层可以跨越地理、延迟和故障域边界。实际上，边缘应用程序可能还会跨越公共或集中的私有云。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Resource usage optimization                          | Since edge computing resources are constrained, an application has to optimize resource usage on a continuous basis. This may mean spinning applications up and down on-demand. It may mean migration and replication based on placement and availability intent. It may mean running different workloads at different times of the day. 由于边缘计算资源有限，应用程序必须不断地优化资源使用。这可能意味着按需启动和停止应用程序。可能会根据位置和可用性意图进行迁移和复制。可能会在一天的不同时间运行不同的工作负载。                                                                                                                                                                                                                                                                                                                                                          |
| Applications are portable and reusable (with limits) | Abstraction layers attempt to provide infrastructure and platform agnostic portability through vendor neutral PaaS. However, because of local resource, hardware platform, security, mobile network and other awareness, configuration options are required to adapt to local differences. 抽象层试图通过中立的 PaaS（平台即服务）提供基础设施和平台无关的可移植性。然而，由于本地资源、硬件平台、安全、移动网络和其他方面的不同，需要配置选项来适应本地差异。                                                                                                                                                                                                                                                                                                                                                                                                       |

### Grouped Edge Native Principles

![Grouped Edge Native Principles](https://i.imgur.com/Yt2Ojcx.png)

These nine principles can be grouped into a smaller set of five principles. Hardware awareness, external device connectivity, and awareness of variable network availability can all be considered under a broader principle of resource and device awareness. Similarly, the need for edge applications to be manageable at scale, centrally observable, and have manageable infrastructure and platforms can all be categorized under a principle of at scale management. The following are the broadened five principles: Spanning, Resource Usage Optimization, Portable and Reusable with Limits, Resource and Device Aware, and at Scale Management.

## Conclusion & Next Steps

This paper is a first edition and may experience revisions. Future papers related to sub-sections of this paper are anticipated.

## How to get involved

The CNCF IoT Edge Working Group has regular meetings, a mailing list, and a Slack. See the [Communication section](https://github.com/cncf/tag-runtime/blob/master/wg/iot-edge.md#communication) of the working group GitHub page for the most up to date information. We welcome the reader to get involved by presenting Edge related projects, bringing an idea for an area of work for the group, or helping to revise this white paper and/or draft follow on paper.

## Working List of Edge Native Open Source Projects and Initiatives

As a part of this paper, the CNCF IoT Edge Working Group is collecting a working list of open source projects that help application developers achieve the edge native application principles outlined in this paper.

The list can be found in [this spreadsheet](https://docs.google.com/spreadsheets/d/1dfa3lUvLuCrzmTH1w1TLeXxU-gy6QfbsE_ZXd1h4zTI/edit#gid=0) or through the QR code. To get edit access to add a project, join the [IoT Edge Working Group Google group](https://groups.google.com/forum/#!forum/kubernetes-wg-iot-edge).

![QR code to list of edge native projects](https://i.imgur.com/sToDBW9.png)

## Contributors

### Authors

Amar Kapadia, Aarna Networks
Brandon Wick, Aarna Networks
Joel Roberts, Cisco
Kate Goldenring, Fermyon
Dejan Bosanac, Red Hat
Tomoya Fujita, Sony US Lab
Ravi Chunduru, Verizon
Natalie Fisher, VMware
Steven Wong, VMware  

### Reviewers

Frédéric Desbiens, Eclipse Foundation
Prakash Ramchandran, eOTF
Mark Abrams, SUSE

## References

Linux Foundation Edge  Whitepaper: https://www.lfedge.org/wp-content/uploads/2020/07/LFedge_Whitepaper.pdf

Open Glossary of Edge Computing [v2.1.0] State of the Edge: https://github.com/State-of-the-Edge/glossary/blob/master/edge-glossary.md#edge-native-application

Cloud Native Computing Foundation (CNCF) Charter: https://github.com/cncf/foundation/blob/main/charter.md

Gartner ‘Cloud Native Isn’t Edge Native’: https://blogs.gartner.com/thomas_bittman/2020/04/17/cloud-native-isnt-edge-native/

Macrometa ‘Edge Native is not Cloud Native’: https://www.macrometa.com/blog/edge-native-is-not-cloud-native

Future CIO ‘Cloud-Native versus Edge-Native: know the difference’: https://futurecio.tech/cloud-native-versus-edge-native-know-the-difference/

Edge Computing Market Size, Share & Trends Analysis Report By Component (Hardware, Software, Services, Edge-managed Platforms), By Application, By Industry Vertical, By Region, And Segment Forecasts, 2022 - 2030
https://www.grandviewresearch.com/industry-analysis/edge-computing-market
