
Downloading the Ethereum wallet can take some time, but the interface is very intuitive and the instructions provided throughout the process are easy to follow.

![tip](Image00003.jpg)Within the Ethereum wallet, you can win test ether to build your test contracts and organizations. You don’t need to mine ether to learn how it works.

## Mining for ether
Ethereum is kept running by a network of computers all over the world that are processing the contracts and securing the network. These computers are sometimes referred to as *nodes,* and they’re mining crypto Ether.

In order to reward individuals for the time and cost involved in mining, there is a prize of five ethers about every 12 seconds. The prize is given to the node that was able to create the latest block in the Ethereum blockchain.

All new blocks have a list of the latest transactions. The proof-of-work consensus algorithm guarantees that prizes are won most often by nodes with the most computational power. Computers that aren’t as powerful can win, too — it just takes longer. If you want to try your hand at mining ether, you can do it with your home computer, but it will take a very long time to successfully mine a block and win ether.

![warning](Image00006.jpg)Mining ether is not for the technical novice. You need to be familiar with `command line`. If you don’t have a clue what `command line` is, you probably want to skip this process. Also, be sure to follow the most up-to-date instructions on the Ethereum GitHub (`http://github.com/ethereum`).

## Setting up your Ethereum wallet
To set up your Ethereum wallet, follow these steps:

1. **Go to** `www.ethereum.org`.

2. **Click the Download button.**
You have to scroll down the page a bit to find the button.
![tip](Image00003.jpg)Be sure to save the Ethereum wallet download someplace you can find it later.

3. **Open the Ethereum wallet.**

4. **Click Use Test Net.**
Here you get set up to mine test ether. This process is much less time-consuming then real ether mining, but it still takes some time.

5. **Create a strong password.**
Don’t forget to save your password someplace safe.

6. **Click through the startup menu.**
The Ethereum team has a few tutorials that are interesting to review while you’re waiting on your test net to download. The download may take ten minutes or so.

7. **Choose** `Develop ⇒ Start Mining`.
Don’t skip this step. You need the ether for later projects.

You’ve just set up your wallet, and you’re earning test ether for your future smart contract projects.

## Building Your First Decentralized Autonomous Organization
DAOs will change how the world does business in the future. They allow anyone in the world to create a new type of company online that is governed by pre-agreed-upon rules that are then enforced through the blockchain network. Creating a DAO is easier than you might think. In this section, you build your first test DAO. I break this project into three sections: build, congress, and governance.

![remember](Image00004.jpg)In order to successfully complete your test DAO, you need to have set up your Ethereum wallet and done some mining on the Ethereum test net (see the preceding section).

Follow these steps to create your first test DAO:

1. **Go to** `www.ethereum.org/dao`.

2. **Scroll down the page to the Code box (shown in** [**Figure 5-3**](#text00009.html#c05-fig-0003) **) and copy the code.**

3. **Open the Ethereum wallet you made earlier.**
You’ll develop your DAO in your Ethereum wallet.

![ FIGURE 5-3:  The Code box.](Image00019.jpg)
[FIGURE 5-3:](#text00009.html#rc05-fig-0003)  The Code box.

### Test net and congress
The next phase of your DAO project is setting up the framework for your DAO. Follow these steps:

1. **In your Ethereum wallet, choose** `Develop ⇒ Network ⇒ Test Net`.

2. **Click the** `Contracts` **tab and then click** `Deploy Contract`.
The Ethereum team has set up a few test templates for DAOs.

3. **Paste the code you copied in the preceding section into the** `Solidity` **code box.**

4. **From the Contract Picker, choose** `Congress`.

5. **Pick some variables when prompted to do so.**
Here are your options:
* The *minimum quorum* for proposals is the fewest votes a proposal needs to have before it can be executed.
* The *minutes for debate* is the shortest amount of time, in minutes, that needs to pass before it can be executed.
* The *margin of votes* for a majority. Proposals pass if there are more than 50 percent of the votes plus the margin. Leave it at 0 for a simple majority.

### Governance and voting
Now you’re going to name and set up the governance of your DAO. You need to set up a *minimum quorum* for proposals (how many votes a new proposal needs to have before it is passed). You also set up the *margin of votes for a majority* (how many votes a plan needs to pass) and the time allotted for discussing new plans.

1. **Name your new DAO.**
This is kind of like naming a company.

2. **For Debate Times, select 5 minutes.**
This is how long new proposals are open for conversation.

3. **Leave Margin of Votes for Majority set to 0.**
This sets up how the democracy of your contract works.

4. **Confirm the price of the DAO.**
You’ve mined some Ether in the test net via your wallet when you first set up it up. If you skipped that step, go back and do it now. You need a little of the test net Ether to build your DAO.

5. **Click Deploy and type your password.**
The DAO may take some time to deploy. When you arrive at your new dashboard, scroll down, and you’ll be able to see your DAO being produced.

6. **Click the New icon.**
A new unique icon will generate that represents your DAO.

Congratulations! You’ve created your first DAO.

## Uncovering the Future of DAOs
Smart contracts and decentralized organizations hold a lot of promise. The pure democratic and hyper-rational nature of them is very appealing. However, at this point, there are more possibilities then knowns, and each contract that is created could be groundbreaking or a massive flop.

If you approach Ethereum as the new frontier that it is, you’ll have more success. The Ethereum network has more benefits than drawbacks if you’re careful. But expecting everything to work flawlessly and all the participants to act with integrity will open you up to greater losses. Ethereum has its share of bandits, not to mention those friendly enthusiasts who would like you to succeed.

The smart contract hacks of 2016 have highlighted the importance of security and properly reviewing contracts. It also illustrated that there are people with integrity that who fight to fix issues.

Reading this book is only the beginning. It will give you a sound bases to build your knowledge of Ethereum, but as with all new technologies, Ethereum is quickly evolving. Keep reviewing best practices and security measures.

In the following sections, I mention some things to keep in mind as you build your first few DAOs, build smart contracts, and debug your new blockchain systems.

### Putting money in a DAO
Don’t trust large sums of money to untested and contracts and contracts that haven’t been fully vetted. Large contracts are more often targeted by hackers. The DAO hack described earlier in this chapter (see the sidebar “[With great power comes … great power](#text00009.html#c05-fea-0001) ”) showed that even well thought-out contracts have unexpected weaknesses.

![remember](Image00004.jpg)Although, smart contracts and blockchains let you conduct business with anyone around the world, it’s still the early days. You can mitigate your risk by working only with known and trusted parties.
