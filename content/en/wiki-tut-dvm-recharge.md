---
id: wiki-tut-dvm-recharge
title: Recharge EVM address
sidebar_label: Recharge EVM address
---

> This tutorial is only used in Pangolin test network.

## Pangolin Testnet

The Pangolin TestNet is a network for contract developers maintained by darwinia team with token `PRING`. This network integrates the DVM(Darwinia Virtual Machine) which will support Ethereum smart contracts in current darwinia network. So, you can also use common ethereum tools, such as Metamask, Remix, etc. Unlike the crab test network,
token in Pangolin is free to apply.

Developer who needs test token to deploy contract or do something else about smart contract in darwinia network, could apply free token in [Darwinia Element](https://app.element.io/?pk_vid=6961ca0f7c45f8bf16052310122d2437#/room/#darwinia:matrix.org).

## Add Pangolin to MetaMask 

We need to query balance of evm account, so add new network in metamask at first.

![add testnet](assets/wiki-tut-dvm-recharge-01.png)

![set testnet](assets/wiki-tut-dvm-recharge-02.png)

Setting Configuration:

- Network Name：`Pangolin`
- RPC URL: `http://t1.hkg.itering.com:9933`
- Chain ID： `43`
- Currency Symbol： `PRING`

Click Save, the pangolin network will be added in metamask successfully. Then, you could transfer token or deploy contracts in metamask.

## Add Pangolin to Apps

Apps is a collection of toolkits provided by Darwinia Team. You can switch to Pangolin network as follows, click https://apps.darwinia.network/,
add custom ternal configuration ws://t1.hkg.itering.com:9944/, save and reload again.

![support apps](assets/wiki-tut-dvm-recharge-03.png)

> Note: if it prompts websocket unsecurity warn, please change chrome safe configuration to allow access to unsafe content.

## Recharge EVM address

The materials needs to be prepared in advance:

- evm address（Metamask generate one account）
- substrate address （have some balance, apply in element）

Recharge:

1. Generate evm address from substrate address

[apps]-[ToolBox]-[DVM address], enter the evm address, the corresponding substrate address will be generated, which represent this evm address to send or receive Pring.


![create substrate address](assets/wiki-tut-dvm-recharge-04.png)
The corresponding substrate address of `0xAa01a1bEF0557fa9625581a293F3AA7770192632` is `5ELRpquT7C3mWtjerXnTxDmKnvVxJjCCstXcN8yG34o4365H`.


2. Transfer balance use Apps

Transfer balance using Apps, the target address is `5ELRpquT7C3mWtjerXnTxDmKnvVxJjCCstXcN8yG34o4365H`.

![transfer pring](assets/wiki-tut-dvm-recharge-05.png)

`Make Transfer` and wait until the extrinsic been finalized in block.


3. Comfirm balance in MetaMask

![confirm balance in mataMask](assets/wiki-tut-dvm-recharge-06.png)

The balance of evm address `0xAa01a1bEF0557fa9625581a293F3AA7770192632` is 100, a successfully recharge completely。