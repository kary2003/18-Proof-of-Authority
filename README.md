# ZBank & Blockchain Technology

## Blockchain Technology: 

According to [Tech4Fresher](https://tech4fresher.com/blockchain-technology-explained-with-infographics/)

"A blockchain is a growing list of records called blocks which are interconnected by utilizing cryptography. Each block contains a cryptographic hash of the previous block, a time stamp, and exchange information"

What can it do and how to utilize it?
1. Blockchains can safely store information over a shared system that is publicly vieweable but can't be easly altered.
2. Blockchains allow the safe exchange of contracts, property, cash, etc without the need of a centralized systems like banks or governement.
3. Blockchain allows for 100% transperancy since all clients are able to see another clients operation. 

---

# Setting up and running a PuperNet private network using `geth`

Proof of Authority consesus Algorithm.

 * Network configuration: '5 second' block times.
 * Network chain ID: 333

The sealer node addresses are:

`0xd84d79a0069fb5d3cf8eca3c689f231d6b603c8f`
`0x7a4f862ab163fc62dce2cfbb734ddac153c5e8cc`

The account password for both nodes is `testnetpassword`

---

## `puppeth` configuration:

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
