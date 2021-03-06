---
title: Hotbit AMA Review | Darwinia CMO Bree
author: @DarwiniaNetwork
authorURL: http://twitter.com/DarwiniaNetwork
---

![](assets/2020-05-21-hotbit-ama.jpeg)

Hot Talk：Polkadot 系列对话第二期，Darwinia CMO Bree 前来报道！「如何打造资产互联网」

<!--truncate-->

### 1、作为波卡生态的优秀项目，来为大家说一说Darwinia是一个怎样的项目吧？

达尔文网络是基于Substrate开发的去中心化异构链跨链桥接网络，专注于建设未来资产互联网络，包括跨链非标资产拍卖市场、稳定币跨链、资产交易兑换等领域。

当前较多跨链方案为中心化或半去中心化，难以避免道德风险。基于轻客户端的BTCRelay项目却失败了，这是因为经典轻客户端是线性relay区块，也就是每一个块都要relay，使得维护成本高昂，经济上不可为继。

而达尔文Chain Relay是一种新颖的跨链验证Relay，实现了超级轻客户端，使用了Merkle Mountain Range（MMR）区块链头承诺，乐观博弈机制Optimistic Verification Game，Relayer激励模型等技术，可以实现仅需要提交对数数量的区块头及其衍生数据，也就是亚线性的性能。大大提高了效率和经济可用性。甚至可以实现按需relay块头并进行验证的能力。有了高效ChainRelay加持，我们就可以安全构建双向桥，在两个异构链上双向对等搭建智能合约和相互的ChainRelay，由智能合约控制资产锁定、赎回等操作，而验证则通过桥头堡达尔文 ChainRelay实现。与其在每两个链之间搭建直连桥，重复制造轮子，可以通过搭建到达尔文中继链的桥来最容易的实现的“从任何地方来”到“任何地方去”的目标。

而一旦达尔文成为波卡的平行链，则可直接打通波卡生态和外界的联系。

### 2、最近达尔文测试网crab网络刚刚发布，介绍一下crab网络吧？期待的达尔文主网什么时候上线呢？

从19年开始，我们已经发布了三个版本的测试网络，最近我们上线了最后一版测试网Crab，定位类似于Kusama网络之于Polkadot。这个测试网络将会长久的运营，即使是主网上线之后也会保留，供开发者测试使用。

Crab 网络初始供应量中一部分 CRING 将分发给 RING & DOT 的持有者，可以免费获得 CRING 空投。Darwinia 官方已于 2020年3月20日，对 RING & DOT 的持有者进行了快照，RING & DOT的持有者可在 Crab 网络上线后自行查询/领取。DOT 的空投比例：1 DOT = 50 CRING，RING 的空投比例：1 RING = 1 CRING。快照包含 ERC-20 和 TRC-20 的 RING，包括古灵阁中存单部分，KTON 不在此次快照范围。

另外Darwinia主网主要的功能已经开发完成，但还需要进行更多的安全审计和测试，此外，我们也在等待Substrate稳定下来，最终主网上线的时间应该会比Polkadot主网稍微晚一点。

### 3、DARWINIA目前有哪些合作伙伴？

Polkadot是我们最重要的合作伙伴，具体来说包括一系列跟W3F和Parity的合作，我们一直积极参与波卡生态建设，包括参与一些线上线下活动，最近也拿到了W3F的一个Grant。

Darwinia最近也经过了层层选拔，最近加入了Web3 foundation bootcamp，最近训练营首期已经开营，在前期的申请过程中，为了选择最佳团队，我们接受了两轮审核，包括书面审核和电话采访，最后和其他14个团队一起加入了突出重围，成功入营。

Darwinia还加入了substrate builders program, 也成功上榜波卡最新发布的轻白皮书，认证成为one of friends polkadot and substrate

其他的合作伙伴还有MakerDAO，麦子钱包，imToken，币乎，Staking节点运营商等等，这些合作伙伴的加入帮助Darwinia丰富了自己的生态。未来我们还有更多的合作伙伴将加入，包括已经很多已经宣布和未宣布的。

### 4、达尔文网络的技术创新是什么？

Darwinia Network采用轻客户端链式中继（ChainRelay）的方法，通过在外源链的目标链上实现链式中继，目标链能够感知源链的状态变化。

Darwinia Relay的创新是将 MMR（Merkle Mountain Range）纳入链头保证，利用乐观的验证博弈（Optimistic Verification Game）实现解决方案，并制定了适当的中继者激励机制。通过这些创新，能够得到一个次线性的中继性能，这意味着不需要对每一个外源链头进行中继，甚至可以实现“按需中继”。

利用 Darwinia ChainRelay 作为公共产品和关键构建块，能够在链和Darwinia网络之间建立桥梁，Darwinia充当中继链，可以将资产从一个链转发到任何其他连接链。

我们的跨链技术方案最近也得到了web3 首席科学家团队的认可，具体的技术细节在最近的波卡官方直播有详细介绍，可以关注我们的公众号观看回顾视频。

### 5、Darwinia会在波卡生态中承担哪种角色？

按照我的理解，Polkadot致力于打造一个跨链的中继网络，在共享安全验证人池的情况下，价值符号可以容易地跨链传递和交互，好比是大家说差不多的方言，沟通就没什么问题；但是，对于外部的异构链，好像就是讲外语的，除了语言以外，文化背景都不一样的，跟他们沟通就不是波卡想要搞定的了。
波卡实际上发过一个RFP，也就是提出一个问题请项目团队来解决，它的原来思想是在波卡和每一个外部异构链之间搭一座桥，好比是一个翻译的角色，来解决这个问题。所以这个问题的本质是异构链之间的互操作性问题，达尔文就是来解决这个问题的。

而Darwinia创新性的提出了去中心化背书技术和去中心化桥接技术，侧重在异构链之间搭建中继桥，帮助波卡生态中的链方便地与外面的世界进行沟通互联，并且达尔文作为一个桥中心，只需要从外部链搭建一座到达尔文的桥。就可以使每一个链接的链实现互联，而不需要两两之间都要建桥。达尔文针对这个应用改造自己的链，来高效实现这个能力。

所以，对波卡生态而言，每一个项目都可以通过达尔文获得这种能力，真正做到专注自己的业务，大家都需要的异构链跨链需求就我们来搞定了，不用每个人都重复造一次轮子。在此基础上，我们希望可以看到众多单链协议可以实现多链版本的升级，比如defi 应用将不再局限于以太坊，接入外部链的高流动性资产，能真正突破应用的格局性瓶颈，实现资产互联将又近了一步。

Darwinia将可以依托这些应用和资产帮助Polkadot生态打造更丰富的落地应用和相互连接的资产互联网。这是我们希望能给波卡以及波卡生态内的项目带来的价值。

波卡生态不同其他网络生态，特别强的一点是各个项目有一定的同源性，举个例子，比如我们的账户公私钥体系是一样的，某个用户因为Darwinia创建了一个Account，实际上他也等于在Acala或者ChainX上有了账户，虽然显示的地址是不同的，但是是通过同一个私钥进行控制的，那么实际上每个项目都是可以共享用户，用户也可以无缝在链间穿梭，大大降低了进入的摩擦阻碍。同时每条链实现的能力同样可以惠及其他生态项目。

所以，让我们一起努力，打造一个丰富多彩的波卡生态。

### 6、Darwinia社区目前也是波卡生态项目中最活跃的社区之一，海内外社区活动有哪些最近进展呢？

最近的海内外活动非常丰富。海外活动方面，我们参加了波卡的sub0 conference, 首次披露了达尔文的技术细节，有超过1000名海内外开发者，区块链爱好者参与了活动，也在5.11在波卡官方crowdcast直播间进行了针对达尔文的技术亮点的专场直播，许多行业大咖，比如web3的首席科学家也在参与了我们的直播互动，回顾视频可以关注我们达尔文的公众号来观看。

Crab网络的节点大赛也在火热进行中，大家可以参与节点运行，有丰厚奖励，还有机会入选Darwinia主网创世节点。

我们和麦子钱包也发布了联名NFT，活动浏览点击转发等累计超过5w人参与，更多精彩的活动欢迎关注我们的twitter和加入我们的电报社群，这款NFT也可以在opensea上找到。

定期的链式反应Meetup一直在和开发者探讨，前沿技术，分享内容干货，追踪行业热点，不定期邀请行业大咖现场教学，如：Substrate，Rust，Polkadot等，也会邀请其他波卡生态项目的伙伴进行分享，比如acala, phala等

### 7、对比于加密货币市场，NFT方面还算是小众市场，达尔文网络将对跨链NFT作出什么样的贡献，日后的游戏资产共享是否成为一种可能呢？

传统金融市场中NFT非标资产规模数倍于标准化资产市场，游戏道具之类的NFT只是一种应用，将来更多的NFT比如供应链金融中的各种票据、仓单；通证化的艺术品等等种类繁多，市场规模也会超过标准化的加密货币市场。

达尔文网络将为基于各种链发行流通的各种NFT资产提供跨链流通和互操作的基础设施。提到的游戏资产共享将是必然出现，一个游戏中的道具将会在不同的游戏中起到作用，游戏间的壁垒将会模糊，这种雏形已经出现，比如进化星球游戏中已经用了加密猫来作为宠物。

我们后面的目标是将进化星球这款跨链游戏作为一个showcase把它的能力充分展示出来，作为一个标杆来展示游戏间是如何可以互相协作的。也包括我们将发布一个跨链版本的NFT交易市场，好比是OpenSea的跨链升级版，也作为应用协议跨链升级的演示。

### 8、Darwinia在大热的Defi方向会如何布局？

在去年，我们已经宣布将会跟MakerDAO合作，Darwinia将搭建稳定币DAI跨链转接桥，并基于Substrate开发支付应用链，DAI将成为其跨链转接桥支持的首个稳定币。稳定币DAI将可通过Darwinia网络跨链至波卡平行链和Darwinia应用链。

DAI的跨链转接桥将允许用户使用Darwinia网络作为转接桥在以太坊网络和Darwinia网络间转移代币，例如DAI作为基于ERC20的稳定币可从以太坊转接桥合约进入，并转移至Darwinia网络，进入波卡其他平行链，或者Darwinia支付应用链。

并且达尔文的去中心化资产跨链技术，可以帮助以太坊上的defi应用实现多资产抵押，规避风险的同时，帮助实现从单链应用到跨链应用的升级，引入多链高流动性的优质资产，突破defi应用在以太坊上的应用瓶颈
