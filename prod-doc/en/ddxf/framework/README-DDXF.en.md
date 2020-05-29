# Ontology Decentralised Data Exchange Framework (DDXF)

- [Overview](#overview)
- [Components and Interfaces](#components)
- [Scenarios of DDXF](#scenarios)
- [Business Solutions Using DDXF](#business)
- [Appendix: Generic Resources Exchange Protocol (brief)](#grep)

## <a name="overview"></a>Overview

The wider adoption of Internet systems is putting more pressure on the existing infrastructure to meet the needs of end users. Accordingly, there is an increasing demand for connected IoT or Internet systems.

Traditional resource management, including information databases and analytics architectures and infrastructures, remains essential. With the growing data management demand, specific capabilities and capacities are required to be able to handle diverse and complex data streams from different sources. The data needs to be processed and managed properly to maximize its value in a secure manner, while complementing it with other sources of information.

The Ontology DDXF defines an infrastracture framework and guidelines to support comprehensive data processing and management frameworks which incorporate reasonable measures to achieve a layered, data-centric paradigm. Due to the research and identification characteristics of effective data processing and management systems, DDXF is focusing on data interoperability, classification, format and security issues that affect various stakeholders.

![framework](../res/framework.png)

The Ontology DDXF uses Ontology blockchain infrastructure, follows an open protocol called [`Ontology GREP (Generic Resources Exchange Protocol)`](#grep), and provides a series of functionalities and interfaces to meet the requirement of trust data interoperability across multiple systems, which serves multiple business requirements and scenarios, especially the data exchange scenarios.

![overall](../res/overall.png)

## <a name="components"></a>Components and interfaces

According to GREP, DDXF has the following features:

1. Off-chain multi-system resource integration;
2. Data access tokenisation, which supports token transaction and cross-chain assets;
3. Resource exchange and data interaction through data pattern change, token transfer and transaction;
5. Data processing and transaction attestation support offline resource and off-chain arbitration to ensure incentives.

The framework functionality modules are divided into "autonomous resource management", "decentralised data processing and resource interaction", and "trusted audit and arbitration".

![component](../res/component.png)

### 1. DToken model - self-sovereign data management

The self-sovereign data management decouples the privilege of data ownership with data accessibility (or other data processing privileges) and manages data upon different privileges from the data owner(s).

The Ontology DDXF provides self-sovereign data management by the combined services of [`data storage`](./data-storage/README.md), [`ONT ID`](../../ontid/framework/README.md), [`DToken`](./spec/data-token.md) and Ontology blockchain infrastructure.

- Data storage provides the capability to store data with data protection and data privacy, with lower cost;
- ONT ID provides the capability to identify data, data owner, and data handler;
- DToken provides the capability to manage data privileges and ensure the data processing is stored on Ontology blockchain infrastructure;
- Ontology blockchain infrastructure provides traceability and trust endorsement.

The DToken model function defines the following features:

- Resource modeling and mapping provides static modeling and mapping functions, where the off-chain resources from Internet or IoT systems are able to be stored online in the form of modeling data and the online data will be mapped with on-chain identifiers;
- DToken generation provides static identifier mapping capability, where the privileges of data are able to be tokenized as DTokens, the use of which will be controlled and logged on-chain.

DToken model provides interfaces to define the entities, resources and operations in DDXF.

[>> Learn more](./data-storage/README.md)

### 2. Decentralized data processing and management - resource exchange

Decentralized data processing and management provides a runtime mechanism to control the business actions of resource exchange, data transfer, and data processing.

- Resource exchange provides runtime for token-based resource transferring and exchange.
- Token usability provides runtime to manage the use of tokens, especially the use of DToken to access data.


Decentralized data processing and management provides interfaces to process and manage data in DDXF.

[>> Learn more](./marketplace/README.md)

### 3. Trust audit

The DDXF marketplace provides the capability to realise resource exchange across systems. 

Based on different business requirements, data could be owned by smart devices, end users or systems. Data processing will change data forms. DDXF enables data processing, transfer and exchange with controlling the ownership and accessibility of the data instances. Audit of off-chain resources and the transactions by end users is to provide trust endorsement of DDXF.

- Resource audit provides a mechanism to ensure the ownership and accessibility of off-chain resources,  the resource quality and transaction behaviours;
- Reputation score is based on the use of DDXF and the transactions are able to provide trust endorsement for DDXF customers.

Trust audit provides interfaces to offer trust endorsement for transactions, data qualification and users in DDXF.

[>> Learn more](./resource-audit/README.md)

## <a name="scenarios"></a>Scenarios of DDXF

DDXF covers the scenarios of most features in the data interoperability cross systems. The framework also covers the scenarios to bring valuable resources to a potential consumer(s), esp., marketplaces for resources cross systems.

- [>> Learn more](../business/scenarios/README.md)

## <a name="business"></a>Business solutions using DDXF

With DDXF, solutions are ready for different domains.

- [>> Learn more](../business/business/README.md)

## <a name="grep"></a>Appendix: Generic Resources Exchange Protocol (brief)

GREP is a set of decentralised resource exchange protocols built on the Ontlogy main chain infrastructure. By using GREP, users can quickly establish on-chain attestation and exchange platform for resources such as data. Thanks to the well-developed Ontology Trust Ecosystem infrastructure, the decentralised identity ONT ID, the trusted multi-source authentication system Trust Anchor, the trusted off-chain data connector Oracle, and the decentralised electronic contract and signature system ONT Sign, GREP lays a solid foundation for trusted decentralized resource exchange.

### 1. Resource tokenisation and assetisation

Through GREP, anyone can instantly and conveniently establish diverse on-chain resource attestation and exchange platform.

- The resources can be digital resources, for example, data, CPU computing power, GPU computing power, storage, on-chain Oracle, and trusted computing platform;
- Some physical resources, such as properties, antiques, and paintings.

The platform can be a general platform and can realise the circulation of diverse resources; it can be an exchange platform for specific resources and realise the circulation of specific resources.

Resource transfer can be in the form of ONG or OEP-4 tokens. Possible resource transfer forms include but not limited to:

- Data circulation, for example, (the analysis result of) medical big data for ONG;
- Computing power circulation, for example, trust computing power for PAX;
- Physical resource circulation, for example, the auction of famous paintings.

The circulation of resources is in fact tokenising the corresponding rights of the resources and circulate the token. For a certain type of resource, it might be the ownership that is circulated, or the right to use or other rights. Resources with off-chain entities need to be delivered off the chain, and the way off-chain delivery is carried out will be determined by the nature of the resources.

In GREP, Ontology provides an important foundation for decentralised trust. GREP users need to generate a corresponding ONT ID for themselves and register and/or verify user credentials according to the needs of the trading market. Resources also need to be registered on the chain during the transaction process. Generally, the unique pattern of the resource is extracted to generate a digital fingerprint and a corresponding ONT ID is generated for the resource.

### 2. Token-based exchange mechanism

The process of resource exchange or data interaction can be seen as the process of token circulation and exchange, and the execution is guaranteed by smart contracts.

GREP defines the following types of roles to implement trusted token exchange:

- **Resource Provider (RP)**: An entity that owns resources and opens the resource to the market, in exchange for a certain amount of revenue (for example, ONG or some other resources). There are many types of such entities, such as data owners, computing power owners, data collection platforms, and data escrow service providers with certain permissions.
- **Resource Consumer (RC)**: The counterparty of the resource provider and an entity that needs a certain resource and obtains (partial) ownership or use rights of the resource from the resource provider for a certain fee (for example, ONG).
- **Resource Authenticator (RA)**: A third party with certain authority, has its own resource quality certification system, according to which the system can provide resources or resource providers with certain ways to enhance the trustworthiness of the resources or resource providers. Certification can be free of charge or requires a certain fee according to different models. Certified resources have more potential buyers and may receive higher revenues than uncertified resources.
- **Off-chain Judge (OJ)**: An off-chain dispute arbiter recognized by resource providers and resource users in resource transactions. Off-chain disputes (for example, the resources are not provided to users) will be determined by the arbitrators off the chain.
- **Trading Marketplace (MP)**: The link between resource providers and resource users. It stores the meta-information of resources, provides flexible display and quick search for resources, and collects transaction fees. Each trading marketplace can provide flexible services according to the characteristics of its own transactions, such as providing meta-information templates and electronic contract templates for resolving disputes off the chain for use by both parties. MP generally has a resource transaction pricing system. In addition, MP generally also has a resource transaction information disclosure system, which can disclose transaction information to the public or regulatory authorities.

GREP specifies process specifications for resource exchange and data interaction. Users select the MP where they want the transaction to take place. Resources that can be delivered multiple times can be traded differently on different MPs, such as the right to use data can be traded on multiple MPs. It is assumed that users, including RP, RC, and OJ, have been qualified according to the corresponding requirements of the MP. The entire resource circulation process involves [resource preparation](../../business/scenarios/resource-preparation.md), [resource publishing](../../business/scenarios/resource-publish.md) , [resource exchange](../../business/scenarios/resource-transaction.md), [fee splitting](../../business/scenarios/resource-incentive-share.md) and [post-transaction review](../../business/scenarios/tx-evaluation.md). On the basis of transaction review, the record of resource exchange and data interaction realised by GREP constitutes [reputation system](../resource-audit/reputation-score.md) to further promote the Ontology Trust Ecosystem.

### 3. Resource verification and audit

The off-chain resources of the entities need to be delivered off the chain. Off-chain behaviours, such as the attestation of the ownership and legitimacy of resources, involve the identification of behaviours and the attestation of rights in the real world. This method of identification needs to be agreed by both parties, and if necessary, adopt the decentralised electronic contract and signature system ONT Sign to clarify off-chain dispute resolution, for example, how should the responsibility be determined off the chain in the event of contract breach.

The off-chain arbitrators are jointly designated by both parties when signing the contract, which is a more reliable and efficient way to resolve the disputes off the chain. The off-chain arbitrator or its agent (for example, the trading market) will record the result of the dispute on the chain. The off-chain arbitrators do not deal with on-chain disputes, which will be directly arbitrated through on-chain evidence. At the same time, some of the off-chain evidence can be sent to the chain via Ontology Oracle for direct ruling on the chain.

### 4. Extension

GREP is an open protocol. As the Ontology ecosystem grows and its technology develops, more and more extensions will be added to the Ontology infrastructure and GREP will also need the corresponding [protocol set](../extensions/README.md).

- GREP supports the pricing of resources and provides pricing-based resource transaction. In real-life transactions, token payment is supported. Since token assets are on multiple blockchains, GREP supports [cross-chain asset payment](../extensions/cross-chain/README.md)