# Workshop Epitech : Use, code & deploy decentralized apps
[Anthony Gourraud](https://anthonyg.eth.limo/) - [anthonyg.eth@ethereum.email](anthonyg.eth@ethereum.email)


Topics : 
- Blockchain
- Ethereum, Polygon
- Solidity, ERC20
- Hardhat, Open Zepellin, Thirdweb
- IPFS, Fleek


## 1- What is a blockchain ? What are the use cases ? 

A blockchain is a distributed database, with data publicly available. Multiple servers, called *nodes*, store and synchronize a copy of a global set of records. Write operations are also open to anyone, as long as modifications are accepted by the majority of nodes. The process of validation, called *consensus*, is what makes a blockchain a real innovation : participating in the well-being of the network is more profitable than acting maliciously.

Bitcoin is considered as the first network to use a blockchain, to provide [a peer-to-peer electronic cash system](https://bitcoin.org/bitcoin.pdf), a way to send and receive monetary value without relying on a trusted party. 

Whereas Bitcoin is mainly developed as an alternative to banks, Ethereum purposes to store and execute code within its blockchain. It allows the emerging of unstoppable applications, open source protocols relying on no one to work. Every interaction with "[dApps](https://ethereum.org/en/dapps/)" that modify the state should be submitted as a transaction to the network. It costs fees (paid in ETH, the Ethereum coin), sent to nodes as incentives to take it in account within the Ethereum blockchain. 

For various reasons, using Ethereum can be really expensive. Different solutions are on tracks to solve the problem. For now, you can use a "sidechain" like Polygon PoS to experiment decentralized applications at a lower cost. On Polygon, fees are paid in a coin called MATIC. 

Code deployed on Ethereum is compatible with Polygon PoS.

---

📝 Explain with your own words what are the main use cases of the following dApps, and why the use of a blockchain like Ethereum is relevant. 

* Aave :
* PoolTogether :  
* Sablier : 
* Uniswap : 

## 2- What are smart contracts ? How to interact with it ? 

We call programs executed on a blockchain "smart contracts". To interact with smart contracts, you need a digital wallet, represented by an *address*. 

To make smart contracts working smoothly together, standards are needed. [ERC20](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/) is the standard for tokens (to create your own crytoasset), [ERC721](https://ethereum.org/en/developers/docs/standards/tokens/erc-721/) the one for NFT (used to prove a digital property).
All contracts are deployed at a specific *address*. 

Testing environments, "testnets" allow any developer get a stagin environment at no cost. Polygon Mumbai is a testnet of Polygon. 

👉 Get your own wallet, and interact with smart contracts deployed on Mumbai.  

1. Install [Metamask](https://metamask.io/)
2. Add the Polygon Mumbai testnet network to Metamask with [Chainlist](https://chainlist.org/)   
3. Get test tokens : MATIC and DERC20 on Mumbai, thanks to the [official Polygon faucet](https://faucet.polygon.technology/). 
4. Copy the address of DERC20 contract. Use it to get your DERC20 balance with Metamask
5. Transfer some DERC20 tokens you receive to someone next to you, with Metamask
5. Exchange ("swap") 0.01 DERC20 to get MATIC with [Uniswap](https://app.uniswap.org/#/swap)
6. Transfer the same amount of DERC20 tokens you receive to someone next to you, with the [`transfer` write function](https://mumbai.polygonscan.com/address/0xfe4f5145f6e09952a5ba9e956ed0c25e3fa4c7f1#writeContract#F9)

📝 Write down what you get from the described actions above 

* Wallet address :  
* DERC20 contract address : 
* DERC20 transfer transaction with Metamask:
* Swap transaction : 

📝 Go deeper with the ERC20 standard

* Check the input data from the transaction details of the transfer you executed with Metamask ("Click to se more", "Decode Input Data"). Explain the value of the argument `amount`. 
* Why did you have to "approve" DERC20 spending before performing a swap ?
* What are "events" ? Why is it useful ? Give an event emitted when you transfered DERC20 tokens.  

### 3- How to code a smart contract ?

[Solidity](https://soliditylang.org/) is the main language to develop smart contracts. [Hardhat](https://hardhat.org/) is a famous framework that helps developers with it. 
To build faster and for secure smart contract development, you can use librairies like [Open Zeppelin contracts](https://github.com/OpenZeppelin/openzeppelin-contracts). 

👉 Build your first contract : an token called "EPICOIN", following ERC20 standard. Add something custom to the contract : a public *address* variable called `lastUser` and a function called `updateLastUser`. This function should update `lastUser` with the wallet's address executing the function and an event `AddressUpdated(address wallet)` should be emitted. 

1. Install NodeJS, VSCode and the Solidity extension from Nomic Foundation.
2. [Set up a new Hardhat project](https://hardhat.org/tutorial/creating-a-new-hardhat-project)  
3. Create your contract EPICOIN.sol contract and code what is necessary to get a ERC20 token called "EPICOIN" (tip : import `ERC20.sol` from Open Zeppelin). 
4. Write a `mint` function to create and send tokens to an address.
5. Write the `updateLastUser` function. 
4. Write down the tests. Ensure `lastUser` is correctly updated when  `updateLastUser` is executed (test with two different wallets), and `AddressUpdated` emitted. 
5. Once tested, deploy the contract on Mumbai with the wallet you created.
6. Use your deployed contract : call the `mint` and `updateLastUser` functions, transfer some tokens. 

📝 Write down what you get from the described actions above

* Deployed contract address : 
* Contract creation transaction : 
* Transfer transaction : 
* `lastUser` variable modification transaction (with `AddressUpdated` event in "Logs") : 

### 4- How to develop a custom UI to interact with smart contracts ?

React + Thirdweb
https://portal.thirdweb.com/react/getting-started
Deploy with Fleek / IPFs : https://blog.fleek.co/posts/fleek-create-react-app
