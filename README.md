**Subnets**

**Subnet Definition:**

A subnet is a special way to make the Stacks blockchain work better. It helps to make things faster and more reliable when developers build things on the Stacks blockchain.

**Mainnet and Subnet:**

The Stacks blockchain is the main network where everything happens. The subnet is like a separate network connected to the main one. It's like having two layers: the main layer (layer-1 or L1) and the subnet layer (layer-2 or L2).

**Communication between Mainnet and Subnet:**

The mainnet and subnet talk to each other through a smart contract. This smart contract is specific to the subnet. Each subnet has its own smart contract to communicate with the mainnet.

**Functions of the Smart Contract:**

The smart contract in the subnet can do various things to help the mainnet and the subnet work together. Some of the important things it does are:

**commit-block:** Subnet miners use this function to save important information on the mainnet.

**deposit:** Regular users use these functions to put their assets into the subnet. The subnet then makes copies of these assets for use on its layer. The original assets are still kept on the mainnet, but they are linked to the subnet.

**withdraw:** Users can use these functions to take their assets back from the subnet. It's a two-step process: first, the user initiates the withdrawal within the subnet, and then the actual withdrawal happens on the mainnet.

**Allowed Assets:**

The subnet has some rules. Only certain assets that are "registered" are allowed to be used within the subnet. To register an asset, the subnet's administrator must use specific functions like register-new-ft-contract or register-new-nft-contract.

**Temporary Asset Holding:**

A subnet is designed to hold Stacks assets temporarily. Users can deposit their assets from the main Stacks blockchain into the subnet. This allows them to benefit from faster transactions and lower fees while operating within the subnet. When they are done using the subnet, they can withdraw their assets back to the main Stacks chain.

**Locking Assets on the Main Chain:**

When a user deposits assets into the subnet, the original asset gets locked in the subnet contract on the main Stacks chain. Meanwhile, representations of those assets are created and made available in the user's Hiro Wallet and can be used by applications running on the subnet.

**Centralized Block Producers:**

The current implementation of a subnet relies on either a single block producer or a fully-trusted federation of block producers. This means that users who interact with a subnet should be aware that they are sacrificing some decentralization and security for the speed provided by the subnet. Therefore, it is essential to only deposit assets into trusted subnets.

**Customizable Throughput:**

Each subnet can define its own throughput settings. By default, the subnet should support at least 4 times higher transaction throughput compared to the main Stacks chain. This means it can handle more transactions per second, which leads to faster confirmation times.

**Interacting with Subnets:**

Interacting with a subnet is similar to interacting with a different Stacks network, like testnet vs. mainnet. Users can use their Hiro Wallet and applications on the subnet to perform various operations with their assets.

**Multiple Subnets Support:**

The Stacks blockchain can support many different subnets, each serving different purposes or applications.

**Custom Consensus Rules:**

Each subnet has the flexibility to use its own consensus rules. This allows different subnets to have unique ways of reaching agreements on transactions and maintaining the network.

**Current Consensus Mechanism:**

This repository implements a consensus mechanism two-phase commit approach among a federated pool of miners. This method helps in achieving consensus and confirming transactions efficiently.

**Asset Support:**

Subnets support different types of assets such as fungible tokens (FTs), non-fungible tokens (NFTs), and the native Stacks token (STX). Users can deposit and withdraw these assets from the subnet using specific layer-1 transactions.
**Deposit and Withdrawal Process:**
To deposit assets into a subnet, users submit a regular layer-1 transaction to invoke the "deposit" method on the subnet's smart contract. For withdrawals, users first commit the withdrawal on the subnet, and then they submit another layer-1 transaction to invoke the "withdraw" method on the subnet's smart contract to complete the withdrawal process.

**Subnet Miner testnet**

Bitcoin node -> Stacks follower node <-> Subnet miner node

- Deploy your own subnet.clar (from this template https://github.com/hirosystems/stacks-subnets/blob/develop/core-contracts/contracts/templates/subnet.clar.mustache)
- Run a subnet miner node configured to follow this contract
- The subnet node needs to talk to a stacks node
- The stacks node needs to talk to a bitcoin node

**Bitcoin Node Testnet**

Open a terminal window and follow these steps:

- Set the BTC_VERSION environment variable:

  - export BTC_VERSION=22.0

- Download the Bitcoin binary:

  - sudo curl -L https://bitcoin.org/bin/bitcoin-core-${BTC_VERSION}/bitcoin-${BTC_VERSION}-osx64.tar.gz -o /Volumes/BlockChain/bitcoin-22.0.tar.gz

- Extract the downloaded archive:

  - sudo tar -xzvf /Volumes/BlockChain/bitcoin-${BTC_VERSION}.tar.gz -C /tmp

- Move the binaries to the appropriate location:

  - sudo cp /Volumes/BlockChain/bitcoin-${BTC_VERSION}/bin/* /usr/local/bin/

- Bitcoin Config:

  - Create the bitcoin data directory:
    - sudo mkdir /Volumes/BlockChain/bitcoin

- nano bitcoin/bitcoin.conf

