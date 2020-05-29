# Ontology Decentralized Data Exchange Framework (DDXF)

- [Overview](#overview)
- [Components and interfaces](#components)
- [Scenarios of DDXF](#scenarios)
- [Business solutions using DDXF](#business)
- [Appendix: Generic Resources Exchange Protocol (brief)](#grep)

## <a name="overview"></a>Overview

The accelerating use of Internet systems is increasing the pressure on the existing infrastructures to meet the needs of end users. Accordingly, there is an increasing demand for connected IoT or Internet systems.

Traditional resource management, including information databases and analytics architectures and infrastructures, remain essential, with the growing data management demands, specific capabilities and capacities are required to be able to handle diverse and complex data streams from different sources. This data needs to be processed and managed properly to maximize its value in a secure manner, while complementing it with other information sources.

Ontology DDXF is to define an infrastracture framework and guidelines to support comprehensive data processing and management frameworks which incorporate reasonable measures to achieve a layered, data-centric paradigm. Due to research, identify and study characteristics of effective data processing and management systems, DDXF is focusing on the data interoperability, classification, format and security issues that affect various stakeholders.

![framework](../res/framework.png)

Ontology DDXF uses Ontology blockchain infrastructure, follows an open protocol called [`Ontology GREP (Generic Resources Exchange Protocol)`](#grep), and provides a series of functions and interfaces to meet the requirement of trust data interoperability cross multiple systems, which serves multiple business requirements and scenarios, esp., the data exchange scenarios.

![overall](../res/overall.png)

## <a name="components"></a>Components and interfaces

根据 GREP 协议，DDXF 具备以下能力：

1. 链外多系统资源整合；
2. 数据权限令牌化通证化，支持通证交易，支持跨链资产；
3. 以数据特征变化、令牌传递和通证交易形式实现资源交换和数据交互；
5. 数据加工和交易确权过程支持线下资源和链外仲裁，保证分成激励。

体现在框架功能模块之上，分成`自治资源管理`、`去中心化数据处理和资源交互`、`可信审计和仲裁`三个模块。

![component](../res/component.png)

### 1. DToken model - self-sovereign data management

The self-sovereign data management is to decouple the privilege of data ownership with data accessibility (or other data processing privileges) and manage data upon different privilege from the data owner(s).

Ontology DDXF provides self-sovereign data management by a combination services of [`data storage`](./data-storage/README.md), [`ONT ID`](../../ontid/framework/README.md), [`DToken`](./spec/data-token.md) and Ontology blockchain infrastructure.

- Data storage provides the capability to store data with data protection and data privacy, with lower cost;
- ONT ID provides the capability to identify the data and the data owner, data handler;
- DToken provides the capability to manage data privileges and ensure the data processing is stored on Ontology blockchain infrastructure;
- Ontology blockchain infrastructure provides the capability for the traceability and trust endorsement.

The DToken model function defines the following features:

- Resource modeling and mapping, provides static modeling and mapping functions, where the off-chain resources from Internet or IoT systems are able to be stored on-line in a form of modeling data and the on-line data will be mapped with on-chain identifiers;
- DToken generation, provides a static identifier mapping capability, where the privileges of data are able to be tokenized to DTokens, the use of DToken will be controlled and logged on-chain.

DToken model provides interfaces to define the entities, resources and operations in DDXF.

[>> Learn more](./data-storage/README.md)

### 2. Decentralized data processing and management - resource exchange

Decentralized data processing and management provides a runtime mechanism to control the business actions of resource exchange, data transfering and data processing.

- Resource exchange, provides runtime for token based resource transfering and exchange.
- Token usability, provides runtime to manage the use of tokens, esp., the use of DToken to access data.


Decentralized data processing and management provides interfaces to process and manage data in DDXF.

[>> Learn more](./marketplace/README.md)

### 3. Trust audit

The DDXF marketplace provides the capability to do resource exchange cross systems. 

Due to different business, data could be owned by the smart devices, end users or systems. Data processing will change the form of data. DDXF is to enable data processing, transfering and exchange with controlling of the ownership and accessibility of the data instances. Audit of off-chain resources and the transactions being taken by end users is to provide trust endorsement of DDXF.

- Resource audit, provides a mechanism to ensure the ownership and accessibility of off-chain resources,  the resource quality and the transaction behaviors;
- Reputation score, based on the use of DDXF, the transactions are able to provide trust endorsement for DDXF customers.

Trust audit provides interfaces to do trust endorsement for transactions, data qualification and users in DDXF.

[>> Learn more](./resource-audit/README.md)

## <a name="scenarios"></a>Scenarios of DDXF

DDXF covers the scenarios of most features in the data interoperability cross systems. The framework also covers the scenarios to bring valuable resources to a potential consumer(s), esp., marketplaces for resources cross systems.

- [>> Learn more](../business/scenarios/README.md)

## <a name="business"></a>Business solutions using DDXF

With DDXF, solutions are ready for different domains.

- [>> Learn more](../business/business/README.md)

## <a name="grep"></a>Appendix: Generic Resources Exchange Protocol (brief)

GREP 是一套建立于 Ontlogy 主链基础设施上的去中心化资源交换协议。通过使用 GREP，用户可以快速建立数据等资源的链上确权和流转平台。得益于 Ontology 信任生态体系基础设施的完备性，在去中心化身份标识 ONT ID、去中心多源认证系统 Trust Anchor、可信链外数据连接器 Oracle 以及去中心化电子合同及签章系统 ONT Sign 等多种信任协作组件的协同支撑下， GREP 可以为去中心化资源交换提供坚实的信任基础。 

### 1. Resource tokenization and assetization

通过 GREP，任何人都可以快速而又便捷地建立多样化的资源链上确权和流转平台。

- 资源可以是数字资源，例如，数据、CPU 算力、GPU 算力、存储、链上 Oracle 和可信计算平台等；
- 一些实体资源，例如房产、古董字画等。

平台可以是个通用性平台，能实现多种资源的流转；它可以是一个特定资源的交换平台，精细化地实现某种特定资源的流转。

资源流转是资源以 ONG、OEP-4 代币等的形式，或是以资源或资源的形式。可能的资源流转形式包括但不限于：

- 数据资源流转，例如:医疗大数据(的分析结果)换取 ONG；
- 算力资源流转，例如:可信计算算力换取 PAX；
- 实体资源流转，例如:名画所有权进行分割拍卖等。

资源的流转实际上就是将资源相应权利 Token 化，并进行 Token 流转。对于某个资源来说，其流转的可能是其所有权，或者是使用权以及其它相应的权利。具有链下实体的资源需要进行链下交割，而链下交割的方式将由资源的性质等方面决定。

在 GREP 中，公链 Ontology 提供了重要的去中心化信任基础。GREP 的用户需要为自己生成一个相应 的 ONT ID，并根据交易市场的需要进行注册和/或相关的用户资质认证。资源在交易过程中同样需要在链上进行注册，一般会抽取资源的唯一特征码生成数字指纹，并为资源生成相应的 ONT ID。

### 2. Token-based exchange mechanism

资源交换或数据交互的过程可以看做是 Token 流转和交换的过程，通过智能合约保证执行。 

GREP 定义以下几类角色实现可信的 Token 交换：

- 资源提供者 Resource Privoder (RP):拥有资源的实体，并将资源开放给市场，以资源通过 某种定价体系换取一定的报酬(例如, ONG 或其它某种资源)。此类实体有很多种类，比如数据所有者、算力拥有者、数据收集平台以及具有一定权限的数据托管方等等。
- 资源需求者 Resource Consumer (RC):资源提供者的交易对手方，是需要某种资源的实体，从资源提供者中获取资源的(部分)所有权或者使用权，并为此支付一定的报酬(例如 ONG)。
- 资源认证方 Resource Authenticator(RA):具有一定权威性的第三方，拥有自己的资源质量认证体系，根据该体系可以给资源或者资源提供者提供一定方式的认证增强资源或者资源提供者的可信度。认证根据不同的模式可以收取或者不收取认证费用。与没有经过认证的资源相比，经过认证的资源会拥有更多的潜在买家以及可能获得更高的报酬。
- 链下仲裁者 Off-chain Judge (OJ):资源提供者和资源需求者在资源交易中都认可的链下纠纷仲裁者。链下产生的纠纷(如资源没有获取到)将由链下仲裁者进行裁定。
- 交易市场 Marketplace (MP):是连系资源提供者和资源需求者的纽带，存储资源的元信息，为资源提供灵活的展示和快捷的搜索，收取交易费用。每个交易市场可以按照自身交易的特性提供伸缩化的灵活服务，比如提供元信息模板、解决链下纠纷的电子合同模板等供交易双方具现化 后使用。MP 一般拥有资源交易定价体系。另外，MP 一般也拥有资源交易信息披露体系，可以对公众或者监管部门进行交易信息披露。

GREP 规定了资源交换和数据交互的流程规范。用户根据自身需要选择想要进行交易的场所 MP。可以多次交付的资源可以在不同的 MP 上以不同的方式进行交易，如数据的使用权可以在多个 MP 进行交易。假定用户，包括 RP、RC 以及 OJ 等，都已经根据该 MP 的相应要求进行资质验证。整个资源的流转过程涉及到[资源准备](../../business/scenarios/resource-preparation.md)、[资源发布](../../business/scenarios/resource-publish.md)、[资源交易](../../business/scenarios/resource-transaction.md)、[分润](../../business/scenarios/resource-incentive-share.md)和[交易后评价](../../business/scenarios/tx-evaluation.md)。在交易评价的基础上，GREP 实现的资源交换和数据交互的记录形成[声誉体系](../resource-audit/reputation-score.md)，进一步促进本体可信生态体系。

### 3. Resource verification and audit

链下实体的资源需要进行链下交割。链下行为，例如资源的所有权和合法性的确定，牵涉到现实世界中行为的认定和权利的确定。这种认定的方式需要由双方协定，并在必要的情况下采用去中心化电子合同以及签章系统 ONT Sign 来约定，并明确链下纠纷的处理方式，比如，违约后的链下责任处理方式。

链下仲裁者，在交易双方签定合同时由双方共同指定，是解决链下纠纷的一种较为可靠和高效的方式。链下仲裁者或者其代理人（例如，交易市场）将纠纷裁定结果上链。链下仲裁者不处理链上纠纷，链上纠纷将直接通过链上证明裁定。同时，某些链外证据可以通过 Ontology Oracle 送到链上，在链上进行直接裁定。

### 4. Extension

GREP 是一个开放性协议，随着技术发展和本体生态的衍化，会有越来越多的扩展功能参与本体基础设施之中，GREP 也需要由相应的[协议集合](../extensions/README.md)去配合。

- GREP 支持对资源的定价，提供基于定价的资源交易。在实际的交易过程中，支持 Token 支付。由于目前区块链的 Token 资产位于多条链上，因此 GREP 支持[跨链资产支付](../extensions/cross-chain/README.md)。