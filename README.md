# ZBank & Blockchain Technology

## Blockchain Technology Basic Info: 

According to [Tech4Fresher](https://tech4fresher.com/blockchain-technology-explained-with-infographics/)

"A blockchain is a growing list of records called blocks which are interconnected by utilizing cryptography. Each block contains a cryptographic hash of the previous block, a time stamp, and exchange information"

### Blockchain Technology can:
1. Safely store information over a shared system that is publicly vieweable but can't be easly altered.
2. Allow the safe exchange of contracts, property, cash, etc without the need of a centralized systems like banks or governement.
3. Allows for 100% transperancy since all clients are able to see another clients operation. 

---
## Blockchain Systems:

  * Proof of Work:
    * Proof of Work (PoW) is the conventional method through which new blocks are created after transactions are completed.
    * Transactions on the blockchain need to be verified by miners. How this works is that a miner verifies a block of transaction through solving a mathematical puzzle based on prime numbers.
    * Blockchain consensus confirms the completion of the transaction/work and a new block is created. Each block gives a certain number of rewards to the miner that completes the transaction.
  * Proof of Authority
    * Proof of Authority (POA) is a consensus method in which a number of blockchain actors within the ecosystem are given the power to validate transactions and ultimately decide whether new blocks will be added to the blockchain or not.
    * In the case of Proof of Authority, it is not suitable for public blockchains as there is essentially a monopoly with a few actors who may confirm transactions.
  * Proof of Stake
    * Proof of Stake means that an individual who wishes to mine or validate a transaction on the blockchain can do so depending on how many blocks they already hold. As the name partially implies, the greater the number of blocks or ‘stake’ that the miner has in the blockchain, the larger the mining power they are given on the blockchain.

---

# Proof of Authority Development Chain

Using the Proof of Authority system too set up a testnet blockchain for ZBank.

I will:

* Set up a custom testnet blockchain.

* Send a test transaction.

* Create a repository.

* Write instructions on how to use the chain for the rest of the team.

* For easy setup I will also provide pre-configured accounts and nodes.

---

## Initial downloads:

### Install the geth node software

Download and install `geth` for your operating system here: <https://geth.ethereum.org/downloads/>

### Install the MyCrypto GUI wallet

Download and install the desktop version of the MyCrypto wallet here: <https://download.mycrypto.com/>

This wallet allows communicating with custom networks, which we will configure later.
  


## intial setup
### Step 1:
* Create a Proof of Authority Directory in your Fintech Folder

### Step 2:
* Download the pre-configured nodes 

We will be using the Clique (Proof of Authority) consesus Algorithm.

 * Network configuration: '5 second' block times.
 * Network chain ID: 333

The sealer node addresses are:

`0xd84d79a0069fb5d3cf8eca3c689f231d6b603c8f`
`0x7a4f862ab163fc62dce2cfbb734ddac153c5e8cc`

The account password for both nodes is `testnetpassword`

---

# `puppeth` configuration:

Open GitBash

1st step:
go to Proof-of-Authority directory

![Directory](https://user-images.githubusercontent.com/70820754/107984190-a46e7280-6f84-11eb-957b-5a3c2bf24e44.png)


2nd Step
Open Ethereum private network manger with:
./puppeth

![puppeth](https://user-images.githubusercontent.com/70820754/107984342-f8795700-6f84-11eb-9c2f-39b0aa0378c2.png)

3rd step: Name the network
homework


4th step (configure new genesis)
Hit option 2

5th step (create new genesis from scratch)
Hit option 1

6th step select consensus engine Clique (proof-of-authority)
Hit option 2

7th step: set time for blocks
5

8th step seal accounts provided:
`0xd84d79a0069fb5d3cf8eca3c689f231d6b603c8f`
`0x7a4f862ab163fc62dce2cfbb734ddac153c5e8cc`

8th step fund the same accounts provided:
`0xd84d79a0069fb5d3cf8eca3c689f231d6b603c8f`
`0x7a4f862ab163fc62dce2cfbb734ddac153c5e8cc`

10th step(manage existing genesis)
Hit 2

11th step (expoert genesis configuration)
Hit 2

13th step
Press enter

Press Control C to exit to exit puppeth and return to blockchain folder

# Setting up and running a private network using `geth`
1st step create/name 1st node

./geth account new --datadir [WHATEVER_YOU_WANT_TO_CALL_NODE]

2nd step Create password for 1st node:
testnetpassword

3rd step create/name 2nd node
./geth account new --datadir [WHATEVER_YOU_WANT_TO_CALL_NODE]

4th step Create password for 2nd node
testnetpassword

5th step Initate file node 1
./geth init [WHAT_YOUR_ACTUAL_JSON_FILE_IS_CALLED].json --datadir [WHATEVER-YOUR-NODE-IS-CALLED]

6th step Initate file node 2
./geth init [WHAT_YOUR_ACTUAL_JSON_FILE_IS_CALLED].json --datadir [WHATEVER-YOUR-NODE-IS-CALLED]

final step Run the first node and enable the mining/sealing
./geth --allow-insecure-unlock --datadir node1 --unlock d84d79a0069fb5d3cf8eca3c689f231d6b603c8f --mine --http

## Open a second gitbash window to run second node:
1st step:
go to fintech/proof-of authority directory

2nd step: Use the first node's enode address as the bootnode for the second node and run on a separate port

`./geth --datadir node2 --unlock "7a4f862ab163fc62dce2cfbb734ddac153c5e8cc" --mine --port 30304 --bootnodes enode://b044f481e52f03950ed88ad18f550ace268ad4e4e1647f80c5808d6ea2c4e7f550d8ed25a14608afa6e5828f1b69fdfcf5d7775394f7c38d8592f600e4a37e90@127.0.0.1:30303`


![puppeth](Screenshots/puppeth.png)


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
