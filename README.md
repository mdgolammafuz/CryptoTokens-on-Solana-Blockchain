# Launching My Own Cryptocurrency on Solana Blockchain : A Decentralized Finance (DeFi) Project

## Installing Solana Programming Library (SPL)

1. Checking whether **solana** is installed on my system :
   <br/>
   
   $ ***solana --version***
   <br/>

2. Installing **SPL** command line interface (**cli**), which is a **RUST** package, for interacting with **SPL token program** that I will be using for creating my token :
   <br/>

   $ ***cargo install spl-token-cli***
   <br/>

   ![alt text](Screenshot119.png#gh-dark-mode-only)
   <br/>
   
   ![alt text](Screenshot121.png)

## Creating my own wallet and checking on Solana Explorer

To **transact** money on the **blockchain**, we need to use a **crypto-wallet** which allows us to store, send and receive **crypto-assets** like **cryptocurrency** or **tokens**.
<br/>

1. Setting up a new **wallet**:
   <br/>

   $ ***solana-keygen new***

   $ ***solana-keygen new --force***
<br/>
1. Checking my **publickey** :<br/>
A blockchain has a unique identifier called **publickey** or **pubkey**, which is a cryptographic string of **alphanumeric** characters.
<br/>

   $ ***solana-keygen pubkey***
<br/>

1. Checking my **balance**:  
<br/>

   $ ***solana balance --url devnet***
<br/>

1. Checking my balance on explorer.solana.com:
<br/>

   I chose ***devnet*** and pasted the ***publickey*** on the searchbox.
<br/>

5. **Airdropping solana currency** in my **wallet**
<br/>

   $ ***solana airdrop 2 <pubkey> --url devnet***
<br/>

![alt text](assets/Screenshot125.png "image title")
<br/>

![alt text](assets/Screenshot124.png)
<br/>

## Creating a Token with SPL library
<br/>

> Difference between **Creating** and **Minting** a **Token** :
* ***Creating a Token*** is like creating the structure of the token.
* ***Minting a Token*** is like actually making copies of that specific token.
<br/>
1. To **create a token** using SPL:
<br/>

   $ ***spl-token create-token --url devnet***

<br/>

When a token goes on the soalna blockchain they are given a **unique address**. In my case, the **unique Token address** is: **3FWpeHmnKE2Ztc8L9oVtnJSGmtjUAsLdLLb7qJKzpEsf**. This actually implies that I have created my own **cryptocurrency** on **Solana Blockchain!**

## Minting a Token

**Accounts** are like files that allow us to store data on blockchain. In a solana wallet, to collect a particular type of **token** we need to have an **account** in our **wallet**, that is specific for that **token** and that can hold that specific **token**. A **wallet** can have multiple **accounts** and each **account** is used to transact one type of **token**.
<br/>

1. To **create an account** that can hold the **tokens** I have created:
 <br/>

   $ ***spl-token create-account 3FWpeHmnKE2Ztc8L9oVtnJSGmtjUAsLdLLb7qJKzpEsf --url devnet***
<br/>

   The id, **FcXu9ypeBZxQgQMMcCk9XiP1u4PZZDPUYkcrwYBExXv8**
, represents the **address** of an **empty token account** in my **wallet**.
<br/>
2. To check the **balance** of my **tokens**, that is the **number of tokens** I have in my newly created **account** :
   <br/>

   $ ***spl-token balance 3FWpeHmnKE2Ztc8L9oVtnJSGmtjUAsLdLLb7qJKzpEsf  --url devnet***
<br/>

   The process of **making tokens** is called **Minting**.
<br/>

3. To **mint** 10000 **tokens** for my **account**:
<br/>

   $ ***spl-token mint 3FWpeHmnKE2Ztc8L9oVtnJSGmtjUAsLdLLb7qJKzpEsf 10000 --url devnet***

## Limiting the total supply and burning my token

1. To view the **circulating supply** of my **tokens**:  
<br/>

   $ ***spl-token supply 3FWpeHmnKE2Ztc8L9oVtnJSGmtjUAsLdLLb7qJKzpEsf  --url devnet***
<br/>

2. To **disable** my **minting authoirty** and never enable it back:
<br/>

   $ ***spl-token authorize 3FWpeHmnKE2Ztc8L9oVtnJSGmtjUAsLdLLb7qJKzpEsf mint --disable  --url devnet***
<br/>

4. Now, if I try to **mint further tokens**, I should get an **error** like the following:
   <br/>

   **RPC response error -32002: Transaction simulation failed: Error processing Instruction 0: custom program error: 0x5 [5 log messages]**

<br/>

5. To **burn** my tokens, which means to remove tokens that I own out of circulations so that they can never be used again :
   <br/>

   ***$ spl-token burn FcXu9ypeBZxQgQMMcCk9XiP1u4PZZDPUYkcrwYBExXv8 1000 --url devnet***

## Sending my tokens to my friend holding a wallet on SOLFARE

**SOLFARE** allows us to transact on the Soalana Blockchain. **SOL** is the native token of the Solana Blockchain. Similar to how **ETH** is to **Ethereum blockchain**. SOL is used to interact and transact on the Solana blockchain. However, we can't send SPL tokens to SOL address like we do with ERC20 tokens because each **SPL token** on Solana blockchain will have their own address. We have to add each **SPL token** separately before we can receive them in any wallet.

1. For the sake of demonstration, let me act as my friend. Let me add an account for my token in my friend's SOLFARE wallet by clicking **+ADD NEW ASSET**. The **publickey** of my friend's wallet is **65Z5XFsqo7iMEFBYJcKR1SZMdWAoiDRrN9M7RB5Hvvfe**
<br/>

1. Change the network from **mainnet** to **devnet**.
<br/>

3. To send my 500 tokens to my friend's wallet:
<br/>
   
   $  ***spl-token transfer 3FWpeHmnKE2Ztc8L9oVtnJSGmtjUAsLdLLb7qJKzpEsf 500 65Z5XFsqo7iMEFBYJcKR1SZMdWAoiDRrN9M7RB5Hvvfe --url devnet --allow-unfunded-recipient --fund-recipient***
