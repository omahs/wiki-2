---
id: getting-started
title: Get Started with Polygon PoS
sidebar_label: Quick Start
description: "Build your next blockchain app on Polygon."
keywords:
  - docs
  - matic
  - polygon
  - build on polygon
  - blockchain
  - introduction
  - how to launch dapp
  - dapps
  - ethereum
  - deploy
  - connect
image: https://wiki.polygon.technology/img/polygon-logo.png
---

import useBaseUrl from '@docusaurus/useBaseUrl';

This guide will introduce you to the Polygon PoS ecosystem. You'll find links to valuable pages, resources and websites that will bring you up to speed on building on Polygon.

:::tip Stay updated

Keep up with the latest builder updates from the Polygon team and the community by subscribing to the
[<ins>Polygon notification groups</ins>](https://polygon.technology/notifications/). You can also find the links to all the [<ins>Polygon communities here</ins>](https://polygon.technology/community/).

:::

## Polygon POS
POS is a sidechain secured by a set of economically-incentivized validators whose main goals are to attest to correct state transitions and guarantee the security of the network.
Driven toward the scalability of the Ethereum network, it aims at providing a low-cost blockchain service, with negligible fees compared to L1, and at the same time benefit from the Ethereum battle-tested security.

### POS architecture
The [design system](/docs/pos/polygon-architecture.md) of the Polygon POS entangles 3 layers: Ethereum (Layer 1), the Tendermint-based Heimdall and GoEthereum-based Bor.

In our design, Ethereum provides smart contracts that support the validator community, such as the ones for staking MATIC and sending out rewards, as well as checkpoint contracts that sync the state of the sidechain with layer 1.
The two other instances of the Polygon ecosystem, Heimdall and Bor, are in charge of all the logic running inside layer 2. 

Bor is the POS instance responsible for producing transaction blocks. Those blocks are consolidated by the validation layer of the POS ecosystem, Heimdall. It gathers the block data produced by the Bor layer and posts it into layer 1 in a Merkle tree format, syncing the L1 with its sidechain.
### Transition to ZkValidium
With Polygon 2.0 and its proposal to position Polygon as the value layer of the internet, Polygon aims at democratizing the internet, facilitating defi and promoting community governance. To accompany this process, POS is also expected to evolve. From a legitimate sidechain, POS is expected to become a first-of-its-kind zkValidium. 

<img src={useBaseUrl("img/pos/zkvalidium.png")} />

The zkValidium name is transparent: the POS whose security and consensus derived solely from the validators work, will now include zero-knowledge proofs and request those same validators to act as decentralized sequencers, that is, being responsible to decide which transactions to include in a block and in which order.

Although this new technology might serve different purposes compared to the zkEVM, the major idea behind Polygon 2.0 is to integrate all solutions. 

### Building on Polygon

If you are an Ethereum developer, you are already a Polygon developer. Simply switch to the [Polygon RPC](https://polygon-rpc.com/) and get started. All the tools you are familiar with on the Ethereum blockchain are supported on Polygon by default, such as Truffle, Remix, and Web3js.

You can deploy decentralized applications to either Polygon Mumbai Testnet or the Mainnet. The Polygon Mumbai Testnet connects with the Ethereum Goërli Testnet, which acts as its ParentChain.

## Deploy on POS

### Building a new dApp on Polygon?

Decentralized applications act as the bridge between users and their data privacy on the blockchain. The increasing number of dApps validates their usefulness within the blockchain ecosystem, solving challenges like executing transactions between two participants without the need for central authority via smart contracts.

Suppose you have no prior experience building decentralized applications. In that case, the below-mentioned resources will give you a head start on the tools required to build, debug, and deploy dApps on the Polygon Network.

Read [our tutorials](/docs/category/deploy-a-contract) to learn how to deploy a dApp on Polygon.

## Connect to POS

### Connecting via RPCs

You can add Polygon to MetaMask or Arkane, which allows you to connect to Polygon using [RPC](https://docs.polygon.technology/docs/tools/wallets/metamask/config-polygon-on-metamask/).

:::note Directory of publicly available PoS RPC endpoints

Check out a list of public endpoints for the Polygon PoS network at [<ins>Alchemy's Chain Connect resource</ins>](https://www.alchemy.com/chain-connect/chain/polygon-pos) and [<ins>Chainlist</ins>](https://chainlist.org/chain/137).

:::

In order to connect with the Polygon network to read blockchain information, we recommend using the Alchemy SDK.

```js
// Javascript
// Setup: npm install alchemy-sdk
const { Alchemy, Network } = require("alchemy-sdk");

const settings = {
  apiKey: "demo", // Can replace with your API Key from https://www.alchemy.com
  network: Network.MATIC_MAINNET, // Can replace with MATIC_MUMBAI
};

const alchemy = new Alchemy(settings);

async function main() {
  const latestBlock = await alchemy.core.getBlockNumber();
  console.log("The latest block number is", latestBlock);
}

main();

```

### Connect your dApp to POS

If you already have a decentralized application and are looking for a platform to help you scale efficiently, then you are at the right place because Polygon allows you to:

1. **Easily migrate from Ethereum Virtual Machine (EVM) based chain**: Polygon prides itself in being the ultimate Layer-2 scaling solution for Ethereum. You don't have to worry about the underlying architecture while moving or deploying your dApps to the Polygon Network as long as it is EVM-compatible.
2. **Use Polygon as a faster transaction layer**: Deploying your dApp to the Polygon Mainnet allows you to leverage Polygon as a faster transaction layer for your dApp. Additionally, you can get your tokens mapped by us. You can join our [technical discussions group](http://bit.ly/matic-technical-group) on Telegram to learn more.

### Bridge assets

By using the [Polygon main site wallet](https://wallet.polygon.technology/) you have access to all bridge solutions that POS offers. Manage cross-chain asset transfers from and to POS seamlessly with the following features:

- [Native bridge](https://wallet.polygon.technology/polygon/bridge/deposit) : the safest and fastest way to bridge cross-chain assets to the Polygon chain. 
- [Faster bridges](https://wallet.polygon.technology/polygon/fast-withdraw) : third-party bridging services that aid cross-chain transfers.
- [Token mapper](https://mapper.polygon.technology/): the way to map tokens between Polygon and Ethereum.
- [Bridge explorer](https://bridge-explorer.polygon.technology/deposits) : check figures and transactions happening on the bridge.
- [Token swap](https://wallet.polygon.technology/polygon/token-swap) : easily exchange tokens on POS.

## Interact with POS
### Wallets

To interact with the Polygon Network, you need to have an Ethereum-based wallet because Polygon runs on Ethereum Virtual Machine (EVM). You can choose to set up a [Metamask](https://github.com/0xPolygon/wiki/blob/master/docs/tools/wallets/metamask/overview.md) or [Arkane](https://github.com/0xPolygon/wiki/blob/master/docs/develop/wallets/arkane/intro_arkane.md) Wallet. More on wallet-related information and why you need one can be found in our [wallet documentation](https://docs.polygon.technology/docs/develop/wallets/getting-started).

### Visualize contracts
[PolygonScan](https://polygonscan.com/) is a way of visualizing everything happening on the POS chain: Matic statistics, transaction figures, block data and other relevant information. For each block, we provide general information such as Block number and timestamp, as well as rewards, difficulty and fees. 

## Resources

Here's a list of valuable resources to help you build your projects on the Polygon ecosystem:

| Infrastructure providers                                                         | Development environments                                        | Wallets                                                                          |
|----------------------------------------------------------------------------------|-----------------------------------------------------------------|----------------------------------------------------------------------------------|
| [Alchemy](https://github.com/0xPolygon/wiki/blob/master/docs/develop/alchemy.md) | [thirdweb](https://portal.thirdweb.com/)                        | [Metamask](https://docs.polygon.technology/docs/tools/wallets/metamask/overview) |
| [Chainstack](https://chainstack.com/)                                            | [Remix](https://docs.polygon.technology/docs/develop/remix/)    | [Arkane](https://docs.polygon.technology/docs/develop/wallets/arkane/intro)      |
| [QuickNode](https://www.quicknode.com/)                                          | [Truffle](https://docs.polygon.technology/docs/develop/truffle) |                                                                                  |
|                                                                                  | [Hardhat](https://hardhat.org/)                                 |                                                                                  |
|                                                                                  | [Replit](https://replit.com/)                                   |                                                                                  |