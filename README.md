# Workshop Epitech : Use, code & deploy decentralized apps
[Anthony Gourraud](https://anthonyg.eth.limo/) - [anthonyg.eth@ethereum.email](mailto:anthonyg.eth@ethereum.email)


Topics : 
- Blockchain
- Ethereum, Polygon
- Solidity, ERC20
- Hardhat, Open Zepellin, Thirdweb
- IPFS, Fleek


## 1- What is a blockchain and what are the use cases 

A blockchain is a distributed database, with data publicly available. Multiple servers, called *nodes*, store and synchronize a copy of a global set of records. Write operations are also open to anyone, as long as modifications are accepted by the majority of nodes. The process of validation, called *consensus*, is what makes a blockchain a real innovation, by its principles that participating in the well-being of the network is more profitable than acting maliciously.

Bitcoin is considered as the first project to use a blockchain, to provide [a peer-to-peer electronic cash system](https://bitcoin.org/bitcoin.pdf), a way to send and receive monetary value without relying on a trusted party. 

Whereas Bitcoin is mainly developed as an alternative to banks, Ethereum purposes to store and execute code within its blockchain. It allows the emerging of unstoppable applications, open source protocols relying on no central entities to work. Every interaction with "[dApps](https://ethereum.org/en/dapps/)" that modify the state should be submitted as a transaction to the network. It costs fees (paid in ETH, the Ethereum coin), sent to nodes as validation incentives. 

For various reasons, using Ethereum can be really expensive. Different solutions are on tracks to solve the problem. For now, you can use a "sidechain" like Polygon PoS to experiment decentralized applications at a lower cost. On Polygon, fees are paid in a coin called MATIC. 

Code deployed on Ethereum is compatible with Polygon PoS.


📝 What are the main use cases of the following dApps, and why the use of a blockchain like Ethereum is relevant ? 

* Aave :
* PoolTogether :  
* Sablier : 
* Uniswap : 

## 2- What are smart contracts and how to interact with it 

We call programs executed on a blockchain "smart contracts". To interact with smart contracts, you need a digital wallet, represented by an *address*. 

For smart contracts to work well together, standards are needed. [ERC20](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/) is the standard for tokens (to create your own cryto asset), [ERC721](https://ethereum.org/en/developers/docs/standards/tokens/erc-721/) the one for NFT (used to prove a digital property).
All contracts are deployed at a specific *address*. 

Testing environments, "testnets", allow any developer to get a staging environment at no cost. Polygon Mumbai is a testnet of Polygon. 

👉 Get your own wallet, and interact with smart contracts deployed on Mumbai.  

1. Install [Metamask](https://metamask.io/)
2. Add the Polygon Mumbai testnet network to Metamask with [Chainlist](https://chainlist.org/)   
3. Get test tokens : MATIC and DERC20 (*Test ERC20 PoS*) on Mumbai, thanks to the [official Polygon faucet](https://faucet.polygon.technology/). 
4. Copy the address of the DERC20 contract. Use it to get your DERC20 balance with Metamask
5. Transfer 0.01 DERC20 to someone next to you, with Metamask
6. Exchange ("swap") 0.02 DERC20 to get MATIC with [Uniswap](https://app.uniswap.org/#/swap)
7. Transfer 0.03 DERC20 to someone next to you, with the [`transfer` write function via the block explorer Polygonscan](https://mumbai.polygonscan.com/address/0xfe4f5145f6e09952a5ba9e956ed0c25e3fa4c7f1#writeContract#F9)

📝 Write down what you get from the described actions above 

* Wallet address :  
* DERC20 contract address : 
* Hash of the DERC20 transfer transaction with Metamask:
* Hash of the swap transaction : 
* Hash of the DERC20 transfer transaction with Polygonscan :

📝 Go deeper with the ERC20 standard

* Check the input data from the transaction details of the transfer you executed with Metamask ("Click to see more", "Decode Input Data"). Why is the argument `amount` different from what you set on Metamask ? 
* Why did you have to "approve" DERC20 spending before performing a swap ?
* What are "events" ? Why is it useful ? Which event(s) are emitted when you transfer DERC20 tokens ?  

## 3- How to code a smart contract, the backend of a decentralized app

[Solidity](https://soliditylang.org/) is the main language to conceive smart contracts. ["Solidity By Example"](https://solidity-by-example.org/) is a great website to learn Solidity easily.

[Hardhat](https://hardhat.org/) is a famous framework that helps developers to code, test and deploy Solidity code. To build faster and for secure smart contract development, you can use libraries like [Open Zeppelin contracts](https://github.com/OpenZeppelin/openzeppelin-contracts). 

👉 Build your first contract : a token called "EPICOIN", following ERC20 standard. This contract should have a custom implementation, with a public *address* variable called `lastUser` and a `updateLastUser()` function too. When a user calls the `updateLastUser` function, `lastUser` should be updated with its wallet address, and an event `AddressUpdated(address wallet)` should be emitted. The `updateLastUser` function should not have any argument.

1. Install NodeJS, VSCode and the Solidity extension from Nomic Foundation.
2. [Set up a new Hardhat project](https://hardhat.org/tutorial/creating-a-new-hardhat-project)  
3. Create your contract EPICOIN.sol contract and code what is necessary to get a ERC20 token named "EPICOIN" (tip : import `ERC20.sol` from Open Zeppelin). 
4. Write a `mint(address wallet, uint256 amount)` function to allow any wallet to create and send EPICOINS tokens to an address.
5. Write the `updateLastUser()` function. 
4. Write down the tests. You can use [Foundry (Solidity)](https://book.getfoundry.sh/), or [Mocha (Javascript)](https://hardhat.org/tutorial/testing-contracts), as you want. Ensure `lastUser` is correctly updated when `updateLastUser` is executed (test with two different wallets), and an event `AddressUpdated` is emitted. Ensure EPICOIN balance changed for a wallet when the `mint` function is executed.
5. Once tested, deploy the contract on Mumbai with the wallet you created with Metamask. You may have to [export your private key](https://support.metamask.io/hc/en-us/articles/360015289632-How-to-export-an-account-s-private-key).
6. Use your deployed contract with Polygonscan : call the `mint` and `updateLastUser` functions, and transfer some EPICOIN tokens to someone next to you. 
Write functions are unavailable ? It's because you need to [verify your contract](https://hardhat.org/hardhat-runner/docs/guides/verifying). 

📝 Write down what you get from the described actions above

* Deployed EPICOIN contract address : 
* Hash of the contract creation transaction : 
* Hashes of mint and transfer transactions with the EPICOIN contract : 
* Hash of a transaction where `lastUser` variable is modified (we should see `AddressUpdated` event in "Logs") : 


## 4- How to develop and deploy a custom UI, the frontend of your decentralized application

Once you have developed your logic with smart contracts, you need an interface to facilitate people to use the implemented features. 

React is a good frontend framework, with several libraries to integrate wallet connection and blockchain transactions easier. [Thirdweb](https://portal.thirdweb.com/react) provides several React hooks, UI components and templates to get started.

But if you deploy a React app on a server (with Vercel for example), the application is not really "decentralized", because you rely on the hosting provider. A solution is a to use [Fleek](https://docs.fleek.co/tutorials/hosting/), and deploy on [IPFS](https://ipfs.tech/), a P2P data storing protocol.  

👉 Build a web app that allows any user to mint EPICOIN tokens. The interface should offer to modify the `lastUser` variable of the contract you deployed too. You may need the [Web3 Button](https://portal.thirdweb.com/react/react.web3button) from Thirdweb. Deploy on IPFS. 

📝 Write down what you get from the described actions above

* IPFS link to the web app : 
