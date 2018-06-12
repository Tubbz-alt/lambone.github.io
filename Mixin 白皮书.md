# Mixin 白皮书

网站： https://mixin.one/
白皮书英文版：https://mixin.one/assets/Mixin-Draft-2018-06-04.pdf

Mixin 网络

> A TEE powered BFT-DAG network that connects all existing blockchains with unlimited throughput.

 基于 TEE驱动 的 BFT-DAG 网络，以无限的吞吐量，连接所有已有的区块链，

## 名词解释

| Acronym | Meaning | 中文 |
| --- | --- | ---|
|consensus algorithm   | consensus algorithm  | 共识算法  |   |
| distribution  | distribution  |  分布式 |
| BFT   | Byzantine Fault-Tolerant  | 拜占庭的容错  |
| DApp   | Distributed App  |  分布式应用  |
| DAG   | Directed acyclic graph   | 有向无环图  |
|DPoS  | Delegated Proof of Stake   | 区块链的共识算法之一 ， DPoS is a more efficient PoS mechanism. DPoS uses a reputation system and real-time voting to achieve consensus. |
| PoS | Proof of Stake  | 区块链的共识算法之一  |   
| PoW  | Proof of Work   | 区块链的共识算法之一    |
| TEE   | Trusted Execution Environment  | 可信执行环境  |  


## 缘由 Motivation

Blockchain and cryptocurrency news have become more familiar to people, but it’s still difficult to get into these fancy things, even for software developers.

区块链和加密货币新闻已经越来越为人们所熟悉，但即使对软件开发人员来说，仍然很难理解这些奇特的事物。

Most blockchain projects focus on the distribution factors and secure key management. However these all lead to slow transactions, private keys loss and difficult understanding. And it’s nearly impossible to deploy these distributed nodes on mobile devices, the most popular computing devices.

大多数区块链项目都侧重于分发因素和安全密钥管理。然而，这些都会导致交易缓慢，私钥丢失和难以理解。而在最流行的计算设备 - 移动设备上部署这些分布式节点几乎是不可能的。

Despite their effort on the distribution dream, we have noticed the reality that even the most distributed blockchain consensus algorithm leads to the control of several large pools. Consider the BCH hard fork to BTC.

尽管他们在分发方面做出了努力，但我们已经注意到即使是最分布式的区块链共识算法也能够控制几个大型池的现实。看一下 BCH 对BTC的硬分叉就清楚了。

Some popular blockchain projects have or plan to choose some not so distributed consensus algorithms by design, Ethereum is migrating to PoS and EOS is implementing DPoS. This effort may improve the transaction throughput, but that’s all.

一些流行的区块链项目已经或计划通过设计选择一些不那么分布式的共识算法，以太坊正在向PoS迁移，而EOS正在实施DPoS。这一努力可能会提高交易吞吐量，但仅此而已。

Still, people have to manage fancy private keys and lose them, pools and whale nodes will fork the network endlessly without effort, developers try their best effort to develop some new tokens, and people have no proper way to use the nodes on their mobile devices.

尽管如此，人们还是不得不管理花哨的私钥，丢失它们，矿池和节点将毫不费力地分配网络，开发人员尽力开发一些新的代币，并且人们没有适当的方式来使用他们的移动设备上的节点。

## 设计 Design

Mixin is an effort to find a balance in distributed network and traditional server clusters, make some tradeoffs to combine the pros of the two together.
*	Limited and trusted full nodes with guaranteed data transparency and consistency.
*	Zero-knowledge proof and free transactions with high throughput and low latency.
*	Inter-blockchain communication protocol to connect all popular blockchain networks.
*	Non-deterministic transactions and interact directly with trusted external sources.
*	Phone number and PIN based account model for easy mobile use.
*	Secure and end-to-end encrypted messaging channel to reach every account for notifications.
*	Developer friendly to facilitate all Linux libraries and programming languages.
*	The largest mobile blockchain network effect should prevent forks.


Mixin 致力于在分布式网络和传统服务器集群中找到平衡点，做出一些折衷，将两者的优点结合在一起。

* 有限且可信的完整节点，保证数据透明度和一致性。
* 具有高吞吐量和低延迟的零知识证明和免费交易。
* 区块链互联通信协议，用于连接所有流行的区块链网络。
* 非确定性交易并直接与可信的外部资源进行交互。
* 电话号码和基于PIN的账户模式，便于移动使用。
* 安全且端到端的加密消息通道可以通知每个账号。
* 开发人员可以方便地使用所有Linux库和编程语言。
* 最大的移动区块链网络，防止分叉。


To accomplish these goals, we designed an unique blockchain model that relies on Trusted Execution Environment technology and relationship, while the consensus algorithm mainly acts as the guarantee for data replication, and the mobile nodes will acts as validators to do runtime attestation of the full nodes.

为了实现这些目标，我们设计了一个独立的区块链模型，它依赖于可信执行环境技术和关系，而共识算法主要作为数据复制的保证，而移动节点将作为验证者来执行完整节点的运行时证明。

As illustrated in the figure above, the fundamental of Mixin network is some trusted full nodes run in the Trusted Execution Environment.

如上图所示，Mixin网络的基础是在可信执行环境中运行的一些可信的完整节点。

All Mixin full nodes are fully trusted because they can verify the identity of all other full nodes and validate the code they run through TEE attestation at runtime.

所有Mixin完整节点都是完全可信的，因为它们可以验证所有其他完整节点的身份并验证它们在运行时通过TEE证明运行的代码。

Mixin full nodes accept transactions and participate in the network’s consensus algorithm. Due to the code validation, only one node should execute DApp code to achieve high throughput and low latency.

Mixin 全节点接受交易并参与网络共识算法。 由于代码验证，只有一个节点应该执行DApp代码来实现高吞吐量和低延迟。

All sensitive components of the network must run inside the Trusted Execution Environment and are responsible for protecting security and privacy, for maintaining data transparency and consistency.

网络中的所有敏感组件都必须在受信任的执行环境中运行，并负责保护安全和隐私，以保持数据的透明度和一致性。

## End-to-End Encryption Messaging 点对点加密通信

Mixin uses the sender key of Signal protocol to manage all conversations, despite direct message or group chat.

不管是单独对话还是群聊，Mixin使用了信号协议的发送者钥匙加密来完成对话。

The protocol is client based, so the server only acts as a proxy of the messages, and due to the strong end- to-end encryption feature, no one could inspect anything from the proxied messages, even the Mixin full nodes.

协议是基于客户端的，服务器只是信息传播中介，鉴于采用了强大的点对点加密技术，没有人——即使是Mixin全节点——也不能够审查通信内容。

All messages will be permanently deleted on the servers once read by all the recipients in the conversation.

经所有的信息接收方接收并读取后，信息就会被服务器永久删除。

Photos, videos and all other attachments are also encrypted with random AES key before uploading to our cloud storage. Then the client will transfer all the meta information, such as thumbnail, AES key to the recipient with Signal sender key encryption.

照片，视频和其它任何附件在上传到我们的云存储之前，也都会采用随机AES钥匙加密。用户之间可以发送经发送者钥匙加密的各种信息。然后，客户端将使用发送者密钥加密将所有元信息（如缩略图，AES密钥）传输到接收方。

As Mixin is using the mature Signal protocol and open source library as the messaging protocol, we won’t dig into the technical details of the specification in this white paper.
Mixin使用的通信协议是很成熟的信令协议和开源的通信协议，我们在白皮书中就不详细说明了。


## Mobile and PIN Based Identity 基于移动和PIN的身份认证

The obstacle that prevents people from using blockchain is not the performance, it’s the identity or account management procedure.

妨碍人们使用区块链的障碍不在于性能，而在于身份或账户管理程序。

All popular blockchain networks require people to obtain and manage at least one private key to keep an identity. This is too complicated, it’s not a bit but hundreds of times more complicated compared to username and password solution.

所有流行的区块链网络都要求人们获取和管理至少一个私钥以保持身份。 这太复杂了，与用户名和密码解决方案相比，这不是一点点，而是几百倍的复杂。

As all existing blockchain data are open to the world, to use an username and password solution, people are still required to manage a complicated password to keep account secure, think about BTS or EOS.

  由于所有现有的区块链数据都向世界开放，为了使用用户名和密码解决方案，人们仍然需要管理复杂的密码以保证账号安全，对照一下BTS或EOS就明白了。

Thanks to the zero-knowledge and secure execution environment in the Mixin network, we are able to design a much simpler identity solution that’s based on phone verification code and PIN.
由于Mixin网络中的零知识和安全执行环境，我们能够设计出基于电话验证码和PIN的更简单的身份识别解决方案。

People just need a phone number and remember a six digit PIN to keep an identity, even easier than username password solution, without complicated private key but comparable security level.
人们只需要一个电话号码，并记住一个六位数的PIN码以保持身份，甚至比用户名密码解决方案更容易，没有复杂的私钥但具有可比的安全级别。

While the phone number verification process to transfer private keys ensure easy phone migration, the 6-digit PIN can be replaced by Touch ID or Face ID on supported mobile phones, this improves the user experience to another level.
虽然传送私钥的电话号码验证过程可确保轻松移动电话，但6位数PIN可由支持的移动电话上的Touch ID或Face ID取代，这将用户体验提升到另一个级别。

A typical BTC transaction should take as long as one hour to confirm, the fee is also too high to send micro- payments. And the public blockchain data make transaction privacy nearly impossible.
典型的BTC交易需要长达一小时的时间才能确认，但发送小额支付的费用也太高。 公开的区块链数据使交易隐私几乎不可能。

To overcome the Bitcoin problem, with the identity procedure above, we designed a cross-chain transaction network similar to the Bitcoin Lighting Network or the Ethereum Raiden Network.
为了克服比特币问题，通过上述身份识别程序，我们设计了类似比特币闪电（Lighting ）网络或以太坊雷电（Raiden）网络的跨链交易网络。

The underlying technique of Mixin PIN identity is still private key management, but secured and made easy by the Mixin zero-knowledge trusted execution network. So it’s feasible to treat this as a smart contract like Lighting Network to manage BTC or any other blockchain assets.

Mixin PIN身份认证的底层基本技术仍然是私钥管理，但通过Mixin零知识可信执行网络保证了安全性并使其变得简单。 因此，将其视为像Lighting Network这样的智能合约来管理BTC或任何其他区块链资产是可行的。

After assets from other blockchains come in to the Mixin Network, whenever a Mixin user start a BTC transaction to another user in Mixin, the server won’t do any real transactions on the Bitcoin blockchain, instead it just managed their balance numbers in the Mixin blockchain, which is as fast as general SQL database operations.

在其他区块链的资产进入Mixin网络后，只要Mixin用户在Mixin中向其他用户启动BTC交易，服务器就不会在比特币区块链上进行任何真实交易，而只是在Mixin中管理其余额 区块链，这与一般的SQL数据库操作一样快。

## XIN - The Token 代币

XIN is the sole token used by many services in Mixin, especially full node collateral, the DApp creation and API calls.

XIN是Mixin中许多服务所使用的唯一代币，特别是全节点的附属，DApp创建和API调用。

To join the network as a full node, it should pledge at least 10,000 XIN token to establish the initial trust.
要作为全节点加入网络，它应承诺至少有10,000个XIN来建立初始信任。

Every DApp creation will cost some XIN for one time, the cost is determined by the resources the DApp claimed to consume. The Mixin API calls from DApp may cost some XIN depends on the call type and count.
开发DApp需要向网络一次性支付一定量的XIN,数量由它所要占用的网络资源决定。 DApp调用Mixin API也一样，需要支付的 XIN数量由调用的类型和数量决定。

All the XIN penalties and fees charged by the network will be recycled to the mining pool.
网络收取的所有的 XIN 罚单和费用将被回收到矿池。

1,000,000 permanent total XIN token is issued to the world at one time, and 400,000 of them have been successfully distributed to holders from 25/11/2017 to 25/12/2017 with rate 20 EOS/XIN.

Mixin一次性发行数量恒定的1,000,000枚XIN，其中 400,000 已于 25/11/2017 to 25/12/2017 以 20 EOS/XIN 的比例兑换.

50,000 XIN have been distributed to early Mixin Messenger adopters. 50,000 XIN are reserved for the development team.

50,000 XIN 已用于 早期 Mixin Messenger。 50,000 XIN 保留给开发团队。

The remaining 500,000 XIN will be the incentives for all Mixin full nodes and light nodes.

其余 500,000 XIN 将作为 Mixin 网络全节点和光节点的奖励。

## Conclusion 结语

Mixin network has unlimited throughput, easy and familiar account model for people, ability to connect and use all currencies on any existing blockchain networks.
Mixin网络具有无限的吞吐量，为人们提供简单且熟悉的账户模式，能够在任何现有的区块链网络上连接和使用所有货币。

Besides the underlying Mixin network, we are building the Mixin Messenger as the first DApp and entrance to it, all code are open sourced to give the developers an overview of how to develop on Mixin.

除了底层的Mixin网络之外，我们正在构建Mixin Messenger作为第一个DApp并入门，所有代码都是开源的，以便开发人员了解如何在Mixin上进行开发。

Treat Mixin Network as the open Android ecosystem, all existing blockchain networks as different phone manufactures and countries, the Mixin Messenger acts as the Google Play role to provide DApp discovery for users, easy notifications and payments for developers.

将Mixin Network视为开放的Android生态系统，将所有现有的区块链网络视为不同的手机制造商和国家，Mixin Messenger充当Google Play的角色，为用户提供DApp发现功能，为开发者提供简单的通知和支付。

With nearly 1,000,000 pre-registered users, Mixin network welcome all developers to develop or port their existing app to the platform, with familiar development environment.

拥有近1,000,000名预注册用户，Mixin网络欢迎所有开发人员、以自己熟悉的开发环境，来开发或将他们现有的应用程序移植到Mixin网络平台上。
