![cover](images/cover.jpeg)

Dr. Hedaya Mahmood Alasooly  

# Quick Guide for Smart Contracts Creation and Deployment on Ethereum Blockchain

## 

  
  
  
  
BookRix GmbH & Co. KG  
80331 Munich  

### Quick Guide for Smart Contracts Creation and Deployment on Ethereum Blockchain

**Quick Guide for Smart Contracts Creation and Deployment on Ethereum Blockchain**

 

 

 

 

 

 

By

Dr. Hedaya Mahmood Alasooly

Hedaya\_alasooly@yahoo.com

 

 

 

 

### 1\. Overview:

**1\. Overview:**

 

This work explains briefly the creation and deployment Of Smart Contract on Ethereum Blockchain. The work consists from the following sections

*   Blockchain
*   Solidity variables and types
*   How to Setup or Install Ethereum on Windows
*   How to compile and deploy smart contract on JavaScriptVM
*   How to install Ganache Blockchain on Windows and deploy smart contract using it.
*   How to compile and deploy Smart Contract on Test Networks,
*   Quick example of deploying ERC20 token smart contract.
*   Getting started tutorial on Solidity
*   Creating ERC-20 smart contract and crowd sale (ICO) smart contract without coding
*   ERC-20 smart contract and crowd sale (ICO) smart contract:
*   Creating Ethereum ERC-20 Tokens and Crowd Sales (ICO) without coding with Token Wizard:
*   Example of creating and deploying an ERC20 token on the test and main network!!!

 

 

### 2\. Blockchain:

**2\. Blockchain:**

 

A blockchain is a digital record of transactions. The name comes from its structure, in which individual records, called blocks, are linked together in single list, called a chain. Blockchains are used for recording transactions made with cryptocurrencies, such as Bitcoin, and have many other applications.

Each transaction added to a blockchain is validated by multiple computers on the Internet. These systems, which are configured to monitor specific types of blockchain transactions, form a peer-to-peer network. They work together to ensure each transaction is valid before it is added to the blockchain. This decentralized network of computers ensures a single system cannot add invalid blocks to the chain.

When a new block is added to a blockchain, it is linked to the previous block using a cryptographic hash generated from the contents of the previous block. This ensures the chain is never broken and that each block is permanently recorded. It is also intentionally difficult to alter past transactions in blockchain since all the subsequent blocks must be altered first.

*   **Blockchain Uses:** While blockchain is widely known for its use in cryptocurrencies such as Bitcoin, Litecoin, and Ether, the technology has several other uses. For example, it enables "smart contracts," which execute when certain conditions are met. This provides an automated escrow system for transactions between two parties. Blockchain can potentially be used to allow individuals to pay each other without a central clearing point, which is required for ACH and wire transfers. It has potential to greatly increase the efficiency of stock trading by allowing transactions to settle almost instantly instead of requiring three or more days for each transaction to clear. Blockchain technology can also be used for non-financial purposes. For example, the InterPlanetary File System (IFPS) uses blockchain to decentralize file storage by linking files together over the Internet. Some digital signature platforms now use blockchain to record signatures and verify documents have been digitally signed. Blockchain can even be used to protect intellectual property by linking the distribution of content to the original source.
*   Blockchain is decentralized database that consists from records and data. The entire data is spread out in bounch of distributed computers to end to be pear to pear p2p network. The records in these databases are stored in form of blocks which linked together in secured way.
*   The bitcoin blockchain stores data specific to keep track of crypto currencies balances between different parties.

*   Ethereum block chain can store much more deep data than bitcoin block chain. Ethereum block chain allows building decentralized apps. These decentralized apps defined by smart contracts. So smart contract allows individuals to exchange information in trusted confident free manner without relying on third party as bank or lawyer or other way. So these Ethereum smart contracts stored in special transections in Ethereum blockchain which can be used then to build applications. So you can think on smart contracts as decentralized api's. As smart contracts stored in Ethereum blockchains, they need to be validated or mined as any other transactions. So there is small costs associated with deploying smart contracts.
*   How to code smart contract. We do that with solidity. Solidity is a code used. Solidity is a language used to code smart contract. And syntax is similar to java script and is designed with Ethereum virtual machine in mind. So we will use solidity to create smart contract in web based ide called remex

 

### 3\. Solidity variables and types

**3\. Solidity variables and types**

 

*   You can write the solidity and test code in https://remix.ethereum.org/.
*   Here screen of https://remix.ethereum.org

 

![](images/159551591299085953_1.jpg)

 

*   Create new contract. I called it Coursetro.
*   Start off by writing (or pasting) the following code:

pragma solidity ^0.4.18;

 

contract Coursetro {

}

The very first line defines the version of solidity you're going to use.

Next, you define the contract and its name and open it up like a JavaScript class.

*   On the right side of the browser under the Run tab, you will see a Deploy button. Click on this. You will notice that underneath the Deploy button shows a new section with the name of the contract and "at 0x..." (memory):

![](images/159551591230265132_2.jpg)

*   This means that the smart contract (yes, it's not very smart at this point) lives at an address. To see this full address along with other information, in the debugger if you click on the **Details** button, it will provide you with more information:
*   Notice there's a **contractAddress**, this is where the smart contract actually lives. No, it's not live on the Ethereum Blockchain because right now, we're simply working within the Javascript EVM.
*   Also notice **gas**. Every time a contract is deployed and modified, nodes on the Ethereum network must verify the contract. It's referred to as being redundantly parallel, as a way to reach consensus.Gas is the name for the execution fee that senders of transactions (in our case, senders of a smart contract transaction) will pay for verification.
*   **Elaborating on this further**, from etherdocs.org:
*   *"Gas is the name for the execution fee that senders of transactions need to pay for every operation made on an Ethereum blockchain. The name gas is inspired by the view that this fee acts as cryptofuel, driving the motion of smart contracts. Gas is purchased for ether from the miners that execute the code. Gas and ether are decoupled deliberately since units of gas align with computation units having a natural cost, while the price of ether generally fluctuates as a result of market forces. The two are mediated by a free market: the price of gas is actually decided by the miners, who can refuse to process a transaction with a lower gas price than their minimum limit. To get gas you simply need to add ether to your account. The Ethereum clients automatically purchase gas for your ether in the amount you specify as your maximum expenditure for the transaction."*
*   In Solidity, you define a variable by first specifying its type.

What other types are there?

1.  **bool**  
    This is a Boolean, which returns true or false.
2.  **int / uint**  
    Both int and uint represent integers, or number values. The primary difference between int and uint (Unsigned Integer), is that int can hold negative numbers as values.
3.  **address**  
    The address type represents a 20 byte value, which is meant to store an Ethereum address. Variables that are typed as address also have members, including balance and transfer.
4.  **bytes1 through 32**  
    This is a fixed-size byte array.
5.  **bytes**  
    A dynamically-sized byte array.
6.  **string**  
    A dynamically signed string.
7.  **mapping**  
    Hash tables with key types and value types. We will look at mappings more in depth later on in the course.
8.  **struct**  
    Structs allow you to define new types. We will also cover this more in depth shortly.

*   Let's define a string variable in our contract.  Let's also define my age. No one can have a negative age, so we will use an unsigned integer for this:

pragma solidity ^0.4.18;

 

contract Coursetro {

string fName = 'Gary';

uint age = 34;

}

*   Solidity has four types of visibilities for both functions and variables:

1.  **Public**  
    This allows you to define functions or variables that can be called internally or through messages.
2.  **Private**  
    Private variables and functions are only available to the current contract and not derived contracts.
3.  **Internal**  
    Fuctions and variables that can only be accessed internally (current contract or derived).
4.  **External**  
    Functions that can be called from other contracts and transactions. They cannot be called internally, except with "this.functionName()".

*   **Let's add the public visibility to our variables:**

pragma solidity ^0.4.18;

 

contract Coursetro {

string public fName = 'Gary';

uint public age = 34;

}

*   Click **Deploy**, we can now see on the right that we have 2 blue buttons with the name of our variables and the associated values. When you define public state variables, the EVM creates getter functions for them. So, you can actually click on these buttons and it will return the value, as if it were a function.
*   Every smart contract has a constructor function. This constructor is called when a contract is created. Inside of it, you can define the values of variables. Let's re-adjust our code to work with a constructor:

pragma solidity ^0.4.18;

contract Coursetro {

 

string public fName;

uint public age;

 

function Coursetro() public {

fName = 'Gary';

age = 34;

}

}

*   Variables can be declared as being constant. As the name suggests, these are variables with a constant value that does not change.Let's transform the **fName** variable to a constant variable:

pragma solidity ^0.4.18;

 

contract Coursetro {

 

string constant fName = 'Gary';

uint public age;

 

function Coursetro() public {

fName = 'Gary';

age = 34;

}

 

}

In your IDE, you'll notice a red "X" next to line 9. If you hover over it, you will notice that it says, "*TypeError: cannot assign to a constant variable*". Remove line 9 and the error goes away.

*   Our smart contract at this point is pretty boring. Let's integrate a potential user interaction where we can manually define a Coursetro Instructor's name and age. Paste the following:

pragma solidity ^0.4.18;

 

contract Coursetro {

string fName;

uint age;

function setInstructor(string \_fName, uint \_age) public {

fName = \_fName;

age = \_age;

}

function getInstructor() public constant returns (string, uint) {

return (fName, age);

}

}

*   Our smart contract at this point is pretty boring. Let's integrate a potential user interaction where we can manually define a Coursetro Instructor's name and age. Paste the following:

pragma solidity ^0.4.18;

 

contract Coursetro {

string fName;

uint age;

function setInstructor(string \_fName, uint \_age) public {

fName = \_fName;

age = \_age;

}

function getInstructor() public constant returns (string, uint) {

return (fName, age);

}

}

*   We have two functions, setInstructor() and getInstructor(). **setInstructor** accepts 2 parameters, \_fName and \_age. Once called, we set our string fName to the returned \_fName, and same with age. Then, our **getInstructor()** function is defined as being constant, and it returns a string and a uint. This is where we return the fName and age variable once it's called. Click **Deploy** and under the red **set Instructor** button, type in: "Gary", 34 and click the button. Next, click on the **getInstructor()** button and you will notice it now returns the inputed value! This is how you set variables from user input in a smart contract.

 

 

 

### 4\. How to setup or install Ethereum on Windows

**4\. How to setup or install Ethereum on Windows**

*   Install chocolatey on windows . Go to "https://chocolatey.org/install" and copy window command or simply run below command to install chocolatey on windows

@"%SystemRoot%System32WindowsPowerShellv1.0powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%chocolateybin"

*   Run below command to install Node Js

choco install nodejs.install –y

*   Or simply download the installer from "https://nodejs.org/en/download/" link
*   Install Git. To install either run below command

choco install git –y

*   Or download the installer from "https://gitforwindows.org/" link.
*   Install Visual Studio Code along with solidity extension. To install either run below command

. choco install VisualStudioCode –y

*   Or download the installer from "https://www.visualstudio.com/downloads/" link
*   Install Python on Windows. To install either run below command

choco install python –y

*   Or download the installer from "https://www.python.org/downloads/" link.
*   Open the visual studio consol. Go to extensions page. Install the solidity extension
*   Install Python on Windows. To install either run below command

choco install python –y

*   Install Ganache on Windows. Download the installer from below link. http://truffleframework.com/ganache/
*   Or install it from command line

npm install –g ganache -cli

*   What is ganache.When you develop application, that application will be held in application server. In case of Ethereum, the Ethereum blockchain will hold the smart contract. The blockchain is acting as application server. Ganache is simulation blockchain that runs locally in the system and simulate the Ethereum blockchin for you. It comes as GUI or command line.
*   When you run ganache, you will see this image. You see many ether addresses. Each ether address has some ethereum on it.

![](images/15955159139154190_1.jpg)

*   Remix is IDE used to build smart contract. Remix web based IDE https://remix.ethereum.org
*   Install IDE from git or npm using below command npm 

install remix-ide -g remix-ide git clone https://github.com/ethereum/remix-ide...

cd remix-ide

npm  install

npm  run setupremix   

npm start

 

### 5\. How to compile and deploy smart contract on JavaScriptVM

**5\. How to compile and deploy smart contract on JavaScriptVM**

 

*   URL to open Remix IDE https://remix.ethereum.org
*   When we compile the solidity code, we get byte code that we can deploy in Ethereum blockchain.
*   Start new contract student.sol
*   Below is smart contract code

pragma solidity ^0.4.18;

 

contract student {

string name;

uint age;

function setStudentDetails(string \_name, uint \_age) public{

name=\_name;

age=\_age;

}

function getStudentDetails() public view returns(string, uint){

return (name, age);

}

}

 

*   We must deploy the smart contract on Blockchain. There are different blockchains available.Among them are: main net block chain and test net blockchains. Or we can deploy the smart conract on our self blockchain environment. We will use first to deploy smart contract on the inbuilt blockchain inside the Remix IDE which is Java Script VM.

 

![](images/159551591335092675_1.jpg)

 

 

*   To deploy the smart contract on Java Script VM blockchain, we need an account. We get bay default in Remix 5 accounts. But if we deploy the smart contract in Ethereum blockchain, we must create an account there.
*   We choose any account and deploy the smart contract on Java Script VM, click deploy. When the smart contract deployed, it will be deployed on some address. The address assigned by blockchain to that smart contract. So we can always refer to smart contract by that address only.
*   We need ethereum to deploy the smart contract in the main net Ethereum blockchain. Because the miner will mine your transection and when itsis confirmed, it must get some fees.
*   When you assign values to variables, you change the state of the variables, that means you make changes in block chain, and you must pay gas for that. Someone will mine the transaction and then it will be successful. Get function output the values of variables and does not change state of block chin. So it does not require mining and no fees required.
*   Debugger allows you to debug the smart contract

 

### 6\. How to install Ganache Blockchain on Windows and deploy smart contract using it:

**6\. How to install Ganache Blockchain on Windows and deploy smart contract using it:**

 

*   This part shows how to deploy smart contract to Ganache blockchain using remix.
*   Install Ganache on Windows. Download the installer from below link. http://truffleframework.com/ganache/
*   Or install it from command line

npm install –g ganache -cli

*   What is ganache?? When you develop application, that application will be held in application server. In case of ethereum, the Ethereum blockchain will hold the smart contract. The blockchain is acting as application server. Ganache is simulation blockchain that runs locally in the system and simulate the Ethereum blockchin for you. It comes as GUI or command line.
*   When you run ganache, you will see this image. You see many ether addresses. Each ether address has some money on it.

![](images/159551591363022050_1.jpg)

 

*   There will be 10 accounts by defaults.
*   The block tab will show the transections blocks
*   The transection tab will show the transactions. Any transection done by smart contract will be shown on this window.
*   The log tab will show all logs.

*   To connect to Ganache block chain through the Remix, return to our previous example. URL to open Remix IDE https://remix.ethereum.org. When we compile the solidity code, we get byte code that we can deploy in Ethereum blockchain.
*   Start new contract student.sol. Below is smart contract code

pragma solidity >=0.4.22 <0.6.0;

contract student {

string name;

uint age;

function setStudentDetails(string \_name, uint \_age) public{

name=\_name;

age=\_age;

}

function getStudentDetails() public view returns(string, uint){

return (name, age);

}

}

 

*   To connect to Ganache block chain, go to run and choose to run with the third option Web3 provider. Assign connecting to the GUI Ganache server port http://localhost:7545. If you use the command line Ganache, use the server port http://localhost:8545
*   It will show the following after connecting to Ganache. I will show 10 accounts of the Ganache block chain and the amount of ethereum on these accounts.

![](images/15955159146808753_2.jpg)

*   Click deploy to deploy the smart contract. We get the following transection log:

![](images/15955159147035594_3.jpg)

*   When we go to ganache dashboard, we can see the transection details

![](images/159551591572128972_4.jpg)

*   When we send the student details: name and age. New transection will be sent which requires mining. It will use some gas fees that will be given to miner.

![](images/159551591512554364_5.jpg)

*   The transaction is shown in Ganache as smart contract call from certain address to other address

![](images/15955159163479181_6.jpg)

 

### 7\. How to compile and deploy Smart Contract on Test Networks:

**7\. How to compile and deploy Smart Contract on Test Networks:**

 

*   This part shows how to deploy smart contract to TesNet blockchain using remix.
*   URL to open Remix IDE https://remix.ethereum.org
*   Start new contract student.sol. Below is smart contract code

pragma solidity >=0.4.22 <0.6.0;

contract student {

string name;

uint age;

function setStudentDetails(string \_name, uint \_age) public{

name=\_name;

age=\_age;

}

function getStudentDetails() public view returns(string, uint){

return (name, age);

}

}

 

*   Install metamask. With metamask, we can deploy the smart contract in either main network, local network in computer, or any of the three test networks: Ropsten Test Network, Kovan Test Network, Rinkeby Test Network.

![](images/159551591697707265_1.jpg)

*   We will use in this example to connect to Ropsten Test Network.
*   First the metamask account will have zero ether.But we need ethereum balance to spend when we do any change in status on blackchain or we do transection .

 

![](images/159551591765408805_2.jpg)

*   To have some ether in the account, we click buy while connecting to Rinkeby Test Network. It will take us to ethereum faucet https://faucet.metamask.io. We do not get real ethereum from the faucet, but just test ether that can be used in our test network.
*   If previous process failed, you can use https://faucet.rinkeby.io/. Send test ether to the metamask account . You must put the ethereum address in twitter tweet and then submit the tweet to the faucet

![](images/159551591777092004_3.jpg)

*   To deploy the contract on the Rinkeby test network, choose to run contract on injected web 3 mode and deploy the contract. Here screenshot when the contract deployed in the Rinkeby trst network blockchain.

![](images/159551591811815232_4.jpg)

 

 

 

 

### 8\. Quick example of deploying ERC20 token smart contract:

**8\. Quick example of deploying ERC20 token smart contract:**

 

*   Install the metamask on the browser
*   After installing meta mask, we have many networks we can work on:

![](images/159551591865305970_1.jpg)

*   We will use the test network.
*   We can get the erc20 token smart contract creation code ready from https://github.com/ethereum/ethereum-org/blob/master/solidity/token-erc20.sol

pragma solidity >=0.4.22 <0.6.0;

interface tokenRecipient {

function receiveApproval(address \_from, uint256 \_value, address \_token, bytes calldata \_extraData) external;

}      

contract TokenERC20 {

// Public variables of the token

string public name;

string public symbol;

uint8 public decimals = 18;

// 18 decimals is the strongly suggested default, avoid changing it

uint256 public totalSupply;

 

// This creates an array with all balances

mapping (address => uint256) public balanceOf;

mapping (address => mapping (address => uint256)) public allowance;

 

// This generates a public event on the blockchain that will notify clients

event Transfer(address indexed from, address indexed to, uint256 value);

// This generates a public event on the blockchain that will notify clients

event Approval(address indexed \_owner, address indexed \_spender, uint256 \_value);

// This notifies clients about the amount burnt

event Burn(address indexed from, uint256 value);

/\*\*

\* Constructor function

\*

\* Initializes contract with initial supply tokens to the creator of the contract

\*/

constructor(

uint256 initialSupply,

string memory tokenName,

string memory tokenSymbol

) public {

totalSupply = initialSupply \* 10 \*\* uint256(decimals); // Update total supply with the decimal amount

balanceOf\[msg.sender\] = totalSupply; // Give the creator all initial tokens

name = tokenName; // Set the name for display purposes

symbol = tokenSymbol; // Set the symbol for display purposes

}

 

/\*\*

\* Internal transfer, only can be called by this contract

\*/

function \_transfer(address \_from, address \_to, uint \_value) internal {

// Prevent transfer to 0x0 address. Use burn() instead

require(\_to != address(0x0));

// Check if the sender has enough

require(balanceOf\[\_from\] >= \_value);

// Check for overflows

require(balanceOf\[\_to\] + \_value >= balanceOf\[\_to\]);

// Save this for an assertion in the future

uint previousBalances = balanceOf\[\_from\] + balanceOf\[\_to\];

// Subtract from the sender

balanceOf\[\_from\] -= \_value;

// Add the same to the recipient

balanceOf\[\_to\] += \_value;

emit Transfer(\_from, \_to, \_value);

// Asserts are used to use static analysis to find bugs in your code. They should never fail

assert(balanceOf\[\_from\] + balanceOf\[\_to\] == previousBalances);

}

 

/\*\*

\* Transfer tokens

\*

\* Send \`\_value\` tokens to \`\_to\` from your account

\*

\* @param \_to The address of the recipient

\* @param \_value the amount to send

\*/

function transfer(address \_to, uint256 \_value) public returns (bool success) {

\_transfer(msg.sender, \_to, \_value);

return true;

}

 

/\*\*

\* Transfer tokens from other address

\*

\* Send \`\_value\` tokens to \`\_to\` on behalf of \`\_from\`

\*

\* @param \_from The address of the sender

\* @param \_to The address of the recipient

\* @param \_value the amount to send

\*/

function transferFrom(address \_from, address \_to, uint256 \_value) public returns (bool success) {

require(\_value <= allowance\[\_from\]\[msg.sender\]); // Check allowance

allowance\[\_from\]\[msg.sender\] -= \_value;

\_transfer(\_from, \_to, \_value);

return true;

}

 

/\*\*

\* Set allowance for other address

\*

\* Allows \`\_spender\` to spend no more than \`\_value\` tokens on your behalf

\*

\* @param \_spender The address authorized to spend

\* @param \_value the max amount they can spend

\*/

function approve(address \_spender, uint256 \_value) public

returns (bool success) {

allowance\[msg.sender\]\[\_spender\] = \_value;

emit Approval(msg.sender, \_spender, \_value);

return true;

}

 

/\*\*

\* Set allowance for other address and notify

\*

\* Allows \`\_spender\` to spend no more than \`\_value\` tokens on your behalf, and then ping the contract about it

\*

\* @param \_spender The address authorized to spend

\* @param \_value the max amount they can spend

\* @param \_extraData some extra information to send to the approved contract

\*/

function approveAndCall(address \_spender, uint256 \_value, bytes memory \_extraData)

public

returns (bool success) {

tokenRecipient spender = tokenRecipient(\_spender);

if (approve(\_spender, \_value)) {

spender.receiveApproval(msg.sender, \_value, address(this), \_extraData);

return true;

}

}

 

/\*\*

\* Destroy tokens

\*

\* Remove \`\_value\` tokens from the system irreversibly

\*

\* @param \_value the amount of money to burn

\*/

function burn(uint256 \_value) public returns (bool success) {

require(balanceOf\[msg.sender\] >= \_value); // Check if the sender has enough

balanceOf\[msg.sender\] -= \_value; // Subtract from the sender

totalSupply -= \_value; // Updates totalSupply

emit Burn(msg.sender, \_value);

return true;

}

 

/\*\*

\* Destroy tokens from other account

\*

\* Remove \`\_value\` tokens from the system irreversibly on behalf of \`\_from\`.

\*

\* @param \_from the address of the sender

\* @param \_value the amount of money to burn

\*/

function burnFrom(address \_from, uint256 \_value) public returns (bool success) {

require(balanceOf\[\_from\] >= \_value); // Check if the targeted balance is enough

require(\_value <= allowance\[\_from\]\[msg.sender\]); // Check allowance

balanceOf\[\_from\] -= \_value; // Subtract from the targeted balance

allowance\[\_from\]\[msg.sender\] -= \_value; // Subtract from the sender's allowance

totalSupply -= \_value; // Update totalSupply

emit Burn(\_from, \_value);

return true;

}

}

*   **We must adjust the following when deploying the cod:**

1- Contact Mycoin must be your contract name

2- totalSupply

3- initalSupply

4- tokenName

5\. tokenSymbol

 

*   Compile the code in https://remix.ethereum.org/
*   Connect the metamask to Rinkbey test network
*   Get test ether from the faucet https://faucet.rinkeby.io/. It will send your ethereum account 3 ether.
*   Setup the following before deploying the account as example

initialSupply: 1000000

tokenName: hidaia

tokenSymbol: hedaia

![](images/159551591983952036_2.jpg)

*   When the contract deployed you will get the following forms that you can fill

![](images/159551591982184671_3.jpg)

*   You can try to burn some tokens,you will see that the total supply decreased by those number you burbed,
*   You can also try any other changes

 

 

**9\. Getting started tutorial on solidity:**

**a) Data Types and Data Structures**

 

Go to https://remix.ethereum.org/ and create new file. I called it MyContrct.sol.

Let's create a new file named MyContract.sol. On the first line of this file, we'll declare the version of the solidity programming language we want to use:

pragma solidity ^0.4.24;

 

Now we can declare the smart contract like this:

pragma solidity ^0.4.24;

contract MyContract {

// ...

}

 

A smart contract is a piece of code that gets executed on the Ethereum blockchain. It functions somewhat like an API microservice on the web that is publicly accessible to everyone. All of the code of the smart contract is visible to the public, and we can allow anyone connected to the network to call functions on the smart contract.

First, we'll program a simple "storage" smart contract that will be able to:

Store a value

Retrieve this value

We'll start by creating a way to store a string value in the smart contract like this. We'll do that with a variable called value. Solidity is a statically typed language, so we must first specify the data type when declaring the variable like this:

pragma solidity ^0.4.24;

contract MyContract {

string value;

 

}

 

Now let's create a function to read this value from storage. We'll start by declaring a function called get() with the function keyword like this:

function get() {

// ...

}

Now we'll return the value from the state variable with the return keyword like this. We'll set the "visibility" of this function to public so that anyone connected to the blockchain can call it. Finally, we'll specify the return value string for the function:

pragma solidity ^0.4.24;

contract MyContract {

string value;

function get() public view returns(string) {

return value;

}

}

let's create a way to set this value from outside the smart contract. We'll create a set function. We simply created a function that accepts a \_value argument of string type. This function is also publicly visible so that anyone connected to the blockchain can call it. Now let's actually update the smart contract value like this:

function set(string \_value) public {

value = \_value;

}

 

Now let's set a default value for the value state variable. We'll do that inside the smart contract constructor function like this:

constructor() public {

value = "myValue";

}

 

Remember, the Etherum blockchain is made up of bundles of records called "blocks" which are "chained together" to make up the public ledger. The basic units of all these blocks are transactions. You're seeing them listed here below. You can click the "down" arrow to see all details of the receipt.

I'll select the JavaScript virtual machine, which will give us a simulated blockchain inside our browser.

Let's update the code in our smart contract to be compatible with the latest version of Solidity at the time of writing this article. We can modify the first line in the smart contract code like this:

pragma solidity ^0.5.1;

 

First, modify the get() and set () functions to look like this:

pragma solidity ^0.5.1;

contract MyContract {

string value;

constructor() public {

value = "myValue";

}

function get() public view returns(string memory) {

return value;

}

function set(string memory \_value) public {

value = \_value;

}

}

 

We can also assign a default value to the state variable like this:

string public value = "myValue";

 

We can also set this value as a constant that will never change like this:

string public constant value = "myValue";

 

We can create a boolean state variable like this:

bool public myBool = true;

 

This can be either true or false.

 

Now we can create an integer like this:

int public myInt = 1;

 

Integers can be positive or negative, i.e., signed. If you don't want a number to be negative, you can create an unsigned integer like this:

uint public myUint = 1;

 

We can specify the number of bits for the number. The above example defaults to 256 bits. We can be explicit like this:

uint256 public myUint256 = 9999;

 

We can also restrict the value to 8 bits, like this:

uint8 public myUint8 = 8;

 

**b) Enums**

 

Now let's go over some basic data structures in solidity. First, let's look at the Enum data structure, which are a way of keeping track of enumerated lists in Solidity. We can check against this list whenever you're writing smart contracts. Let's create an enum in the smart contract like this:

enum State { Waiting, Ready, Active }

 

Just as an example, this will help us keep track of the active state of the smart contract by providing Waiting, Ready, and Active options. We can check the current state of the smart contract like this:

State public state;

 

Now, we can set the default state in the constructor:

constructor() public {

state = State.Waiting;

}

We can update the current state to active like this:

function activate() public {

state = State.Active;

}

 

And finally, we can check against the enum list to see if the state is currently active like this:

function isActive() public view returns(bool) {

return state == State.Active;

}

 

Now the final smart contract code should look like this:

pragma solidity 0.5.1;

contract MyContract {

enum State { Waiting, Ready, Active }

State public state;

constructor() public {

state = State.Waiting;

}

function activate() public {

state = State.Active;

}

function isActive() public view returns(bool) {

return state == State.Active;

}

}

 

**c) Structs**

 

Solidity allows you to define your own data types with Structs. You can basically model any kind of data you want with arbitrary attributes of varying data types. Let's look at how this works by creating a people struct:

struct Person {

string \_firstName;

string \_lastName;

}

 

We've modeled a person here that has a \_firstName and \_lastName. Notice that we're able to specify any data type that we want! We've used strings for both attributes here. We could add up to 17 different attributes here with any data type.

 

Now we need a place to store this person struct. Let's use an array for this! We can declare people array like this:

Person\[\] public people;

 

Notice we declare the type within the array, i.e., Person. We also set the visibility to public and assigned it to a state variable called people. This will provide us with a function that will allow us to access the people inside this array. I should mention though, that calling the people() function outside the smart contract will not return the entire array. Instead, the people() function will accept an index argument that will allow us to reference the person inside the array based upon that index, which is zero-based. For example, we can access the first person in the people array like this: people(0)

 

Now let's create a way to add a person to this array. We'll create an addPerson() function like this:

This function will accept the arguments for the person struct attributes, then instantiate a new person and add it to the people array with the push function. It also increments the peopleCount state variable by 1. We can implement that state variable in the smart contract like this: uint256 public peopleCount;

function addPerson(string memory \_firstName, string memory \_lastName) public {

people.push(Person(\_firstName, \_lastName));

peopleCount += 1;

}

 

Now the completed smart contract code should look like this:

pragma solidity 0.5.1;

contract MyContract {

Person\[\] public people;

uint256 public peopleCount;

 

struct Person {

string \_firstName;

string \_lastName;

}

function addPerson(string memory \_firstName, string memory \_lastName) public {

people.push(Person(\_firstName, \_lastName));

peopleCount += 1;

}

**}            **

 

**d) Mapping**

 

Solidity provides a data structure called a mapping which allows us to store key-value pairs. This structure acts much like an associative array or a hash table in other functions. We can declare a mapping in the smart contact like this:

mapping(uint => Person) public people;

 

This will be a mapping where we store person structs. It will replace the people array we used in the previous example. The key will be an unsigned integer, and the value will be a person struct. We'll treat the key like a database id. We can update the person struct to keep track of that id like this:

struct Person { uint \_id; string \_firstName; string \_lastName; }

 

Now we can modify the addPerson() function to update the people mapping. The following code uses the peopleCount counter cache to create an id for the person. Then it instantiates a new person struct with the id and the passed in attributes. It then adds this to the people mapping. The completed smart contract code should look like this:

pragma solidity 0.5.1;

 

contract MyContract {

uint256 peopleCount = 0;

 

mapping(uint => Person) public people;

 

struct Person {

uint \_id;

string \_firstName;

string \_lastName;

}

 

function addPerson(string memory \_firstName, string memory \_lastName) public {

peopleCount += 1;

people\[peopleCount\] = Person(peopleCount, \_firstName, \_lastName);

}

}

 

We can deploy the contract to check the code. If I putin addPerson field:

“\_firstName”=”Hidaia” and “\_secondName”=”Alassouli”

This will be stored as the first element in people array. I put 1 in people field and I will get the data stored in the element 1 in array people.

![](images/159551592035104727_4.jpg)

 

 

**e) Function Visibility**

 

Let's talk about function visibility. In the last sections, we used the public function visibility several times so that the smart contract functions can be called outside the smart contract by accounts connected to the network. What if we wanted to create functions that are only used inside the smart contract? We can do this with the internal visibility. Let’s increment the peopleCount to its own internal function like this:

**function incrementCount() internal {**

peopleCount += 1;

}

 

This function will only be accessible inside the smart contract, not by the public interface for other accounts. Now we can call this function inside the addPerson() function like this:

function addPerson(string memory \_firstName, string memory \_lastName) public {

incrementCount()

people\[peopleCount\] = Person(peopleCount, \_firstName, \_lastName);

}

 

**f) Modifiers**

 

Now that's an example of other types of function visibly. Let's talk about function modifiers. These will allow us to add special behavior to our functions, like add permissions. Let's create a modifier that only allows an admin or "owner" to call the addPerson() function, and restrict everyone else from calling this function.

First, we'll create a way to store the owner of this smart contract. We can do that with a state variable like this:

address owner;

 

Now let's create a modifier that checks if the person calling the function is the owner:

modifier onlyOwner() {

require(msg.sender == owner);

\_;

}

 

Let me explain this code:

First, we declare the modifier with the modifier keyword, followed by the modifier name onlyOwner.

Next, we access the current account that's calling the function with msg.sender.

Next, we use require() to check that the account calling the function is the owner. If the result of the expression passed into require() evaluates to true, then code resumes execution. If not, it throws an error. In this case, if the account calling the function is not the owner, then Solidity will throw an error.

Now we can set the owner inside the smart contract as the account that deploys the smart contract like this:

constructor() public {

owner = msg.sender;

}

 

Now we can add the modifier to the addPerson() function so that only the owner can call it.Try to run your code to see if only the owner can call the function successfully without any errors! At this point, the complete smart contract code should look like this:

pragma solidity 0.5.1;

 

contract MyContract {

uint256 public peopleCount = 0;

mapping(uint => Person) public people;

 

address owner;

 

modifier onlyOwner() {

require(msg.sender == owner);

\_;

}

 

struct Person {

uint \_id;

string \_firstName;

string \_lastName;

}

 

constructor() public {

owner = msg.sender;

}

 

function addPerson(

string memory \_firstName,

string memory \_lastName

)

public

onlyOwner

{

incrementCount()

people\[peopleCount\] = Person(peopleCount, \_firstName, \_lastName);

}

 

function incrementCount() internal {

peopleCount += 1;

}

}

 

**g) Time**

 

We can create a new modifier that uses time to illustrate a use case for time in Solidity. We'll create a new modifier called onlyWhileOpen that will check that the current time on the blockchain is past a time that we specify. This is a common practice when creating ICO crowdsale smart contracts that have an "opening time". Often times, these smart contracts will reject investor contributions that are made before the crowdsale has started. We can model similar behavior by restricting access to the addPerson() function until after the opening time has passed. First let's create a state variable to store the opening time:

uint256 startTime;

 

We can store the startTime with this state variable in seconds, as that's how we express timestamps in Solidity. In fact, the time stamps are expressed in unix time which is the number of seconds that have passed since Thursday, 1 January 1970. Now I'll set the start time in the constructor like this:

constructor() public {

startTime = (unic timestamp);

}

 

You can use https://www.epochconverter.com/ to generate a unix timestamp in the future for your own purposes! Now let's create a modifier to check that the start time has passed like this:

modifier onlyWhileOpen() {

 **require(block.timestamp >= startTime);**

\_;

}

 

First, we declare the modifier, just like we did in the last example. Next, we require the specific condition.Then we compare the start time to "now", by checking the current block's timestamp with block.timestamp.

 

Now we can add the modifier to the addPerson() function

pragma solidity 0.5.1;

 

contract MyContract {

**uint256** **public peopleCount = 0;**

**mapping(uint => Person) public people;**

 

uint256 startTime;

 

 **modifier onlyWhileOpen() {**

require(block.timestamp >= startTime);

\_;

}

 

 **struct Person {**

 **uint \_id;**

 **string \_firstName;**

 **string \_lastName;**

}

 

**constructor()** **public {**

**startTime =** **1544668513; // Update this value**

}

 

 **function addPerson(**

 **string memory \_firstName,**

 **string memory \_lastName**

 **)**

 **public**

onlyWhileOpen

 **{**

people\[peopleCount\] = Person(peopleCount, \_firstName, \_lastName);

}

 

 **function incrementCount() internal {**

**peopleCount +=** **1;**

}

}

 

 

 

**h) Sending Ether & Events**

 

Now let's write a function that accepts Ether. To demonstrate this, I'll create an ico-like contract with a buyToken() function. This will allow an account to send ether to pay for tokens with Ether. The smart contract will be responsible for issuing the tokens, tracking the balance of the account, and also transferring the Ether funds to another wallet address.

First we'll create a mapping to track the token balances like this:

mapping(address => uint256) public balances;

 

Now I'll create the buyToken() function that will increment the balance like this:

function buyToken() public {

balances\[msg.sender\] += 1;

}

 

Now I'll declare a wallet where the ether funds will be sent whenever an account buys tokens:

address wallet;

 

Now we can transfer funds to the wallet whenever the buyToken() function is called like this:

function buyToken() public payable {

balances\[msg.sender\] += 1;

wallet.transfer(msg.value);

}

 

Now let me explain this code:

We can transfer ether directly to the wallet by calling wallet.transfer()

We can get the value of the Ether sent in by function caller with msg.value, just like msg.sender

We also must use the payable modifier so that accounts can send Ether when calling the function.

 

Likewise, to update to Solidity 0.5.1, we must explicitly declare the wallet payable as well:

address payable wallet;

 

Now let's set the wallet address inside the constructor function of the contract (we'll use the payable modifier here, too):

constructor(address payable \_wallet) public {

wallet = \_wallet;

}

 

Awesome! Now watch the video above as I demonstrate how to send Ether with this function inside of Remix. You complete smart contract code should look like this up to this point:

contract MyContract {

mapping(address => uint256) public balances;

address payable wallet;

 

constructor(address payable \_wallet) public {

wallet = \_wallet;

}

 

function buyToken() public payable {

balances\[msg.sender\] += 1;

wallet.transfer(msg.value);

}

}

 

We can test the code. When running the code, I deployed the contract with some ether address. Then I bought tokens with other ether addr by clicking buy token and I set the amount ex: 2 eth. Then I clicked the balance button. It shows the balance incremented by 1 and the ether balances increased in deployed contract by 2 and decreased for the buyer ether address by 2.

 

![](images/159551592057389693_5.jpg)

 

Now I'll show you how to create a default or "fallback" function inside Solidity. This is a function that will get called anytime an account sends Ether to a smart contract. This is a very common pattern for ICO smart contracts, where you simply send Ether to a smart contract and it executes a function. That's exactly what we'll do here. We'll declare a fallback function that wraps the buyTokens() function. It will purchase tokens any time an account sends Ether to the smart contract. We can do that like this:

function() external payable {

buyToken();

}

 

Now let's talk about Events. Events are a way of dealing with the asynchronous nature of the blockchain. We can declare events inside smart contracts that can be subscribed to by external consumers. These consumers will be able to listen for these events to know that something happened inside the smart contract. We'll declare a Purchase event at the top of the smart contract like this:

event Purchase(

address \_buyer,

uint256 \_amount

);

 

This event will log the buyer and the token amount. We'll be able to trigger this event inside the buyToken() function like this:

function buyToken() public payable {

balances\[msg.sender\] += 1;

wallet.transfer(msg.value);

emit Purchase(msg.sender, 1);

}

 

This event will allow us to know any time a token is purchased inside this smart contract. But what if we only wanted to listen for events that were relevant to our account? Good news! Solidity allows us to subscribe to filter events by indexed values. We can index the \_buyer inside the event like this:

event Purchase(

address indexed \_buyer,

uint256 \_amount

);

 

Now you know how to work with events inside Solidity. At this point your complete smart contract code should look like this:

pragma solidity 0.5.1;

contract MyContract {

mapping(address => uint256) public balances;

address payable wallet;

event Purchase(

address indexed \_buyer,

uint256 \_amount

);

 

constructor(address payable \_wallet) public {

wallet = \_wallet;

}

function() external payable {

buyToken();

}

function buyToken() public payable {

balances\[msg.sender\] += 1;

wallet.transfer(msg.value);

emit Purchase(msg.sender, 1);

}

}

 

Here the log generated when buying a token:

![](images/159551592143285549_6.jpg)

 

**j) Smart contract interaction**

 

I'll show you how to work with multiple smart contracts in solidity. First, I'll show you how to call smart contract functions from within another smart contract.

I'll create the token contract like this:

contract ERC20Token {

string name;

mapping(address => uint256) public balances;

 

function mint() public {

balances\[msg.sender\] += 1;

}

}

 

Now we can mint tokens from MyContract using the ERC20Token contract. In order to do this, we need to a few things: the address of the token, and the smart contract code in order to call its mint() function. First I'll store the token address in a state variable like this:

contract MyContract {

address public token;

//...

}

 

Now we can set the value for the token address inside the constructor like this:

constructor(address payable \_wallet, ERC20Token \_token) public {

wallet = \_wallet;

token = \_token;

}

 

Now that we have the address available, we can access the smart contract code inside of the buyToken() function like this, and call the mint() function on it like this:

function buyToken() public payable {

ERC20Token \_token = ERC20Token(address(token));

\_token.mint();

wallet.transfer(msg.value);

}

 

I want to draw your attention to something before we continue. If you were to call the buyToken() function from your personal account right now, you would not mint any tokens for yourself. Why is that!? Let's revisit the mint() function as it is now:

function mint() public {

balances\[msg.sender\] += 1;

}

 

The reason it will not mint tokens for your account is because msg.sender is actually referencing the address of MyContract, which is calling the function from inside its buyToken()function! If we want to mint tokens for our own account, we must use tx.origin to reference the account that originated the transaction on the blockchain like this:

function mint() public {

balances\[tx.origin\] += 1;

}

 

You will need to deploy the token smart contract first, obtain its address, and then include it as an argument whenever you deploy the second smart contract. At this point your complete smart contract code should look like this:

pragma solidity 0.5.1;

 

contract ERC20Token {

string name;

mapping(address => uint256) public balances;

 

function mint() public {

balances\[tx.origin\] += 1;

}

}

 

contract MyContract {

address public token;

 

address payable wallet;

 

constructor(address payable \_wallet, address \_token) public {

wallet = \_wallet;

token = \_token;

}

 

function buyToken() public payable {

ERC20Token \_token = ERC20Token(address(token));

\_token.mint();

wallet.transfer(msg.value);

}

}

 

Now test the code

*   Deploy the ERC20Token contract first.
*   Take the contract address from debug menu
*   Deploy MyContract after putting the creator wallet address and ERC20Token smart contract address arguments in deploy field.
*   Press the buyToken field
*   Then presss the balance field in ERC20Token contract and put the buyer address to show the balance (address of the person initiated the transection)

 

![](images/159551592146506453_7.jpg)

 

**k) Inheritance**

 

Now let's talk about inheritance. Solidity allows you to create smart contracts that inherit from one another. Let's create a new pseudo token called MyToken that inherits from our original token smart contract. We'll use inheritance to give it a unique name, symbol, and mint function. We can inherit from the smart contract like this

 

contract MyToken is ERC20Token {

// ...

 

}

 

Now we can keep track of the token name in the parent smart contract like this:

pragma solidity 0.5.1;

 

contract ERC20Token {

string public name;

mapping(address => uint256) public balances;

 

constructor(string memory \_name) public {

name = \_name;

}

 

function mint() public {

balances\[tx.origin\] ++;

}

}

 

We can override the name of the parent token inside the constructor of our child token. While we're here, we'll also create a symbol for the child token and set it in the constructor. I'll show you how to override the parent token contract constructor, while assigning the new values like this:

contract MyToken is ERC20Token {

string public symbol;

 

constructor(

string memory \_name,

string memory \_symbol

)

ERC20Token(\_name)

public {

symbol = \_symbol;

}

}

Awesome! Now we have customized MyToken. Now let's update the mint() function to override the functionality of the parent token. First, let's create a way to store the address of all the token owners. We'll also set the count of all the owners like this:

contract MyToken is ERC20Token {

address\[\] public owners;

uint256 public ownerCount;

//...

}

 

Now let's update these values inside our own mint() function while preserving the behavior of the parent token smart contract. We can do that with the super keyword like this:

function mint() public {

super.mint();

ownerCount ++;

owners.push(msg.sender);

}

 

Awesome! Now we've created our own custom token that inherits from the parent token. Your full smart contract code should look like this:

pragma solidity 0.5.1;

 

contract ERC20Token {

string public name;

mapping(address => uint256) public balances;

 

constructor(string memory \_name) public {

name = \_name;

}

 

function mint() public {

balances\[tx.origin\] ++;

}

}

contract MyToken is ERC20Token {

string public symbol;

address\[\] public owners;

uint256 public ownerCount;

 

constructor(

string memory \_name,

string memory \_symbol

)

ERC20Token(\_name)

public {

symbol = \_symbol;

}

 

function mint() public {

super.mint();

ownerCount ++;

owners.push(msg.sender);

}

 

}

 

Now test the code. I deployed the contract “MyToken” with the name argument “Hidaia” and symbol “HED”

The following data showed for each contract field: balances, name, ownerCount, owners, and symbol.

 

![](images/159551592261574373_8.jpg)

 

**l) Library**

 

Library is used so we don’t repeat the code I each new contract code. Lets declare library Math.

pragma solidity 0.5.1;

 

library Math{

function divide(uint256 a, uint256 b) internal pure returns (uint256) {

require(b>0);

uint256 c=a/b;

return c;

}

}

contract MyContract {

uint256 public value;

function calaculate (uint \_value1, uint \_value2) public {

value=Math.divide(\_value1, \_value2);

}

}

 

MyContract will use the defined library Math to divide a and b.

Deploy MyContract and give the values of a and b in the Calculate function fields. Attached the screenshot og the result:

 

![](images/159551592223141044_9.jpg)

 

 

 

**m) Including library in separate file**

 

We can put the library in separate file and call it inside the contract by including the library file.

As an example, we opened new file for the Math library we wrote. The new file is Library.sol. Here the code inside the library:

pragma solidity 0.5.1;

library Math{

function divide(uint256 a, uint256 b) internal pure returns (uint256) {

require(b>0);

uint256 c=a/b;

return c;

}

}

 

Then we can call the library file Math.sol inside MyContract.sol file through import command. Here the complete code:

pragma solidity 0.5.1;

 

import "./Math.sol";

 

contract MyContract {

uint256 public value;

function calaculate (uint \_value1, uint \_value2) public {

value=Math.divide(\_value1, \_value2);

}

}

 

**n) SafeMath**

 

There is a common library called SafeMath.sol makes the athematicoperations much simple. The library in this link

https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/math/SafeMath.sol

*   I created SafeMath.sol with the code in that page.

 

pragma solidity ^0.5.0;

 

/\*\*

\* @dev Wrappers over Solidity's arithmetic operations with added overflow

\* checks.

\*

\* Arithmetic operations in Solidity wrap on overflow. This can easily result

\* in bugs, because programmers usually assume that an overflow raises an

\* error, which is the standard behavior in high level programming languages.

\* \`SafeMath\` restores this intuition by reverting the transaction when an

\* operation overflows.

\*

\* Using this library instead of the unchecked operations eliminates an entire

\* class of bugs, so it's recommended to use it always.

\*/

library SafeMath {

/\*\*

\* @dev Returns the addition of two unsigned integers, reverting on

\* overflow.

\*

\* Counterpart to Solidity's \`+\` operator.

\*

\* Requirements:

\* - Addition cannot overflow.

\*/

function add(uint256 a, uint256 b) internal pure returns (uint256) {

uint256 c = a + b;

require(c >= a, "SafeMath: addition overflow");

 

return c;

}

 

/\*\*

\* @dev Returns the subtraction of two unsigned integers, reverting on

\* overflow (when the result is negative).

\*

\* Counterpart to Solidity's \`-\` operator.

\*

\* Requirements:

\* - Subtraction cannot overflow.

\*/

function sub(uint256 a, uint256 b) internal pure returns (uint256) {

return sub(a, b, "SafeMath: subtraction overflow");

}

 

/\*\*

\* @dev Returns the subtraction of two unsigned integers, reverting with custom message on

\* overflow (when the result is negative).

\*

\* Counterpart to Solidity's \`-\` operator.

\*

\* Requirements:

\* - Subtraction cannot overflow.

\*

\* NOTE: This is a feature of the next version of OpenZeppelin Contracts.

\* @dev Get it via \`npm install @openzeppelin/contracts@next\`.

\*/

function sub(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256) {

require(b <= a, errorMessage);

uint256 c = a - b;

 

return c;

}

 

/\*\*

\* @dev Returns the multiplication of two unsigned integers, reverting on

\* overflow.

\*

\* Counterpart to Solidity's \`\*\` operator.

\*

\* Requirements:

\* - Multiplication cannot overflow.

\*/

function mul(uint256 a, uint256 b) internal pure returns (uint256) {

// Gas optimization: this is cheaper than requiring 'a' not being zero, but the

// benefit is lost if 'b' is also tested.

// See: https://github.com/OpenZeppelin/openzeppelin-contracts/pull/522

if (a == 0) {

return 0;

}

 

uint256 c = a \* b;

require(c / a == b, "SafeMath: multiplication overflow");

 

return c;

}

 

/\*\*

\* @dev Returns the integer division of two unsigned integers. Reverts on

\* division by zero. The result is rounded towards zero.

\*

\* Counterpart to Solidity's \`/\` operator. Note: this function uses a

\* \`revert\` opcode (which leaves remaining gas untouched) while Solidity

\* uses an invalid opcode to revert (consuming all remaining gas).

\*

\* Requirements:

\* - The divisor cannot be zero.

\*/

function div(uint256 a, uint256 b) internal pure returns (uint256) {

return div(a, b, "SafeMath: division by zero");

}

 

/\*\*

\* @dev Returns the integer division of two unsigned integers. Reverts with custom message on

\* division by zero. The result is rounded towards zero.

\*

\* Counterpart to Solidity's \`/\` operator. Note: this function uses a

\* \`revert\` opcode (which leaves remaining gas untouched) while Solidity

\* uses an invalid opcode to revert (consuming all remaining gas).

\*

\* Requirements:

\* - The divisor cannot be zero.

\* NOTE: This is a feature of the next version of OpenZeppelin Contracts.

\* @dev Get it via \`npm install @openzeppelin/contracts@next\`.

\*/

function div(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256) {

// Solidity only automatically asserts when dividing by 0

require(b > 0, errorMessage);

uint256 c = a / b;

// assert(a == b \* c + a % b); // There is no case in which this doesn't hold

 

return c;

}

 

/\*\*

\* @dev Returns the remainder of dividing two unsigned integers. (unsigned integer modulo),

\* Reverts when dividing by zero.

\*

\* Counterpart to Solidity's \`%\` operator. This function uses a \`revert\`

\* opcode (which leaves remaining gas untouched) while Solidity uses an

\* invalid opcode to revert (consuming all remaining gas).

\*

\* Requirements:

\* - The divisor cannot be zero.

\*/

function mod(uint256 a, uint256 b) internal pure returns (uint256) {

return mod(a, b, "SafeMath: modulo by zero");

}

 

/\*\*

\* @dev Returns the remainder of dividing two unsigned integers. (unsigned integer modulo),

\* Reverts with custom message when dividing by zero.

\*

\* Counterpart to Solidity's \`%\` operator. This function uses a \`revert\`

\* opcode (which leaves remaining gas untouched) while Solidity uses an

\* invalid opcode to revert (consuming all remaining gas).

\*

\* Requirements:

\* - The divisor cannot be zero.

\*

\* NOTE: This is a feature of the next version of OpenZeppelin Contracts.

\* @dev Get it via \`npm install @openzeppelin/contracts@next\`.

\*/

function mod(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256) {

require(b != 0, errorMessage);

return a % b;

}

}

 

*   Then I called the library in MyContract.sol with import command. Now any athematic operation is easier. Here the MyContract.sol code :

pragma solidity 0.5.1;

 

import "./SafeMath.sol";

 

contract MyContract {

using SafeMath for uint256;

uint256 public value;

function calaculate (uint \_value1, uint \_value2) public {

value=\_value1.div(\_value2);

}

}

 

*   Attached screenshot when deploying MyContract.sol

 

![](images/159551592354341205_10.jpg)

 

### 10\. ERC-20 smart contract and crowd sale (ICO) smart contract:

**10\. ERC-20 smart contract and crowd sale (ICO) smart contract:**

I'm going to show you how to code your own cryptocurrency on the Ethereum blockchain and sell it! I'll show you how to create your own ERC-20 token and crowd sale step-by-step with Ethereum smart contracts, how to test the smart contracts, how to deploy the smart contracts to the Ethereum blockchain, and how to build an ICO website deployed to the web. I'll also explain what an ERC-20 token is, how an Ethereum token works, how an initial coin offering (ICO) works.

**a. What is an ERC-20 Token?**

The Ethereum blockchain allows you to create your own cryptocurrency, or token, that can be purchased with Ether, the native cryptocurrency of the Ethereum blockchain. ERC-20 is simply a standard that specifies how these tokens behave, so that they are compatible with other platforms like cryptocurrency exchanges.

Ethereum is a blockchain like Bitcoin. Like Bitcoin, Ethereum keeps track of account balances for people who own Ether, Ethereum’s native cryptocurrency. Unlike Bitcoin, Ethereum is also a platform that allows you to create your own token without creating a new blockchain.

You can create an Ethereum token with a smart contract. ERC-20 is a standard that specifies how this token smart contract should work.

Let’s use an example to understand how an ERC-20 token smart contract works. Let’s say that we want to create a token called “My Token” with the symbol “MTK” and that there will be 100,000,000 of these tokens in existence.

First, the token smart contract keeps track of some basic token attributes. For example it records the name “My Token", the symbol that you see on a cryptocurrency exchange, and how many total tokens exist.

It also keeps track of who owns “My Token” and how much.

ERC-20 tokens can be transferred from one account to another as payment, just like any other cryptocurrency.

They can also be purchased in a crowd sale, like an ICO, which we will examine in the next section.

They can also be bought and sold on a cryptocurrency exchange.

 

### b. How ERC-20 Tokens Work

**b. How ERC-20 Tokens Work**

Ethereum allows developers to write applications that run on the blockchain with smart contracts, which encapsulate all of the business logic of these applications. They enable us to read and write data to the blockchain, as well as execute code. Smart contacts are written in a programming language called Solidity, which looks a lot like Javascript. It is a full blown programming language that will allow us to do many of the same types of things Javascript is capable of, but it behaves a bit differently because of its use case, as we’ll see in this tutorial.

In the case of an ERC-20 token, the smart contract governs all of the behavior about how the token works, and keeps track of token ownership and account balances.

ERC-20 is an API specification for how Ethereum tokens should be built. It is a community adopted standard that allows tokens to be supported in a variety of use cases. We want to build a token that is compliant with this standard so that it can be widely accepted. If we did not have a standard like this, we could have endless ways to create tokens, and they might not be compatible with one another!

Using the ERC-20 standard ensures that a token is compliant for the following use cases (and more):

*   Wallet transfers - sending tokens from one account to another
*   Buying and selling on cryptocurrency exchanges
*   Purchasing tokens in an crowd sale (ICO) like we'll demonstrate in this tutorial

The ERC-20 specification essentially dictates the interface that the smart contract must respond to. It specifies the structure of the smart contract and types of functions that the smart contract must have. It also provides some suggested functions that are nice to have, but ultimately optional. It dictates certain events that our token must have, like a transfer event. See, smart contracts can emit events that consumers can subscribe to, and with this standard, we can subscribe to events that tell us when tokens are sold.

Here is an example implementation of the transfer function specified by the ERC-20 standard. It is required by the smart contract, and governs how someone can send an ERC-20 token from their wallet to another.

contract ERC20Token {

 **// ...**

 

 **function transfer(address \_to, uint256 \_value) public returns (bool success) {**

 **require(balanceOf\[msg.sender\] >= \_value);**

 

balanceOf\[msg.sender\] -= \_value;

balanceOf\[\_to\] += \_value;

 

Transfer(msg.sender, \_to, \_value);

 

 **return true;**

}

 

 **// ...**

}

 

This function implements the ERC-20 standard the following ways:

*   The function exists.
*   It accepts the correct arguments.
*   It fails if the user doesn't have enough tokens to transfer, i.e., an insufficient balance.
*   It transfers the balance from the sender's account to the receiver's account.
*   It triggers a sell event.
*   It returns the correct value, e.g., true.

 

 

### c. How a crowd sale (ICO) works

**c. How a crowd sale (ICO) works**

ERC-20 tokens can be distributed in a variety of ways. One popular method is holding a crowd sale, or an initial coin offering (ICO). Crowd sales are a way for a company to raise capital for their business by creating their own ERC-20 token that can be purchased by investors with Ether.

You can watch this video below for more information on how crowd sales work in addition to following along with this article.

Whenever a crowd sale takes place, the company gets liquid capital in the form of Ether that was paid by the investors, as well as holding onto a reserved amount of the ERC-20 tokens that were sold in the crowd sale.

In order to participate in a crowd sale, an investor must connect to the Etherum Blockchain with an account. This account has a wallet address that can store Ether, as well as the ERC-20 tokens that are purchased in the crowd sale.

The investor must visit a crowd sale website that talks to a smart contract. The smart contract governs all of the rules for how the crowd sale works.

Whenever an investor purchases tokens on the crowd sale website, they send Ether from their wallet to the smart contract, and the smart contract instantly dispenses the purchased tokens to their wallet.

The smart contract sets the price of the token in the crowd sale and governs how the crowd sale behaves.

Crowd sales can take on all kinds of shapes and sizes. They can have multiple tiers or phases, like Pre ICO, ICO, and ICO Bonus phase. Each of these tiers can happen at different points of time and can behave differently.

They can also have white lists to restrict which investors can purchase tokens.

They can also have a reserved amount of tokens that are not sold in the crowd sale. These reserves are usually set aside for specific members of each company like founders and advisors. These reserves can be a fixed amount of tokens or a percentage.

Whenever a crowd sale ends, it can be finalized by an administrator. Whenever this happens, all of the reserved tokens will be distributed to the appropriate accounts and the crowd sale will officially be over.

 

 

### d. Short code of ERC20 smart contract

**d. Short code of ERC20 smart contract**

 

Let’s start building our ERC-20 token! Here is the complete ERC-20 token smart contract Solidity code. C**eate the file DappToken.sol**

 

pragma solidity ^0.4.2;

 

contract DappToken {

string public name = "DApp Token";

string public symbol = "DAPP";

string public standard = "DApp Token v1.0";

uint256 public totalSupply;

 

event Transfer(

address indexed \_from,

address indexed \_to,

uint256 \_value

);

 

event Approval(

address indexed \_owner,

address indexed \_spender,

uint256 \_value

);

 

mapping(address => uint256) public balanceOf;

mapping(address => mapping(address => uint256)) public allowance;

 

function DappToken (uint256 \_initialSupply) public {

balanceOf\[msg.sender\] = \_initialSupply;

totalSupply = \_initialSupply;

}

 

function transfer(address \_to, uint256 \_value) public returns (bool success) {

require(balanceOf\[msg.sender\] >= \_value);

 

balanceOf\[msg.sender\] -= \_value;

balanceOf\[\_to\] += \_value;

 

Transfer(msg.sender, \_to, \_value);

 

return true;

}

 

function approve(address \_spender, uint256 \_value) public returns (bool success) {

allowance\[msg.sender\]\[\_spender\] = \_value;

 

Approval(msg.sender, \_spender, \_value);

 

return true;

}

 

function transferFrom(address \_from, address \_to, uint256 \_value) public returns (bool success) {

require(\_value <= balanceOf\[\_from\]);

require(\_value <= allowance\[\_from\]\[msg.sender\]);

 

balanceOf\[\_from\] -= \_value;

balanceOf\[\_to\] += \_value;

 

allowance\[\_from\]\[msg.sender\] -= \_value;

 

Transfer(\_from, \_to, \_value);

 

return true;

}

}

 

Let's take a look at what this smart contract does, and how it implements the ERC-20 standard:

*   It stores the token name string public name = "DApp Token".
*   It stores the token symbol for cryptocurrency exchanges string public symbol = "DAPP".
*   It stores the total supply of tokens in existence uint256 public totalSupply.
*   It uses a Solidity mapping to store the balance of each account that owns tokens mapping(address => uint256) public balanceOf.
*   It implements a transfer function to allow users to send tokens to another account.
*   It implements an approve function that allows another account to spend tokens, like on a cryptocurrency exchange. This updates the allowance mapping to see how much the account is allowed to spend.
*   It implements a transferFrom that allows another account to transfer tokens.

 

### e. Short code of Crowd sale (ICO) smart contract

**e. Short code of Crowd sale (ICO) smart contract**

Now we can build a crowd sale smart contract that will allow investors to purchase tokens in an initial coin offering (ICO). Here is the complete crowd sale smart contract Solidity code:

pragma solidity ^0.4.2;

 

import "./DappToken.sol";

 

contract DappTokenSale {

address admin;

DappToken public tokenContract;

uint256 public tokenPrice;

uint256 public tokensSold;

 

event Sell(address \_buyer, uint256 \_amount);

 

function DappTokenSale(DappToken \_tokenContract, uint256 \_tokenPrice) public {

admin = msg.sender;

tokenContract = \_tokenContract;

tokenPrice = \_tokenPrice;

}

 

function multiply(uint x, uint y) internal pure returns (uint z) {

require(y == 0 || (z = x \* y) / y == x);

}

 

function buyTokens(uint256 \_numberOfTokens) public payable {

require(msg.value == multiply(\_numberOfTokens, tokenPrice));

require(tokenContract.balanceOf(this) >= \_numberOfTokens);

require(tokenContract.transfer(msg.sender, \_numberOfTokens));

 

tokensSold += \_numberOfTokens;

 

Sell(msg.sender, \_numberOfTokens);

}

 

function endSale() public {

require(msg.sender == admin);

require(tokenContract.transfer(admin, tokenContract.balanceOf(this)));

 

// Just transfer the balance to the admin

admin.transfer(address(this).balance);

}

}

Let's take a look at what this smart contract does, and how it functions as a crowd sale:

*   It stores an admin account for the crowd sale address admin.
*   It references the ERC-20 token smart contract DappToken public tokenContract.
*   It stores the token price uint256 public tokenPrice.
*   It stores the number of tokens sold uint256 public tokensSold.
*   It implements a sell event so that consumers can get notifications whenever a token has been sold.
*   It implements a buyTokens function that allows users to purchase tokens in the crowd sale.
*   It implements an endSale function that allows an admin to end the crowd sale and collect the Ether funds that was raised during the sale.

 

### 11\. Creating Ethereum ERC-20 Tokens and Crowd Sales (ICO) without coding with Token Wizard:

**11\. Creating Ethereum ERC-20 Tokens and Crowd Sales (ICO) without coding with Token Wizard:**

 

The POA network wizard allows you to create ERC20 token and crowd sales web site in easy steps.

*   Connect the metamask in some test network as Rinkeby test network.
*   Go website https://wizard.oracles.org/#/:
*   Start by clicking New Crowdsale

![](images/159551592379938201_1.jpg)

*   Click whitelist crowdsale. Then continue.

![](images/159551592430649232_2.jpg)

*   This is the page that we will put all token specification that we want to sell:

![](images/159551592493197221_3.jpg)

*   Here setup your token details

Name: Hidaia

Ticker: HIDI (Token symbol)

Decimals: 18 (The token can be divided by 18 decimal amounts)

*   In reserved token section, we are allowed to reserve certain amountof tokens that will not be sold in crowd sale. You can reserve a fixed amount of tokens or percentage of sales for some addresses you choose.
*   I chose to reserve 1000 tokens for this address 0xa4F8b494facbda8888DA6C8b2f4B9498F33dc981

![](images/159551592413927553_4.jpg)

*   Then click continue. Here we get the token settings:

![](images/15955159258473446_5.jpg)

 

*   In this window we can specify the gas rice for each transection. This is the fee that the investor will pay when he purchase token.
*   You can also specify in “Investor Min CAP” the minimum amount of tokens that investor can purchase. I selected 1.
*   In “Enable whitelisting” field, you can restrict the accounts that can participate in the crowdsale. We will leave it off
*   Setup the Crowd sale setup address. I chose “HIDAIAICO”
*   You can specify the start and end time for token sale.
*   Then you can specify the exchange rate of the tokens. This specifies the number of tokens the investor will receive for one ether.Example, if you setu this field with 100. Then the investor will get 100 tokens when he pays 1 ether.
*   Then you can setup the supply. Which is the number of tokens that can be sold on this crowdsale. I setup 1000000 tokens to be sold in this tiere of crowdsale.
*   Here the complete setup

![](images/159551592639841391_6.jpg)

*   Click add TIER. Then you sign all transactions in the following windows.

![](images/159551592715914312_7.jpg)

*   Then the page that will be shown to investor when he wants to participate in crowdsale

![](images/159551592821343859_8.jpg)

*   Click invest to show the full page that will be shown to investor that wants to participate in crowd sale

https://wizard.oracles.org/invest?addr=0x300213fF03Bf91299d6654e2986ABca6E26f92Bf&networkID=4

![](images/1595515929389228_9.jpg)

*   Put the number of tokens you want to send to buy and then click invest and then confirm transection

![](images/159551592938858086_10.jpg)

*   Here the details

0xa4F8b494facbda8888DA6C8b2f4B9498F33dc981

Current Account

0x13cE73594E51341A34a31F99675a3ff21F77C925

Token Address

0x300213fF03Bf91299d6654e2986ABca6E26f92Bf

Crowdsale Contract Address

HIDAIA

Name

HIDI

Ticker

1000000 HIDI

Total Supply

 

*   **You can check token received in etherscan**

https://rinkeby.etherscan.io/address/0xa4F8b494facbda8888DA6C8b2f4B9498F33dc981

 

 

### 12\. Example of creating and deploying an ERC20 token on the test and main network!!!

**12\. Example of creating and deploying an ERC20 token on the test and main network!!!**

 

**a. Write the ERC20 smart contract codes in Remix from https://github.com/ConsenSys**

 

1-Go to https://remix.ethereum.org/

2- Create new file EIP20.sol file. Copy on it the code found in https://github.com/ConsenSys/Tokens/blob/master/contracts/eip20/EIP20.sol

// Abstract contract for the full ERC 20 Token standard

// https://github.com/ethereum/EIPs/blob/master/EIPS/eip-20.md

pragma solidity ^0.4.21;

 

 

contract EIP20Interface {

/\* This is a slight change to the ERC20 base standard.

function totalSupply() constant returns (uint256 supply);

is replaced with:

uint256 public totalSupply;

This automatically creates a getter function for the totalSupply.

This is moved to the base contract since public getter functions are not

currently recognised as an implementation of the matching abstract

function by the compiler.

\*/

/// total amount of tokens

uint256 public totalSupply;

 

/// @param \_owner The address from which the balance will be retrieved

/// @return The balance

function balanceOf(address \_owner) public view returns (uint256 balance);

 

/// @notice send \`\_value\` token to \`\_to\` from \`msg.sender\`

/// @param \_to The address of the recipient

/// @param \_value The amount of token to be transferred

/// @return Whether the transfer was successful or not

function transfer(address \_to, uint256 \_value) public returns (bool success);

 

/// @notice send \`\_value\` token to \`\_to\` from \`\_from\` on the condition it is approved by \`\_from\`

/// @param \_from The address of the sender

/// @param \_to The address of the recipient

/// @param \_value The amount of token to be transferred

/// @return Whether the transfer was successful or not

function transferFrom(address \_from, address \_to, uint256 \_value) public returns (bool success);

 

/// @notice \`msg.sender\` approves \`\_spender\` to spend \`\_value\` tokens

/// @param \_spender The address of the account able to transfer the tokens

/// @param \_value The amount of tokens to be approved for transfer

/// @return Whether the approval was successful or not

function approve(address \_spender, uint256 \_value) public returns (bool success);

/// @param \_owner The address of the account owning tokens

/// @param \_spender The address of the account able to transfer the tokens

/// @return Amount of remaining tokens allowed to spent

function allowance(address \_owner, address \_spender) public view returns (uint256 remaining);

 

// solhint-disable-next-line no-simple-event-func-name

event Transfer(address indexed \_from, address indexed \_to, uint256 \_value);

event Approval(address indexed \_owner, address indexed \_spender, uint256 \_value);

}

 

2- Create new file EIP20Factory.sol file. Copy on it the code found in

https://github.com/ConsenSys/Tokens/blob/master/contracts/eip20/EIP20Factory.sol

import "./EIP20.sol";

 

pragma solidity ^0.4.21;

 

 

contract EIP20Factory {

 

mapping(address => address\[\]) public created;

mapping(address => bool) public isEIP20; //verify without having to do a bytecode check.

bytes public EIP20ByteCode; // solhint-disable-line var-name-mixedcase

 

function EIP20Factory() public {

//upon creation of the factory, deploy a EIP20 (parameters are meaningless) and store the bytecode provably.

address verifiedToken = createEIP20(10000, "Verify Token", 3, "VTX");

EIP20ByteCode = codeAt(verifiedToken);

}

 

//verifies if a contract that has been deployed is a Human Standard Token.

//NOTE: This is a very expensive function, and should only be used in an eth\_call. ~800k gas

function verifyEIP20(address \_tokenContract) public view returns (bool) {

bytes memory fetchedTokenByteCode = codeAt(\_tokenContract);

 

if (fetchedTokenByteCode.length != EIP20ByteCode.length) {

return false; //clear mismatch

}

 

//starting iterating through it if lengths match

for (uint i = 0; i < fetchedTokenByteCode.length; i++) {

if (fetchedTokenByteCode\[i\] != EIP20ByteCode\[i\]) {

return false;

}

}

return true;

}

 

function createEIP20(uint256 \_initialAmount, string \_name, uint8 \_decimals, string \_symbol)

public

returns (address) {

 

EIP20 newToken = (new EIP20(\_initialAmount, \_name, \_decimals, \_symbol));

created\[msg.sender\].push(address(newToken));

isEIP20\[address(newToken)\] = true;

//the factory will own the created tokens. You must transfer them.

newToken.transfer(msg.sender, \_initialAmount);

return address(newToken);

}

 

//for now, keeping this internal. Ideally there should also be a live version of this that

// any contract can use, lib-style.

//retrieves the bytecode at a specific address.

function codeAt(address \_addr) internal view returns (bytes outputCode) {

assembly { // solhint-disable-line no-inline-assembly

// retrieve the size of the code, this needs assembly

let size := extcodesize(\_addr)

// allocate output byte array - this could also be done without assembly

// by using outputCode = new bytes(size)

outputCode := mload(0x40)

// new "memory end" including padding

mstore(0x40, add(outputCode, and(add(add(size, 0x20), 0x1f), not(0x1f))))

// store length in memory

mstore(outputCode, size)

// actually retrieve the code, this needs assembly

extcodecopy(\_addr, add(outputCode, 0x20), 0, size)

}

}

}

 

3- Create new file EIP20Interface.sol file. Copy on it the code found in

https://github.com/ConsenSys/Tokens/blob/master/contracts/eip20/EIP20Interface.sol

// Abstract contract for the full ERC 20 Token standard

// https://github.com/ethereum/EIPs/blob/master/EIPS/eip-20.md

pragma solidity ^0.4.21;

 

 

contract EIP20Interface {

/\* This is a slight change to the ERC20 base standard.

function totalSupply() constant returns (uint256 supply);

is replaced with:

uint256 public totalSupply;

This automatically creates a getter function for the totalSupply.

This is moved to the base contract since public getter functions are not

currently recognised as an implementation of the matching abstract

function by the compiler.

\*/

/// total amount of tokens

uint256 public totalSupply;

 

/// @param \_owner The address from which the balance will be retrieved

/// @return The balance

function balanceOf(address \_owner) public view returns (uint256 balance);

 

/// @notice send \`\_value\` token to \`\_to\` from \`msg.sender\`

/// @param \_to The address of the recipient

/// @param \_value The amount of token to be transferred

/// @return Whether the transfer was successful or not

function transfer(address \_to, uint256 \_value) public returns (bool success);

 

/// @notice send \`\_value\` token to \`\_to\` from \`\_from\` on the condition it is approved by \`\_from\`

/// @param \_from The address of the sender

/// @param \_to The address of the recipient

/// @param \_value The amount of token to be transferred

/// @return Whether the transfer was successful or not

function transferFrom(address \_from, address \_to, uint256 \_value) public returns (bool success);

 

/// @notice \`msg.sender\` approves \`\_spender\` to spend \`\_value\` tokens

/// @param \_spender The address of the account able to transfer the tokens

/// @param \_value The amount of tokens to be approved for transfer

/// @return Whether the approval was successful or not

function approve(address \_spender, uint256 \_value) public returns (bool success);

 

/// @param \_owner The address of the account owning tokens

/// @param \_spender The address of the account able to transfer the tokens

/// @return Amount of remaining tokens allowed to spent

function allowance(address \_owner, address \_spender) public view returns (uint256 remaining);

 

// solhint-disable-next-line no-simple-event-func-name

event Transfer(address indexed \_from, address indexed \_to, uint256 \_value);

event Approval(address indexed \_owner, address indexed \_spender, uint256 \_value);

}

 

### b. Deploy and test the ERC20 smart contract codes:

**b. Deploy and test the ERC20 smart contract codes:**

 

*   First deploy the smart contracts on Rinkeby test network
*   Run EIP20. When deploying the EIP20 smart contract, you must input Initail amount, token symbol , number of decimals and token name. I setup initial amount= 100000000,token name=”Hidaia”, token symbol=”HIDI”, number of decimals=2 . Here screenshot
*    

![](images/159551593099238062_1.jpg)

 

*   Click transact. Then the contract deployed. We get the following data that we can query

![](images/159551593114927686_2.jpg)

 

*   We can query any data. Example, BalanceOf= 100000000

![](images/159551593166352841_3.jpg)

*   We can transfer tokens to other address from transfer field. Just setup the etherum address you want to transfer tokens to it and amount of tokens.Example to transfer 1000 tokens to address 0x5673C69337457E0Cf7F68e86D878B2D35B0F9F46. Then check the balance

![](images/159551593172245506_4.jpg)

*   You can test transection in Rinkeby test network using https://rinkeby.etherscan.io/
*   You can repeat the procedure in the main ethereum network after confirming it in in the test network.

 

 

  
  
  
Publisher:  
BookRix GmbH & Co. KG  
Implerstraße 24  
80331 Munich  
Germany  
  
  
  
Publication Date: July 23rd 2020  
  
[https://www.bookrix.com/-kf086886aac2de5](https://www.bookrix.com/-kf086886aac2de5)  
  
ISBN: 978-3-7487-5106-9  
  
  
BookRix-Edition, publishing information We thank you for choosing to purchase this book from BookRix.com. We want to invite you back to [BookRix.com](https://www.bookrix.com/) in order to evaluate the [book](https://www.bookrix.com/_ebook-dr-hedaya-mahmood-alasooly-quick-guide-for-smart-contracts-creation-and-deployment-on-ethereum-block). Here you can discuss with other readers, discover more [books](https://www.bookrix.com/books.html) and even become an author yourself.  
  
Thank you again for supporting our BookRix-community.