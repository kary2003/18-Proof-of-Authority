

ZBank & Blockchain Technology

Blockchain Technology: 

According to Tech4Fresher https://tech4fresher.com/blockchain-technology-explained-with-infographics/

"A blockchain is a growing list of records called blocks which are interconnected by utilizing cryptography. Each block contains a cryptographic hash of the previous block, a time stamp, and exchange information"

What can it do and how to utilize it?
1. Blockchains can safely store information over a shared system that is publicly vieweable but can't be easly altered.
2. Blockchains allow the safe exchange of contracts, property, cash, etc without the need of a centralized systems like banks or governement.
3. Blockchain allows for 100% transperancy since all clients are able to see another clients operation. 

permissioned and a permissionless blockchains: How we can use it here at ZBank

A permissionless blockchain allows for decentralization elimintating the need for government or banks to process transactions for clients. 

Therefore our team developed

a permissioned blockchain which will allow us more control over the configuration of the network and also allows for the restriction on the consensus participants. 

The benefits of permissioned block chains according to 

* Efficient performance: When we compared permissioned blockchains to permissionless blockchains, they offer better performance. The core reason behind this is the limited number of nodes on the platform. This removes the unnecessary computations required to reach consensus on the network, improving the overall performance. On top of that, permissioned networks have their own pre-determined nodes for validating a transaction.

* Proper governance structure: Permissioned networks do come with an appropriate structure of governance. This means that they are organized. Administrators also require less time to update the rules over the network, which is considerably faster when compared to public blockchains. The public blockchain network suffers from the consensus problem as not all nodes work together to get the new update implemented. These nodes might place their self-interest above the needs of the blockchain, which, in return, means slower updates to the whole network. In comparison, permissioned blockchain doesn’t have the problem, as the nodes work together to move the updates faster.

*Decentralized storage: Permissioned networks also make proper use of blockchain, including utilizing its decentralized nature for data storage.

*Cost-Effective: There is no doubt that permissioned blockchains are more cost-effective when compared with the permissionless blockchains.










In this tutorial, I will demonstrate using `geth`, the official Ethereum client, how to run a PupperNet private network.

This network is configured for `5 second` block times, and uses the Clique Proof of Authority consensus algorithm. This
will ensure fast and efficient testing, so no need to worry about your CPU. The chain ID is `333`.

The sealer node addresses are:

`0xd84d79a0069fb5d3cf8eca3c689f231d6b603c8f`
`0x7a4f862ab163fc62dce2cfbb734ddac153c5e8cc`

The account password for both nodes is `testnetpassword`

This is the configuration from `puppeth`:

![puppeth](Screenshots/puppeth.png)

## Install the geth node software

Download and install `geth` for your operating system here: <https://geth.ethereum.org/downloads/>

## Install the MyCrypto GUI wallet

Download and install the desktop version of the MyCrypto wallet here: <https://download.mycrypto.com/>

This wallet allows communicating with custom networks, which we will configure later.

## Run the first node and enable the mining/sealing

`geth --datadir node1 --unlock "d84d79a0069fb5d3cf8eca3c689f231d6b603c8f" --mine --rpc`

We enable the `--rpc` flag on the first node to talk to it later. This defaults to port `8545`.
We need to unlock the node's account to enable it to sign blocks.

## Copy the enode address from this node

For example:
`enode://b044f481e52f03950ed88ad18f550ace268ad4e4e1647f80c5808d6ea2c4e7f550d8ed25a14608afa6e5828f1b69fdfcf5d7775394f7c38d8592f600e4a37e90@127.0.0.1:30303`

## Use the first node's enode address as the bootnode for the second node and run on a separate port

`geth --datadir node2 --unlock "7a4f862ab163fc62dce2cfbb734ddac153c5e8cc" --mine --port 30304 --bootnodes enode://b044f481e52f03950ed88ad18f550ace268ad4e4e1647f80c5808d6ea2c4e7f550d8ed25a14608afa6e5828f1b69fdfcf5d7775394f7c38d8592f600e4a37e90@127.0.0.1:30303`

Using the first node as a bootnode will enable the nodes to communicate with each other, and discover new nodes later.

## Success!

You should now be mining/sealing blocks using the Proof of Authority algorithm! Now it's time to send a transaction.

## Send a test transaction

Open up MyCrypto and select `Change network` at the bottom left.

Select `Add Custom Node` and use `127.0.0.1:8545` to connect to the first node, add a name, use chain ID `333` and save.

Your configuration should look like this:

![custom-node](Screenshots/custom-node.png)

You should now be connected to the local blockchain.

Click on the `Keystore file` option to access the first node's wallet, and navigate to `node1/keystore` and select
the keystore file, then enter `testnetpassword` as the password.

You should now be able to send a transaction. Fill in the second node's account and send it one ETH.

![transaction-send](Screenshots/transaction-send.png)

Once confirmed, you can check the TX Status by clicking the button in the popup, or pasting the TX Hash into the TX Status section of the app.

![transaction-success](Screenshots/transaction-success.png)

Voila! You can now use the PupperNet blockchain for your local development!
