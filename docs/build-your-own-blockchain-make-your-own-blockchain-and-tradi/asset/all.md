![](Images/bod_cover.jpg)

## Build your own Blockchain

1.  [Titelseite](#titelseite.xhtml#toc_marker-0)
2.  [Copyright](#impressum.xhtml)

# 

![](Images/rId12_edit_140086947772624.jpeg)

[Translated from German to English - www.onlinedoctranslator.com](https://www.onlinedoctranslator.com/en/?utm_source=onlinedoctranslator&utm_medium=pdf&utm_campaign=attribution)

| 

## **Smart contracts for the Ethereum**

 || **+** [Cryptocurrencies](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html) ||  |
| --- | --- | --- |
|  || **+** || [TechDocs](https://www.torsten-horn.de/techdocs/index.htm) ||  ||  ||  ||  |
| 

## **blockchain**

 || **+** ||  || **Seek** ||  ||  |
|  ||  ||  ||  ||  ||  |
|  ||  ||  ||  ||  ||  ||  |

[Blockchain](https://de.wikipedia.org/wiki/Blockchain) **refers to a continuously expandable list of data records, which are linked to one another by means of cryptographic processes, so that the chain of data records is unchangeable and forgery-proof. New transactions are validated and packed into blocks, and the blocks are appended to the blockchain after going through a consensus algorithm and sent to all other blockchain servers.**

![](Images/rId17_edit_140086947772560.jpeg)

[Ethereum](https://www.ethereum.org/) **is based on a public blockchain, which is used** [in a](https://www.ethereum.org/) **decentralized peer-to-peer network on many Ethereum** [servers as](https://www.ethereum.org/) **DLT** **is operated.** **Ethere** [um](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html#DLT) **includes the** **Cryptocurrency** [Ether and](https://www.ethereum.org/) **also** [enables "](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html#Ethereum-Ether-ETH-ETC) **Smart contracts** **".** [This allows](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html#Kryptowaehrung) [contracts](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html#Ethereum-Ether-ETH-ETC) **to be programmed, which** [are then](https://de.wikipedia.org/wiki/Smart_Contract) **executed and checked electronically. For this purpose, scripts are created (mostly in the programming language** **Solidity** **) and executed in the Ethereum Virtual Machine (EVM).**

![](Images/rId23_edit_140086947773264.png)

**This opens up very diverse possibilities, for example many are based** **ICOs** [thereon.](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html#ICO) **However,** **special care must be taken when programming** **smart contracts: those who are programmed**

![](Images/rId28_edit_140086947773200.png)

**Security gaps can have fatal consequences, as with "** **The DAO** [Hack",](https://www.wired.de/collection/business/wie-aus-dem-hack-des-blockchain-fonds-dao-ein-wirtschaftskrimi-wurde) [which](https://www.wired.de/collection/business/wie-aus-dem-hack-des-blockchain-fonds-dao-ein-wirtschaftskrimi-wurde) **led to the Ethereum hard fork" Ethereum Classic ".**

![](Images/rId30_edit_140086947773008.png)

**Basic explanations can be found under:** [Cryptocurrencies, Bitcoin,](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html) [Ethereum, Blockchain](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html) **. Some simple programming examples for smart** **contracts are shown below.**

![](Images/rId32_edit_140086947773328.png)

**contents**

**1.** [Basic installations: Geth, Solc, private test Ethereum](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Installation-Geth-Solc-Test-Blockchain) [blockchain](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Installation-Geth-Solc-Test-Blockchain)

![](Images/rId35_edit_140086947773392.png)

**2.** [First smart contract: hello world demo](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Hallo-Welt-Demo)

![](Images/rId37_edit_140086947773456.png)

**3.** [Mini token smart contract: MeinToken demo](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo)

![](Images/rId39_edit_140086947773520.png)

**4th** [Remix Online Solidity Compiler as a graphical](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Remix-Online-Solidity-Compiler) [development environment (GUI-IDE)](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Remix-Online-Solidity-Compiler)

![](Images/rId41_edit_140086947773584.png)

**5.** [Perform a MeinToken transfer with the GUI tool Mist](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#MeinToken-Mist)

![](Images/rId44_edit_140086947773648.png)

**6th** [DApp website for the smart contract with Node.js](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Node.js-DApp-Webseite) **7th** [Transfer of Ether with Web3j and Java](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#EtherWeb3jDemo)

![](Images/rId47_edit_140086947773712.png)

**8th.** [Transfer of your own smart contract tokens with Web3j and Java](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#MeinTokenWeb3jDemo)

![](Images/rId50_edit_140086947773776.png)

**9.** [DApp website for the smart contract with Java](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Java-DApp-Webseite)

![](Images/rId52_edit_140086947773840.png)

**10.** [Public Rinkeby Test Ethereum blockchain instead of private](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Rinkeby) [blockchain](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Rinkeby)

![](Images/rId54_edit_140086947773904.png)

**11.** [Deploy smart contract in the public Rinkeby blockchain](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Smart-Contract-Rinkeby)

![](Images/rId57_edit_140086947773968.png)

**12th** [DApp website for the smart contract in the Rinkeby](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Rinkeby-DApp-Webseite) [blockchain](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Rinkeby-DApp-Webseite)

![](Images/rId59_edit_140086947774032.png)

**13th** [Truffle for easy development and quick testing](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Truffle) **14th** [Embark for easy development and quick testing](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Embark)

![](Images/rId62_edit_140086947774096.png)

**15th** [DApp website for the smart contract with both Truffle and](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#DApp-Webseite-Truffle-Embark) [Embark](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#DApp-Webseite-Truffle-Embark)

![](Images/rId65_edit_140086947774160.png)

**16.** [Use of the Oraclize service for external](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Oraclize) [information queries](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Oraclize)

![](Images/rId68_edit_140086947774224.png)

**17th** [Analysis of the blocks and transactions](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Analyse-Bloecke-Transaktionen)

![](Images/rId71_edit_140086947774288.png)

**18th** [Solidity plug-in for JetBrains IntelliJ IDEA](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Intellij-Solidity)

![](Images/rId73_edit_140086947774352.png)

**19th** [documentary](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Doku)

![](Images/rId75_edit_140086947774416.png)

**Basic installations: Geth, Solc, private test Ethereum blockchain**

**This demo shows:**

**\-As "geth"(Go Ethereum) will be installed.**

**\-As "solc"(Solidity Compiler) will be installed.**

**\-Like your own private Test Ethereum Blockchain is set up and started.**

**\-As a Account created and Mining is started.**

**The following versions are used:**

**\-geth 1.8.2**

**\-solc 0.4.19**

**\-web3 0.20.1**

**\-Windows 10**

**The following text focuses on simplicity and good comprehensibility. For the time being, only command line tools are used. On graphical tools will** **further down** **received.**

![](Images/rId77_edit_140086947771920.png)

**In this example, a private Ethereum blockchain that only exists on your own PC is set up. How a public Ethereum blockchain can be used will** **further down** **shown.**

![](Images/rId78_edit_140086947771984.png)

**The commands are shown for Windows. When using Linux or Mac OS X, it is often sufficient to replace "\\" with "/" in path specifications and ";" in PATH specifications. with ":" and with placeholders% MEINE\_VARIABLE% by $ MEINE\_VARIABLE.**

**Follow the steps outlined below.**

**1.** **Change to your preferred workspace directory (e.g. \\**

![](Images/rId79_edit_140086947770512.jpeg)

**Mein** Workspace) and **execute the following commands:**

**cd \\ MyWorkspace**

![](Images/rId81_edit_140086947770704.png)

**mkdir EthereumDemo**

![](Images/rId82_edit_140086947770640.png)

**cd EthereumDemo**

![](Images/rId83_edit_140086947770576.png)

**mkdir solc**

![](Images/rId84_edit_140086947770768.png)

**mkdir src**

![](Images/rId85_edit_140086947770832.png)

**tree / F**

![](Images/rId86_edit_140086947770896.png)

**2.** **Install solc (** **Solidity** [Compiler):](https://solidity.readthedocs.io/) **Download** **from** **https://github.com/ ethereum/solidity/releases** [the installation file suitable for your](https://github.com/ethereum/solidity/releases) **operating system, e.g. for Windows: solidity-windows.zip.**

![](Images/rId89_edit_140086947770960.png)

**Under Windows, unzip this zip file in the directory:**

**\\ MeinWorkspace \\ EthereumDemo \\ solc.**

**For other operating systems, proceed either analogously or as described under:** **In** [stalling the Solidity Compiler](https://solidity.readthedocs.io/en/develop/installing-solidity.html) **.**

1.  **Execute in the command line window:cd \\ MeinWorkspace \\ EthereumDemo solc \\ solc.exe --version**

**solc \\ solc.exe --help**

**Both commands must show plausible results.**

![](Images/rId92_edit_140086947771024.png)

**4th** **Install geth (Go Ethereum):**

![](Images/rId94_edit_140086947771152.jpeg)

**Download**

**from** [https://geth.ethereum.org/downloads](https://geth.ethereum.org/downloads/) **/** **a Geth version suitable for your operating system,**

**for example for Windows "Geth 1.8.2 for Windows".**

**Do not use Geth versions 1.8.0 and**

**1.8.1, because it means that** [the Web3j](https://github.com/web3j/web3j/issues/318) **Issue** **318** **comes. For Windows you will receive the file "geth-windowsamd64-1.8.2-b8b9f7f4.exe". Run this file. The installation extends the Windows search PATH to include the Geth directory.**

![](Images/rId97_edit_140086947771344.png)

**For other operating systems, proceed as described under:** **https://** **www.e** [thereum.org/cli or https://git](https://www.ethereum.org/cli) [hub.com/ethereum/go](https://github.com/ethereum/go-ethereum/wiki/Building-Ethereum)

![](Images/rId100_edit_140086947771216.png)

[\- ethereum / wiki / Building-Ethereum.](https://github.com/ethereum/go-ethereum/wiki/Building-Ethereum)

1.  **Open a new command line window for configuration changes and PATH extensions to take effect. In it do:**

**cd \\ MeinWorkspace \\ EthereumDemo**

![](Images/rId101_edit_140086947771472.png)

**geth version**

![](Images/rId102_edit_140086947771600.png)

**geth help**

![](Images/rId103_edit_140086947771728.png)

**Both commands must show plausible results.**

**You can also find a list of the command line options of geth under:** **Command** [line options.](https://github.com/ethereum/go-ethereum/wiki/Command-Line-Options)

![](Images/rId105_edit_140086947771792.png)

**6th** **Genesis block:**

**To start your own private test Ethereum blockchain, manual initialization of the first Genesis block is required. Create the JSON file in the src subdirectory:**

**genesis-block.json**

![](Images/rId106_edit_140086947116304.png)

**{**

**"alloc": {},**

**"coinbase": "0x0000000000000000000000000000000000000000",**

**"config": {},**

**"difficulty": "0x4000",**

**"extraData": "0x4711",**

**"gasLimit": "0xffffffff",**

**"mixhash": "0x0000000000000000000000000000000000000000000000000000000000000000",**

**"nonce": "0x0000000000000042",**

**"parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",**

**"timestamp": "0x00"**

**}**

**When saving, make sure that the file must be saved with Unix line end characters and as an ASCII file without UTF-BOM.**

**You can find some notes on the Genesis block at:** **Creating** [The](https://github.com/ethereum/go-ethereum/wiki/Private-network) [Genesis Block.](https://github.com/ethereum/go-ethereum/wiki/Private-network)

![](Images/rId108_edit_140086947116112.png)

1.  **Create the Genesis Block by running:cd \\ MeinWorkspace \\ EthereumDemo**

**geth -datadir "Private-Blockchain" init src /genesisblock.json**

![](Images/rId109_edit_140086947116368.png)

**You will receive, among other things:**

![](Images/rId111_edit_140086947116496.png)

**Successfully wrote genesis state**

**8th.Start of the own test Ethereum blockchain (without mining for the time being): Execute (in one line):**

**geth -networkid 77 --identity "MyDevChain"**

![](Images/rId112_edit_140086947116624.png)

*   **\- datadir "Private-Blockchain" --nodiscover --rpc**

*   **\- rpcapi "db, eth, net, web3, personal, txpool"**

*   **\- rpccorsdomain "\*" console**

![](Images/rId113_edit_140086947116752.png)

**You will receive, among other things:**

![](Images/rId114_edit_140086947116880.png)

**Starting peer-to-peer node**

**HTTP endpoint opened: http://127.0.0.1:8545 Welcome**

**to the Geth JavaScript console!**

**And you get the Geth-JavaScript-Console, in which you can enter Geth-JavaScript commands.**

**9.** **Take a look at the documentation on the web3.eth commands:** [web3.eth](https://web3js.readthedocs.io/en/1.0/web3-eth.html)

![](Images/rId116_edit_140086947117008.png)

[1.0](https://web3js.readthedocs.io/en/1.0/web3-eth.html) **respectively.** [Web3 0.20.x JavaScript](https://github.com/ethereum/wiki/wiki/JavaScript-API) **API** **. Query the**

![](Images/rId118_edit_140086947117136.png)

**Web3.js version you are using:**

**web3.version.api**

![](Images/rId119_edit_140086947117264.png)

1.  **Test whether accounts already exist. If the insertion of commands with Ctrl + V does not work, try the right mouse button, "Insert" and Return:**

**web3.eth.accounts**

![](Images/rId120_edit_140086947117392.png)

**You will get an empty quantity:**

![](Images/rId121_edit_140086947117520.png)

**\[\]**

**11.Create Account:**

**Create an account (think of a more difficult password and remember it well):**

**personal.newAccount ("My Ethereum Test Passphrase"**

![](Images/rId122_edit_140086947117648.png)

## **)**

**You will receive a 40-digit hex number as an account address, for example:**

![](Images/rId123_edit_140086947117776.png)

**"0x2f94831a57a96041064d9d0c24583b12f807f2a5"**

1.  **Test again for existing accounts: web3.eth.accounts**

**For example, this time you will get:**

![](Images/rId124_edit_140086947117904.png)

**\["0x2f94831a57a96041064d9d0c24583b12f807f2a5"\]**

**13th** **Query account balances:**

**Create the JavaScript file in the src subdirectory:**

**checkAllBalances.js**

![](Images/rId126_edit_140086947118032.png)

**function checkAllBalances () {**

**web3.eth.getAccounts (function (err, accounts) {**

**accounts.forEach (function (id) {**

**web3.eth.getBalance (id, function (err, balance) {**

**console.log ("" + id + ": \\ tbalance:" + web3.fromWei (balance, "ether")**

**\+ "ether");**

**});**

**});**

**});**

**};**

**checkAllBalances ()**

1.  **Run in the Geth JavaScript Console:loadScript ('src / checkAllBalances.js')**

**You receive:**

![](Images/rId127_edit_140086947118160.png)

**0x2f94831a57a96041064d9d0c24583b12f807f2a5:balance: 0 ether**

**15thStart mining manually:**

**Execute (do not execute the individual JavaScript commands too quickly one after the other):**

**miner.setEtherbase (web3.eth.accounts \[0\]) miner.start (1)**

![](Images/rId129_edit_140086947118288.png)

**You get a never-ending output of mining commands:**

![](Images/rId130_edit_140086947118416.png)

**Starting mining operation Commit**

**new mining work Successfully sealed**

**new block mined potential block**

**. . .**

**If mining does not start for you: Sometimes it happens that mining only starts after maybe 10 minutes.**

**Give the mining some time, about a minute. You will then find Ether on the account.**

**16\. End the test Ethereum blockchain:exit**

![](Images/rId131_edit_140086947118544.png)

**17th** **Start script:**

**Create the batch file in the EthereumDemo project directory start-test-**

**Ethereum-Blockchain.bat with the following content (in one line):**

**geth --networkid 77 --identity "MeineDevChain"**

![](Images/rId132_edit_140086947118672.png)

*   **\- datadir "Private-Blockchain" --nodiscover --rpc**

*   **\- rpcapi "db, eth, net, web3, personal, txpool"**

*   **\- rpccorsdomain "\*" --mine --minerthreads 1 console**

**2 >> priv-geth.log**

![](Images/rId133_edit_140086947118800.png)

**Note that this time mining is automatically activated with "--mine -- minerthreads 1", and with "2 >> priv-geth.log" the many outputs are redirected to a log file.**

**18thStart of our own test Ethereum blockchain including mining:Do:**

**cd \\ MeinWorkspace \\ EthereumDemo start-test-Ethereum-Blockchain.batFor example, you get:**

![](Images/rId134_edit_140086947118928.png)

**Welcome to the Geth JavaScript console!**

**instance: Geth / MeineDevChain / v1.8.2-stable-b8b9f7f4 / windows-amd64 / go1.9 coinbase:**

**0x2f94831a57a96041064d9d0c24583b12f807f2a5**

**at block: 1448 (Mon, 22 Jan 2018 12:53:13 CET)**

**datadir: \\ MeinWorkspace \\ EthereumDemo \\ Private-Blockchain**

**modules: admin: 1.0 debug: 1.0 eth: 1.0 miner: 1.0 net: 1.0 personal: 1.0 rpc: 1.0 txpool: 1.0 web3: 1.0**

**19.Run in the Geth JavaScript Console:loadScript ('src / checkAllBalances.js')**

![](Images/rId135_edit_140086947119056.png)

**This time you will receive a positive amount, for example:**

![](Images/rId136_edit_140086947116048.png)

**0x2f94831a57a96041064d9d0c24583b12f807f2a5:balance: 4711 ether**

1.  **Carry out further commands to get to know each other, for example:**

**admin.datadir**

![](Images/rId137_edit_140086947115152.png)

**admin.nodeInfo**

![](Images/rId138_edit_140086947115280.png)

## **eth**

**eth.getBlock ("latest")**

![](Images/rId139_edit_140086947115408.png)

**miner.getHashrate ()**

![](Images/rId140_edit_140086947115536.png)

**personal.listAccounts**

![](Images/rId141_edit_140086947115664.png)

**txpool.content**

![](Images/rId142_edit_140086947115792.png)

## **web3**

**See the explanations for the** **Management** [commands at.](https://github.com/ethereum/go-ethereum/wiki/Management-APIs)

![](Images/rId144_edit_140086955038032.png)

**21\. End the test Ethereum blockchain:exit**

![](Images/rId145_edit_140086955036880.png)

**22ndChecking the keystore file and the directory structure:Do:**

**to you** \\ MeinWorkspace \\ EthereumDemo \\ Private- Blockchain \\ keystore

![](Images/rId147_edit_140086955039888.png)

**There is the** **Keystore** [file, for examp](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html#Keystore) **le:**

![](Images/rId149_edit_140086955039120.png)

**UTC - 2018-01-22T09-50-58.520494400Z - 2f94831a57a96041064d9d0c24583b12f807f2a5**

**23** **The project structure now looks like this (check it under**

**Windows with tree / F and under Linux with tree):**

![](Images/rId150_edit_140086955037776.png)

**\[\\ MeinWorkspace \\ EthereumDemo\]**

*   **\- priv-geth.log**

*   **\- start-test-Ethereum-Blockchain.bat**

**| - \[private blockchain\]**

*   **| - History**

*   **| - \[geth\]**

**||** **'- ...**

*   **'- \[keystore\]**

*   **'- UTC - 2018-01-22T09-50-58 ...**

**| - \[solc\]**

*   **| - msvcp140.dll**

*   **| - solc.exe**

*   **'- soltest.exe**

**'- \[src\]**

*   **\- checkAllBalances.js**

**'-genesis-block.json**

**First smart contract: hello world demo**

![](Images/rId151_edit_140086955040144.png)

**This demo shows:**

**\-Like a simple one Solidity script for one Ethereum Smart Contract can look like.**

**\-Like the Solidity script compiled and into the Ethereum blockchain deployed will.**

**\-Like the Ethereum Smart Contract executed will.**

**In this demo, too, only command line tools are used. On graphical tools will** **further down** **received.**

![](Images/rId152_edit_140086955040336.png)

**Follow the steps outlined below.**

**1.** **All above below** [Basic installations: Geth, Solc, private test Ethereum](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Installation-Geth-Solc-Test-Blockchain) [blockchain](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Installation-Geth-Solc-Test-Blockchain) **The steps described must have been carried out.**

![](Images/rId153_edit_140086955037008.png)

**2.** **Change to your EthereumDemo workspace directory set up above (e.g. \\ MeinWorkspace** \\ EthereumDemo):

![](Images/rId155_edit_140086955039248.png)

**cd \\ MeinWorkspace \\ EthereumDemo**

![](Images/rId156_edit_140086955037264.png)

**3.** **In the src subdirectory, create the** **Solidit** [y-Script](https://solidity.readthedocs.io/) **:**

**Greeter.sol**

![](Images/rId157_edit_140086955037520.png)

**pragma solidity 0-4.19;**

**/ \* Auxiliary class so that the smart contract can be removed after use \* /** **contract mortal {**

**/\* Owner \*/**

**address owner;**

**/ \* Constructor, is called during initialization \* /**

**function Mortal() public {**

**owner = msg.sender;**

**}**

**/ \* Remove the contract \* /**

**function kill () public {**

**if (msg.sender == owner) selfdestruct (owner);**

**}**

**}**

*   **\* Main application class, derived from Mortal \* /** **contract Greeter is Mortal {**

**/ \* Text to be saved \* /**

![](Images/rId158_edit_140086955040464.png)

**string greeting;**

**/ \* Constructor, is called during initialization \* /**

**function Greeter(string \_greeting) public {**

**greeting = \_greeting;**

**}**

**/ \* Main application method, playback of stored text \* /**

**function greet() public constant returns (string) {**

**return greeting;**

**}**

**}**

**This is a slightly expanded version of the demo below** **The** [Greeter.](https://www.ethereum.org/greeter)

[You will](https://www.ethereum.org/greeter) **also find comments on the** **Solidity** **\-Source** [code.](https://solidity.readthedocs.io/)

![](Images/rId160_edit_140086955040528.png)

1.  **Compile the Solidity script:cd \\ MeinWorkspace \\ EthereumDemo**

**solc \\solc -o target --bin --abi --overwrite src / Greeter.sol**

![](Images/rId162_edit_140086955039952.png)

**you target**

![](Images/rId164_edit_140086955039184.png)

**You will get the new "target" directory with four new files:**

![](Images/rId165_edit_140086955038992.png)

**\[\\ MeinWorkspace \\ EthereumDemo\]**

*   **\- priv-geth.log**

*   **\- start-test-Ethereum-Blockchain.bat**

**| - \[private blockchain\]**

*   **'- ...**

*   **\- \[solc\]**

*   **'- ...**

*   **\- \[src\]**

*   **| - checkAllBalances.js**

*   **| - genesis-block.json**

*   **'- Greeter.sol**

**'- \[target\]**

*   **\- Greeter.abi**

*   **\- Greeter.bin**

*   **\- Mortal.abi**

**'-Mortal.bin**

1.  **In order to deploy this compiled Ethereum Smart Contract into the Ethereum blockchain, a JavaScript file is created that begins with the following two commands:**

![](Images/rId166_edit_140086955038480.png)

**var greeterFactory = eth.contract ( {Contents of the file target / Greeter.abi} )var greeterCompiled = "0x" + "{Content of the file target / Greeter.bin}" . . .**

**The two placeholder expressions "{...}" must be replaced by the respective file contents.**

**Under Windows, create the following three files in the src directory, each without the end of line characters:**

**greeterJsTeil1.txt**

![](Images/rId167_edit_140086955038352.png)

**var greeterFactory = eth.contract (**

**greeterJsTeil2.txt**

![](Images/rId168_edit_140086955038864.png)

**)**

**var greeterCompiled = "0x" + "**

**greeterJsTeil3.txt**

![](Images/rId169_edit_140086955040592.png)

**"**

**var \_greeting = "Hello world!"**

**var greeter = greeterFactory.new (\_greeting, {from: eth.accounts \[0\], data:**

**greeterCompiled, gas: 47000000}, function (e, contract) {**

**if (e) {**

**console.log (e);**

**} else {**

**if (! contract.address) {**

**console.log ("Contract transaction send: TransactionHash:" + contract.transactionHash + "waiting to be mined ...");**

**} else {**

**console.log ("Contract mined! Address:" + contract.address);**

**console.log (contract);**

**}**

**}**

**})**

**Then do:**

**copy / B / Y src \\ greeterJsTeil1.txt + target \\ Greeter.abi + src \\ greeterJsTeil2.txt + target \\ Greeter.bin + src \\ greeterJsTeil3.txt src \\ GreeterDeploy.js**

![](Images/rId170_edit_140086955040080.png)

**type src \\ GreeterDeploy.js**

![](Images/rId171_edit_140086948410320.png)

**6th** **Alternatively, you could use the above Solidity source code in the Remix Online Solidity Compiler**

**under** [http://remix.ethereum.o](http://remix.ethereum.org/) **rg** **copy, click "Start to compile" and "Details", and copy the JavaScript under "WEB3DEPLOY" into the file "src \\ GreeterDeploy.js".**

**7\. The project structure now looks like this:**

![](Images/rId173_edit_140086948412752.png)

**\[\\ MeinWorkspace \\ EthereumDemo\]**

*   **\- priv-geth.log**

*   **\- start-test-Ethereum-Blockchain.bat**

**| - \[private blockchain\]**

*   **| - History**

*   **| - \[geth\]**

**||** **'- ...**

*   **'- \[keystore\]**

*   **'- UTC - 2018-01-22T09-50-58 ...**

**| - \[solc\]**

*   **| - msvcp140.dll**

*   **| - solc.exe**

*   **'- soltest.exe**

**| - \[src\]**

*   **| - checkAllBalances.js**

*   **| - genesis-block.json**

*   **'- Greeter.sol**

*   **| - GreeterDeploy.js**

*   **| - greeterJsTeil1.txt**

*   **| - greeterJsTeil2.txt**

*   **| - greeterJsTeil3.txt**

**'- \[target\]**

*   **\- Greeter.abi**

*   **\- Greeter.bin**

*   **\- Mortal.abi**

**'-Mortal.bin**

1.  **Start the test Ethereum blockchain including mining:cd \\ MeinWorkspace \\ EthereumDemo start-test-Ethereum-Blockchain.bat**

![](Images/rId174_edit_140086948409488.png)

**9.** **Execute the following three commands in the Geth JavaScript console and check the result in each case (the two loadScript () response texts come from the GreeterDeploy.js JavaScript code above, and the Greeter.greet () response comes from Smart Contract):**

**personal.unlockAccount(web3.eth.accounts \[0\], "My Ethereum Test Passphrase")**

![](Images/rId175_edit_140086948409424.png)

**true**

![](Images/rId176_edit_140086948411088.png)

**loadScript ('src / GreeterDeploy.js')**

![](Images/rId177_edit_140086948412240.png)

**Contract transaction send: TransactionHash: 0xe194 ... 7dad waiting to be mined ... true**

**. . .**

**Contract mined! Address: 0xcd5e3f508e24fb8424ea38425f3f0c860b52372d**

**Greeter.greet ();**

![](Images/rId178_edit_140086948409936.png)

**"Hello World!"**

**You have successfully executed the Ethereum Smart Contract.**

**10.** **Since the Solidity script has a kill () method, it can be removed from the blockchain as follows:**

**personal.unlockAccount (web3.eth.accounts \[0\], "My Ethereum test passphrase")**

![](Images/rId180_edit_140086948411280.png)

**Greeter.kill.sendTransaction ({from: eth.accounts \[0\]})**

![](Images/rId181_edit_140086948410768.png)

**The control takes place via:eth.getCode (Greeter.address)**

![](Images/rId182_edit_140086948413264.png)

**You receive:**

![](Images/rId183_edit_140086948412304.png)

**"0x"**

![](Images/rId184_edit_140086948409872.png)

**Mini token smart contract: MeinToken demo**

**This demo shows:**

**\-A smart contract for a own token (which could represent its own cryptocurrency), but only in a very simplified version that only clarifies the basic principle.**

**\-A much more complete and extensive ERC20 token demo can be found at:** **Contract TokenERC20** [.](https://www.ethereum.org/token)

![](Images/rId186_edit_140086948411024.png)

**\-The implementation is initially carried out with the command line tools Geth and Solc. Below is the same demo with the graphical tools** **Remix** [Online Solidity IDE and](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Remix-Online-Solidity-Compiler) **Damn** **implemented and used. The** **demo with the**

![](Images/rId187_edit_140086948412496.png)

**Development frameworks** **Truffle** **and** **Embark** **implemented and used.**

![](Images/rId188_edit_140086948410000.png)

**\-First, the smart contract is deployed and executed in its own private blockchain. Further** **belo** [w thi](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Smart-Contract-Rinkeby) **s is done in the public Rinkeby blockchain.**

**Follow the steps outlined below.**

**1.** **All above below** [Basic installations: Geth, Solc, private test Ethereum](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Installation-Geth-Solc-Test-Blockchain) [blockchain](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Installation-Geth-Solc-Test-Blockchain) **The steps described must have been carried out.**

![](Images/rId190_edit_140086948412048.png)

**2.** **Change to your prepared EthereumDemo workspace directory (e.g. \\ M** einWorkspace \\ EthereumDemo **):**

**cd \\ MeinWorkspace \\ EthereumDemo**

![](Images/rId191_edit_140086948410576.png)

**3.** **In the src subdirectory, create the Solidity script:**

**MyToken.sol**

![](Images/rId192_edit_140086948411472.png)

**pragma solidity 0-4.19;**

**contract MyToken {**

**/ \* Map with account addresses and associated account balances \* /** **mapping (address => uint256) public balanceOf;**

**/ \* Constructor, is called during initialization,**

**transfers the initial amount of tokens to the creator of the smart contract \* /** **function MyToken(uint256 initialSupply) public {**

**balanceOf \[msg.sender\] = initialSupply;**

**}**

**/ \* Transfer tokens \* /**

**function transfer(address \_to, uint256 \_value) public {**

**require (msg.sender! = \_to);**

**require (balanceOf \[msg.sender\]> = \_value);**

**require (balanceOf \[\_to\] + \_value> = balanceOf \[\_to\]);**

**balanceOf \[msg.sender\] - = \_value;**

**balanceOf \[\_to\] + = \_value;**

**}**

**}**

**4th** **Create the following three JavaScript fragments in the src subdirectory, each without end-of-line characters.**

**meinTokenJsTeil1.txt**

![](Images/rId193_edit_140086948410896.png)

**var myTokenFactory = eth.contract (**

**meinTokenJsTeil2.txt**

![](Images/rId194_edit_140086948412560.png)

**)**

**var myTokenCompiled = "0x" + "**

**meinTokenJsTeil3.txt**

![](Images/rId195_edit_140086948411792.png)

**"**

**var initialSupply = 888**

**var gasOffer = eth.getBlock ("latest") .gasLimit / 2**

**var MyToken = meinTokenFactory.new (initialSupply, {from: eth.accounts \[0\], data:**

**meinTokenCompiled, gas: gasOffer}, function (e, contract) {**

**if (e) {**

**console.log (e);**

**} else {**

**if (! contract.address) {**

**console.log ("Contract transaction send: TransactionHash:" + contract.transactionHash + "waiting to be mined ...");**

**} else {**

**console.log ("Contract mined! Address:" + contract.address);**

**console.log (contract);**

**}**

**}**

**})**

**5.** **In the EthereumDemo project directory, create the batch file: build-MeinToken.bat**

![](Images/rId196_edit_140086948410832.png)

**solc \\ solc -o target --bin --abi --overwrite src / MeinToken.sol dir target**

**copy / B / Y src \\ meinTokenJsTeil1.txt + target \\ MeinToken.abi + src \\ meinTokenJsTeil2.txt + ^**

**target \\ MeinToken.bin +**

**src \\ MeinTokenJsTeil3.txt src \\ MeinTokenDeploy.js**

**type src \\ MeinTokenDeploy.js**

1.  **Execute the following commands:cd \\ MeinWorkspace \\ EthereumDemo build-MeinToken.bat**

**tree / F**

![](Images/rId197_edit_140086948412624.png)

**7th** **The project structure now looks like this (if you also use the** [above](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Hallo-Welt-Demo) [First smart contract: hello world](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Hallo-Welt-Demo) **demo** **you have a few extra files that don't bother you):**

![](Images/rId199_edit_140086948412880.png)

**\[\\ MeinWorkspace \\ EthereumDemo\]**

*   **\- build-MeinToken.bat**

*   **\- priv-geth.log**

*   **\- start-test-Ethereum-Blockchain.bat**

**| - \[private blockchain\]**

*   **| - History**

*   **| - \[geth\]**

**|**

![](Images/rId201_edit_140086948413200.png)

**|**

**'- ...**

*   **'- \[keystore\]**

*   **'- UTC - 2018-01-22T09-50-58 ...**

**| - \[solc\]**

*   **| - msvcp140.dll**

*   **| - solc.exe**

*   **'- soltest.exe**

**| - \[src\]**

*   **| - checkAllBalances.js**

*   **| - genesis-block.json**

*   **'- MeinToken.sol**

*   **| - MeinTokenDeploy.js**

*   **| - meinTokenJsTeil1.txt**

*   **| - meinTokenJsTeil2.txt**

*   **'- meinTokenJsTeil3.txt**

**'- \[target\]**

*   **\- MeinToken.abi**

**'-MeinToken.bin**

**8\. Start the blockchain:**

**cd \\ MeinWorkspace \\ EthereumDemo start-test-Ethereum-Blockchain.bat**

![](Images/rId202_edit_140086948413328.png)

1.  **Execute in the Geth JavaScript Console (do not execute the individual JavaScript commands too quickly one after the other):**

**// The first account must have ether (you may have to wait for the minig):**

**loadScript ('src / checkAllBalances.js')**

![](Images/rId203_edit_140086948411664.png)

**// Create another account (at least two accounts are required):**

**personal.newAccount ("My Ethereum Test Passphrase"**

![](Images/rId204_edit_140086948409680.png)

## **)**

**web3.eth.accounts**

![](Images/rId205_edit_140086947598416.png)

**// Deploy Smart Contract:**

**personal.unlockAccount (web3.eth.accounts \[0\], "My Ethereum test passphrase")**

![](Images/rId206_edit_140086947598672.png)

**loadScript ('src / MeinTokenDeploy.js')**

![](Images/rId207_edit_140086947598544.png)

*   **Wait until "Contract mined!" appears.**

*   **Define and unlock default account:**

**web3.eth.defaultAccount = web3.eth.accounts \[0\]**

![](Images/rId208_edit_140086947598736.png)

**personal.unlockAccount (web3.eth.defaultAccount, "My Ethereum Test Passphrase")**

![](Images/rId209_edit_140086947598864.png)

**// Check the account balance of the new token (at the beginning: 888/0, see: MeinTokenDeploy.js):**

**MeinToken.balanceOf (web3.eth.accounts \[0\])**

![](Images/rId210_edit_140086947598992.png)

**MeinToken.balanceOf (web3.eth.accounts \[1\])**

![](Images/rId211_edit_140086947599120.png)

**// Execute token transfer (transfer 188 tokens):**

**MeinToken.transfer (web3.eth.accounts \[1\], 188);**

![](Images/rId212_edit_140086947599248.png)

*   **Wait about 30 seconds for mining.**

*   **Check changed account balances (700/188):**

**MeinToken.balanceOf (web3.eth.accounts \[0\]) MeinToken.balanceOf (web3.eth.accounts \[1\])You receive:**

![](Images/rId213_edit_140086947599376.png)

**. . .**

*   **MeinToken.transfer (web3.eth.accounts \[1\], 188); "0xc99b4ebfc87e24c6e77462f8ddf360ab716da385d114b83304479514e19e0f41"**

*   **MeinToken.balanceOf (web3.eth.accounts \[0\])**

**700**

*   **MeinToken.balanceOf (web3.eth.accounts \[1\]) 188**

**You have successfully implemented a smart contract with your own tokens and transferred tokens from one account to another.**

1.  **Execute in the Geth-JavaScript-Console: MyToken.address**

![](Images/rId216_edit_140086947599504.png)

**You have to remember this 40-digit hex address for the demos below. Save the address in the MyToken.address.priv.txt file.**

**11.** **This little mini token demo is of course still missing a lot of functionality for a real token. See this for yourself** **ERC20 token** [example at.](https://www.ethereum.org/token)

![](Images/rId217_edit_140086947599632.png)

**Remix Online Solidity Compiler as a graphical development environment (GUI-IDE)**

**This demo shows:**

![](Images/rId219_edit_140086947599760.jpeg)

**\-Like the above** [Mini token smart contract:](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) [MeinToken demo in](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) **stead of using the** **command line tools Geth and Solc with the graphical**

![](Images/rId220_edit_140086947600080.png)

**Development environment** [Remix Online Solidity Compiler](http://remix.ethereum.org/) **can be realized.**

![](Images/rId221_edit_140086947600016.png)

**\-The web browser-based Remix Online Solidity Compiler can not only compile Solidity code, but also offers syntax highlighting, auto-completion (code completion) and find usages. And it can display syntax errors, create ready-made Web3 JavaScript code for deployment, and even deploy, run and debug Solidity code.**

**See the documentation for** **R** [emix - Solidity IDE a](http://remix.readthedocs.io/) **nd the** **R** [emix Wiki a](https://theethereum.wiki/w/index.php/Remix) **t. The following is the implementation and usage of the above** **Mini t** [oken](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) [demo-Smart](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) **contracts demonstrated.**

**1.** **Your own local test Ethereum blockchain must be installed, if possible similar to the one below** **Basic** [installations: Geth, Solc,](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Installation-Geth-Solc-Test-Blockchain) [private test Ethereum blockchain](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Installation-Geth-Solc-Test-Blockchain) **described.**

![](Images/rId224_edit_140086947600144.png)

1.  **Start the test Ethereum blockchain including mining:cd \\ MeinWorkspace \\ EthereumDemo start-test-Ethereum-Blockchain.bat**

![](Images/rId225_edit_140086947600272.png)

**3.** **Open the Remix Online Solidity Compiler website:**

**http://remix.ethereum.org** [.](http://remix.ethereum.org/)

![](Images/rId226_edit_140086947600400.png)

**4th** **Start a new project by clicking the little plus sign in the upper left corner of the website.**

**For "File Name" enter: MeinToken.sol**

**5.** **In the upper middle empty window titled "browser / MyToken.sol" paste the Solidity script source code from** **MeinToken.sol** [a.](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#MeinToken.sol)

![](Images/rId228_edit_140086947600528.png)

1.  **Click in the top right third on the tab "Compile" and then on the button "Start to compile".**
2.  **Click the Details button to view the compilation results. Under "WEB3DEPLOY" you will find a finished JavaScript program for deploying the MeinToken smart contract. You could execute this JavaScript as shown above with the command line tool Geth in the Geth JavaScript console. In this demo, however, everything is to be carried out via the graphical development environment instead.**

1.  **Connect the Remix Online Solidity Compiler to your own local test Ethereum blockchain:**

**Click in the top right third on the tab "Run", select "Web3 Provider" under Environment, confirm "Are you sure you want to connect to an ethereum node?" and "Web3 Provider Endpoint" "http: // localhost: 8545".**

**9.** **Test the connection:**

**In the lower middle window, at the very bottom next to the ">"**

**sign, enter:**

**web3.eth.accounts**

**You will receive the addresses of your accounts, for example:**

![](Images/rId229_edit_140086947600656.png)

*   **web3.eth.accounts**

**\[**

**"0x4597a26af9991b297b5ccc2a8c0966e9a1a17035",**

**"0x63d7d5b64dc9cc0744dedf87971f8b0777d7e226"**

**\]**

**10.** **Deploy your MeinToken smart contract to the local blockchain:**

**In the lower middle window, at the very bottom next to the ">"**

**sign, enter:**

**web3.personal.unlockAccount (web3.eth.accounts \[0\], "My Ethereum test passphrase")**

**Then enter an initial token amount for "uint256 initialSupply" in the middle part of the right window, for example 888, and click the "Create" button next to it. For example, you will receive:**

![](Images/rId230_edit_140086947600784.png)

*   **web3.personal.unlockAccount (web3.eth.accounts \[0\], "My Ethereum test passphrase") true**

**creation of MeinToken pending ...**

**\[block: 2532 txIndex: 0\] from: 0x459 ... 17035, to: MeinToken. (constructor), value: 0 wei, 0 logs, data: 0x606 ...**

**00378, hash: 0xc25 ... c86b1**

**The MeinToken smart contract has been successfully deployed in the local blockchain.**

**11.** **Query the token account balance for your first two account addresses determined with web3.eth.accounts:**

**Enter the two account addresses one after the other in the right third next to the "balanceOf" button under "address" and press the "balanceOf" button in each case. Make sure that you enter the hex addresses preceded by "0x" and enclosed in quotation marks, for example as follows:**

**"0x4597a26af9991b297b5ccc2a8c0966e9a1a17035"**

**You will get 888 and 0.**

**12th** **Use the MeinToken smart contract to transfer tokens:**

**In the lower middle window, at the very bottom next to the ">"**

**sign, enter:**

**web3.personal.unlockAccount (web3.eth.accounts \[0\], "My Ethereum test passphrase")**

**Then enter in the right third next to the "transfer" button**

**for "address \_to, uint256 \_value" the second account address (again including quotation marks) and an amount, for example like this:**

**"0x63d7d5b64dc9cc0744dedf87971f8b0777d7e226", 111 Press the "transfer" button and wait a little for the mining.**

1.  **Check the token account balances of the two accounts again using the "balanceOf" button:**

**You get 777 and 111.**

**Tokens were successfully transferred between accounts in the MeinToken smart contract.**

![](Images/rId231_edit_140086947600912.jpeg)

**Perform a MeinToken transfer with the GUI tool Mist**

**This demo shows:**

![](Images/rId233_edit_140086947601232.jpeg)

**\-Like the GUI tool instead of the command line tool geth** [Dam](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html#Mist) **n can be used.**

**\-How crap interacts with its own Ethereum blockchain.**

**\-Like crap the smart contract deployed in the example above "** [MeinToken.so](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#MeinToken.sol) **l** **"How its transfer method is called and how the account balances of the implemented token are queried can be used.**

**For example, information on the Ethereum client Mist can be found at:** **Ethereum Mist W** [iki at GitHub, Ethereum Mist at G](https://github.com/ethereum/mist/wiki) **it** [Hub, Using Mist Ethereum](https://github.com/ethereum/mist/) [Wallet,](http://www.ethdocs.org/en/latest/account-management.html#using-mist-ethereum-wallet) [Getting Started w](http://www.ethdocs.org/en/latest/account-management.html#using-mist-ethereum-wallet) **ith** [Ethereum Mist Wallet.](https://medium.com/@attores/step-by-step-guide-getting-started-with-ethereum-mist-wallet-772a3cc99af4)

![](Images/rId239_edit_140086947601360.png)

**Follow the steps outlined below.**

**1.** **If you haven't installed Mist yet: Download from** **Ethereum Wallet and Mist Cliente Lige** [ro (GitHub) the installation file suitable for](https://github.com/ethereum/mist/releases) [your](https://github.com/ethereum/mist/releases) **operating system, e.g. for Windows: Mist-installer-0-9-3.exe. Run the installation file.**

![](Images/rId242_edit_140086947601296.png)

**2.** **All above below** [Mini token smart contract: MeinToken demo The](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) [steps](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) **described must have been carried out, your Ethereum blockchain must be active, and the MeinToken smart contract must** **deployed** **be.**

![](Images/rId243_edit_140086947601424.png)

**3\. If you haven't already, start the test Ethereum blockchain:**

**cd \\ MeinWorkspace \\ EthereumDemo start-test-Ethereum-Blockchain.bat**

![](Images/rId245_edit_140086947601552.png)

1.  **Execute in the Geth JavaScript Console: web3.eth.accounts**

![](Images/rId246_edit_140086947601680.png)

**You will receive the hex addresses of the two accounts. You will need these addresses below.**

1.  **Start crap. Make sure crap has connected to your own test Ethereum blockchain.**

1.  **Click on "Wallets" in the upper left corner.**

**The steadily increasing account balance in ether is displayed at the top right. Below you will find the two accounts you have set up under "Accounts overview". If you click on an individual account, the respective 40-digit account address is displayed.**

**You can set up additional accounts under "Add account".**

**7th** **Click on "Contracts" in the upper right corner.**

**Under "Publish new contracts" you can create and deploy another smart contract.**

**To use the smart contract that has already been deployed, click under "Own contracts" on "Monitor contracts". An input dialog appears. Enter:**

**\- Contract address: The address in the** ["MeinToken.address.priv.txt" file](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#MeinToken.address)

![](Images/rId248_edit_140086947601808.png)

**stored address of the smart contract,**

*   **Contract name: MeinToken,**

*   **JSON interface: The content of the file**

**"EthereumDemo \\ target \\ MeinToken.abi".**

1.  **Your Smart Contract "MyToken" is displayed under "My Contracts".**

**Under "Read contract" / "Balance of" you can query the account balance of the implemented token: Enter one of the two account addresses: You will receive the last account balance, i.e. 700 or 188 tokens.**

**Under "Write in contract" select the "Transfer" method under "Select function". Two input fields appear for the two parameters of the transfer method:**

*   **to address: Enter the account address of the second account here** **a,**
*   **value: Here you enter the number of tokens to be transferred, e.g.** **111**

**Click on "Run". A dialogue follows in which after the**

**Password is asked: Enter "My Ethereum Test Passphrase" and press "Send Transaction".**

**Ask again under "Read contract" / "Balance of" the two token account balances: You will receive the changed values 589 and 299.**

**The smart contract transaction was executed successfully.**

![](Images/rId249_edit_140086947601936.jpeg)

**DApp website for the smart contract with Node.js**

**This demo shows:**

![](Images/rId251_edit_140086947602256.jpeg)

**\-As a** **DApp** [(Decentralized Application) can](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html#DApp) **be created which the above Ethereum Smart Contract** [MyToken](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) **used.**

**\-How to do this with a website** [Node.js i](https://nodejs.org/) **s created.**

**The following versions are used:**

**\-git 2.16.1**

**\-Node.js 9.6.1**

**\-npm 5.6.0**

**\-web3 0.20.4**

**\-Windows 10**

**Watch the documentary git, np** [m, N](https://docs.npmjs.com/) **o** [de.js an](https://nodejs.org/en/docs/) **d we** [b3.js at](https://web3js.readthedocs.io/en/1.0/index.html) **.**

![](Images/rId257_edit_140086947602384.png)

**If you are using newer versions than those mentioned above, you may receive error messages about missing web3.min.js. In this case, please refer to the website:** **web3.min.js** [is missing.](https://ethereum.stackexchange.com/questions/67604/web3-min-js-is-missing-in-node-modules-web3-dist)

![](Images/rId259_edit_140086946886288.png)

**Follow the steps outlined below.**

**1.** **All above below** [Mini token smart contract: MeinToken](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) [demo](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) **The steps described must have been carried out.**

![](Images/rId260_edit_140086946886544.png)

**2.** **Change to your workspace directory (e.g. \\ Mein** Workspace) and **create a new project directory parallel to the EthereumDemo project directory:**

**cd \\ MyWorkspace**

![](Images/rId261_edit_140086946886416.png)

**mkdir EthNodejsDApp**

![](Images/rId262_edit_140086946886608.png)

**cd EthNodejsDApp**

![](Images/rId263_edit_140086946886736.png)

**3.** **You need the most up-to-date version of** **Git** **. If you don't have Git installed, or if your Git version is not up-to-date enough, download from** **https://git-scm.** [com/download/ the installatio](https://git-scm.com/download/) **n file suitable for your operating system, e.g. for Windows Git-2.16.1-64-bit.exe, and use it to carry out the installation of Git. Check the installation with:**

![](Images/rId265_edit_140086946886864.png)

**git --version**

![](Images/rId266_edit_140086946886992.png)

**git --help**

![](Images/rId267_edit_140086946887120.png)

**4th** **You need a current version of** **Node.js** [.](https://nodejs.org/) **Download** **from** **https:// nod** [ejs.org the install](https://nodejs.org/) **ation file suitable for your operating system, e.g. for Windows node-v9.6.1-x64.msi, and use it to install Node.js. Check the installation with:**

![](Images/rId268_edit_140086946887248.png)

**node -v**

![](Images/rId269_edit_140086946887376.png)

**node -h**

![](Images/rId270_edit_140086946887504.png)

**npm -v**

![](Images/rId271_edit_140086946887632.png)

**npm -h**

**5.** **Switch to your new EthNodejsDApp project directory and initiate a Node.js project:**

**cd \\ MeinWorkspace \\ EthNodejsDApp**

![](Images/rId272_edit_140086946887760.png)

**npm install web3@0.20.4**

![](Images/rId273_edit_140086946887888.png)

**npm install ethereum / web3.js npm**

![](Images/rId274_edit_140086946888016.png)

**init**

![](Images/rId275_edit_140086946888144.png)

**npm list**

![](Images/rId276_edit_140086946888272.png)

**type package.json**

![](Images/rId277_edit_140086946888400.png)

**dir node\_modules \\ web3 \\ dist \\ web3.min.js**

![](Images/rId278_edit_140086946888528.png)

**6th** **In the EthNodejsDApp project directory, create the DApp HTML file:**

**MeinTokenDAppWebseite.html**

![](Images/rId279_edit_140086946888656.png)

**<html>**

**<head>**

**<title> MeinToken-Smart-Contract-DApp </title>**

**<meta http-equiv = "content-type" content = "text / html; charset = utf-8"> <style> \* {font-family: sans-serif; } </style>**

**<script type = "text / javascript" src = "./ node\_modules / web3 / dist /web3.min.js"> </script> <script type = "text / javascript">**

**// Enter the address of the deployed MeinToken smart contract here:**

![](Images/rId280_edit_140086946888784.png)

**const contractAddress = "0xf07a9248ac043cf039a6f76113b78f89d483b2c8 ";** **// Enter the content of the target \\ MeinToken.abi file here:**

**const abi = '\[{"constant ": true," inputs ": \[{" name ":" ","**

**type ":" address "}\]," name ":" balanceOf ", \\**

**"outputs":**

**\[{"name": "", "type": "uint256"}\], "payable": false, "stateMutability": "view", "type": "function"}, \\**

**{"constant": false, "inputs": \[{"name": "\_ to", "type": "address"},**

**{"name": "\_ value", "type": "uint256"}\], \\**

**"name": "transfer", "outputs":**

**\[\], "payable": false, "stateMutability": "nonpayable", "type": "function"}, \\**

**{"inputs":**

**\[{"name": "initialSupply", "type": "uint256"}\], "payable": false, "stateMutability": "nonpayabl e", \\**

**"type": "constructor"}\] ';**

**const Web3 = require ('web3');**

**const web3 = new Web3 (new Web3.providers.HttpProvider ('http: // localhost: 8545')**

**);**

**const myTokenContract = web3.eth.contract (JSON.parse (abi));**

**const myTokenContractInstance = meinTokenContract.at (contractAddress); const account0 = web3.eth.accounts \[0\]; const account1 = web3.eth.accounts \[1\];**

**web3.eth.defaultAccount = web3.eth.accounts \[0\];**

**function myTokenGetBalanceOf () {**

**try {**

**var balanceOf0 = myTokenContractInstance.balanceOf (account0); var balanceOf1 = myTokenContractInstance.balanceOf (account1);**

**document.getElementById ('account0'). innerText = "Account 0 (" + account0**

**\+ "): balanceOf:" + balanceOf0;**

**document.getElementById ('account1'). innerText = "Account 1 (" + account1**

*   **"): balanceOf:" + balanceOf1; } catch (e) {**

**document.write ("<br/> <b> Error:" + e.message + "</b>");**

**}**

**}**

**function myTokenTransfer () {**

**var amount** **\= document.MyForm.Amount.value;**

**var passphrase = document.MyForm.passphrase.value;**

**if (null == amount|| "" == amount**

**) {alert ("Amount missing!"**

**);**

**return false; }**

**if (null == passphrase || "" == passphrase) {alert ("Passphrase missing!");**

**return false; }**

**var message = "Transfer starts with amount" + amount + "."; document.getElementById ('message'). innerText = message;**

**try {**

![](Images/rId281_edit_140086946888912.png)

**if (passphrase! = "-") {web3.personal.unlockAccount (account0,**

**passphrase); }**

**myTokenContractInstance.transfer (account1, amount); if (passphrase! = "-") {web3.personal.lockAccount (account0); }**

**message + = "\\ nWait about 30 seconds for mining, then press F5**

**refresh. "**

**document.getElementById ('message'). innerText = message; alert (message);**

**} catch (e) {**

**document.write ("<br/> <b> Error:" + e.message + "</b>");**

**}**

**}**

**</script>**

**</head>**

**<body bgcolor = "# EEFFEE" onload = "meinTokenGetBalanceOf ()"> <h1>DApp website for the MeinToken smart contract</h1> <div id = "account0"> </div>**

**<div id = "account1"> </div> <br/>**

**<form name = "MyForm" method = "post" onSubmit = "myTokenTransfer ()">**

**Amount:<input type = "text" name = "amount"** **size = "10" maxlength = "10">**

**Passphrase: <input type = "text" name = "passphrase" size = "45" maxlength = "42"> <input type = "submit" value = "start transfer">**

**</form>**

**<div id = "message"> </div>**

**</body>**

**</html>**

**With "const contractAddress = ..." you have to enter the address o** [f the MeinToken smart co](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#MeinToken.address) **ntract saved in the file "MeinToken.address.priv.txt".**

**7\. The project structure now looks like this:**

![](Images/rId282_edit_140086946889040.png)

**\[\\ MyWorkspace\]**

**| - \[EthereumDemo\]**

*   **'- ...**

**'- \[EthNodejsDApp\]**

*   **\- MeinTokenDAppWebseite.html**

*   **\- package-lock.json**

*   **\- package.json**

**'- \[node\_modules\]**

**'- ...**

**8\. If you haven't already, start the test Ethereum blockchain:**

**cd \\ MeinWorkspace \\ EthereumDemo start-test-Ethereum-Blockchain.bat**

![](Images/rId283_edit_140086946889168.png)

**9\. Open the DApp website:**

**cd \\ MeinWorkspace \\ EthNodejsDApp start** MeinTokenDAppWebseite.htmlFor **example, you will receive:**

![](Images/rId285_edit_140086946889296.png)

1.  **Make a note of the current account balance, enter an amount of tokens to be transferred and the passphrase "My Ethereum test passphrase", and click the "Start transfer" button. Wait long enough for the transaction to be added to the blockchain via mining. Then refresh the website, in most web browsers with F5 or with Ctrl + R. You will see the account balances changed by the amount entered.**

![](Images/rId288_edit_140086946889424.png)

**Transfer of Ether with Web3j and Java**

**This demo shows:**

![](Images/rId289_edit_140086946889552.jpeg)

**\-How to interact with the Ethereum blockchain using Java.**

**\-How to set up a Maven project with the integration of Web3j.**

**\-How ethers can be transferred with the Java program.**

**The following versions are used:**

**\-Java JDK 9**

**\-Maven 3.5.0**

**\-geth 1.8.2**

**\-Web3j 3.3.1**

**\-Windows 10**

**Look at yourself: Java, JD** [K 9, M](https://www.java.com/de/about/whatis_java.jsp) **a** [ven, We](http://www.oracle.com/technetwork/java/javase/downloads/jdk9-downloads-3848520.html) **b** [3j projec](https://www.torsten-horn.de/techdocs/maven.htm) **t** **,** [Web3j documenta](https://web3j.io/) **ti** [on, Web3j docu](https://docs.web3j.io/) **m** [entation.](https://web3j.readthedocs.io/)

![](Images/rId296_edit_140086946885712.png)

**Follow the steps outlined below.**

**1.** **An actual** **JDK** [9 and](http://www.oracle.com/technetwork/java/javase/downloads/jdk9-downloads-3848520.html) **a current one Ma** [ven m](https://www.torsten-horn.de/techdocs/maven.htm) **ust be installed.**

![](Images/rId297_edit_140086946886224.png)

**2.** **A Java IDE such as** **JetBrains Intelli** [J IDEA or Eclipse is not absolutely](https://www.torsten-horn.de/techdocs/IntelliJ-IDEA.html) **necessary,** [but](https://www.torsten-horn.de/techdocs/java-eclipse.htm) **simplifies the development process enormously.**

![](Images/rId300_edit_140086946885776.png)

**3.** **Change to your workspace directory (e.g. \\ Mein** Workspace) and **execute the following commands:**

**cd \\ MyWorkspace**

![](Images/rId302_edit_140086946885904.png)

**mkdir EthJavaDApp**

![](Images/rId303_edit_140086955606992.png)

**cd EthJavaDApp**

![](Images/rId304_edit_140086955609424.png)

**md src \\ main \\ java \\ de \\ mycompany \\ myproject tree /**

**F**

![](Images/rId305_edit_140086949166928.png)

**4th** **In the EthJavaDApp project directory, create the** **Maven** [\-](https://www.torsten-horn.de/techdocs/maven.htm) **configuration file:**

![](Images/rId306_edit_140086949166864.png)

**pom.xml**

![](Images/rId307_edit_140086949167056.png)

**<project xmlns = "http://maven.apache.org/POM/4.0.0" xmlns: xsi = "http://www.w3.org/2001/XMLSchema-instance"**

**xsi: schemaLocation = "http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd ">**

**<modelVersion> 4.0.0 </modelVersion>**

**<groupId> de.mycompany.myproject </groupId>**

**<artifactId>EthJavaDApp</artifactId>**

**<version> 1.0-SNAPSHOT </version>**

**<packaging> jar </packaging>**

**<name> EthJavaDApp </name>**

**<properties>**

**<project.build.sourceEncoding> ISO-8859-1 </project.build.sourceEncoding>**

**</properties>**

**<build>**

**<plugins>**

**<plugin>**

**<groupId> org.apache.maven.plugins </groupId>**

**<artifactId> maven-compiler-plugin </artifactId>**

**<version> 3.7.0 </version>**

**<configuration>**

**<source> 1.8 </source>**

**<target> 1.8 </target>**

**</configuration>**

**</plugin>**

**</plugins>**

**</build>**

![](Images/rId308_edit_140086949163600.png)

**<dependencies>**

**<dependency>**

**<groupId>org.web3j</groupId>**

**<artifactId>core</artifactId>**

**<version> 3.3.1 </version>**

**</dependency>**

**</dependencies>**

**</project>**

**5.** **Create the Java class in the src \\ main \\ java \\ de \\ mycompany \\ myproject subdirectory:**

**EtherTransfer.java**

![](Images/rId309_edit_140086949166800.png)

**package de.mycompany.myproject;**

**import org.web3j.protocol.Web3j; import**

**org.web3j.protocol.admin.Admin;**

**import org.web3j.protocol.admin.methods.response.PersonalUnlockAccount; import org.web3j.protocol.core.DefaultBlockParameterName; import org.web3j.protocol.core.methods.request.Transaction;**

**import org.web3j.protocol.core.methods.response.EthGetTransactionCount; import**

**org.web3j.protocol.core.methods.response.EthSendTransaction; import**

**org.web3j.protocol.core.methods.response.TransactionReceipt; import**

**org.web3j.protocol.http.HttpService;**

**import org.web3j.tx.Contract;**

**import org.web3j.tx.ManagedTransaction; import**

**org.web3j.utils.Convert;**

**import java.math.BigInteger; import**

**java.util.Optional;**

**public class EtherTransfer{**

**public static void Main(String \[\] args) throws exception**

**{**

**// Extend the program so that parameters are read out or transferred:**

**transfer ether("http: // localhost: 8545",**

*   **Enter the addresses of the two accounts here (result of:**

**web3.eth.accounts):**

**"0x4597a26af9991b297b5ccc2a8c0966e9a1a17035",**

**"0x63d7d5b64dc9cc0744dedf87971f8b0777d7e226",**

*   **Enter the amount to be transferred and the passphrase here:** **"10", "My Ethereum Test Passphrase");**

**}**

**public static void transfer ether(**

![](Images/rId310_edit_140086949163984.png)

**String ethereumUrl, String senderAdresse, String receiverAddress, String amountEther, String passphrase)**

**throws exception**

**{**

**Admin admin = Admin.build (new HttpService (ethereumUrl));**

**PersonalUnlockAccount personalUnlockAccount =**

**admin.personalUnlockAccount(senderaddress, passphrase) .send ();**

**if (! personalUnlockAccount.accountUnlocked ()) {**

**System.out.println ("\\ nError: Account unlock failed.");**

**return;**

**}**

**Web3j web3j = Web3j.build (new HttpService (ethereumUrl)); EthGetTransactionCount txCount = web3j.ethGetTransactionCount (**

**senderAdresse, DefaultBlockParameterName.LATEST) .sendAsync (). get (); BigInteger nonce = txCount.getTransactionCount ();**

**BigInteger amount = Convert.toWei (amountEther, Convert.Unit.ETHER) .toBigInteger ();**

**Transaction transaction = Transaction.createEtherTransaction (**

**senderAdresse, nonce, ManagedTransaction.GAS\_PRICE, Contract.GAS\_LIMIT, recipient address, amount);**

**EthSendTransaction response = web3j.ethSendTransaction(transaction) .sendAsync (). get ();**

**if (response.hasError ()) {**

**System.out.println ("\\ nError:" + response.getError (). GetMessage ()); return;**

**}**

**String txHash = response.getTransactionHash ();**

**System.out.print ("\\ nTxHash:" + txHash + "\\ nWaiting for mining"); for (int i = 0; i <600; i ++) {**

**Optional <TransactionReceipt> transactionReceipt =**

**web3j.ethGetTransactionReceipt (txHash) .send (). getTransactionReceipt (); if (transactionReceipt.isPresent ()) {**

**System.out.println ("\\ nTransfer of" + amountEther + "Ether completed, amount of gas used: "+**

**transactionReceipt.get (). getGasUsed ());**

**return;**

**}**

**System.out.print (".");**

**Thread.sleep (1000);**

**}**

**System.out.println ("\\ nThe transfer could not be completed within 10 minutes. Is mining active?");**

**}**

**}**

![](Images/rId311_edit_140086949166992.png)

**In the main () method, replace the addresses of the two accounts with yours.**

**6th** **Compile EtherTransfer.java:cd \\**

**MeinWorkspace \\ EthJavaDApp mvn**

![](Images/rId312_edit_140086949847248.png)

**clean package**

![](Images/rId313_edit_140086949847952.png)

**The Java program is compilable and Web3j has been successfully integrated.**

**7\. The project structure now looks like this:**

![](Images/rId314_edit_140086949849808.png)

**\[\\ MyWorkspace \\ EthJavaDApp\]**

*   **\- pom.xml**

**| - \[src\]**

*   **'- \[main\]**

*   **'- \[java\]**

*   **'- \[de\]**

**|**

**|**

**|**

**'- \[my company\]**

**'- \[my project\]**

**'- EtherTransfer.java**

**'- \[target\]**

*   **\- EthJavaDApp-1.0-SNAPSHOT.jar**

**'- ...**

**8th.** **All above below** [Basic installations: Geth, Solc, private test](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Installation-Geth-Solc-Test-Blockchain) [Ethereum](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Installation-Geth-Solc-Test-Blockchain) **blockchain** **The steps described must have been carried out.**

![](Images/rId315_edit_140086949848528.png)

1.  **Start the test Ethereum blockchain:cd \\ MeinWorkspace \\ EthereumDemo start-test-Ethereum-Blockchain.bat**

![](Images/rId316_edit_140086949848464.png)

**Query the accounts and ether account balances in the Geth JavaScript console:**

**loadScript ('src / checkAllBalances.js')**

![](Images/rId317_edit_140086949848336.png)

**There must be at least two accounts. If there is only one, create another, like** **above** **described.**

![](Images/rId318_edit_140086949848976.png)

**10\. Now there are three options:**

**\-The most sensible variant is, at least during the development phase, an IDE (e.g.** [IntelliJ IDEA](https://www.torsten-horn.de/techdocs/IntelliJ-IDEA.html) **or** **E** [clipse)](https://www.torsten-horn.de/techdocs/java-eclipse.htm) **where you open and run the project.**

![](Images/rId319_edit_140086949848080.png)

**\-Alternatively, you can extend the pom.xml with the assembly plug-in, as described under:** **Executable** [jar file included](https://www.torsten-horn.de/techdocs/maven.htm#MvnJarMitLibs)

![](Images/rId321_edit_140086949848720.png)

[Dependencies with the assembly plugin.](https://www.torsten-horn.de/techdocs/maven.htm#MvnJarMitLibs)

![](Images/rId322_edit_140086949849168.png)

**Then you can run the generated jar file directly.**

**\-A third possibility would be to copy all required jar libs into a subdirectory, add this directory to the classpath, and with it the**

**run the compiled EtherTransfer.class.**

**11.** **Run the EtherTransfer program. For example, you will receive:**

![](Images/rId323_edit_140086949850384.png)

**TxHash: 0xdc96314d6443c81d86c7a4afc6413b2b4127fee739b9bb7ae607ef7267bad417 Waiting**

**for mining ........................................ Transfer of 10 Ether completed, amount of gas used: 21000**

**Check the ether account balances with your wallet application or in the Geth JavaScript con** [sole with loadScript ('src / checkAllBa](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#checkAllBalances.js) **lances.js').**

**10 ethers were successfully transferred from one account to another.**

![](Images/rId325_edit_140086949851024.png)

**Transfer of your own smart contract tokens with Web3j and Java**

**This demo shows:**

![](Images/rId326_edit_140086949849552.jpeg)

**\-How to use Java to interact with a smart contract on the Ethereum blockchain.**

**\-How a Java interface class is automatically generated from the smart contract definition files.**

**\-How your own smart contract tokens can be transferred with a Java program.**

**\-This example creates a Java command line application. Below under** **DApp website for the smar** [t contract with Java a corresponding DApp](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Java-DApp-Webseite) **website is created.**

![](Images/rId327_edit_140086949847824.png)

**The one shown above is used as a smart contract** [MeinToken](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) [smart co](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) **ntract** **used.**

![](Images/rId328_edit_140086949850128.png)

**Follow the steps outlined below.**

**1.** **Both all above below** **M** [einToken smart contract a](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) **s well as all under** [Transfer of Ether with Web3j and Java](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#EtherWeb3jDemo) **The steps described must have been carried out.**

**2.** **To create the Java interface class to interact with the smart contract, the** **Web3j command** [line tool needed. Download](https://docs.web3j.io/command_line.html) **web3j-**

**3.3.1.zip from** [https://github.com/web3j/web3j/relea](https://github.com/web3j/web3j/releases) **ses** **. Unzip this file into the subdirectory web3j-3.3.1 in your EthJavaDApp project directory. Check the installation with:**

**cd \\ MeinWorkspace \\ EthJavaDApp**

![](Images/rId331_edit_140086949848912.png)

**web3j-3.3.1 \\ bin \\ web3j.bat version**

![](Images/rId332_edit_140086949848144.png)

**web3j-3.3.1 \\ bin \\ web3j.bat solidity**

![](Images/rId333_edit_140086949850576.png)

**3.** **The following commands assume that the** **MeinToken** [smart](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) [contract in the](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo)

![](Images/rId334_edit_140086949849232.png)

**Project directory \\ MeinWorkspace \\ EthereumDemo was created parallel to the current project directory \\ MeinWorkspace \\ EthJavaDApp. If this is different for you, you have to adapt the paths. Do:**

**cd \\ MyWorkspace \\ EthJavaDApp**

![](Images/rId335_edit_140086949848016.png)

**web3j-3.3.1 \\ bin \\web3j.bat solidity generate .. \\EthereumDemo \\ target \\MeinToken.bin .. \\Ethe reumDemo \\ target \\MeinToken.abi -o src \\ main \\ java -p de.mycompany.myproject**

![](Images/rId336_edit_140086949849360.png)

**dir src \\ main \\ java \\ de \\ mycompany \\ myprojectThe new Java class MeinToken.java was generated.**

![](Images/rId337_edit_140086949847760.png)

**4th** **Create the Java class in the src \\ main \\ java \\ de \\ mycompany \\ myproject subdirectory:**

**MeinTokenTransfer.java**

![](Images/rId338_edit_140086949847120.png)

**package de.mycompany.myproject;**

**import org.web3j.crypto.CipherException; import**

**org.web3j.crypto.Credentials; import**

**org.web3j.crypto.WalletUtils; import**

**org.web3j.protocol.Web3j;**

**import org.web3j.protocol.core.RemoteCall;**

**import org.web3j.protocol.core.methods.response.TransactionReceipt; import**

**org.web3j.protocol.http.HttpService;**

**import org.web3j.tx.Contract;**

**import org.web3j.tx.ManagedTransaction; import**

**java.io. \*;**

**import java.math.BigInteger; import**

**java.util. \*;**

**import java.util.concurrent.CompletableFuture;**

**public class MyTokenTransfer{**

![](Images/rId339_edit_140086949848592.png)

*   **Here is the address of the MeinToken smart contract in the blockchain**

*   **and enter either the passphrase or the private key:**

**public static final String DEFAULT\_CONTRACT\_ADRESSE** **\=**

**"0xf07a9248ac043cf039a6f76113b78f89d483b2c8";**

**public static final String DEFAULT\_PASSPHRASE\_OR\_PRIVKEY = "My Ethereum Test Passphrase";**

**public static final String DEFAULT\_ETHEREUM\_URL public static final List <String> DEFAULT\_KEYSTORE\_DIRS "../EthereumDemo/Private-Blockchain/keystore", "../EthereumDemo/Rinkeby-Blockchain/keystore");**

**\= "http: // localhost: 8545"; = Arrays.asList (**

**public static void Main(String \[\] args) throws exception**

**{**

**if (args.length <1) {**

**System.out.println ("\\ nThe following parameters can be transferred:\\ n "+**

*   **Number of tokens to be transferred \\ n "+**

*   **Passphrase or Private Key \\ n "+**

*   **Sender account address \\ n "+**

*   **Recipient account address \\ n "+**

*   **MyToken-Contract-Address \\ n "+**

*   **Keystore directory \\ n "+**

*   **Ethereum Blockchain URL \\ n ");**

**}**

**String amountStr** **\= (args.length> 0)? args \[0\]: "0";**

**String pssPhrOrPrvK = (args.length> 1)? args \[1\]:**

**DEFAULT\_PASSPHRASE\_OR\_PRIVKEY;**

**String contractAdr** **\= (args.length> 4)? args \[4\]: DEFAULT\_CONTRACT\_ADRESSE;**

**String keystoreDir** **\= (args.length> 5)? args \[5\]: "";**

**String ethereumUrl** **\= (args.length> 6)? args \[6\]: DEFAULT\_ETHEREUM\_URL;**

**List <String> accounts = determineAccounts(ethereumUrl);**

**String sender address** **\= (args.length> 2)? args \[2\]: accounts.get (0);**

**String receiver address = (args.length> 3)? args \[3\]: accounts.get (1);**

**System.out.println ("Accounts:** **"+ accounts);**

**List <String> keystoreDirs = new ArrayList <> ();**

**keystoreDirs.add (keystoreDir);**

**keystoreDirs.addAll (DEFAULT\_KEYSTORE\_DIRS);**

**MyToken myToken = null;**

**List <BigInteger> account balances = null;**

**try {**

![](Images/rId340_edit_140086949849616.png)

**myToken = initMyToken(ethereumUrl, contractAdr, senderAdresse, pssPhrOrPrvK, keystoreDirs);**

**account balances = read account balances(my token, sender address, recipient address);**

**System.out.println ("Account balances:" + account balances.get (0) + "/" + kontostaende.get (1));**

**} catch (exception ex) {**

**System.out.println ("Error when querying the MeinToken Smart Contract."**

**+**

**"Are contract address and passphrase or private**

**Key correct? ");**

**ex.printStackTrace ();**

**return;**

**}**

**long amount = Long.parseLong (amountStr);**

**if (amount> 0) {**

**System.out.println (amount + "tokens are transferred, approx. 30 seconds wait for mining ... ");**

**account balances = transfer tokens(my token, sender address, recipient address, amount, 180);**

**System.out.println ("Account balances:" + account balances.get (0) + "/" + kontostaende.get (1));**

**}**

**}**

**public static List <String> determineAccounts(String ethereumUrl) throws IOException**

**{**

**Web3j web3j = Web3j.build (new HttpService (ethereumUrl)); return web3j.ethAccounts (). send (). getAccounts ();**

**}**

**public static MyToken initMyToken(String ethereumUrl, String myTokenContractAdresse,**

**String account, String**

**passphraseOrPrivateKey, List <String> keystoreDirs)**

**{**

**Web3j web3j = Web3j.build (new HttpService (ethereumUrl));**

**Credentials credentials = null;**

**try {**

**credentials = getCredentialsFromKeystore (account, passphraseOrPrivateKey,**

**keystoreDirs);**

**} catch (exception ex1) { try {**

**credentials = Credentials.create (passphraseOrPrivateKey);**

**} catch (exception ex2) {**

![](Images/rId341_edit_140086949850832.png)

**throw new RuntimeException (ex1);**

**}**

**}**

**returnMeinToken.load(**

**myTokenContractAdresse, web3j, credentials, ManagedTransaction.GAS\_PRICE, Contract.GAS\_LIMIT);**

**}**

**public static List <BigInteger> read account balances(**

**MeinToken myToken, String senderAddress, String recipientAddress) throws**

**Exception**

**{**

**List <BigInteger> account balances = new ArrayList <> ();**

**kontostaende.add ( myToken.balanceOf(sender address ). send ()); kontostaende.add ( myToken.balanceOf(recipient address) .send ()); return account balances;**

**}**

**public static List <BigInteger> transfer tokens(**

**MeinToken meinToken, String senderAdresse, String receiverAddress, long amount, int timeoutSec)**

**throws exception**

**{**

**if (amount> 0) {**

**RemoteCall <TransactionReceipt> rc = myToken.transfer(recipient address, BigInteger.valueOf (amount));**

**CompletableFuture <TransactionReceipt> txFuture = rc.sendAsync (); for (int i = 0; i <timeoutSek; i ++) {**

**if (txFuture.isDone ()) {break; }**

**System.out.print (".");**

**Thread.sleep (1000);**

**}**

**if (timeoutSek> 0) {System.out.println (""); }**

**if (txFuture.isCompletedExceptionally () || txFuture.isCancelled ()) {**

**throw new Exception ("MyToken transfer failed:" + txFuture.get (). getStatus ());**

**}**

**if (! txFuture.isDone () && timeoutSek> 0) {**

**throw new Exception ("The MeinToken transfer could not be done within"**

**\+ timeoutSek +**

**"Seconds to be completed. Is mining**

**active? ");**

**}**

**if (txFuture.isDone ()) {**

**TransactionReceipt txReceipt = txFuture.get ();**

![](Images/rId342_edit_140086949849104.png)

**System.out.println ("MeinToken transfer successful, GasUsed:" + txReceipt.getGasUsed () +**

**", BlockNumber:" + txReceipt.getBlockNumber () + ", TxHash:" + txReceipt.getTransactionHash ());**

**}**

**}**

**return read account balance (my token, sender address, recipient address);**

**}**

**private static credentials getCredentialsFromKeystore(String account, String passphrase, List <String> keystoreDirs)**

**throws IOException, CipherException**

**{**

**File \[\] ksDateien = null;**

**for (String ksDir: keystoreDirs) {**

**ksDateien = new File (ksDir) .listFiles (f -> f.isFile () && f.getName (). contains (account.substring (2)));**

**if (ksDateien! = null && ksDateien.length! = 0) {**

**break;**

**}**

**}**

**if (ksDateien == null || ksDateien.length == 0) {**

**throw new IOException (**

**"Error: No keystore file matching the account" + account + "in the keystore directories "+**

**keystoreDirs + "found." );**

**}**

**return WalletUtils.loadCredentials (passphrase, ksFiles \[0\]);**

**}**

**}**

**Do you wear**

**Enter the values from your blockchain for**

**DEFAULT\_PASSPHRASE\_OR\_PRIVKEY and keystoreDirs, and**

**at DEFAULT\_CONTRACT\_ADRESSE the**

**Sm** [art contract address store](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#MeinToken.address) **d in MeinToken.address.priv.txt.**

**5\. The two project structures now look like this:**

![](Images/rId343_edit_140086949849744.png)

**\[\\ MeinWorkspace \\ EthereumDemo\]**

*   **\- build-MeinToken.bat**

*   **\- MeinToken.address.priv.txt**

*   **\- priv-geth.log**

*   **\- start-test-Ethereum-Blockchain.bat**

**| - \[private blockchain\]**

*   **| - History** ![](Images/rId344_edit_140086949848656.png)

*   **| - \[geth\]**

**||** **'- ...**

*   **'- \[keystore\]**

*   **| - UTC - 2018-01-26T18-36-00 ...**

*   **'- UTC - 2018-01-26T18-37-34 ...**

**| - \[solc\]**

*   **'- ...**

*   **\- \[src\]**

*   **'- ...**

**'- \[target\]**

**| - MeinToken.abi**

**\[\\ MyWorkspace \\ EthJavaDApp\]**

*   **\- pom.xml**

**| - \[src\]**

*   **'- \[main\]**

*   **'- \[java\]**

*   **'- \[de\]**

| **|** || **'- \[my company\]** |
| --- | --- |
| **|** || **'- \[my project\]** |
| **|** || **| -** || **EtherTransfer.java** |
| **|** || **| -** || **MyToken.java** |
| **|** || **'-** || **MeinTokenTransfer.java** |
| **| - \[target\]** ||  |
| **|** || **'- ...** ||  |
| **'- \[web3j-3.3.1\]** ||  |
|  || **| - \[am\]** ||  |

*   **'- web3j**

*   **'- web3j.bat**

**'- \[lib\]**

**'- ...**

1.  **Compile the Java classes:cd \\ MeinWorkspace \\ EthJavaDApp mvn clean package**

![](Images/rId345_edit_140086954838992.png)

**7th** **To run the MeinTokenTransfer Java class, there are three again** **above** [mentioned](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#EtherWeb3jDemo-Java-ausfuehren) **possibilities.**

![](Images/rId348_edit_140086954836368.png)

**8th.** **If you run MeinTokenTransfer without command line parameters, a text appears that lists the possible parameters and the two account addresses.**

**If you call up MeinTokenTransfer with:**

**0 "My Ethereum Test Passphrase"**

**you will then receive the two account addresses and their MeinToken account balances.**

**If you call up MeinTokenTransfer with:**

**10 "My Ethereum test passphrase" you will then receive for example:**

![](Images/rId349_edit_140086954838352.png)

**Accounts: \[0x4597a26af9991b297b5ccc2a8c0966e9a1a17035, 0x63d7d5b64dc9cc0744dedf87971f8b0777d7e226\]**

**Account balance: 828/60**

**10 tokens are transferred, wait approx. 30 seconds for mining ...**

**...............................**

**MeinToken transfer successful, GasUsed: 33924, BlockNumber: 3390, TxHash:**

**0xae0d815da94ef13354dfc8 ...**

**Account balance: 818/70**

**Wait a while for the mining and check the account balances again.**

**10 MeinTokens were successfully transferred from one account to another.**

**9\. If you get the following error message:**

**org.web3j.protocol.exceptions.TransactionException: Error processing**

**request: unknown transaction**

**Then you are probably using an awkward combination of Geth and Web3j. For example, with combinations of Geth 1.8.0 to 1.8.1 with Web3j 3.2.0 to 3.3.1 there is this error. See also:**

**Web3j** [Issue 318.](https://github.com/web3j/web3j/issues/318)

![](Images/rId350_edit_140086954838736.png)

**Use Geth either in version 1.7.3 or in at least version 1.8.2 to avoid the error.**

![](Images/rId351_edit_140086954837200.png)

**DApp website for the smart contract with Java**

**This demo shows:**

![](Images/rId352_edit_140086954836816.jpeg)

**\-As a** **DApp** [(Decentralized Application) can](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html#DApp) **be created which the above Ethereum Smart Contract** [MyToken](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) **used.**

**\-How to do this with a website** [Java](https://www.java.com/de/about/whatis_java.jsp) **and** [JSP i](http://www.oracle.com/technetwork/java/javaee/jsp/index.html) **s created.**

**\-Like a Maven web project with the integration of** **We** [b3j an](https://web3j.io/) **d using the** **Jetty w** [eb server can be](https://www.eclipse.org/jetty/) **put on.**

**\-How your own smart contract tokens can be transferred with the Java DApp website.**

**Used this demo** **JSP (Jav** [aServer Pages) to keep t](http://www.oracle.com/technetwork/java/javaee/jsp/index.html) **he example short. In serious applications, other web frameworks that can be used with Java are more likely to be used, such as** **JSF** **,** **Spring MVC** [or](https://www.torsten-horn.de/techdocs/jsf.htm) **An** [gular.](https://www.torsten-horn.de/techdocs/Spring-DI-AOP.html#Spring-MVC-Demo)

![](Images/rId357_edit_140086954837456.png)

**As a smart contract, the one shown above is used again** [MeinToken](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) [smart co](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) **ntract** **used.**

![](Images/rId360_edit_140086954838544.png)

**Follow the steps outlined below.**

**1.** **The under** [Transfer of your own smart contract tokens with Web3j](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#MeinTokenWeb3jDemo) [and](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#MeinTokenWeb3jDemo) **Java** **The steps described must have been carried out.**

![](Images/rId361_edit_140086954839760.png)

**2.** **In the EthJavaDApp project directory, replace the contents of the**

**Maven project configuration file:**

**pom.xml**

![](Images/rId362_edit_140086954838416.png)

**<project xmlns = "http://maven.apache.org/POM/4.0.0" xmlns: xsi = "http://www.w3.org/2001/XMLSchema-instance"**

**xsi: schemaLocation = "http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd ">**

**<modelVersion> 4.0.0 </modelVersion>**

**<groupId> de.mycompany.myproject </groupId>**

**<artifactId>EthJavaDApp</artifactId>**

**<version> 1.0-SNAPSHOT </version>**

**<packaging> was </packaging>**

**<name> EthJavaDApp </name>**

**<properties>**

**<project.build.sourceEncoding> ISO-8859-1 </project.build.sourceEncoding>**

**</properties>**

**<build>**

**<plugins>**

**<plugin>**

**<groupId> org.apache.maven.plugins </groupId>**

**<artifactId> maven-compiler-plugin </artifactId>**

**<version> 3.7.0 </version>**

**<configuration>**

**<source> 1.8 </source>**

**<target> 1.8 </target>**

**</configuration>**

**</plugin>**

**<plugin>**

**<groupId> org.eclipse.jetty </groupId>**

**<artifactId>jetty-maven-plugin</artifactId>**

**<version> 9.4.8.v20171121 </version>**

![](Images/rId363_edit_140086954836944.png)

**<configuration>**

**<webAppConfig>**

**<contextPath> /$ {project.artifactId} </contextPath>**

**</webAppConfig>**

**</configuration>**

**</plugin>**

**</plugins>**

**</build>**

**<dependencies>**

**<dependency>**

**<groupId>org.web3j</groupId>**

**<artifactId>core</artifactId>**

**<version> 3.3.1 </version>**

**</dependency>**

**</dependencies>**

**</project>**

1.  **Create the additional webapp directory:cd \\ MeinWorkspace \\ EthJavaDApp mkdir src \\ main \\ webapp \\ WEB-INF**

![](Images/rId364_edit_140086954838672.png)

**4th** **Create the webapp configuration file in the src \\ main \\ webapp \\**

**WEB-INF directory:**

**web.xml**

![](Images/rId365_edit_140086954839696.png)

**<? xml version = "1.0" encoding = "UTF-8"?>**

**<web-app xmlns = "http://xmlns.jcp.org/xml/ns/javaee"**

**xmlns: xsi = "http://www.w3.org/2001/XMLSchema-instance"**

**xsi: schemaLocation = "http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app\_3\_1.xsd "**

**version = "3.1">**

**<display-name> MeinToken-Smart-Contract-DApp (EthJavaDApp) </display-name> </web-app>**

**5.** **In the src \\ main \\ webapp directory, create the JSP file:**

**index.jsp**

![](Images/rId366_edit_140086954836176.png)

**<% @ page import = "java.math.BigInteger"%> <% @**

**page import = "java.util. \*"%>**

**<% @ page import = "de.mycompany.myproject. \*"%>**

**<%**

**String ethereumUrl = MyTokenTransfer.DEFAULT\_ETHEREUM\_URL;** **long** **newTimestamp = (new Date ()). getTime ();**

![](Images/rId367_edit_140086954837072.png)

**List <String> accounts = MeinTokenTransfer.ermittleAccounts(ethereumUrl);**

**String contract** **\= request.getParameter ("contract");**

**String account0** **\= request.getParameter ("account0");**

**String account1** **\= request.getParameter ("account1");**

**String password** **\= request.getParameter ("password");**

**String amount** **\= request.getParameter ("amount"**

**String timestamp = request.getParameter ("timestamp");**

**);**

**if (contract == null || contract.isEmpty ()) {contract =**

**MeinTokenTransfer.DEFAULT\_CONTRACT\_ADRESSE; }**

**if (account0 == null || account0.isEmpty ()) {account0 = accounts.get (0); } if (account1 == null || account1.isEmpty ()) {account1 = accounts.get (1); } if (password == null || password.isEmpty ()) {password =**

**MyTokenTransfer.DEFAULT\_PASSPHRASE\_OR\_PRIVKEY; }**

**if (amount== null || amount.isEmpty ()** **) {amount = ""; }**

**MyToken myToken = null;**

**List <BigInteger> account balances = null;**

**try {**

**myToken = MyTokenTransfer.initMyToken(**

**ethereumUrl, contract, account0, password,**

**MeinTokenTransfer.DEFAULT\_KEYSTORE\_DIRS);**

**account balances = MeinTokenTransfer.lies account balances(myToken, account0, account1);**

**} catch (exception ex) {**

**out.println ("\\ n <br> <font color = 'red'> Error when querying the MeinToken Smart Contract." +**

**"Are contract address and passphrase or private key**

**correct? <br> \\ n "+**

**ex.getMessage () + "</font> <br> <br> \\ n");**

**account status = new ArrayList <BigInteger> ();**

**kontostaende.add (BigInteger.valueOf (-1));**

**kontostaende.add (BigInteger.valueOf (-1));**

**}**

**if (meinToken! = null &&! amount.isEmpty () && ("" + timestamp) .equals (session.getAttribute ("timestamp"))) {**

**try {**

**long betr = Long.parseLong (amount);**

**if (betr> 0) {**

**System.out.println ("transfer" + betr + "Tokens from" + account0 +**

**"to" + account1);**

**account balances = MyTokenTransfer.transferTokens(myToken, account0, account1, betr, 180);**

**}**

![](Images/rId368_edit_140086954837328.png)

**} catch (exception ex) {**

**out.println ("\\ n <br> <font color = 'red'> Error during MeinToken transfer." +**

**"Is the passphrase or private key correct?**

**<br> \\ n "+ ex.getMessage () +" </font> <br> <br> \\ n ");**

**}**

**}**

**session.setAttribute ("timestamp", "" + newTimestamp);**

**%>**

**<html>**

**<head>**

**<title> MeinToken-Smart-Contract-DApp </title>**

**<meta http-equiv = "content-type" content = "text / html; charset = utf-8"> <style> \* {font-family: sans-serif; } </style> </head>**

**<body bgcolor = "# EEEEFF">**

**<h2>DApp website for the MeinToken Smart Contract with Java</h2>**

**<form name = "myForm" method = "post"**

**onSubmit = "alert ('Press OK, wait about 30 seconds for mining and then refresh with F5.')">**

**<table border = 0 cellspacing = 9 cellpadding = 0> <tr>**

**<td valign = "top">Contract:</td>**

**<td> <input type = "text" name = "contract" value = '<% = contract%>' size = '45 'maxlength = '42'> <br> </td>**

**</tr>**

**<tr>**

**<td valign = "top">Account0:</td>**

**<td> <input type = "text" name = "account0" value = '<% = account0%>' size = '45 'maxlength = '42'>:**

**<input type = "text" value = '<% = kontostaende.get (0)%>' size = '12 'maxlength = '10' readonly> MyToken <br>**

**<input type = "text" name = "password" value = '<% = password%>' size = '45 'maxlength = '66'> <br> </td>**

**</tr>**

**<tr>**

**<td valign = "top">Account1:</td>**

**<td> <input type = "text" name = "account1" value = '<% = account1%>' size = '45 'maxlength = '42'>:**

**<input type = "text"** **value = '<% = kontostaende.get (1)%>' size = '12 'maxlength = '10'**

**readonly> MyToken <br> </td>**

**</tr>**

**<tr>**

**<td valign = "top">Amount:</td>**

**<td> <input type = "text"**

![](Images/rId369_edit_140086954839824.png)

**name = "amount"value = '<% = amount%>' size = '12 '**

**maxlength = '10 '>**

**<input type = "submit" name = "calculate"** **value = "start transfer"> <br>**

**<input type = "hidden" name = "timestamp" value = '<% = "" + newTimestamp%>'> </td>**

**</tr>**

**</table>**

**</form>**

**</body>**

**</html>**

**Check the values entered** [in MeinTokenTransfer.j](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#EtherWeb3jDemo-MeinTokenTransfer.java) **ava above**

**for DEFAULT\_CONTRACT\_ADRESSE, DEFAULT\_PASSPHRASE\_OR \_PRIVKEY and DEFAULT\_KEYSTORE\_DIRS.**

**6\. The project structure now looks like this:**

![](Images/rId371_edit_140086954838608.png)

**\[\\ MyWorkspace \\ EthJavaDApp\]**

*   **\- pom.xml**

**| - \[src\]**

*   **'- \[main\]**

*   **| - \[java\]**

| **|** || **|** || **'- \[de\]** ||  |
| --- | --- | --- | --- |
| **|** || **|** || **'- \[my company\]** |
| **|** || **|** || **'- \[my project\]** |
| **|** || **|** || **| -** || **EtherTransfer.java** |
| **|** || **|** || **| -** || **MyToken.java** |
| **|** || **|** || **'-** || **MeinTokenTransfer.java** |

*   **'- \[webapp\]**

*   **'- index.jsp**

*   **'- \[WEB-INF\]**

**|'- web.xml**

**| - \[target\]**

**|'- ...**

**'- \[web3j-3.3.1\]**

**| - \[am\]**

*   **'- web3j**

*   **'- web3j.bat**

**'- \[lib\]**

**'- ...**

1.  **If you haven't already, start the test Ethereum blockchain: cd \\ MeinWorkspace \\ EthereumDemo**

![](Images/rId372_edit_140086954838288.png)

**start-test-Ethereum-Blockchain.bat**

![](Images/rId373_edit_140086954839248.png)

1.  **Start the Jetty web server with the EthJavaDApp web application:**

**cd \\ MeinWorkspace \\ EthJavaDApp**

![](Images/rId374_edit_140086955147536.png)

**mvn jetty: run-war**

![](Images/rId375_edit_140086955148368.png)

**Wait a while for "Started Jetty Server" to appear. Go to the website:**

**begin** **http:** [// localhost: 8080 / EthJavaDApp](http://localhost:8080/EthJavaDApp)

![](Images/rId377_edit_140086955148560.png)

1.  **Make a note of the current account balance, enter the desired account address, the passphrase or the private key and the amount of tokens to be transferred, and press the "start transfer" button. Wait long enough for the transaction to be added to the blockchain via mining. Then refresh the website, in most web browsers with F5 or with Ctrl + R. You will see the account balances changed by the amount entered.**

**10.** **If you swap the two account addresses, you can also transfer in the other direction. The prerequisite for this is that the account from which the tokens are transferred has enough Ether to pay the transaction fees, for example by using** **Transfer of Ether with Web3j and Java** **transfer a few ethers.**

![](Images/rId378_edit_140086955149840.png)

**11\. For example, you will receive:**

![](Images/rId380_edit_140086955149520.jpeg)

**Public Rinkeby Test Ethereum blockchain instead of private blockchain**

**This demo shows:**

![](Images/rId382_edit_140086955148752.jpeg)

**\-How to create a synchronized copy of the Rinkeby Test Ethereum public blockchain on your PC.**

**\-How to create a new account in the public Rinkeby-Test-Ethereum-Blockchain.**

**\-How to transfer ether to this account.**

**\-How you can query the account balance via the Etherscan Internet service and thus show that your newly created account also exists on third-party Ethereum nodes and is publicly available.**

**The previous demos used a private Ethereum blockchain that only existed on your own PC. This example uses the public Rinkeby-Test Ethereum blockchain.**

**Follow the steps outlined below.**

**1.** **If you have already created the EthereumDemo project directory in the previous demos, switch to this directory. Otherwise create it:**

**cd \\ MyWorkspace**

![](Images/rId383_edit_140086960358288.png)

**mkdir EthereumDemo**

![](Images/rId384_edit_140086959708944.png)

**cd EthereumDemo**

![](Images/rId385_edit_140086959709328.png)

**mkdir src**

![](Images/rId386_edit_140086959708240.png)

**tree / F**

![](Images/rId387_edit_140086947659536.png)

**2.** **Start script:**

**Create the batch file in the EthereumDemo project directory start-Rinkeby-Ethereum-Blockchain.bat with the following content (in one line):**

**geth --rinkeby --networkid 4 --datadir "Rinkeby-Blockchain" --rpc --rpcapi**

![](Images/rId388_edit_140086947659344.png)

**"db, eth, net, web3, personal, txpool" --rpccorsdomain "\*" console 2 >> rinkeby-geth.log**

![](Images/rId389_edit_140086947659600.png)

**3.Start of the Rinkeby-Test-Ethereum-Blockchain:cd \\ MeinWorkspace \\ EthereumDemo start-Rinkeby-Ethereum-Blockchain.bat**

![](Images/rId390_edit_140086947659728.png)

**You get the Geth-JavaScript-Console, in which you can enter Geth-JavaScript commands.**

1.  **First make sure in a second command line window that you are operating the desired test Ethereum blockchain (and not the real Ethereum blockchain):**

**cd \\ MeinWorkspace \\ EthereumDemo type rinkeby-geth.log**

![](Images/rId391_edit_140086947659280.png)

**Approximately on the sixth line, a message similar to:**

![](Images/rId393_edit_140086947655824.png)

**INFO \[02-02 | 16: 17: 18\] Initializing Ethereum protocolnetwork = 4** **versions = "\[63 62\]"**

**The network number is important: for Rinkeby it must be 4.**

**5.** **You can also check the network number in the Geth JavaScript console:**

**admin.nodeInfo**

![](Images/rId394_edit_140086947655952.png)

1.  **When the local Rinkeby blockchain is started for the first time, it can take hours until the entire blockchain is synchronized with the local PC. You can observe this in the log file.**

**7th** **Script to query the account balances:In case you don't already like** **above** **suggested that you** [have](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#checkAllBalances.js) **created the file checkAllBalances.js in the src directory, create it.**

![](Images/rId395_edit_140086947656080.png)

**8th.Create Account:**

**Switch back to the window with the Geth JavaScript console. Create an account (think of a more difficult password and remember it well):**

**web3.eth.accounts**

![](Images/rId396_edit_140086947656208.png)

**personal.newAccount ("My Ethereum Test Passphrase"**

![](Images/rId397_edit_140086947656336.png)

## **)**

**web3.eth.accounts**

![](Images/rId398_edit_140086947656464.png)

**9.Query account balances:**

**You can now check your account balances. In the Geth-**

**JavaScript-Console run:**

**loadScript ('src / checkAllBalances.js')You receive:**

![](Images/rId399_edit_140086947656592.png)

**0x39bbbe004272e72dba0c13a0e60443cfcceead3c:balance: 0 ether**

**10.Checking the keystore file and the directory structure:Do:**

**to you** \\ MeinWorkspace \\ EthereumDemo \\ Rinkeby- Blockchain \\ keystore

![](Images/rId402_edit_140086947656720.png)

**There is the** **Keystore** [file, for examp](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html#Keystore) **le:**

![](Images/rId404_edit_140086947656848.png)

**UTC - 2018-02-02T16-17-18.123456789Z - 39bbbe004272e72dba0c13a0e60443cfcceead3c**

1.  **The project structure now looks like this (depending on which examples you have carried out, there can be more or fewer files):**

![](Images/rId405_edit_140086947656976.png)

**\[\\ MeinWorkspace \\ EthereumDemo\]**

*   **\- build-MeinToken.bat**

*   **\- MeinToken.address.priv.txt**

*   **\- priv-geth.log**

*   **\- rinkeby-geth.log**

**| - start-Rinkeby-Ethereum-Blockchain.bat**

*   **\- start-test-Ethereum-Blockchain.bat** ![](Images/rId406_edit_140086947657104.png)

**| - \[private blockchain\]**

*   **'- ...**

**| - \[Rinkeby blockchain\]**

*   **| - \[geth\]**

| **|** || **|** || **| - \[chaindata\]** |
| --- | --- | --- |
| **|** || **|** || **|** || **'- ...** |
| **|** || **|** || **'- ...** ||  |

*   **'- \[keystore\]**

*   **'- UTC - 2018-02-02T16-17-18 ...**

**| - \[solc\]**

*   **'- ...**

*   **\- \[src\]**

*   **| - checkAllBalances.js**

*   **| - genesis-block.json**

*   **| - MeinToken.sol**

*   **| - MeinTokenDeploy.js**

*   **| - meinTokenJsTeil1.txt**

*   **| - meinTokenJsTeil2.txt**

*   **'- meinTokenJsTeil3.txt**

**'- \[target\]**

*   **\- MeinToken.abi**

**'-MeinToken.bin**

**The Rinkeby-Blockchain \\ geth \\ chaindata directory contains the Rinkeby-Blockchain data and is several gigabytes in size after complete synchronization.**

**12th** **Transfer ether to the account:**

**Since this is a test blockchain, the ethers in this blockchain are**

**worthless. Nevertheless, you need ether on your test account if you**

**want to carry out further experiments. Under** **https://**

**faucet.** [rinkeby.io you will fin](https://faucet.rinkeby.io/) **d instructions for this: You need a "Social**

**network URL" from Facebook, Google Plus or Twitter. For example,**

**on Google Plus, in the window "What's new for you?" Enter your**

**account address (preceded by "0x") (eg:**

**0x39bbbe004272e72dba0c13a0e60443cfcceead3c) and click on**

**"\[public\] post". Then open the post in its own window and copy the**

**URL that is then displayed in the web browser, for example:**

**"https: //plus.google.com/1016 ... / posts / ZZLx ...". Please include this URL** [https://faucet.rinkeby.io](https://faucet.rinkeby.io/) **and select on the right next to "Give me Ether": "3 Ethers / 8 hours". You will receive the confirmation "Funding**

**request accepted ". Then wait about 1 minute for mining.**

**13th** **Since the Rinkeby-Ethereum-Blockchain is a public blockchain, you can query the account balance with the public Etherscan internet service via:** **https://rinkeby.etherscan.io/address/** [{my account](https://rinkeby.etherscan.io/address/0x39bbbe004272e72dba0c13a0e60443cfcceead3c) [address} (replace "{my ac](https://rinkeby.etherscan.io/address/0x39bbbe004272e72dba0c13a0e60443cfcceead3c) **count address}" with your account address).**

![](Images/rId409_edit_140086947657232.png)

1.  **Determine the account balances again via the Geth JavaScript console:**

**loadScript ('src / checkAllBalances.js')You receive:**

![](Images/rId410_edit_140086947657360.png)

**0x39bbbe004272e72dba0c13a0e60443cfcceead3c:balance: 3 ethers**

**15th** **View information and statistics about Rinkeby at:**

**https://www.rinkeby.io** [.](https://www.rinkeby.io/)

![](Images/rId413_edit_140086947657488.png)

**Deploy smart contract in the public Rinkeby blockchain**

**This demo shows:**

**\-How you can deploy your own smart contract in the public Rinkeby blockchain.**

**\-How you can execute your own smart contract on the Rinkeby blockchain.**

**The one shown above is used as a smart contract** [MeinToken](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) [smart co](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) **ntract** **used.**

![](Images/rId415_edit_140086947657616.png)

**Follow the steps outlined below.**

**1.** **All above below** [Public Rinkeby Test Ethereum blockchain instead of](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Rinkeby) [private blockchain](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Rinkeby) **The steps described must have been carried out.**

![](Images/rId416_edit_140086947657744.png)

**2.** **All of the above in the example** [MeinToken Smart](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) [Contr](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) **act Demo** **files described are required.**

![](Images/rId417_edit_140086947657872.png)

1.  **Execute the following commands:cd \\ MeinWorkspace \\ EthereumDemo build-MeinToken.bat**

![](Images/rId418_edit_140086947658000.png)

**4th** **If you haven't already done so, start with the** **ab** [ove](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#starte-Rinkeby-Ethereum-Blockchain.bat) **Batch file created the Rinkeby-Test-Ethereum-Blockchain:**

**cd \\ MeinWorkspace \\ EthereumDemo start-Rinkeby-Ethereum-Blockchain.bat**

![](Images/rId420_edit_140086947658128.png)

**You will likely have to wait for the blockchain to sync.**

1.  **Your own account must have Ether: web3.eth.accounts**

**loadScript ('src / checkAllBalances.js')**

1.  **Deploy the MeinToken smart contract:**

![](Images/rId421_edit_140086947658256.png)

**personal.unlockAccount (web3.eth.accounts \[0\], "My Ethereum test passphrase")**

![](Images/rId423_edit_140086947658384.png)

**loadScript ('src / MeinTokenDeploy.js')You receive:**

![](Images/rId424_edit_140086947658512.png)

**Contract transaction send: TransactionHash: 0x5759 ... waiting to be mined ...**

**And after maybe 30 seconds:**

![](Images/rId425_edit_140086947658640.png)

**Contract mined! Address: 0xf07a9248ac043cf039a6f76113b78f89d483b2c8**

1.  **If you get either of the following two error messages:Error: exceeds block gas limit**

**Error: Contract transaction couldn't be found after 50 blocks**

![](Images/rId426_edit_140086947658768.png)

**Then there is usually something wrong with the amount of gas offered. Neither too little nor too much gas may be offered. Adjust the variable gasOffer in the**

**Scripts src / MeinTokenJsTeil3.txt or src / MeinTokenDeploy.js are suitable. If you do not want to calculate the exact value yet, you can use "eth.getBlock ('latest') .gasLimit / 2" in the first step.**

**8th.** **Check the assignment in the rinkeby-geth.log log file. A line similar to:**

 
| **INFO \[02-02 | 12: 13: 14\] Submitted contract creation contract =** || **fullhash = 0x5759 ...** |
| --- | --- |
| **0xF07a ...** ||  |
|  ||  |

1.  **Request the address of the deployed smart contract: MyToken.address**

![](Images/rId428_edit_140086947658896.png)

**You have to remember this 40-digit hex address. Save the address in the MyToken.address.Rinkeby.txt file.**

1.  **Carry out a transfer of MeinToken with the deployed smart contract. If you don't already have one, create a second account beforehand. Check that at least the first account**

**has ether. Read the MeinToken account balances before and after the transfer.**

**personal.newAccount ("My Ethereum Test Passphrase"**

![](Images/rId429_edit_140086947659024.png)

## **)**

**web3.eth.accounts**

![](Images/rId430_edit_140086947978448.png)

**loadScript ('src / checkAllBalances.js')**

![](Images/rId431_edit_140086947978256.png)

**web3.eth.defaultAccount = web3.eth.accounts \[0\]**

![](Images/rId432_edit_140086947978512.png)

**personal.unlockAccount (web3.eth.defaultAccount, "My Ethereum Test Passphrase")**

![](Images/rId433_edit_140086947978640.png)

**MeinToken.balanceOf (web3.eth.accounts \[0\])**

![](Images/rId434_edit_140086947978768.png)

**MeinToken.balanceOf (web3.eth.accounts \[1\])**

![](Images/rId435_edit_140086947978896.png)

**MeinToken.transfer (web3.eth.accounts \[1\], 19);**

![](Images/rId436_edit_140086947979024.png)

**// Wait about 30 seconds for mining.**

**MeinToken.balanceOf (web3.eth.accounts \[0\])**

![](Images/rId437_edit_140086947979152.png)

**MeinToken.balanceOf (web3.eth.accounts \[1\])**

![](Images/rId438_edit_140086947978128.png)

**// Check that the ether balance on your account has been reduced by a small amount:**

**loadScript ('src / checkAllBalances.js')**

![](Images/rId439_edit_140086947975248.png)

**11.** **You can also track your transactions via the public Etherscan internet service:** **https://r** [inkeby.etherscan.io/address/ ZonenMeine-](https://rinkeby.etherscan.io/address/0x39bbbe004272e72dba0c13a0e60443cfcceead3c) [Account-Adresse}](https://rinkeby.etherscan.io/address/0x39bbbe004272e72dba0c13a0e60443cfcceead3c) **(replace "{my account address}" with your account address).**

**12th** **With the one below** **Analysis** [of the blocks and](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Analyse-Bloecke-Transaktionen) [transactions d](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Analyse-Bloecke-Transaktionen) **escribed blocks reading**

![](Images/rId440_edit_140086947975376.png)

**JavaScript getTransactionsByAccount () you can also track the transactions in the Rinkeby blockchain. Pass in your account address as a parameter so that you don't have to search under too many other blocks.**

![](Images/rId441_edit_140086947975504.png)

**DApp website for the smart contract in the Rinkeby blockchain**

**This demo shows:**

**\-How you can use the smart contract in the Rinkeby blockchain with the DApp websites implemented above for Node.js and for Java.**

**1.** **All above below** [Deploy smart contract in the public Rinkeby](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Smart-Contract-Rinkeby) [blockcha](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Smart-Contract-Rinkeby) **in** **The steps described must have been carried out.**

![](Images/rId442_edit_140086947975632.png)

**2.** [DApp website for the smart contract with Node.js:](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Node.js-DApp-Webseite)

![](Images/rId443_edit_140086947975760.png)

**Replace in the Node.js-DApp-**

**Website EthNodejsDApp / MeinTokenDAppWebseite.html in the line const contractAddress = "0x ..."; the address of the MeinToken smart contract with the new address from the Rinkeby blockchain (stored in MeinToken.address.Rinkeby.txt).**

**Start the Node.js DApp website:cd \\ MeinWorkspace \\ EthNodejsDApp start**

![](Images/rId444_edit_140086947975888.png)

MeinTokenDAppWebseite.html

![](Images/rId445_edit_140086947976016.png)

**You can transfer MeinToken amounts as usual:**

![](Images/rId446_edit_140086947976144.jpeg)

**3.** [DApp website for the smart contract with Java:](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Java-DApp-Webseite)

![](Images/rId447_edit_140086947976464.png)

**You can choose the new address of the MeinToken smart contract from the Rinkeby blockchain and the passphrase of the first account either in the Java**

![](Images/rId448_edit_140086947976400.jpeg)

**Source code MeinTokenTransfer.java in**

**EthJavaDApp \\ src \\ main \\ java \\ de \\ mycompany \\ myproject directory in the two lines**

**public static final String DEFAULT\_CONTRACT\_ADRESSE = "0x ..."; public static final String DEFAULT\_PASSPHRASE\_OR\_PRIVKEY = "...";**

**or, alternatively, enter it on the website at runtime.**

**With the blockchain running, start the Jetty web server with the**

**EthJavaDApp web application:**

**cd \\ MeinWorkspace \\ EthJavaDApp**

![](Images/rId449_edit_140086947976720.png)

**mvn jetty: run-war**

![](Images/rId450_edit_140086947976656.png)

**Wait a while for "Started Jetty Server" to appear. Go to the website:**

**begin** **http:** [// localhost: 8080 / EthJavaDApp](http://localhost:8080/EthJavaDApp) **You can transfer MeinToken amounts as usual:**

![](Images/rId451_edit_140086947976784.png)

**Truffle for easy development and quick testing**

![](Images/rId453_edit_140086947976912.png)

**This demo shows:**

![](Images/rId454_edit_140086947977040.jpeg)

**\-Like you that** [Truffle development framework t](http://truffleframework.com/) **o install.**

**\-How you can create, deploy and execute your own Ethereum Smart Contracts with Truffle.**

**\-Like you with truffle and the** [Ganache test blockchain](https://github.com/trufflesuite/ganache-cli) **very fast** [Tests in JavaScript](http://truffleframework.com/docs/getting_started/javascript-tests) **can create.**

![](Images/rId458_edit_140086947977360.png)

**\-Please note: This demo uses only a small fraction of the many features of Truffle.**

**\-Look at the** **Truffle do** [cumentary a](http://truffleframework.com/docs/) **t.**

**\-Truffle competes with the one presented below** **Embark** [.](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Embark)

![](Images/rId460_edit_140086947977296.png)

**The following versions are used:**

**\-nvm 0.33.8**

**\-npm 5.6.0**

**\-node 9.5.0**

**\-Solidity 0.4.19**

**\-truffle 4.0.6**

**\-ganache-cli 6.0.3**

**\-Ubuntu 04/16/3 LTS**

**\-Windows 10 version 1709**

**Truffle can be used with Linux, Windows, and Mac. Since the installation and use under Linux is a little easier than under Windows, Truffle is described in the following under Windows, but in the bash of** **WSL (Window** [s Subsystem for Linux) used. If you](https://www.torsten-horn.de/techdocs/WSL.html) **w** **ork directly under** **Linux (e.g. Ubuntu), you can simply skip the first steps.**

![](Images/rId462_edit_140086947977424.jpeg)

**1.** **If you haven't already, install** **WSL (Window** [s Subsystem for](https://docs.microsoft.com/en-us/windows/wsl/install-win10) [Linux). The prerequis](https://docs.microsoft.com/en-us/windows/wsl/install-win10) **ite for this is Windows 10 in at least version 1709. Call up the version query with:**

**winver**

![](Images/rId464_edit_140086947977744.png)

**2.** **Change to your workspace directory (e.g. \\ Mein** Workspace) and **execute the following commands:**

**cd \\ MyWorkspace**

![](Images/rId465_edit_140086947977680.png)

**mkdir EthTruffle**

![](Images/rId466_edit_140086947977808.png)

**cd EthTruffle**

![](Images/rId467_edit_140086947977936.png)

1.  **Start the WSL-Bash, execute the following commands for control and orientation, and update your Linux:**

## **bash**

![](Images/rId468_edit_140086953964432.png)

**MyName @ MyPC : / mnt / d / MyWorkspace / EthTruffle $**

**cat / etc / issue**

![](Images/rId469_edit_140086953965776.png)

**Ubuntu 16.04.3 LTS \\ n \\ l**

## **pwd**

![](Images/rId471_edit_140086953964496.png)

**/ mnt / d / MyWorkspace / EthTruffle**

**sudo apt-get update -y && sudo apt-get upgrade -y**

![](Images/rId472_edit_140086953967376.png)

**4th** **Install the** **Node Version Manager** [nvm, Node.js,](https://github.com/creationix/nvm)

![](Images/rId474_edit_140086953967440.png)

[Truf](https://github.com/creationix/nvm) **fl** [e and G](https://nodejs.org/) **a** [nache](http://truffleframework.com/docs/getting_started/project) **CLI** **:**

![](Images/rId476_edit_140086953964304.png)

**curl -o-**

![](Images/rId477_edit_140086949248016.png)

**https://raw.githubusercontent.com/creationix/nvm/v0.3**

![](Images/rId478_edit_140086949248784.png)

**3.8 / install.sh | bash**

![](Images/rId479_edit_140086949246864.png)

**exec bash**

![](Images/rId480_edit_140086949246992.png)

**nvm --version**

![](Images/rId481_edit_140086949247120.png)

**nvm --help**

![](Images/rId482_edit_140086949247248.png)

**nvm ls**

![](Images/rId483_edit_140086949247376.png)

**nvm install node**

![](Images/rId484_edit_140086949247504.png)

**node -v**

![](Images/rId485_edit_140086949247632.png)

**npm -v**

![](Images/rId486_edit_140086949247760.png)

**npm install -g truffle ganache-cli ls -al ~**

![](Images/rId487_edit_140086949247888.png)

**ls -al ~ / .nvm / versions / node / v9.5.0 / bin**

![](Images/rId489_edit_140086949248400.png)

**ls -al ~ / .nvm / versions / node / v9.5.0 / lib / node\_modules truffle**

![](Images/rId490_edit_140086949248272.png)

**version**

![](Images/rId491_edit_140086949248144.png)

**truffle init**

![](Images/rId492_edit_140086949245072.png)

**ls -al**

![](Images/rId493_edit_140086949245200.png)

## **tree**

![](Images/rId494_edit_140086949245328.png)

**You receive:**

![](Images/rId495_edit_140086949245456.png)

**.**

**\+ - - contracts**

**¦ + - -Migrations.sol**

**\+ - - migrations**

![](Images/rId496_edit_140086949245584.png)

**¦ + - -1\_initial\_migration.js**

*   **\- - test**

*   **\- - truffle-config.js**

*   **\- - truffle.js**

**5.** **In the EthTruffle project directory, replace the contents of** [the](http://truffleframework.com/docs/advanced/configuration)

![](Images/rId498_edit_140086949245712.png)

[Truffle configuratio](http://truffleframework.com/docs/advanced/configuration) **n file** **(use the correct port number, see** **below** **):**

![](Images/rId499_edit_140086949245840.png)

**truffle.js**

![](Images/rId500_edit_140086949245968.png)

**module.exports = {**

**networks: {**

**development: {**

**host: "localhost",**

**port: 8545,**

**network\_id: "\*"**

**}**

**}**

**};**

**6th** **For the test to be created, the smart contract from the above should again be used** **Mi** [ni token smart contract: MeinToken demo to ser](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) **ve.**

**Either you manually copy the Smart Contract Solidity source code from the above** [MeinToken.so](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#MeinToken.sol) **l** **into the new MeinToken.sol file in the contracts subdirectory.**

**Or, if you have the demo above in**

**Have run the EthereumDemo project directory, copy the file in bash:**

**cp ../EthereumDemo/src/MeinToken.sol contracts / ls -al contracts**

![](Images/rId501_edit_140086949246096.png)

**7th** **Create the deployment configuration file for the MyToken smart contract in the migration subdirectory:**

**2\_MyToken\_migration.js**

![](Images/rId503_edit_140086949246224.png)

**var MyToken = artifacts.require ("./MyToken.sol");**

**module.exports = function (deployer) {**

**deployer.deploy (MeinToken, 999);**

**};**

**If you specify 999, the amount of 999 MeinToken is initially credited to the first account (you can of course specify any other value).**

**8th.** **For the MeinToken smart contract in the test subdirectory, create** [the JavaScript test program](http://truffleframework.com/docs/getting_started/javascript-tests) **: MeinTokenTest.js**

![](Images/rId504_edit_140086949246352.png)

**const MyToken = artifacts.require ("MyToken");**

**contract ('MyToken', function ( accounts ){**

**let instance;**

**before (async function () {**

**instance = await MeinToken.deployed ();**

**});**

**it ("Initial MeinToken account balances:** **999/0 ", async function () {**

**balance0 = await instance.balanceOf.call (accounts \[0\]);**

**balance1 = await instance.balanceOf.call (accounts \[1\]);**

**assert.equal (balance0.valueOf (), 999, "Account 0: The MeinToken account balance is not 999");**

**assert.equal (balance1.valueOf (), not 0 ");** **0, "Account 1: The MeinToken account balance is**

**});**

**it ("Transfer of 11 MeinToken, then: 988/11", async function () { await instance.transfer (accounts \[1\], 11);**

**balance0 = await instance.balanceOf.call (accounts \[0\]);**

**balance1 = await instance.balanceOf.call (accounts \[1\]);**

**assert.equal (balance0.valueOf (), 988, "Account 0: The MeinToken account balance is not 988");**

**assert.equal (balance1.valueOf (), 11, "Account 1: The MeinToken account balance is not 11");**

**});**

**});**

**You have to send the initial amount 999 to the above**

**Ad** [just the amount entered i](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#EthTruffle-2_MeinToken_migration.js) **n 2\_MyToken\_migration.js.** **9.** [Compile Th](http://truffleframework.com/docs/getting_started/compile) **e two Solidity source files:ls -al** **contracts**

![](Images/rId507_edit_140086949246480.png)

**truffle compile**

![](Images/rId509_edit_140086949246608.png)

**ls -al build / contracts /**

![](Images/rId510_edit_140086949246736.png)

**You will receive two .json files.**

**10.** **Truffle offers various test blockchains, see** **Truffle Eth** [ereum](http://truffleframework.com/docs/getting_started/client) [clients. With "truf](http://truffleframework.com/docs/getting_started/client) **fle develop " would you do a test**

**Get blockchain with JavaScript console. Instead, the following is the more common one** **G** [anache blockchain b](https://github.com/trufflesuite/ganache-cli) **e used:**

**ganache-cli --help**

![](Images/rId512_edit_140086949248912.png)

**mkdir ganache blockchain**

![](Images/rId513_edit_140087074615760.png)

**ganache-cli -d -i 66 --db Ganache blockchainYou receive:**

![](Images/rId514_edit_140086954820624.png)

**Ganache CLI v6.0.3 (ganache-core: 2.0.2)**

**Available accounts**

**\===================**

1.  **0x90f8bf6a479f320ead074411a4b0e7944ea8c9c1**

1.  **0xffcf8fdee72ac11b5c542428b35eef5769c409f0**

**. . .**

**Private keys**

**\===================**

1.  **4f3edf983ac636a65a842ce7c78d9aa706d3b113bce9c46f30d7d21715b23b1d**

1.  **6cbed15c793ce57650b9877cf6fa156fbef513c4e6134f022a85b1ffdd59b2a1**

**. . .**

**. . .**

**Listening on localhost: 8545**

**10 accounts were automatically created, each with 100 ethers. These accounts and their private keys are displayed. At least copy the first private key so that you can use the** **Java DApp website** **can use.**

![](Images/rId516_edit_140086954821776.png)

**The different blockchains that can be started with Truffle use different port numbers. You must therefore pay close attention to the "Listening on ..." output. This specification must match that in** [the abo](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#EthTruffle-truffle.js) **ve truffle.js.**

**11\. Resulting project structure:**

**Open a second command line window, switch back to WSL-bash, and look at the resulting project structure:**

**cd \\ MeinWorkspace \\ EthTruffle bash**

![](Images/rId518_edit_140086954822672.png)

## **tree**

![](Images/rId519_edit_140086954820432.png)

**.**

**\+ - - build**

*   **\+ - - contracts**

*   **\+ - - MyToken.json**

*   **\+ - - Migrations.json + - - contracts** ![](Images/rId520_edit_140086954820304.png)

*   **\+ - - MeinToken.sol**

*   **\+ - - Migrations.sol**

**\+ - - Ganache blockchain**

*   **\+ - -! blockHashes! ...**

*   **. . .**

**\+ - - migrations**

**¦+ - - 1\_initial\_migration.js**

**¦+ - - 2\_MyToken\_migration.js**

**\+ - - test**

**¦ + - -MeinTokenTest.js**

**\+ - - truffle-config.js**

**\+ - - truffle.js**

**12\. Automated test of the smart contract:**

**Of the** **test** **with MeinTokenTest.js temporarily deploys the MeinToken smart contract and executes the JavaScript test program:**

![](Images/rId521_edit_140086954821520.png)

**truffle test**

![](Images/rId522_edit_140086954823376.png)

**Using network 'development'.**

**Contract: MyToken**

**Initial MeinToken account balances:999/0 (39ms)**

**Transfer of 11 MeinToken, then: 988/11 (65ms)**

**2 passing (126ms)**

**You have successfully deployed your own smart contract temporarily in the ganache blockchain and executed it in a repeatable and automatable test and tested the smart contract.**

**Unlike in other blockchains, you don't have to wait long for mining.**

**13\. Deploying the smart contract for manual tests:**

[Deploy Yo](http://truffleframework.com/docs/getting_started/migrations) **u can use the smart contracts for further manual tests (e.g. via**

**DAp** [p) into](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#DApp-Webseite-Truffle-Embark) **the ganache blockchain:**

**truffle migrate**

![](Images/rId524_edit_140086954823312.png)

**Using network 'development'.**

**Running migration: 1\_initial\_migration.js**

**Deploying Migrations ...**

**. . . 0xb787070eb6a20cece690a7f9ded231a2a8c74466685156b4d244e745dc7a7b83 Migrations: 0x26b4afb60d6c903165150c6f0aa14f8016be4aec Saving**

**successful migration to network ...**

*   **. . 0x4ae2f8c27694fc1ed60f892e0bd5eaa845a03d8d8a505259c51ce45f6930f5a1 Saving artifacts ...**

**Running migration: 2\_MyToken\_migration.js**

![](Images/rId525_edit_140086954819856.png)

**Deploying MyToken...**

**. . . 0xd60f0c6b6dd4d26cbfca7d1b735703d1baf43c2fbf3d7446cbe2b52d0e2d754f**

**MeinToken: 0x0e696947a06550def604e82c26fd9e493e576337**

**Saving successful migration to network ...**

*   **. . 0xe81f630f8d07e4121b0be7d30280de301edab5e28e675aa619a6d8e6f60d85b5 Saving artifacts ...**

**14th** **Open the truffle** **Console** [:](http://truffleframework.com/docs/getting_started/console)

![](Images/rId527_edit_140086954822352.png)

**truffle console**

![](Images/rId528_edit_140086954822736.png)

**Here you can execute truffle JavaScript commands, for example:**

**web3.eth.accounts**

![](Images/rId529_edit_140086954820752.png)

**MyToken.address**

![](Images/rId530_edit_140086954820176.png)

**MeinToken.at (MeinToken.address) .balanceOf.call (web 3.eth.accounts \[0\]);**

![](Images/rId531_edit_140086954821840.png)

**MeinToken.at (MeinToken.address) .balanceOf.call (web 3.eth.accounts \[1\]);**

![](Images/rId532_edit_140086954820880.png)

**15th** **See below how you can address the smart contract in the truffle test blockchain with a DApp website using either Node.js or Java:** **DApp website for the smart contra** [ct with both Truffle and Embark.](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#DApp-Webseite-Truffle-Embark)

![](Images/rId533_edit_140086954823440.png)

**Embark for easy development and quick testing**

**This demo shows:**

![](Images/rId535_edit_140086954822544.jpeg)

**\-Like you that** [Embark development framework](https://github.com/embark-framework/embark) **to install.**

**\-How you can create, deploy and execute your own Ethereum Smart Contracts with Embark.**

**\-How to create very fast tests in JavaScript with Embark and an integrated test blockchain.**

**\-Please note: This demo uses only a small fraction of the many features of Embark.**

**\-Look at the** **Embark** [documentary](https://embark.readthedocs.io/) **at.**

**\-Embark competes with the one presented above** **Truffle** [.](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Truffle)

![](Images/rId538_edit_140086950894160.png)

**The following versions are used:**

**\-nvm 0.33.8**

**\-npm 5.6.0**

**\-node 9.5.0**

**\-Solidity 0.4.17**

**\-embark 2.6.6**

**\-ganache-cli / ethereumjs-testrpc 6.0.3**

**\-Ubuntu 04/16/3 LTS**

**\-Windows 10 version 1709**

**As already** **o** [n top with truf](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Truffle) **fle the bash of WSL (Windows Subsystem for Linux) used. If** [you work directly under Linux (e.g.](https://docs.microsoft.com/en-us/windows/wsl/install-win10) **Ubuntu), you can simply skip some steps.**

![](Images/rId539_edit_140086950894416.png)

**1.** **If you haven't already, install** **WSL** **,** **npm** **and** **Node.js** **how** **up f** [or tr](https://docs.microsoft.com/en-us/windows/wsl/install-win10) **u** [ffle](https://docs.npmjs.com/) **described.**

![](Images/rId540_edit_140086950894288.png)

**2.** **Change to your workspace directory (e.g. \\ Mein** Workspace):cd \\ **MyWorkspace**

![](Images/rId541_edit_140086950894480.png)

**3\. Start the WSL-Bash, update your Linux and install Embark:**

## **bash**

**sudo apt-get update -y && sudo apt-get upgrade -y npm -g install embark ethereumjs-testrpc ls -al ~**

![](Images/rId542_edit_140086950894608.png)

**ls -al ~ / .nvm / versions / node / v9.5.0 / bin**

![](Images/rId544_edit_140086950894736.png)

**ls -al ~ / .nvm / versions / node / v9.5.0 / lib / node\_modules embark**

**\--version**

![](Images/rId545_edit_140086950894864.png)

**embark --help**

![](Images/rId546_edit_140086950894992.png)

1.  **Start a new Embark project:embark new EthEmbark**

**cd EthEmbark ls -al**

## **tree**

**You receive:**

![](Images/rId547_edit_140086950895120.png)

**.**

**\+ - - app**

*   **\+ - - contracts** ![](Images/rId552_edit_140086950895248.png)

*   **\+ - - css**

*   **\+ - - index.html**

*   **\+ - - js**

*   **\- - chains.json**

*   **\- - config**

*   **\+ - - blockchain.json**

*   **\+ - - communication.json**

*   **\+ - - contracts.json**

*   **\+ - - development**

**¦¦** **\+ - - genesis.json**

**¦¦** **\+ - - password**

*   **\+ - - storage.json**

*   **\+ - - testnet**

*   **¦ + - - password**

*   **\+ - - webserver.json + - - embark.json**

**\+ - - package.json + - - test**

*   **\- - contract\_spec.js**

**5.** **For the test to be created, the smart contract from the above should again be used** **Mi** [ni token smart contract: MeinToken demo to ser](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Mini-Token-Demo) **ve.**

**Either you manually copy the Smart Contract Solidity source code from the above** **MeinTok** [en.sol into the](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#MeinToken.sol) **new file MeinToken.sol in the subdirectory app / contracts.**

**Or, if you have the demo above in**

**Have run the EthereumDemo project directory, copy the file in bash:**

**cp ../EthereumDemo/src/MeinToken.sol app / contracts / ls -al app / contracts**

![](Images/rId553_edit_140086950895376.png)

**In the copied MeinToken.sol in the app / contracts subdirectory, replace the line:**

 
| **pragma solidity** || **0̂.4.19;** |
| --- | --- |
|  ||  |

## **by:**

 
| **pragma solidity** || **0̂.4.17;** |
| --- | --- |
|  ||  |

**6th** **In the config subdirectory in the configuration file contracts.json, replace the two lines:**

![](Images/rId554_edit_140086950895504.png)

**"contracts": {**

**}**

**by:**

**"contracts": {**

![](Images/rId555_edit_140086950894032.png)

**"MyToken": {**

**"args": \[999\]**

**}**

**}**

**7th** **For the MeinToken smart contract in the test subdirectory, create** [the JavaScript test program](https://embark.readthedocs.io/en/2.6.6/tests.html) **: MeinTokenTest.js**

![](Images/rId557_edit_140086950891600.png)

**describe ("MyToken", function () {**

**before (function (done) {**

**this.timeout (0);**

**var contractsConfig = {**

**"MyToken": {**

**args: \[999\]**

**}**

**};**

**EmbarkSpec.deployAll (contractsConfig, done);**

**});**

**it ("Initial MeinToken account balances:** **999/0", function () {**

**web3.eth.getAccounts (function (err, accounts) {**

**balance0 = MeinToken.balanceOf.call (accounts \[0\]);**

**balance1 = MeinToken.balanceOf.call (accounts \[1\]);**

**assert.equal (balance0.valueOf (), 999, "Account 0: The MeinToken account balance**

**is not 999 ");**

**assert.equal (balance1.valueOf (),** **0, "Account 1: The MeinToken account balance**

**is not 0 ");**

**})**

**});**

**it ("Transfer of 11 MeinToken, then: 988/11", function () {**

**web3.eth.getAccounts (function (err, accounts) {**

**MeinToken.transfer (accounts \[1\], 11);**

**balance0 = MeinToken.balanceOf.call (accounts \[0\]);**

**balance1 = MeinToken.balanceOf.call (accounts \[1\]);**

**assert.equal (balance0.valueOf (), 988, "Account 0: The MeinToken account balance**

**is not 988 ");**

**assert.equal (balance1.valueOf (), 11, "Account 1: The MeinToken account balance**

**is not 11 ");**

**})**

**});**

**});**

1.  **Resulting project structure: tree**

![](Images/rId558_edit_140086950891728.png)

**.**

**\+ - - app**

*   **\+ - - contracts**

*   **¦ + - -MeinToken.sol**

*   **\+ - - css**

*   **\+ - - index.html**

*   **\+ - - js**

*   **\- - chains.json**

*   **\- - config**

*   **\+ - - blockchain.json**

*   **\+ - - communication.json**

*   **\+ - - contracts.json**

*   **\+ - - development**

**¦¦** **\+ - - genesis.json**

**¦¦** **\+ - - password**

*   **\+ - - storage.json**

*   **\+ - - testnet**

*   **¦ + - - password**

*   **\+ - - webserver.json + - - embark.json**

**\+ - - package.json + - - test**

*   **\- - contract\_spec.js**

*   **\- - MeinTokenTest.js**

**9\. Automated test of the smart contract:**

**The test with MeinTokenTest.js temporarily starts its own test blockchain, deploys the smart contract, executes the JavaScript test program and ends the test blockchain again:**

**cd \\ MeinWorkspace \\ EthEmbark**

![](Images/rId559_edit_140086950891856.png)

**bash**

**embark test**

![](Images/rId560_edit_140086950891984.png)

**You receive:**

 
| **MyToken** ||  |
| --- | --- |
| **deployed contracts** ||  |
| **Initial MeinToken account balances:** || **999/0** |
| **Transfer of 11 MeinToken, then: 988/11** ||  |
| **2 passing (4s)** ||  |
|  ||  |

**You have successfully deployed your own smart contract in the test blockchain and in a repeatable and**

**Automated test carried out and the smart contract tested.**

**Unlike in other blockchains, you don't have to wait long for mining.**

1.  **Manual test of the smart contract with JavaScript commands:**

**Similar to the Geth JavaScript Console, you can also execute Web3 JavaScript commands directly in the Embark Terminal Dashboard.**

**Start the test blockchain integrated in Embark in bash:embark simulator**

![](Images/rId561_edit_140086950892112.png)

**The automatically created accounts and their private keys are displayed. At least copy the first private key so that you can use the** **Java DApp website** **can use.**

![](Images/rId562_edit_140086950892240.png)

**Open a second command line window, start bash, open the Embark dashboard, and deploy the smart contract:**

**cd \\ MeinWorkspace \\ EthEmbark**

![](Images/rId563_edit_140086950892368.png)

**bash**

**embark run**

![](Images/rId564_edit_140086950892496.png)

**In the Embark dashboard (see screenshot) at the bottom of the "Console" section, you can directly execute JavaScript commands, for example:**

**MyToken.address**

![](Images/rId565_edit_140086950892624.png)

**MeinToken.balanceOf (web3.eth.accounts \[0\]) MeinToken.balanceOf (web3.eth.accounts \[1\]) MeinToken. transfer(web3.eth.accounts \[1\], 19th )MeinToken.balanceOf (web3.eth.accounts \[0\]) MeinToken.balanceOf (web3.eth.accounts \[1\])**

![](Images/rId566_edit_140086950892752.png)

**11.Live blockchain:**

**Of course, you can use Embark not only with the Embark test blockchain, but also with all other Ethereum blockchains. Do not use the command shown above for thisembark simulator, but instead embark blockchain.**

![](Images/rId570_edit_140086950892880.png)![](Images/rId571_edit_140086950893008.png)

**12.DApp website:**

**See in the following chapter how you can address the smart contract in the Embark-Test-Blockchain with a DApp website either with Node.js or with Java.**

![](Images/rId572_edit_140086950893136.png)

**DApp website for the smart contract with both Truffle and Embark**

**1.Node.js DApp website:**

![](Images/rId573_edit_140086950893264.jpeg)

**You can use the smart contract deployed in the truffle or embark test blockchain with the above under** **DApp websit** [e for the smart contract](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Node.js-DApp-Webseite) [with Node.js Use the create](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Node.js-DApp-Webseite) **d DApp website.**

**Replace in the Node.js-DApp-**

**Website EthNodejsDApp / MeinTokenDAppWebseite.html in the line const contractAddress = "0x ..."; the address of the MeinToken smart contract with the new address from the truffle or embark test blockchain, which you receive by entering in the truffle or embark console:**

**MyToken.address**

![](Images/rId574_edit_140086950893584.png)

**With the test blockchain running, start the Node.js DApp website:cd \\ MeinWorkspace \\ EthNodejsDApp start**

![](Images/rId575_edit_140086950893520.png)

MeinTokenDAppWebseite.html

![](Images/rId576_edit_140086950893648.png)

**The correct MeinToken account balances are displayed. To transfer MeinToken amounts, enter a minus sign ("-") as the passphrase.**

**2\. Java DApp website:**

**Even with the** [DApp website for the smart contract with](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Java-DApp-Webseite) [Java](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Java-DApp-Webseite) **you can use the smart contract deployed in the** **truffle or embark test blockchain.**

![](Images/rId577_edit_140086950893776.png)

**You will need those with MyToken.address Determined address of the MeinToken smart contract and the private key of the sender account (e.g. the first account). The private keys of the accounts are used when executing "ganache-cli -d -i 66 --db Ganache blockchain " or from "embark simulator " to start the integrated test blockchain.**

![](Images/rId578_edit_140086949767440.png)

**You can choose to have the contract address and the private key either in the Java source code MeinTokenTransfer.java in**

**EthJavaDApp \\ src \\ main \\ java \\ de \\ mycompany \\ myproject directory in the two lines**

**public static final String DEFAULT\_CONTRACT\_ADRESSE = "0x ..."; public static final String DEFAULT\_PASSPHRASE\_OR\_PRIVKEY = "...";**

**or, alternatively, enter it on the website at runtime.**

**With the test blockchain running, start the Jetty web server with the**

**EthJavaDApp web application:**

**cd \\ MeinWorkspace \\ EthJavaDApp**

![](Images/rId579_edit_140086949767696.png)

**mvn jetty: run-war**

![](Images/rId580_edit_140086949766864.png)

**Wait a while for "Started Jetty Server" to appear. Go to the website:**

**begin** **http:** [// localhost: 8080 / EthJavaDApp](http://localhost:8080/EthJavaDApp)

![](Images/rId581_edit_140086949766608.png)

**The correct MeinToken account balances are displayed and you can transfer MeinToken amounts as usual.**

![](Images/rId582_edit_140086949769040.png)

**Use of the Oraclize service for external information queries**

**This demo shows:**

![](Images/rId583_edit_140086949769104.jpeg)

**\-How external information can be queried, for example, via JSON-REST interface and loaded into an Ethereum smart contract, although smart contracts cannot access external services.**

**Smart contracts can execute program code and calculations and store the results in the blockchain. But smart contracts cannot communicate with the outside world. For some smart contracts, however, queries have to be carried out in order to be able to check certain "real-world" conditions, for example stock exchange prices, flight delays or weather data. So-called oracles are programmed as intermediaries ("data feed") (e.g. in** **Solidity) and added the blockchain.** [A](https://solidity.readthedocs.io/) **smart contract can query the Oracle, and the Oracle can call up external interfaces, for example via REST / JSON, and transmit the result to the smart contract via callback. See also:** **Oracle Services (Christoph Niemann), Types of oracles** [, Building an Oracle for](https://www.maibornwolff.de/sites/default/files/news/files/javaspektrum_orakeldienste_blockchain_drchristophniemann.pdf) [Ethereum](https://www.maibornwolff.de/sites/default/files/news/files/javaspektrum_orakeldienste_blockchain_drchristophniemann.pdf) **(** [John Weldon), O](https://blockchainhub.net/blockchain-oracles/) **r** [acles bring data to the blockchain (Jules](https://medium.com/@mustwin/building-an-oracle-for-an-ethereum-contract-6096d3e39551) [Dourlen](https://medium.com/@mustwin/building-an-oracle-for-an-ethereum-contract-6096d3e39551) **s** [), Ethereum and Oracles (Vitalik Buterin), Oraclize.it:](https://ethereumdev.io/oracles-getting-data-inside-blockchain/) **D** [ata Carrier](https://blog.ethereum.org/2014/07/22/ethereum-and-oracles/) [for decentralized Apps.](https://blog.ethereum.org/2014/07/22/ethereum-and-oracles/)

![](Images/rId589_edit_140086949765968.png)

**One of the most famous service providers for such Oracle services** [is](http://www.oraclize.it/) **Oraclize.it** **. A smart contract using this service is presented below.**

![](Images/rId593_edit_140086949768592.png)

**1.** **Using the Oraclize service is a bit more complex with a private Ethereum blockchain, since a** **Ethereum bridge** **would need to be installed.** [That is why](https://docs.oraclize.it/#integrations) **the Rinkeby Ethereum blockchain is used here where this is not required.**

![](Images/rId595_edit_140086949768848.png)

**2.** **If you haven't already done so, start with the** **ab** [ove B](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#starte-Rinkeby-Ethereum-Blockchain.bat) **atch file created the Rinkeby-Test-Ethereum-Blockchain:**

**cd \\ MeinWorkspace \\ EthereumDemo start-Rinkeby-Ethereum-Blockchain.bat**

![](Images/rId596_edit_140086949767568.png)

**You will likely have to wait for the blockchain to sync.**

1.  **Your own account must have Ether: web3.eth.accounts**

**loadScript ('src / checkAllBalances.js')**

![](Images/rId597_edit_140086949767312.png)

**If you have not yet created any accounts: See above** **Public** [Rinkeby](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Rinkeby)

![](Images/rId599_edit_140086949765392.png)

[Test Ethereum Blockchain. If you h](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Rinkeby) **ave accounts but do not yet have**

**ethers: see above** **Transfer eth** [er to the Rinkeby account. In case you](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Rinkeby-Ether-transferieren)

[have already](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#Rinkeby-Ether-transferieren) **transferred Ether, but after a restart the Ether amount**

![](Images/rId601_edit_140086949765776.png)

**appears to be 0: You will probably just have to wait longer for the**

**blockchain synchronization. It is best to check whether the Rinkeby**

**account has ether with** **https://rinkeby.etherscan.io/address/**

**Zon** [enMeine-Account-Adresse} (replace "{my account address}"](https://rinkeby.etherscan.io/address/0x39bbbe004272e72dba0c13a0e60443cfcceead3c) **with**

**your account address).**

1.  **The exchange rate query from the British pound to the euro is to be demonstrated. The service accessible via the following REST URL should be used for this purpose:**

[http://api.fixer.io/latest?symbols=USD,GBP](http://api.fixer.io/latest?symbols=USD,GBP)

![](Images/rId603_edit_140086949768784.png)

**For example, the JSON result is (it is displayed differently formatted depending on the web browser):**

![](Images/rId604_edit_140086949767632.png)

**{**

**"base": "EUR",**

**"date": "2018-02-13",**

**"rates": {**

**"GBP": 0.88935,**

**"USD": 1.2333**

**}**

**}**

**5.** **The Oraclize demo ExampleContract is used as the smart contract calling this external service** **https://doc** [s.oraclize.it/#ethereu m-quick-](https://docs.oraclize.it/#ethereum-quick-start) [start used.](https://docs.oraclize.it/#ethereum-quick-start)

![](Images/rId606_edit_140086949768080.png)

**6th** **As recommended on the Oraclize website, the** **Remix** [Online](http://remix.readthedocs.io/) [Solidity Compiler IDE](http://remix.readthedocs.io/) **used.**

![](Images/rId607_edit_140086949767824.png)

**7th** **Open the Remix Online Solidity Compiler IDE:**

[http://remix.ethereum.org.](http://remix.ethereum.org/)

![](Images/rId608_edit_140086949765200.png)

**8th.** **Start a new project by clicking the little plus sign in the upper left corner of the website.**

**For "File Name" enter: ExampleContract.sol**

**9.** **In the upper middle empty window with the title "browser / ExampleContract.sol" paste the ExampleContract-Solidity-Sourcecode from** [https://docs.oraclize.it/#ethereum-quickstart a](https://docs.oraclize.it/#ethereum-quick-start) [(see](https://docs.oraclize.it/#ethereum-quick-start) **also the screenshot below** **below** **).**

![](Images/rId609_edit_140086949768400.png)

**In the ExampleContract Solidity source code, look in particular at:**

**As with "import" github.com/oraclize/ethereum-api/oraclizeAPI.sol ";" another Solidity source code is imported,**

**as in "contract ExampleContract is usingOraclize"**

**the ExampleContract is derived from usingOraclize,**

**how a callback method is implemented with "function \_\_callback (bytes32 myid, string result)",**

**and how with "oraclize\_query (" URL "," json (http://api.fixer.io/latest? symbols = USD, GBP) .rates.GBP ") the external JSON-REST interface is queried and a value from the JSON response is extracted.**

1.  **Click in the top right third on the tab "Compile" and then on the button "Start to compile". You get a lot of orange warnings but no red error messages.**

1.  **Click the Details button to view the compilation results. Under "WEB3DEPLOY" you will find a finished JavaScript program for deploying the ExampleContract smart contract. You could execute this JavaScript in the Geth JavaScript Console. However, in this demo everything is supposed to be done through the Remix IDE instead.**

1.  **Connect the Remix Online Solidity Compiler to your Rinkeby blockchain:**

**Click in the top right third on the tab "Run", select "Web3 Provider" under Environment, confirm "Are you sure you want to connect to an ethereum node?" and "Web3 Provider Endpoint" "http: // localhost: 8545".**

**At the top right of Environment is displayed: "Rinkeby (4)".**

**And under Account appears your account address and behind it the Ether account balance in brackets.**

**13th** **Test the connection:**

**In the lower middle window, enter Geth commands at the very bottom next to the ">" sign, for example:**

**web3.eth.accounts**

**and press the return key.**

**14th** **Deploy your ExampleContract smart contract to the Rinkeby blockchain:**

**In the lower middle window, at the very bottom next to the ">"**

**sign, enter:**

**web3.personal.unlockAccount (web3.eth.accounts \[0\], "My Ethereum test passphrase")**

**Press the "Create" button in the middle part of the right window.**

**For example, you will receive:**

![](Images/rId612_edit_140086949766224.png)

*   **web3.personal.unlockAccount (web3.eth.accounts \[0\], "My Ethereum test passphrase") true**

**creation of ExampleContract pending ...**

**\[block: 1764901 txIndex: 2\] from: 0x39b ... ad3c, to: ExampleContract. (constructor), value: 0 white, 2 logs, data:**

**0x606 ... 0029, hash: 0xfb1 ... bda4**

**The ExampleContract smart contract has been successfully deployed in the Rinkeby blockchain.**

**Click the Details button in the lower middle window to view more information. For example, you can see the required amount of gas there.**

**15th** **Important: Make a note of the contract address so that you can find the ExampleContract smart contract again later. Click on the copy icon to the right of "ExampleContract at 0x ... (blockchain)" and save the copied contract address in the file Oraclize.ExampleContract.address.Rinkeby.txt.**

**16.** **Query the EUR-GBP rate initially determined by clicking on the EURGBP button on the right. You get the same value as above for the** **JSON REST query** [.](http://api.fixer.io/latest?symbols=USD,GBP)

![](Images/rId613_edit_140086949768464.png)

**Access to the external JSON REST interface worked.**

**17th** **Run the updatePrice () method of the ExampleContract smart contract by first performing an unlock:**

**web3.personal.unlockAccount (web3.eth.accounts \[0\], "My Ethereum test passphrase")**

**And then click on the updatePrice button on the right. You receive:**

![](Images/rId614_edit_140086949765264.png)

**\> web3.personal.unlockAccount (web3.eth.accounts \[0\], "My Ethereum test passphrase")**

**true**

![](Images/rId615_edit_140086949766544.png)

**transact to ExampleContract.updatePrice pending ...**

**\[block: 1764970 txIndex: 2\] from: 0x39 ... 3c, to: ExampleContract.updatePrice () 0xfb ... 26, value: 0 wei, 1 logs,**

**data: 0x67 ... 28, hash: 0x20 .. .0e**

**Executing the updatePrice () method of the ExampleContract smart contract including renewed access to the external JSON REST interface worked.**

**If you are lucky that the EUR-GBP rate has changed in the meantime, you will see the new value.**

**18th** **Of course, simply transferring the market value to the blockchain makes no sense. But depending on the market value, the smart contract could make further decisions or start actions. Under** **http:// dapps.** [oraclize.it you can find](http://dapps.oraclize.it/) **examples for "Oraclize-based DApps".**

**19th** **Theoretically, the Oraclize service could falsify the information transmitted. To rule this out, Oraclize** **Authenticity** [proofs at.](https://docs.oraclize.it/#ethereum-quick-start-authenticity-proofs)

![](Images/rId618_edit_140086949768144.png)![](Images/rId620_edit_140086949768528.jpeg)

**Analysis of the blocks and transactions**

![](Images/rId621_edit_140086949765840.png)

**Under** [Common useful JavaScript snippets for get](https://ethereum.stackexchange.com/questions/2531/common-useful-javascript-snippets-for-geth/) **h** **you will find some useful Geth JavaScript scripts, such as the**

**following getTransactionsByAccount ():**

1.  **Add the following script to the Geth JavaScript console while the blockchain is running:**

![](Images/rId623_edit_140086949768016.png)

**function getTransactionsByAccount(myaccount, startBlockNumber, endBlockNumber) { if (endBlockNumber == null) {**

**endBlockNumber = eth.blockNumber;**

**console.log ("Using endBlockNumber:" + endBlockNumber);**

**}**

**if (startBlockNumber == null) {**

**startBlockNumber = endBlockNumber - 50;**

**console.log ("Using startBlockNumber:" + startBlockNumber);**

**}**

**console.log ("Searching for transactions to / from account \\" "+ myaccount +" \\ "within blocks" +**

**startBlockNumber + "and" + endBlockNumber);**

**for (var i = startBlockNumber; i <= endBlockNumber; i ++) {**

**if (i% 10 == 0) {**

**console.log ("Searching block" + i);**

**}**

**var block = eth.getBlock (i, true);**

**if (block! = null && block.transactions! = null) {**

**block.transactions.forEach (function (e) {**

**if (myaccount == "\*" || myaccount == e.from || myaccount == e.to) {**

| **console.log ("** || **tx hash** || **: "+ e.hash +" \\ n "** |
| --- | --- | --- |
| **\+ "** || **nonce** ||  || **: "+ e.nonce +" \\ n "** |
| **\+ "** || **blockHash** || **: "+ e.blockHash +" \\ n "** |
| **\+ "** || **blockNumber** || **: "+ e.blockNumber +" \\ n "** |
| **\+ "** || **transactionIndex: "+ e.transactionIndex +" \\ n "** |
| **\+ "** || **from** ||  || **: "+ e.from +" \\ n "** |
| **\+ "** || **to** ||  || **: "+ e.to +" \\ n "** |
| **\+ "** || **value** ||  || **: "+ e.value +" \\ n "** |
| **\+ "** || **time** ||  || **: "+ block.timestamp +" "+ new** |
| **Date (block.timestamp \* 1000) .toGMTString () + "\\ n"** |
| **\+ "** || **gasPrice** ||  || **: "+ e.gasPrice +" \\ n "** |
| **\+ "** || **gas** ||  || **: "+ e.gas +" \\ n "** |
| **\+ "** || **input** ||  || **: "+ e.input);** |

**}**

![](Images/rId624_edit_140086949766480.png)

**})**

**}**

**}**

**}**

1.  **You can then view certain transactions in the Geth JavaScript console, for example the last transactions for all accounts:**

**getTransactionsByAccount ("\*")**

![](Images/rId625_edit_140086949768976.png)

**3\. Or for a specific account in a specific range of block numbers:**

**getTransactionsByAccount (eth.accounts \[0\], 100, 200)**

![](Images/rId626_edit_140086949289040.png)

**4\. Suppose you get for the last two blocks:**

![](Images/rId627_edit_140086949288720.png)

**tx hash**

**nonce**

**blockHash**

**blockNumber**

**transactionIndex: 0**

**: 0x7f3ef240d563e843f2cc577d63cc9f9382da8526aff4c7ea565db137c093fc4e**

**: 110**

**: 0xeae4e8e1c9b2d73f35fc4f3d5013e37184bbf36ef4b27a303b6fccdcd80f4f4e**

**: 9087**

**from**

**to**

**value**

**time**

**gasPrice**

**gas**

**: 0x4597a26af9991b297b5ccc2a8c0966e9a1a17035**

**: 0x63d7d5b64dc9cc0744dedf87971f8b0777d7e226**

**: 10000000000000000000**

**: 1517595662 Fri, Feb 02 2018 18:21:02 GMT**

**: 22000000000**

**: 4300000**

**input**

**: 0x**

**tx hash**

**nonce**

**blockHash**

**blockNumber**

**transactionIndex: 0**

**: 0xba9d2cdbe9a1ea65a3551f0d8f39486acb0746f4c2a3ab6f20449eb698e959e5**

**: 111**

**: 0x5964c99158f57252ee97043e267846dc2441472ed766feb89a85698ba19c9514**

**: 9091**

**from**

**to**

**: 0x4597a26af9991b297b5ccc2a8c0966e9a1a17035**

**: 0xa7818f6043df69bcf6c0db5d766e674d034dacfc**

**value**

**: 0**

**time**

**: 1517595743 Fri, Feb 02, 2018 18:22:23 GMT**

**gasPrice**

**: 22000000000**

**gas**

**: 4300000**

**input:**

**0xa9059cbb00000000000000000000000063d7d5b64dc9cc0744dedf87971f8b0777d7e226000000000000 ..**

**.**

**In the penultimate block, 10 ethers (value: 10000000000000000000) are transferred from account 0x4597 ... to account 0x63d7 ... (per** [EtherTransfer](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#EtherWeb3jDemo-EtherTransfer.java) **).**

**No ethers are transferred in the last block (value: 0). Instead, the account 0x4597 ... executes the smart contract under 0xa781 ... (input: 0xa905 ...) (per** **MyTokenTransfer** [).](https://www.torsten-horn.de/techdocs/Ethereum-Smart-Contracts.html#EtherWeb3jDemo-MeinTokenTransfer.java)

![](Images/rId629_edit_140086949287952.png)

**Solidity plug-in for JetBrains IntelliJ IDEA**

**If you are** [JetBrains IntelliJ IDEA](https://www.jetbrains.com/idea/) **you can use that** **Intellij** **solid** [ity plugin to install:](https://plugins.jetbrains.com/plugin/9475-intellij-solidity)

![](Images/rId633_edit_140086949286352.jpeg)

**1.** **Instructions for installing IntelliJ IDEA are available at:** **Install** [and set up IntelliJ IDEA. Further in](https://www.jetbrains.com/help/idea/install-and-set-up-intellij-idea.html) **formation can be found** **here** **.**

![](Images/rId635_edit_140086949286032.png)

1.  **Update IntelliJ IDEA to the latest version.**

1.  **To install the Intellij Solidity plug-in, select:**

**File | Settings ... | Plugins | Browse repositories ... | Solidity | IntelliJ-Solidity | right mouse button | Download and Install.**

**4\. After restarting IntelliJ IDEA, you can create Solidity files via:**

**File | New | Smart contract.**

**In version 2.0.4 the plugin offers syntax highlighting, auto-completion (code completion) and find usages.**

**6th** **However, this also offers the** [Remix Online Solidity Compile](http://remix.ethereum.org/) **r** **which also offers many other features, such as displaying syntax errors, compiling, creating finished Web3 JavaScript code for deployment (under Details | WEB3DEPLOY), and even deploying, executing and debugging Solidity code.**

![](Images/rId636_edit_140086949287824.png)

**documentary**

**Documentation on cryptocurrencies, blockchain, Ethereum, Geth, smart contracts and solidity:**

**\-** [Cryptocurrencies, Bitcoin, Ethereum, Blockchain](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html)

![](Images/rId637_edit_140086949288272.png)

**\-** [Ethereum Command Line Tools (Ethereum.org)](https://www.ethereum.org/greeter)

![](Images/rId638_edit_140086949287760.png)

**\-** [Contract Tutorial (Ethereum on GitHub)](https://github.com/ethereum/go-ethereum/wiki/Contract-Tutorial)

![](Images/rId640_edit_140086949289360.png)

**\-** [Solidity (Ethereum on ReadTheDocs)](http://solidity.readthedocs.io/en/develop/)

![](Images/rId642_edit_140086949286608.png)

**\-** [Solidity Tutorials (Ethereum Builder's Guide as GitBook)](https://ethereumbuilders.gitbooks.io/guide/content/en/solidity_tutorials.html)

![](Images/rId644_edit_140086949289616.png)

**\-** [Tutorials for Ethereum Developers (EthereumDev.io)](https://ethereumdev.io/)

![](Images/rId646_edit_140086949288336.png)

**\-** [Smart Contract in Solidity (Techracers)](http://www.techracers.com/smart-contract-solidity) **\-** [Learning Solidity by Example (Bill Brock)](https://www.verypossible.com/blog/ethereum-smart-contracts-learning-solidity-by-example) **\-** [Ethereum Stack Exchange](https://ethereum.stackexchange.com/) **\-** [Grid to ethereum / web3.js](https://gitter.im/ethereum/web3.js)

![](Images/rId651_edit_140086949288528.png)

**\-** [Grid to ethereum / solidity](https://gitter.im/ethereum/solidity)

![](Images/rId656_edit_140086949286800.png)

**\-** [34,000 vulnerabilities in smart contracts on Ethereum](https://www.heise.de/newsticker/meldung/Forscher-finden-34-000-Sicherheitsluecken-in-Smart-Contracts-auf-Ethereum-3986439.html)

![](Images/rId658_edit_140086949289808.png)

**Other topics:** **Cryp** [tocurrencies, Tec](https://www.torsten-horn.de/techdocs/Kryptowaehrungen.html) [hDocs](https://www.torsten-horn.de/techdocs/index.htm)

![](Images/rId659_edit_140086949288208.png)

**© 2018 Torsten Horn, Aachen**

© 2021 Magelan Cybersexurity

Alle Rechte vorbehalten.

ISBN: 9783755711360

Herstellung und Verlag: BoD - Books on Demand, Norderstedt

[![Books on Demand](Images/bod_logo.jpg)](http://www.bod.de/)