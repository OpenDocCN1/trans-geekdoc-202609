
In this section, you dive into building your first blockchain. You build it in two steps. The first step is to prepare your computer to create your private blockchain. Don’t worry — it’s made easier with tools from Docker and work that has been done by talented developers on GitHub. The second step is building your blockchain inside your Docker terminal.

## Preparing your computer
You need to download some software on to your computer in order to try this blockchain project. Start by downloading the Docker Toolbox. Go to [`www.docker.com/toolbox`](http://www.docker.com/toolbox) to download the correct version for your operating system.
Next, download GitHub Desktop. Go to [`http://desktop.github.com`](http://desktop.github.com). After you’ve installed GitHub Desktop, create a GitHub account at [`www.github.com`](http://www.github.com) by clicking Sign Up and entering a username, email address, and password, and then clicking the Sign Up for GitHub button.
Now you need to create a place to store your blockchain data. Create a folder on your computer’s desktop called `ethereum`. You’ll use this folder to hold your future repository and other files. Follow these steps to complete the process:
1. **Open GitHub Desktop.**
2. **Sign into the GitHub Desktop application on your computer with your new GitHub account.**
3. **Return to your web browser and go to** [`www.github.com/Capgemini-AIE/ethereum-docker`](https://www.github.com/Capgemini-AIE/ethereum-docker)**.**
You see the page shown in [Figure 3-4](#text00006.html#c03-fig-0004).
4. **Click the Clone or Download button.**
You’ll be given two choices: Open in Desktop or Download Zip (see [Figure 3-5](#text00006.html#c03-fig-0005)).
5. **Select the Open in Desktop option.**
The GitHub Desktop application will reopens.
**In the GitHub Desktop application, navigate to the project folder** `ethereum` **and click Clone.**
![ FIGURE 3-4:  Navigate to this page at GitHub.](Image00013.jpg)
[FIGURE 3-4:](#text00006.html#rc03-fig-0004)  Navigate to this page at GitHub.
![ FIGURE 3-5:  Open in Desktop.](Image00014.jpg)
[FIGURE 3-5:](#text00006.html#rc03-fig-0005)  Open in Desktop.
Cloning from GitHub copies the information you need to build your new blockchain. Follow the steps in the next section to get started building your private blockchain.

## Building your blockchain
You’re going to use the free Docker Quick Start Terminal tool to build your blockchain. It gives you access to a virtual machine, cutting down the time required to set up and debug your system. Because of these features, it lets you create a stable environment for your blockchain, so you don’t have to worry about the settings on your machine, and you can get up and running faster.
Follow these steps:
1. **Launch Docker on your computer using the Docker Quick Start Terminal.**
![tip](Image00003.jpg)The Quick Start Terminal should be located with your applications or on your desktop.
The Docker application launches a terminal you will use to build your blockchain.
2. **Change directories in the terminal to** `ethereum`.
The files you create making the new blockchain will go into the desktop file you made in the preceding section. You need to give a command to the terminal in order to change directories. If you’re on a Mac or running Linux, enter the following command:
`cd ~ /Desktop/ethereum/ethereum-docker/`
If you’re on a PC, enter the following command:
`cd ~ \Desktop\ethereum\ethereum-docker\`
![tip](Image00003.jpg)If these commands don’t work for some reason, search the web for tutorials that explain how to change directories for your type of system.
Now you can utilize the Ethereum–Docker files.
3. **Create one standalone Ethereum node by entering the following command into your terminal:**
`docker-compose -f docker-compose-standalone.yml up -d`
This one line of code will have created the following:
* One Ethereum bootstrapped container
* One Ethereum container that connects to the bootstrapped container
* One Netstats container with a web UI to view activity in the cluster
4. **Take a look at your new blockchain by opening a web browser and going to** `http://$(docker-machine ip default):3000`.
Congratulations! You’ve built your own private blockchain. If you’re so inclined, say a word of thanks to Graham Taylor and Andrew Dong, who put a lot of time into creating the Ethereum–Docker integration.

# Part 2

## Developing Your Knowledge
IN THIS PART …
Discover the beginning of blockchain technology with the Bitcoin blockchain.
Clarify your knowledge of the Ethereum network, and expand your understanding of decentralized autonomous organizations and smart contracts.
Identify the core concepts of the Ripple network and how it exchanges almost any type of value instantly.
Evaluate the Factom blockchain and its ability to secure data and systems.
Dig into the high-speed DigiByte blockchain, and learn about some of the fun applications being built around blockchain technology.

# Chapter 4

## Beholding the Bitcoin Blockchain
IN THIS CHAPTER
![check](Image00001.jpg)**Understanding where the Bitcoin blockchain came from**
![check](Image00001.jpg)**Straightening out some myths about Bitcoin**
![check](Image00001.jpg)**Staying safe when using Bitcoin**
![check](Image00001.jpg)**Mining for Bitcoins**
![check](Image00001.jpg)**Making a paper wallet to hold your Bitcoins**
Warning! After reading this chapter, you may become hooked on this cool emerging technology. Read at your own peril.
Bitcoin demonstrates the purest aspects of blockchain technology. It’s the baseline that all other blockchains are compared to and the framework that nearly all have drawn upon. Knowing the basics of how the Bitcoin blockchain operates will allow you to better understand all the other technology you encounter in this ecosystem.
In this chapter, I fill you in on the fundamentals of how the Bitcoin blockchain operates. I offer safety tips that will make your Bitcoin experience smoother and more successful. I also show you practical things you can start doing now with Bitcoin. In these pages, you find out how to mine the Bitcoin token, giving you a new way to get your hands on Bitcoins without buying them. Finally, you discover how to transfer your tokens to paper wallets, and other practical ways to keep your tokens safe online.

### Getting a Brief History of the Bitcoin Blockchain
Bitcoin and the concept of its blockchain were first introduced in the fall of 2008 as a whitepaper and later released as open-source software in 2009. (You can read the Bitcoin whitepaper at [`www.bitcoin.org/bitcoin.pdf`](http://www.bitcoin.org/bitcoin.pdf).)
The author who first introduced Bitcoin in that 2008 whitepaper is an anonymous programmer or cohort working under the name of Satoshi Nakamoto. Nakamoto collaborated with many other open-source developers on Bitcoin until 2010. This individual or group has since stopped its involvement in the project and transferred control to prominent Bitcoin core developers. There have been many claims and theories concerning the identity of Nakamoto, but none of them have been confirmed as of this writing.
Regardless, what Nakamoto created is an extraordinary peer-to-peer payment system that enables users to send Bitcoin, the value transfer token, directly and without an intermediary to hold the two parties accountable. The network itself acts as the intermediary by verifying the transactions and assuring that no one tries to cheat the system by spending Bitcoins twice.
