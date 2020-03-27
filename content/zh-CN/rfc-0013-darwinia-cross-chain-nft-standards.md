---
id: rfc-0013-darwinia-cross-chain-nft-standards
title: 0013 Darwinia Cross Chain Nft Standards
sidebar_label: 0013 Darwinia Cross Chain Nft Standards
custom_edit_url: https://github.com/darwinia-network/rfcs/edit/master/RFC/zh_CN/0013-darwinia-cross-chain-nft-standards.md
---

- rfc: 13
- title: 0013-darwinia-cross-chain-nft-standards
- status: Draft
- desc: Darwinia Cross-chain NFT Standards
- 

# Cross-chain NFT Standards

## I. 概述

为了方便的标记一个物品或者一个资产，我们会用一个唯一的标识来标记它，不同的物品具有不同的标识。我们先拿物理空间里面的物品举例，在理想情况下，所有的物品都应该在同一个时空里面，这样大家都能观察的到，并且方便做区分和标识。但是现实情况是，不同的物品可能存在于不同的时空里面，并且观察者也不一定能看到每一个物品。同样的情况，在虚拟资产世界，因为存在不同的账本或称区块链网络(简称域)，不同的物品在同一个域里面因为有不同的标识，可以容易的区分和定位，但是该域里面的观察者无法识别和解析来自外部域的物品标识。

目前现有的很多通证标准的设计，都主要是针对域内资产进行标识设计，没有将不同域内的资产复用考虑进来，这样导致在对非同质资产进行复用时，单独的Token ID无法标识唯一的资产，还需要带上很多域信息，实现起来十分复杂。

跨链技术可以极大的帮助通证在更广泛的区块链网络中实现互联互通，但是同时，也给开发者和用户带来了一些认知和使用门槛，其中就包括通证可识别性的问题。

因为目前的通证标准，例如ERC20或ERC721，只记录的其在某个特定链上的所有权信息，没有考虑到通证有可能会分布在两个区块链网络。当通证同时分布在两个区块链网络时，我们需要一套识别和解析系统帮助用户和通证应用来解析和查询当前的通证状态。当我们给出一个NFT的Token ID时，我们无法确定它目前所在区块链网络是哪个，其所有者是谁，因为当NFT发生跨链转移后，在其中一个区块链网络上该通证处于活跃状态，而其他则处于不可用状态，比如锁定状态。在没有通证解析系统的情况下，链外操作无法确定该NFT在哪条链上时处于活跃状态。

跨链环境下，Token面临的识别性和解析问题，需要新的解决方案和标准来解决。因此我们引入一个基于通证跨链证明的解析系统来解决通证跨链时的定位和解析需求，通过通证解析系统和域内唯一标识，我们可以存在与不同域的通证之间的关联关系映射起来，并标识他们之间的相同与不同。

本文将在[RFC-0010 Darwinia Cross-chain NFT Bridge Protocol](./rfc-0010-darwinia-cross-chain-nft-bridge-protocol)的基础上，进一步细化NFT相关的标准和设计细节。



## II. 介绍

### A. 目标

- 可识别。NFT在跨链过程中，应该保证NFT的token id可被追溯。因为不同区块链的token id表示的类型不同，所以NFT在不同区块链之间流转的过程中，token id的内容和类型都可能会发生变化；甚至同一个NFT在从chain A跨到chain B，再从chain B跨回chain A后，在chain A上的token id也可能会发生变化，token id的不可识别直接导致资产价值归零。因此与fungible token不同的是，保持NFT的可识别性是NFT跨链安全的重要部分。
- 可追踪。因为NFT在跨链过程中，token id会不断发生变化，因此了解同一个NFT在不同链上的token id可以对应用层的建立更加复杂的逻辑提供极大的帮助。
- 访问友好。鉴于需要和外部的钱包/RPC客户端交互，因此减少外部访问的成本，提高效率和友好性也是NFT跨链中的重要内容。在 [0010-darwinia-cross-chain-nft-bridge-protocol](https://github.com/darwinia-network/rfcs/blob/master/RFC/zh_CN/0010-darwinia-cross-chain-nft-bridge-protocol.md) 实现方案中，随着NFT在Bridge Core内流转的次数越多，在Bridge Core内沉淀的信息也就越多。因此外部钱包/RPC客户端只需要向Bridge Core请求一次，就可以得到该NFT在所有链的local token id 信息。而不需要向每条链分别请求获取。



### B. 术语

- **GID / Global ID**， 表示NFT在所有链中的全局唯一标识。适用范围：全局
- **Local ID / Local token id**，表示NFT在不同的区块链中的token id. 适用范围：某一条区块链



### C. 分类

当我们讨论NFT跨链时，可以根据NFT所在基础设施的网络情况，分成几类：

- 跨平行链(Polkadot内)

当在平行链之间进行跨链时，例如在Polkadot网络中，因为有共享安全，共享运行时SPREE等设计，因此将通证解析系统放在中继链上时最合适的，因为通证跨平行链的消息会流经中继链，中继链可以通过在消息中继模块之外，嵌入一个收集模块，将通证跨链消息规范化统一收集之后，提供给通证解析服务。

- 跨异构公链

在异构跨链模式下，例如Ethereum和EOS之间，或者Ethereum和Tron之间，通证跨链一般通过跨链转接桥的方案等进行跨链，例如ACCS(HTLCs), XClaim, Parity Bridge(Mainet/Sidechain)，Darwinia Bridge Core等等。

对基于Darwinia Bridge Core技术搭建的跨链转接桥，其NFT的跨链是通过在对手链上构建超额抵押的对称CBA，并利用Chain Relay技术来保证可赎回性和可解析性。Darwinia Bridge Core跟其他转接桥技术的区别有两点，1. 背书链也支持Chain Relay以更好的验证外链证明，而不需要担保质押 2. 通过在不同的公链上构建Darwinia Chain Relay，并利用一个Hub结构来优化利用这些基础设施，实现公链间的互联互通。设计细节可以参考RFC0010.

本文所讨论的NFT跨链标准，主要集中的Polkadot内部，也就是平行链之间的NFT跨链标准，而对于公链间的跨链桥细节和外部公链上的NFT标准则不包含在本文范围。



## III. 跨链共享标准

### A. 全局唯一标识GID和Local ID

鉴于NFT跨链的目标，本方案会在跨链时为NFT分配一个唯一个全局ID，并且在跨链桥内部保留其在外部链上的local token id，达到可识别、可追踪、访问友好的目标。

（跨链桥Bridge Core的实现细节详见[0010-darwinia-cross-chain-nft-bridge-protocol](https://github.com/darwinia-network/rfcs/blob/master/RFC/zh_CN/0010-darwinia-cross-chain-nft-bridge-protocol.md)）[1]

为了将不同标准的通证标识符进行规范化，以提供识别和解析方法，与现有的标准进行很好的协调和对接，并满足社区基础设施建设的标准需求。跨链系统将为每一个跨链后的通证分配一个全局ID(global_id)。

#### GID生成方式

GID 作为 NFT的全局标识，需要保证唯一性。因此不同的NFT在跨链时为其通过自增的方式分配一个GID即可。

#### CID-based Local ID 编码方式

**Local ID** 为了保证其跨链可识别性，需包含一下三个字段：

```python
<chain id><contract id><token id>
```

不同的区块链的数据类型不同、加密方式等都不相同，因此local token id很可能从内容到类型都差别很大。

这里，我们借鉴IPLD[2]中CID的编码方式。鉴于IPLD用来解决不同区块链上的内容寻址问题，因此也非常适合用来解决这里的local token id的索引问题。

```python
<mbase><version><chain id><data>
```

解释：

- **mbase**: 编码方式，base58,base64 etc.

- **version**: 版本信息。

- **chain id**: chain id信息

- **data**： 包含以下两个字段

  ```python
  <contract id><token id>
  ```

  contract id 和 token id 又遵从以下格式：

  ```python
  <hash func><len><value>
  ```

  因此完整的data字段如下：

  ```python
  <hash func><len><contract id content><hash func><len><token id content>
  ```

通过这种编码方式，既可以清晰地寻址到 local token id，又节省了字节数，提高了传输效率。

### B. Utlilising Fungible/Non-fungible assets on Polkadot

基于已有的polkadot内部fungible asset的标识和使用方案[3]进行扩展，我们可以使用如下一行URI格式的标识方式，为钱包/ RPC客户端的访问提供便利：

同一个NFT资产可以用：

```html
polkadot://<nft|ft flag>/<Local ID>
```

可以用：

```python
polkadot://<nft|ft flag>/<Global ID>/<chain ID>
```

来表示。

> 其中nft|ft flag, 0表示fungible token, 1 表示  non-fungible token

举例：假设`z43AaGEvwdfzjrCZ3Sq7DKxdDHrwoaPQDtqF4jfdkNEVTiqGVFW`表示以太坊上合约为`0x14a4123da9ad21b2215dc0ab6984ec1e89842c6d`，token id为`0x01`的NFT，它对应的GID为`42`，那么

```python
polkadot://1/z43AaGEvwdfzjrCZ3Sq7DKxdDHrwoaPQDtqF4jfdkNEVTiqGVFW
```

表示，也可以用：

```python
polkadot://1/42/eth
```

表示。

这两个URI会寻址到同一个NFT. 因为Bridge Core已经提供了GID和Local ID间的关系拓扑



### C. 数据请求格式

如果有钱包/RPC客户端向Bridge Core请求NFT的拓扑信息，可以根据GID得到所有已知链的local ID信息：

```html
{
	GID: 42,
	total: [
		{
			chain_id: eth,
		  contract_id: 0x1234,
			token_id: 0x01
     },
		{
			chain_id: eos,
			asset_id: dgoods,
			token_id: 1.2.3
		},
	  ...
	]
}
```

### D. 基于UNFO的解析模块

通证解析模块是NFT cross-chain协议内嵌的一个模块，用于在 *Issuing chain* 或者其连接的中继链上记录和解析当前通证在中继链范围内的全局状态，并规范化处理成解析格式的方式，来为跨链网络提供通证解析查询和可追踪性。由于在NFT跨链桥协议中，使用了UNFO来记录与NFT相关的跨链信息，协议和其他映射信息，因此我们可以利用这些证明信息，并引入NFT解析模块来记录、更新和解析UNFO及相关信息。

在NFT通过Bridge Core 从B链转移至I链的过程中，Bridge Core会为每一个NFT分配一个GID，并将中间状态及其转移过程表达成UNFO，包括GID, (External Chain ID, External Contact Address, External Token ID), lock_script等信息。

这些UNFO记录集合会被归集在一个记录解析表里面，通过这个解析表，可以为跨链协议(e.g redeem)提供NFT通证解析服务，也可以为外部系统提供NFT解析服务。

| UNFO | GID     | Externl Chain ID | External Contact Address | External Token ID | Lock_Script                  | Active Status |
| ---- | ------- | ---------------- | ------------------------ | ----------------- | ---------------------------- | ------------- |
| 1    | GID0001 | Ethereum         | A_ERC721                 | 12                | script_issuing_burn_or_relay | False         |
| 2    | GID0001 | Tron             | B_TRC721                 | ?                 | script_backing_redeem        | True          |
| 3    | GID0002 | EOS              | C_dGoods                 | 2.5.4             | script_issuing_burn_or_relay | False         |
| 4    | GID0002 | EOS              | C_dGoods                 | 2.5.4             | script_ownership_contract    | True          |
| 5    | GID0003 | Bridge Core      | None                     | None              | script_ownership_contract    | True          |
| 6    | GID0004 | ETC              | ETC_ERC721               | 23                | script_issuing_burn_or_relay | False         |
| 7    | GID0004 | Ethereum         | D_ERC1155                | 13                | script_backing_redeem        | False         |

GID0001: This NFT is cross-chain transfered from (Ethereum, A_ERC721, 12) to (Tron, B_TRC721, ?) trough Bridge Core, Currently it is active on Tron.

GID0002: This NFT is cross-chain transfered from (EOS, C_dGoods, 2.5.4) to an account Bridge Core,the script_ownership_contract is linking to an ownership managemetn contract on Bridge Core.

GID0003: This NFT is originally created on Bridge Core, it is recorded as UNFO because the golobal identifier is generated in the UNFO module, the script_ownership_contract is linking to an ownership managemetn contract on Bridge Core.

GID0004: This NFT is cross-chain transfered from (ETC, ETC_ERC721, 23) to (Ethereum, D_ERC1155, ?) trough Bridge Core, and then redeem reversely back. The 7th UNFO's External Local ID is unknow before redeem, but when redeeming, it will be updated to reveal it's value.


<center>Figure: UNFO Set Table Sample</center>
备注: 

1. External Token ID有可能是未知状态，用"?"表示，之所以会出现这种情况，是因为在issue过程中, 目标发行链上生成的External Token ID 不会通知和反馈给Bridge Core，没有相关的交易证明信息，UNFO也就只好设置该值为未知。但是，当后面某些新的赎回交易发生时，发起者发送给Bridge Core的赎回交易有可能会包含GID和External Token ID，此时可以通过这个交易证明，更新原来未知的External Token ID值为已知值。
2. 为了保持良好的一致性，在NFT通过Bridge Core跨链流转的生命周期内，希望保持External Chain ID和 (External Contact Address, External Token ID) 的映射关系保持不变，此时可以通过上面提到的解析服务，至历史UNFO记录里面查询相应的External Token ID，以保持一致性。

### E. 跨平行链操作

在稍后的III章节，我们将会假设转账是发生在同一条链上的，关于如何处理跨链间的转账，我们将会使用一个关联的SPREE模块来解决(参考Polkadot相关方案[3]实现)。

通证解析系统还可以设计一个关联的SPREE模块(共享存储和共享运行时)，这样可以把解析模块当做一个共享的模块，开放给其他平行链来使用。SPREE模块还可以帮助在解析模块内定义约束条件，例如全局的通证总量，发行规则，并部署至SPREE模块，可以实现中继网络管辖范围的验证和可信互操作。



## IV. NFT Standard on Polkadot/Darwinia

A cross-chain non fungible token standard is required for blockchains to transfer assets across the ecosystem and for clients (e.g. wallet, browser extension) to offer unified support of the token that provided by different chains.

将参考以太坊中的ERC721和ERC1155标准。所有权管理模块或者合约将直接使用GID作为NFT通证的ID，而GID是由UNFO模块中负责管理和生成的，这一点跟ERC721不同，因为在ERC721中，NFT合约负责管理和生成NFT 的Token ID。

NFT标准主要由几部分组成，GID管理、资源描述、所有权管理、扩展标准。

### A. NFT Descriptions

NFT descriptions offers a universal way to describe, display the details about a token. This information may not be stored on-chain to reduce usage of on-chain storages. A centralized or decentralized token registry may be used to discovery the token description, which is out of the scope here.

### B. 所有权管理

[WIP]

### C. 规范

[WIP]



### 参考

[1] https://github.com/darwinia-network/rfcs/blob/master/RFC/zh_CN/0010-darwinia-cross-chain-nft-bridge-protocol.md

[2] https://ipld.io/

[3] https://hackmd.io/gQKQGf42TeOODid3hM4_1w

[4] https://en.wikipedia.org/wiki/Unique_identifier
[5] https://en.wikipedia.org/wiki/Identifiers.org#Comparison_with_other_URI_systems
[6] https://elixir-europe.org/platforms/interoperability