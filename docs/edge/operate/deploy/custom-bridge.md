---
id: custom-bridge
title: How to Use a Custom Bridge
sidebar_label: How to Use a Custom Bridge
description: "Learn how to disable the native bridge through allowlisting."
keywords:
  - docs
  - polygon
  - cdk
  - bridge
  - custom
  - disable
---

Before we dive in, it is important to note that it is not possible to fully disable the native bridge. What we can do instead is significantly limit its usage through the use of allowlists.

## Limiting the Use of the Native Bridge

The Edge deployer can restrict the native bridge usage by defining an address of the bridge allow list admin via the `--bridge-allow-list-admin` flag at genesis. This action deploys allowlist predicates which verify each bridge transaction. If a sender is not permitted, the transaction will fail and revert.

As a deployer, setting your own address as the `Admin` and not including any other address in the allowlist effectively denies all other addresses from using the native bridge.

## Implementing a Third-Party Bridge

When it comes to implementing a third-party bridge, it is necessary to utilize the state sync mechanism. This can be done through the `StateSender` and `L2StateSender` contracts, employing the `syncState` functions. This method permits the transmission of arbitrary data (in byte array form) from rootchain to childchain and vice versa.

Remember that receiver contracts must implement onStateReceive functions for receivers on layer 2, and onL2StateReceive for receivers on layer 1.

### Flow for L1 to L2

Here are the steps to bridge from rootchain to childchain:

1. **Initiate Transaction**: The user initiates a transaction on L1 by specifying the StateSender contract, the receiver on L2, and the data to be sent.
2. **Event Emission**: An event, state sync event, is emitted and detected by validators on L2.
3. **Commitment Creation**: Validators generate a commitment from the state sync events and commit it to the StateReceiver contract on L2. This state transaction is automatically created by validators on each sprint block, given there are state sync events to commit.
4. **Event Execution**: After the commitment is submitted, the Relayer executes state sync events on the StateReceiver contract. This requires a node to be initiated with the --relayer flag.
5. **Data Reception**: During the execution step on StateReceiver, the onStateReceive function is called on the receiver contract, passing the byte array (data) from step 1.

### Flow for childchain to rootchain

For bridging from childchain back to rootchain, follow these steps:

1. **Initiate Transaction**: The user sends a transaction on the childchain to the L2StateSender contract.
2. **Exit Event Emission**: An exit event is emitted and picked up by validators on L2. The ID of this exit event can be found in the transaction receipt, which will be used in the subsequent steps.
3. **Checkpoint Creation**: Validators generate a checkpoint from these exit events and submit it to the CheckpointManager contract on L1. This occurs at the end of every epoch if there are exit events to checkpoint.
4. **Proof of Exit Generation**: Once the checkpoint containing their exit event is submitted, the user can call the bridge_generateExitProof jsonRPC endpoint on an L2 node using the exit event ID from step 2. This returns a proof of exit for the user and some additional data needed to complete the data bridge back to L1.
5. **Data Bridging**: The user then sends a transaction to the ExitHelper contract (function exit), using the data returned by the jsonRPC endpoint in the previous step. This action bridges the user's data back to L1.
