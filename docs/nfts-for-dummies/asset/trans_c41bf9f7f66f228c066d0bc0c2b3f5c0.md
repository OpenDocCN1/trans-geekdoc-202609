
by default, memory variables as opposed to state variables:

function updateMsg(string memory newMsg) public {
    storedMsg = newMsg; 
    emit LogMsg(storedMsg); 
}

The first line of this updateMsg() function replaces the text being stored in the storedMsg state variable with the text that was passed to this function when it was called. The second line triggers the LogMsg event so that the latest contents of storedMsg can be written to the contract’s event log.

Finally, we complete the block of contract code with a closing curly bracket:

}

Compiling before takeoff

After you prepare your LittleBear.sol file and add the neces- sary code, you can compile that code by following these steps:

1\. Click the Compiler icon located in the navigation pane on the left, as shown in Figure 9-4. 

2\. In the Solidity Compiler pane that appears, click the Compile LittleBear.sol button, as shown in Figure 9-5. 

The compilation details for this contract appear underneath the Compile button, as shown in Figure 9-6.

Excellent! You’re now ready to deploy your smart contract.

After you deploy your smart contract, you can’t go back and change any of the code. If you want to make corrections, you have to deploy a new smart contract with the updated code.

CHAPTER 9 Deploying Your First Smart Contract  175

![](images/00084.jpg)

![](images/00100.jpg)

FIGURE 9-4:

LittleBear.

sol source

code, ready

for

compilation

on Remix.

FIGURE 9-5:

Solidity

Compiler on

Remix.

Deploying

Before you get to the real thing, practice deploying this contract on your local Ganache environment (which we discuss in Chapter 8).

1\. Click the Ethereum icon in the navigation pane on the left (the icon beneath the Compiler icon). 

This step opens the Deploy & Run Transactions pane, shown in Figure 9-7.

176  PART 3  Developing Your Knowledge: A Step-by-Step Guide to Programming Your Own NFT

![](images/00114.jpg)

![](images/00126.jpg)

FIGURE 9-6:

Accessing

compilation

details on

Remix.

FIGURE 9-7:

Deploy &

Run

Transactions

on Remix.

CHAPTER 9 Deploying Your First Smart Contract  181

![](images/00024.jpg)

FIGURE 9-12:

Deploying

the

LittleBear

contract to

the Ropsten

test

network.

3\. Click the Deploy button and confirm the transaction in the 

MetaMask notification that pops up, as shown in Figure 9-13. 

The transaction takes longer to mine this time because

blocks on the Ropsten test network aren’t automatically

mined, as they are on local blockchain instances in the

Ganache environment.

CHAPTER 9 Deploying Your First Smart Contract  181

![](images/00014.jpg)

FIGURE 9-13:

Confirming

contract

account

creation on

the Ropsten

test

network.

4\. Access the updateMsg function to update the text that’s 

being stored. 

We’re making two updates: first to say, “Hello Mama Kim!”

and next to say, “Hello Papa Kim!” Both changes appear in

the event logs shown a bit later, in Figure 9-17.

5\. To view this newly deployed LittleBear contract on the 

Ropsten blockchain, start by clicking the double-page icon 

(to the right of the LittleBear heading) to copy the 

contract account address, as shown in Figure 9-14. 

In our case, this address is 0x1F922670Ce8bC699e780b9b

12960Fb80F998573e

6\. [Point your browser to https://ropsten.etherscan.io](https://ropsten.etherscan.io/), paste the contract account address into the search bar, as 

shown in Figure 9-15, and then click the Search button. 

Figure 9-16 shows that our contract has three transactions

associated with it: the transaction that created the contract

followed by two transactions to call the updateMsg function.

Note that the newest transactions appear on top.

182  PART 3  Developing Your Knowledge: A Step-by-Step Guide to Programming Your Own NFT

![](images/00033.jpg)

![](images/00047.jpg)

![](images/00062.jpg)

7\. Click the Events tab to view the event logs created by 

our contract. Hint: For the sake of readability, use the 

drop-down tabs to convert the log outputs from Hex to

Text, as shown in Figure 9-17. 

FIGURE 9-14:

Copying a

contract

address

after

deployment

via Remix.

FIGURE 9-15:

The

Ropsten

Testnet

Explorer on

Etherscan.

FIGURE 9-16:

Our

LittleBear

smart

contract on

the Ropsten

test

network, as

shown on

Etherscan.

CHAPTER 9 Deploying Your First Smart Contract  183

![](images/00076.jpg)

FIGURE 9-17:

Our

LittleBear

event logs.

Ta-da! You have now successfully deployed your first smart con-

tract onto a public blockchain. At this point, you can repeat the

preceding steps to deploy this contract on the Ethereum Mainnet.

As for us, we’re opting to save our valuable (real!) ETH and to

avoid adding unnecessary baggage to the EVM because we don’t

plan to use our LittleBear contract other than to demonstrate

how to deploy a smart contract.

184  PART 3  Developing Your Knowledge: A Step-by-Step Guide to Programming Your Own NFT

![](images/00090.jpg)

IN THIS CHAPTER

» Getting to know Ethereum 

development standards

» Looking at token interfaces

» Exploring ERC-20 (fungible) tokens

» Diving into ERC-721 non-fungible 

tokens

Chapter 10

