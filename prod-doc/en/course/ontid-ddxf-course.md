# ONT ID and DDXF

## 摘要

对于互联网应用来说，业务的本质是实现信息化数据的处理。应用有两个核心模块，业务（数据）处理模块和用户账号模块。

由于现阶段的数据大都以中心化的形式保存和管理，数据的使用不经过数据所有者（产生者）的授权，造成未经授权数据交易的作恶成本非常低。本体提供去中心化数据和身份体系，所有的数据使用都需要经过数字身份的确权，在有授权的情况下使用数据，数据处理的过程可以追溯，形成信任平台。

本体采用 ONT ID 和 DDXF 实现**去中心化身份体系**和**数据加工和交换确权**，满足应用用户账户的自主管理和业务处理的确权和追溯功能。

## ONT ID

Ontology DID (AKA: ONT ID) is a decentralized identification protocol which based on W3C DID specifications. It supports collaborative services such as distributed and diversified ownership confirmation, identification, and authentication of various entities including individuals, legal entities, objects, and contents. ONT ID establishes a cryptographically-based digital identity for each entity, allowing self-sovereign of data authorization and ownership confirmation, which makes the identity and data truly assets that the user can control. ONT ID has the characteristics of decentralization, self-management, privacy protection, security and ease of use.

Ontology establishes a decentralized trust model and distributed trust delivery system through ONT ID and verifiable claim, and uses the C-L signature algorithm and zero-knowledge proof protocol to assure privacy protection of verifiable claim. Through ONT ID, Ontology will also incorporate various authentication service agencies, and establish multi-source authentication of the entity’s identity to achieve complete identity portrait.

In addition to relying on specific central entities to build trust relationships, entities can also build equally strong trust relationships by themselves. Trust transfer is achieved through mutual authentication between entities. Entities will have higher credibility if they receive more authentications from other entities – especially if those other entities have high credibility.

### 1. Introduction

ONT ID framework is targeting to provide 

1. self-sovereign identity for web applications, to buy in end user(s) of web-apps as stakeholder(s), and,
2. a platform to match the targeting user(s) for web-app(s) via a collection of third party claims, which results as the trust mechanism of Ontology.

#### 1.1 Self-sovereign identity

In Ontology `ONT ID framework`, "entity" refers to individuals, legal entities (organizations, enterprises, institutions, etc.), objects (mobile phones, automobiles, IoT devices, etc.), and contents (articles, copyrights, etc.) in the real world, and "identity" refers to the entity's identity within the network. 

1. **ONT ID** `ONT ID(s)` are identifier(s) of ONT ID framework. All entities in Ontology system shall have an `ONT ID`. Ontology uses Ontology Identifier (`ONT ID`) to identify and manage the entities' identities. On Ontology blockchain, one entity can correspond to multiple individual identities, and there is no relation between multiple identities.
2. **ONT Auth** and **Signing server** `ONT ID` services are deployed to Ontology mainnet. Users own `ONT IDs`. To make full use of `ONT ID`, a mobile application `ONT Auth` is used to enable self-sovereign identity. A `signing server` is a server side service to bridge `ONT ID` from end user to account system inside web-app. 

##### Workaround for centralized business

In order to satisfy traditional web-app user experiences, some web-apps may start with centralized id business. ONT ID framework provides workaround solution to meet the requirement above.

The centralized identifiers are able to be handed back to the ONT ID owners, via change the  `Owner` of `ONT ID` DDO from web-app to the end user.

#### 1.2 Ontology trust mechanism (the claim system)

Entities issue claims and "sell" them to their customers, where there are verification scenarios. The close loop of issuing request, creation and consuming of claims setup the Ontology trust mechanim.

本体使用可信声明的技术实现信任机制。

To active the mechanism, the following components are setup in `ONT ID framework`.

1. **Trust anchor** Trust anchor refers to the partner that provides authentication services on the Ontology ecosystem. It may be government agencies, universities, banks, third-party authentication service agencies (such as CA agencies), biometric technology companies, etc.
   - **Verifiable Claim Protocol** A statement to confirm a claim made by one entity about another (including themselves). The claim is accompanied by a digital signature that can be used by other entities for authentication. The verifiable claim protocol describes in detail the procedures and specifications about issue, store, and verification of verifiable claim.
2. **Claim store** A `claim store` is an entity to provide service for "`claim owners`" to manage their claims online, notify `claim owner(s)` when there is `claim consumer` for certain credentials. A `claim store` is usually an entity with NDA to ensure data privacy.
3. **ONT Auth** As a mobile application, `ONT Auth` is able to manage personal claims.

本课程中，集中介绍自治身份。关于本体信任机制的课程，将在后续推出。

本课程中，将教会同学们使用 ONT ID 的组件实现传统互联网应用的账户管理模块（用户系统）的去中心化改造。

### 2. 环境部署

本体提供 ONT ID 的商用解决方案，在本课程中，集中介绍独立部署互联网应用去中心化身份改造的**去中心化身份应用服务器**。

使用 docker 安装 signing server

1. 手续费代付账户准备
   1. 配置 Gas 代付钱包，预存 ONG
      1. 可以自行部署同步节点 // TODO：下载链接和截图，如果没有，删除
      2. 监控钱包余额，不足时报警
2. 下载
3. 配置
4. 运行

// TODO: 补充命令行、下载链接和截图

### 3. 去中心化账户改造

去中心化账户改造的核心思想是：中心化账户体系不变，将账户体系和 ONT ID 公钥绑定，通过验证 ONT ID 私钥的签名来实现对应账户的鉴权工作。

#### 3.1 注册改造

1. 用户使用 ONT Auth 注册自我管理的`ONT ID` // TODO：下载链接和截图
2. *传统 web-app 注册流程，账户内容准备。比如，*
   1. 注册信息填写
   4. 老账户查重
   5. 新账户锁定，注册信息缓存
      - session 绑定缓存，过期删除
      - 由于异步返回，建议对账户锁定缓存
3. Web-app 使用 signing sdk 或调用 restful api  `verify` 接口，用返回的数据生成二维码。提醒用户安装 ONT Auth 并注册 `ONT ID`
   1. 预定义方法参数为：`register`
   2. // TODO：调用方法细节和链接，signing sdk？restful api ？ verify ？如何生成二维码，截图
4. Web-app 使用signing sdk或调用restful api `result`接口，将上一步成功返回的id作为参数传入，轮询该action的执行结果 // TODO：方法细节和链接，截图
   1. 用户使用 ONT Auth 扫描二维码并签名，发送给signing-server // TODO: 操作截图
   2. signing-server 收到 ONT Auth 的签名数据并验证签名，若验证通过则会将用户使用 ONT Auth 签名的 `ONT ID` 返回给 web-app
5. Web-app 自行将用户账号和 `ONT ID` 进行绑定，注册缓存信息转成用户账户信息 // TODO：代码

#### 3.2 登录改造

1. Web-app 使用 signing sdk 或调用 restful api 的 `verify`接口，用返回的数据生成二维码
   1. 预定义方法参数为：`login`
   2. // TODO：调用方法细节和链接，signing sdk？restful api ？ verify ？如何生成二维码，截图
2. Web-app 使用 signing sdk 或调用 restful api 的  `result`接口，将上一步成功返回的 id 作为参数传入，轮询该 action 的执行结果 // TODO：方法细节和链接
   1. 用户使用 ONT Auth 扫描二维码并签名，发送给 signing-server // TODO：链接，截图
   2. signing-server 收到 ONT Auth 的签名数据并验证签名，若验证通过则会返回给 web-app 成功结果，不通过则返回给 web-app 失败结果

#### 3.3 关键动作上链改造

1. 定义预设上链动作的模板 // TODO: 模板链接
2. 判断是否上链还是作为验签和驱动动作 // TODO：举例和链接
   3. 如果 上链，实现上链动作的智能合约 // TODO：举例和链接
3. 实现上链动作的后续链外动作 // TODO：举例和链接
4. 自定义配置上链操作 // TODO: 文档模板和举例

#### 3.4 中心化托管方案

为了平滑用户体验从中心化用户习惯到自治身份的过渡，可以使用[中心化托管方案](#cent-id)。本课程不再深入。

### 4. 其他

通过去中心化改造的应用，可以实现用户个人管理所有的账户体系，同时保证了数据的所有权，使得针对数据的使用都在有授权的情况下完成，有效避免了中心化数据泄露和作恶。ONT ID 为本体信任框架提供数据确权和数据加工溯源的去中心化ID。

进一步的，在 Ontology trust mechanism 的支持之下，本体提供了更加丰富的用户到本体应用的导流方案。为本体应用的快速发展和运营提供解决方案和技术支持。关于本体信任机制的课程，将在后续推出。

## DDXF

在 ONT ID 的基础之上，本体信任框架的 DDXF 为应用业务数据处理和跨系统数据交换提供可信的数据确权和数据跟踪记录。

The wider adoption of Internet systems is putting more pressure on the existing infrastructure to meet the needs of end users. Accordingly, there is an increasing demand for connected IoT or Internet systems.

Traditional resource management, including information databases and analytics architectures and infrastructures, remains essential. With the growing data management demand, specific capabilities and capacities are required to be able to handle diverse and complex data streams from different sources. The data needs to be processed and managed properly to maximize its value in a secure manner, while complementing it with other sources of information.

### 1. Introduction

The Ontology DDXF defines an infrastracture framework and guidelines to support comprehensive data processing and management frameworks which incorporate reasonable measures to achieve a layered, data-centric paradigm. Due to the research and identification characteristics of effective data processing and management systems, DDXF is focusing on data interoperability, classification, format and security issues that affect various stakeholders.

![framework](../ddxf/res/framework.png)

The Ontology DDXF uses Ontology blockchain infrastructure, follows an open protocol called [`Ontology GREP (Generic Resources Exchange Protocol)`](#grep), and provides a series of functionalities and interfaces to meet the requirement of trust data interoperability across multiple systems, which serves multiple business requirements and scenarios, especially the data exchange scenarios.

![overall](../ddxf/res/overall.png)

According to GREP, DDXF has the following features:

1. Off-chain multi-system resource integration;
2. Data access tokenisation, which supports token transaction and cross-chain assets;
3. Resource exchange and data interaction through data pattern change, token transfer and transaction;
4. Data processing and transaction attestation support offline resource and off-chain arbitration to ensure incentives.

#### 1.1 DToken model - self-sovereign data management

The self-sovereign data management decouples the privilege of data ownership with data accessibility (or other data processing privileges) and manages data upon different privileges from the data owner(s).

The Ontology DDXF provides self-sovereign data management by the combined services of `data storage`, `ONT ID`, `DToken` and Ontology blockchain infrastructure.

- Data storage provides the capability to store data with data protection and data privacy, with lower cost;
- ONT ID provides the capability to identify data, data owner, and data handler;
- DToken provides the capability to manage data privileges and ensure the data processing is stored on Ontology blockchain infrastructure;
- Ontology blockchain infrastructure provides traceability and trust endorsement.

The DToken model function defines the following features:

- Resource modeling and mapping provides static modeling and mapping functions, where the off-chain resources from Internet or IoT systems are able to be stored online in the form of modeling data and the online data will be mapped with on-chain identifiers;
- DToken generation provides static identifier mapping capability, where the privileges of data are able to be tokenized as DTokens, the use of which will be controlled and logged on-chain.

DToken model provides interfaces to define the entities, resources and operations in DDXF.

#### 1.2 Decentralized data processing and management - resource exchange

Decentralized data processing and management provides a runtime mechanism to control the business actions of resource exchange, data transfer, and data processing.

- Resource exchange provides runtime for token-based resource transferring and exchange.
- Token usability provides runtime to manage the use of tokens, especially the use of DToken to access data.

Decentralized data processing and management provides interfaces to process and manage data in DDXF.

#### 1.3 Trust audit

The DDXF marketplace provides the capability to realise resource exchange across systems. 

Based on different business requirements, data could be owned by smart devices, end users or systems. Data processing will change data forms. DDXF enables data processing, transfer and exchange with controlling the ownership and accessibility of the data instances. Audit of off-chain resources and the transactions by end users is to provide trust endorsement of DDXF.

- Resource audit provides a mechanism to ensure the ownership and accessibility of off-chain resources,  the resource quality and transaction behaviours;
- Reputation score is based on the use of DDXF and the transactions are able to provide trust endorsement for DDXF customers.

Trust audit provides interfaces to offer trust endorsement for transactions, data qualification and users in DDXF.

本课程中，集中介绍链上数据交换的确权和跟踪。关于数据质量的审计和仲裁的课程，将在后续推出。

### 2. 环境部署

本体提供 DDXF 数据交换的商用解决方案，在本课程中，集中介绍独立部署互联网应用数据自治的**去中心化数据交换应用服务器**。

ddxf 将为数据拥有者上传至marketplace的数据生成dataId,以及买家购买后生成相应数据使用权的dataToken。使用 DToken 访问真实的数据。

本体提供三方数据储存的商业解决方案，三方数据储存的收费方案的整合，将在后续推出相关课程。

储存服务器

1. 部署
2. 配置
3. 启动

// TODO: 补充命令行、下载链接和截图

数据交换平台

1. 手续费代付账户准备
   1. 配置 Gas 代付钱包，预存 ONG
      1. 可以自行部署同步节点 // TODO：下载链接和截图，如果没有，删除
      2. 监控钱包余额，不足时报警
2. Deploy smart contract
3. Deploy docker
4. Config and run
   1. Smart contract configuration
   2. Server configuration

// TODO: 补充命令行、下载链接和截图

### 3. 数据管理

数据管理保存用户数据，本教程给出简单的中心化数据储存的数据交换。

本体同时提供去中心化数据储存方案，关于数据质量的审计和仲裁的课程，将在后续推出。

为了满足不同数据交换和交易的场景，本体提供不同的场景模板，本课程主要围绕简单的虚拟商品（数据资产）交换场景。将在后续推出更多场景模板的课程。

#### 3.1 数据保存

1. RP 上传的资源数据需要平台方自己开发存储方案
2. 通过 marketplace 提供的 API 或者 SDK 方法生成DataId 之后，平台方进行数据与 ID 的绑定

// TODO: 补充命令行、下载链接和截图

#### 3.2 数据权限令牌化和令牌通证化

1. RP 预上传数据之后，需要生成 Dataid 实现与数据的绑定
2. Dataid生成之后，注册生成 DToken 的参数，包括 DToken 的价值，DToken 对应的DataID，访问次数、访问时间、DToken二次流转的次数等
   1. 可参考[合约字段](../../../framework/data-storage/smart-contract-api.md)

// TODO: 补充命令行、下载链接和截图

#### 3.3 数据令牌的使用

1. RC 凭借此 DToken 访问 DataID 对应的Data资源

// TODO: 补充命令行、下载链接和截图

### 4. 数据交换的确权和链上记录

#### 4.1 挂单

对应数据和数据令牌的展示，由数据自行设计用户界面和交互。

1. DToken 注册参数的陈列
2. DToken 价值作为标价

// TODO: 补充样例原型的截图

#### 4.2 交易

1. RC 选择需要购买的数据，购买 DToken的数量，通常支付用于等价交换的 utility token 或 DToken，进行下单操作
2. 在购买时生成对应的 DToken
   1. 基于预设的DToken模板，根据支付（交换）的 Token（DToken）生成对应数量和对应权限的 DToken
      1. 提供基本字段和数据，比如生成Token数量
      2. 调用DToken合约，通过Onto Auth 扫码签名进行数据的购买操作
         1. 合约会生成DToken与这条数据进行绑定
3. 购买完成后新生成的 DToken 所有权归到 RC 名下，对应交换的 token 的所有权归 挂单者 所有。

// TODO: 补充合约、SDK接口文档，代码样例，原型的截图

### 5. 其他

关于数据质量的审计和仲裁的课程，将在后续推出。

## <a name="cent-id"></a>附录 I. ONT ID signing server - centralized identity

Centralized identity system is a workaround for self-sovereign identity solution.

Conceptually, `ONT ID` is delegated from end users to web-app server host.

Terms and agreement shall be prepared in advance, for end users to accept the "delegate" action.

Technically, delegated `ONT ID` contails three key features,

1. to generate `ONT ID` with web-app `root key` to manage `owner key` of `ONT ID` DDO on behalf of end user
2. to sign on on-chain actions, e.g., registration, login, on behalf of end user and publish to Ontology mainnet
3. to enable end users to take over the ownership of `ONT ID` if they want
