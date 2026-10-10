
## 10.  Now add a new migrations file under migrations node as shown in the following screenshot and call it `2_deploy_contracts.js` and move the deploy code from `1_initial_migration.js` to this newly created file:

     ![](images/Figure_3.2.21.jpg)

     **Figure 3.2.21**

## 11.  So, the file contains the code as below.

```
var HelloWorld = artifacts.require("./helloworld.sol");

module.exports = function(deployer) {
    deployer.deploy(HelloWorld);
};
```

## 12.  Now again, go to the PowerShell window where we got an error and again compile the code by typing the command `truffle compile` and press *Enter*. Once you press *Enter*, the code will again be compiled for the latest changes we made in VS Code. Now again, run the command `truffle migrate` for deployment.

     ![](images/Figure_3.2.22.jpg)

     **Figure 3.2.22**

     This time our migrations run fine as they find the current running server. See the above image as it successfully deploys our contract. We can also see the address it got while uploading.

## 13.  Now, you can go ahead to create a user interface to test the contract we just deployed; alternatively, Truffle also provides a mechanism to interact with the contracts. We can do this via truffle console. To start the truffle in console mode, run the command `truffle console`, as shown in the following screenshot:

     ![](images/Figure_3.2.23.jpg)

     **Figure 3.2.23**

     This opens a console listener for Truffle. In this mode, we can directly write *JavaScript* code for our contract. Let’s do it step by step.

# [Test smart contract](#toc.xhtml#s63a)

In the truffle console mode, define a variable named `helloW` or any of your choices with the `var` keyword. And press *Enter*. We’ll try to access our contract with this variable. After pressing *Enter*, we get `undefined`, and that is obvious because the variable is still not defined with any content. Since the communication with contracts should be async, we write an async code to access the contract now. Since in our code, the contract was referenced using the `deployed` keyword, so we’ll also access it via `helloWorld.deployed();` after that, a `then` keyword is used to create an async method that maps our deployed contract with the variable that we created earlier, i.e., `helloW`. The command would be `helloworld.deployed().then(function(deployed){helloW=deployed});` See the following screenshot with all the commands to understand in detail.

![](images/Figure_3.2.24.jpg)

**Figure 3.2.24**

Now, access and test the contract with the variable we mapped it to in our last step. Use the method `call()` to the `helloworld` contract method to invoke the contract as `helloW.PrintHelloWorld.call()` as shown in following screenshot:

![](images/Figure_3.2.25.jpg)

**Figure 3.2.25**

Here we get the string that we were returning from that method and so our method and contract are tested running on internal private Blockchain.

Was it fun to implement and test our smart contract?

# [Conclusion](#toc.xhtml#s64a)

In this chapter, we learned about smart contracts, and the language used to develop smart contracts on Ethereum, Truffle, and Test RPC. This section serves as a primer to those who are beginners in blockchain development and new to Ethereum and smart contracts. This section gives a foundation on how to start and proceed with smart contract development. I hope you enjoyed creating your smart contract, deploying, and testing it.

*Happy Coding!*

![](images/Figure_3.2.26.jpg)

**Figure 3.2.26**

# [Questions](#toc.xhtml#s65a)

1.  What is a smart contract? Which language is used to develop a smart contract?

2.  What is byte code?

3.  How do you compile the smart contract?

4.  What is the very first thing you must specify in a solidity file?

5.  What is a smart contract mining?

6.  What is the use of Test RPC in smart contract development?

7.  Can smart contracts be trusted?

8.  Are there standards for smart contracts?

9.  Is the execution of smart contracts free?

10.  What happens if the execution of a smart contract costs more than the specified gas?

# [Section - IV](#toc.xhtml#p04)

# [Blockchain in Real World](#toc.xhtml#p04)

Let’s talk a bit more about what is the need of blockchain, and what more offerings can blockchain provide.

# [CHAPTER 1](#toc.xhtml#p04c01)

# [Blockchain-Offerings and Usages](#toc.xhtml#p04c01)

# [Structure](#toc.xhtml#s66a)

In this chapter we will discuss the following topics

*   Need, usages, and offerings of blockchain.

*   Impact of blockchain technology in education.

# [Objectives](#toc.xhtml#s67a)

After studying this unit, you should be able to

*   Understand the real-time applications of blockchain

*   Understand how blockchain is impacting/influencing day to day life.

*   Understand what all places blockchain technology can contribute or is contributing to?

# [Need, usages, and offerings](#toc.xhtml#s68a)

The vital question your company should ask is, do we need a blockchain? There's a simple list of questions that you can ask to help determine this. First, do you need a shared public database between multiple parties? If we're using a public blockchain, do you need the data on this blockchain to be accessible by anyone? If you're using a private blockchain, do you need for this data to be shared between several known parties or companies? If the answer is no, then a blockchain might not be the best technology for you to use. The next question to ask is if multiple parties need to share the data, do any of these parties have conflicting incentives, or are they not trusted? One of the primary purposes of a blockchain is to enable trust between multiple parties. So, if there is a level of distrust between the other parties and they have conflicting incentives, then a blockchain is an excellent solution to look at.

Otherwise, a blockchain may not be needed, and you can use a database instead. The next question you should ask is, are the other parties able to play by the same rules? By this, we mean, will you be able to get them to use the same rules to govern the transactions added onto the blockchain and the same rules to verify the transactions? If the answer is no and you don't think you can get all the parties to play by the same rules, which is easier said than done, then a blockchain isn't going to be an excellent solution to use.

The next question is, do you need an immutable log of all actions to be recorded? Blockchains work best with transactional data like financial transactions or insurance claim settlements, for example. For transactions like this, it makes sense to log them in a long chain of related data items. If this isn't something you intend to do, then a blockchain is the wrong solution. If you answered yes to all of those questions, then you've probably determined that a blockchain will be useful to your organization. At this point, you need to determine whether you are happy to use a public blockchain where everyone is participating in the network and can access and verify your data, or whether you want to use a private blockchain, which is more limited to a consortium of companies.

There are many emerging blockchain implementations, but if you look at the current major ones, we have, of course, the Bitcoin blockchain as the biggest one. Ethereum from Consensus and Microsoft is getting quite a bit of traction from the makers of non-financial applications. It is also the implementation that we will be using later in this course. IMB blockchain on Bluemix is also an alternative for those who want to create their blockchain.

# [Usages for blockchain](#toc.xhtml#s69a)
