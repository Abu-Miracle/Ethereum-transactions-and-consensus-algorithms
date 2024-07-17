# Ethereum Transacations
Ethereum transactions are cryptographically signed data messages that comprises of a set of instructions. These instructions can interpret to sending Ether from one Ethereum account to another or interacting with a smart contract deployed on the blockchain. Transactions are a simple but essential concept that has allowed users worldwide to interact on a decentralized network. 

:::success
Ethereum transactions are network messages that include (among other things) a sender, recipient, value, and data payload.
:::


## Accounts in Ethereum Transations
There are basically two types of accounts that can be involved in an ethereum transaction
- **Externally Owned Accounts (EOAs)**
- **Smart contract accounts**

1. **Externally Owned Accounts (EOAs)** - These are accounts that are managed by human beings, such as a Metamask or Coinbase wallet. This account is identified by a public key (also known as an `account address`) and is controlled by a private key. The public key is derived from the private key using cryptographic algorithms such as  `Elliptic Curve Cryptography (ECC)` and the `Keccak-256 hash function.`
2. **Smart contract accounts** - A smart contract account, also known as `contract accounts` or a `smart contract`, is a type of Ethereum account that contains code. Contract accounts control themselves by the logic in the code stored within the account. Smart contracts can receive and send transactions, store data, and perform computations based on predefined logic.

:::info
An important point to note is that while smart contracts can receive and send transactions, they cannot initiate a transaction. Only Externally Owned Accounts (EOAs) can initiate transactions
:::

## Types of Transactions
1. **Regular Transactions (EOA to EOA)** - This is the most common type of transaction which involves a transaction from one Externally Owned Account (EOA) to another. An example is where one account sends Ethers or Tokens to another account, both being externally owned. `The data field in regular transactions are left empty`
2. **Contract creation transactions** - These transactions involves creation and deployment of new smart contracts that can execute code and store data on the blockchain. These transactions have no recipient(to) address. `The data field in contract creation transactions contains the bytecode that defines the contract's code and any initialization parameters for its constructor.`
3. **Execution of a contract** - This is a type of transaction that involves the interaction of an EOA with a deployed smart contract. In this case, the recipient(to) address is the smart contract's address. `The data field contains the encoded function selector and any parameters for the function being called.`

## Key Components of an Ethereum Transaction
A standard ethereum transaction has the following components
- **Sender Address (From)**: The address of the account initiating the transaction.
- **Recipient Address (To)**: The address of the account receiving the transaction. For contract creation transactions, this field is left blank.
- **Value**: The amount of Ether being transferred from the sender to the recipient.
- **Data**: Optional data field used for interacting with smart contracts. It can contain information about the function to be executed and the parameters to pass.
- **Gas Price**: The amount of Ether the sender is willing to pay per unit of gas to process the transaction. Gas Price = base fee + priority fee(tip).
- **Gas Limit**: The maximum amount of gas units the sender is willing to use for the transaction.
- **Gas Fee**: This represents the cost in Ether (ETH) for using computational resources (gas) to execute a transaction on the Ethereum blockchain.
> NOTE: Gas is a unit used in Ethereum to measure the computational effort required to execute operations or run transactions
- **Nonce**: In ethereum, a nonce (number used once) is a counter that ensures each transaction from an account is unique and processed in the correct order and without replay attacks. It is specific to the sender's address. The nonce is simply the number of transactions sent from that address (starting from 0 for the first transaction).
- **Signature**: The cryptographic signature that proves the transaction was authorized by the sender's private key. It is simply a cryptographic proof of authenticity and integrity.
- **Transaction Hash**: also known as a tx hash or transaction ID, is a unique identifier generated whenever a transaction is initiated on Ethereum

:::info
**Understanding Gas (Example)**
The unit of Gas price in Ethereum is typically denominated in Gwei (giga-wei), where 1 Gwei equals 
10^-9^ Ether (ETH).

If you set a gas limit of 100,000 units and a gas price of 10 Gwei (0.00000001 ETH) per unit of gas, and your transaction uses 50,000 units of gas:

Gas Used = 50,000 units of gas.
Transaction Fee = Gas Used * Gas Price = 50,000 * 0.00000001 ETH = 0.0005 ETH.

There are standard gas limits for different types of transactions
- For simple Ether transfer, it is usually around **21,000** units of gas
- For Token transfers, the gas limit can vary but often ranges from **50,000** to **100,000** units, depending on the token and its complexity.
- Gas limits for contract deployments can range from **200,000** to **3,000,000** units or more, depending on the size and complexity of the contract
:::

## Transaction States
- **Pending**: Transactions broadcasted to the network waiting to be mined. 
- **Queued**: A transaction that cannot be mined yet due to another pending transaction in the queue first or an out of sequence nonce.
- **Cancelled**: Can no longer be mined. Replaced by a transaction with a higher gas fee, same nonce value, and a null value for the data and/or value field.
- **Replaced**: Can no longer be mined. Used to replace current pending orders for faster execution or modification of values and data. This also consists of using the same nonce as the transaction you want to cancel and a higher gas fee.
- **Failed**: A transaction that resulted in an error due to a revert error, bad instructions, illogical code, or not enough gas to run the remainder of a function call.
- **Confirmed**: A transaction is considered confirmed when it has been included in a sufficient number of blocks (typically several blocks deep)

# Ethereum Consensus Algorithm
Ethereum currently uses a consensus algorithm called **Proof of Stake (PoS)**. Ethereum officially switched to a Proof of Stake (PoS) consensus mechanism in 2022 as a more secure and energy-efficient way to validate transactions and add new blocks to the blockchain. Previously, Ethereum used the Proof of Work (PoW) algorithm.

:::info
**What is a Consensus Algorithm(Mechanism)**
Generally speaking, consensus is a process used to reach an agreement among a group of people. In terms of blockchain, the consensus is the process by which a group of nodes on a network determines which blockchain transactions are valid. A consensus mechanism is the methodology to achieve this agreement. 

There are many types of consensus mechanisms. Each work in different ways but have one purpose: to ensure that transaction records on a blockchain are **true** and **honest**. Proof of Stake (PoS) is one of the most popular consensus mechanisms.
:::

### Proof of Stake (PoS) Consensus Algorithm

In PoS, validators (participants who vote on the authenticity of a new block of transactions, thus communally ensuring new blocks are valid before permanently adding them to the blockchain) are chosen based on the amount of cryptocurrency they hold and are willing to "stake" as collateral.
In the validation process, validators create and validate new blocks by staking their cryptocurrency as a guarantee of honesty. If they validate a block correctly, they earn transaction fees and rewards.
PoS is more energy-efficient compared to Proof of Work, which relies on computational power (mining) to validate transactions.

However, there is a special validator node called the `Block Proposer` who is responsible for building and suggesting the new block of transactions and broadcasting it to the other nodes to be verified.

:::info
**How does the Ethereum Network select Validators?**
The validator selection in Ethereum’s Proof of Stake (PoS) system is based on a validator’s stake in the network. The greater the stake, the more likely that node will be selected to add the new block to the chain. Each validator must stake the network’s native tokens (in this case, 32 ETH).
:::

With the recent Merge now complete after years of work, Ethereum’s transition to Proof of Stake is now active. But the process as a whole is not complete, so its full impact is still not seen. Ethereum 2.0 is still yet to arrive.

