# Launching My Cryptocurrency on Solana Blockchain : A Decentralized Finance (DeFi) Project

## Prerequisites

1. An **IDE** of your choice, which is **Visual Studio Code** in my case. You can download it from this [link](https://code.visualstudio.com/download).
    <br/>
   
2. **Solana** on your computer. You can get the clear steps to download it from this [link](https://docs.solana.com/cli/install-solana-cli-tools#use-solanas-install-tool).
   
## Demystifying Jargons !!!

> **Token** or a **Coin**???

***Tokens***: Tokens are an abstraction that represents ownership. Ownership implies certain privileges such as the right to use or sell an item like a vehicle or a house. A token is any digital asset created on the blockchain. It is usually issued or minted on another blockchain, often existing alongside several other tokens that belong to different projects.

***Coin***: A coin is a cryptocurrency that runs on its blockchain. It is also referred to as the **“native token”** of the blockchain and often serves as a way for projects to pay transaction fees while building out their applications on the same blockchain.

* **Ether (ETH)** is a **coin** and the **‘native token’** of the **Ethereum** blockchain.
<br/>

* For example, the **Ethereum** blockchain allows developers to create their own **tokens** on top of the network using a standard called [**ERC-20**](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/). The **ERC-20** standard is used when creating a **fungible, or mutually interchangeable** token. Any **token** created on **Ethereum** might be referred to as a **‘token’** and not a **‘coin’**. **Ether (ETH)** is the **Ethereum** network’s native **cryptocurrency**.
<br/>

* Examples of **ERC-20** **tokens** on **Ethereum** include **Basic Attention Token (BAT)**, **Chainlink (LINK)**, **Tether (USDT)**, **Wrapped Bitcoin (WBTC)**, **Dai (DAI)**, **Compound (COMP)**, and many others.
<br/>

* **Tokens** can eventually become **coins** when the project develops its own blockchain and migrate their tokens to the new blockchain as a **coin**. Successful migration cases include **Binance Coin (BNB)**, **Tron (TRX)**, **Zilliqa (ZIL)** which previously existed as tokens on the **Ethereum** blockchain.

   
## Installing Solana Programming Library (SPL)

1. Checking whether **solana** is installed on my system:
   <br/>

   $ ***solana --version***
   <br/>

2. Installing **SPL** command line interface (**cli**), which is a **RUST** package, for interacting with **SPL token program** that I will be using for creating my token :
   <br/>

   $ ***cargo install spl-token-cli***
   <br/>

   ![alt text](Screenshot119.png)
   <br/>

   ![alt text](Screenshot121.png)

## Creating my wallet and checking on Solana Explorer

To **transact** money on the **blockchain**, we need to use a **crypto-wallet** which allows us to store, send and receive **crypto-assets** like **cryptocurrency** or **tokens**.
   <br/>

1. Setting up a new **wallet**:
   <br/>

   $ ***solana-keygen new***

   $ ***solana-keygen new --force***
   <br/>

1. Checking my **publickey**:
   <br/>

   A blockchain has a unique identifier called **publickey** or **pubkey**, which is a cryptographic string of **alphanumeric** characters.
   <br/>

   $ ***solana-keygen pubkey***
   <br/>

2. Checking my **balance**:  
   <br/>

   $ ***solana balance --url devnet***
   <br/>

3. Checking my balance on explorer.solana.com:
   <br/>

   Choose ***devnet*** and pasted the ***publickey*** onto the searchbox.
   <br/>

4. **Airdropping** solana currency in my **wallet**
   <br/>

   $ ***solana airdrop 2 <pubkey> --url devnet***
   <br/>

   ![alt text](Screenshot125.png)
   <br/>

   ![alt text](Screenshot123.png)
   <br/>

   ![alt text](Screenshot124.png)
   <br/>

## Creating a Token with SPL library   

> Difference between **Creating** and **Minting** a **Token** :

* ***Creating a Token*** is like creating the structure of the token.
<br/>

* ***Minting a Token*** is like actually making copies of that specific token.

1. To **create a token** using SPL:
<br/>

   $ ***spl-token create-token --url devnet***

<br/>
   
When a token goes on the soalna blockchain, they are given a **unique address**. In my case, the **unique Token address** is: **3FWpeHmnKE2Ztc8L9oVtnJSGmtjUAsLdLLb7qJKzpEsf**. This actually implies that I have created my own **cryptocurrency** on **Solana Blockchain!**

## Minting a Token

**Accounts** are like files that allow us to store data on blockchain. In a solana wallet, to collect a particular type of **token** we need to have an **account** in our **wallet**, that is specific for that **token** and that can hold that specific **token**. A **wallet** can have multiple **accounts** and each **account** is used to transact one type of **token**.
<br/>

1. To **create an account** that can hold the **tokens** I have created:
<br/>

   $ ***spl-token create-account 3FWpeHmnKE2Ztc8L9oVtnJSGmtjUAsLdLLb7qJKzpEsf --url devnet***
<br/>

   The id, **FcXu9ypeBZxQgQMMcCk9XiP1u4PZZDPUYkcrwYBExXv8**, represents the **address** of an **empty token account** in my **wallet**.
<br/>

2. To check the **balance** of my **tokens**, that is the **number of tokens** I have in my newly created **account**:
   <br/>

   $ ***spl-token balance 3FWpeHmnKE2Ztc8L9oVtnJSGmtjUAsLdLLb7qJKzpEsf  --url devnet***
   <br/>

   The process of **making tokens** is called **Minting**.
   <br/>

3. To **mint** 10000 **tokens** for my **account**:
   <br/>

   $ ***spl-token mint 3FWpeHmnKE2Ztc8L9oVtnJSGmtjUAsLdLLb7qJKzpEsf 10000 --url devnet***

   <br/>

   ![](Screenshot126.png)

## Limiting the total supply and burning my token

1. To view the **circulating supply** of my **tokens**:  
   <br/>

   $ ***spl-token supply 3FWpeHmnKE2Ztc8L9oVtnJSGmtjUAsLdLLb7qJKzpEsf  --url devnet***
   <br/>

2. To **disable** my **minting authoirty** and never enable it back:
   <br/>

   $ ***spl-token authorize 3FWpeHmnKE2Ztc8L9oVtnJSGmtjUAsLdLLb7qJKzpEsf mint --disable  --url devnet***
   <br/>

3. Now, if I try to **mint further tokens**, I should get the **error**:
   <br/>

   **RPC response error -32002: Transaction simulation failed: Error processing Instruction 0: custom program error: 0x5 [5 log messages]**

<br/>

4. To **burn** my tokens, which means to remove tokens that I own out of circulations so that they can never be used again :
   <br/>

   ***$ spl-token burn FcXu9ypeBZxQgQMMcCk9XiP1u4PZZDPUYkcrwYBExXv8 1000 --url devnet***

   ![](Screenshot127.png)

## Sending my tokens to my friend holding a wallet on SOLFARE

**SOLFARE** allows us to transact on the Soalana Blockchain. **SOL** is the native token of the Solana Blockchain. Similar to how **ETH** is to **Ethereum blockchain**. SOL is used to interact and transact on the Solana blockchain. However, we can't send SPL tokens to SOL address like we do with ERC20 tokens because each **SPL token** on Solana blockchain will have their own address. We have to add each **SPL token** separately before we can receive them in any wallet.

1. For the sake of demonstration, let me act as my friend. Let me add an account for my token in my friend's SOLFARE wallet by clicking **+ADD NEW ASSET**. The **publickey** of my friend's wallet is **65Z5XFsqo7iMEFBYJcKR1SZMdWAoiDRrN9M7RB5Hvvfe**
   <br/>

2. Change the network from **mainnet** to **devnet**.
   <br/>

3. To send my 500 tokens to my friend's wallet:
   <br/>

   $  ***spl-token transfer 3FWpeHmnKE2Ztc8L9oVtnJSGmtjUAsLdLLb7qJKzpEsf 500 65Z5XFsqo7iMEFBYJcKR1SZMdWAoiDRrN9M7RB5Hvvfe --url devnet --allow-unfunded-recipient --fund-recipient***
   <br/>

   ![](Screenshot134.png)
   <br/>

   ![](Screenshot128.png)
   <br/>

   ![](Screenshot129.png)
   <br/>

   ![](Screenshot131.png)
   <br/>
   
   ![](Screenshot132.png)
   
<br/>
    
## References
    
1. Bitcoin and cryptocurrency technologies : A Comprehensive Introduction
 ARVIND NARAYANAN, JOSEPH BONNEAU, EDWARD FELTEN, ANDREW MILLER, AND STEVEN GOLDFEDER
 PRINCETON UNIVERSITY PRESS 
    <br/>
    
2. Hands-On Smart Contract Development with Solidity and Ethereum by Kevin Solorio, Randall Kanna, and
David H. Hoover (O’Reilly). Copyright 2020 Kevin Solorio, Randall Kanna, and
David H. Hoover, 978-1-492-04526-7.
    <br/>
    
3. [LearnWithArjun/solana-env-setup](https://github.com/LearnWithArjun/solana-env-setup)
    <br/>
    
4. [Solana Blockchain Developer Bootcamp with Rust + JavaScript](https://www.udemy.com/course/solana-developer/)
