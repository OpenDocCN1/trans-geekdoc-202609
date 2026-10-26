```
```solidity
function pickWinner() public restricted {
    uint index = random() % contestants.length;
    contestants[index].transfer(this.balance);
    contestants = new address[](0);
}
```
```

**FIGURE 9.22**  Updated pickWinner() function.

Above line of code creates a new dynamic array of type address. “(0)” marks that we want to create a new array of type address. We want that array to be dynamic in nature and have an initial size of 0.

# 9.10  REQUIRING MANAGERS

Our random function is pseudo random in nature. So, if some stranger realized that if they called “pickWinner” function at the right time, they would potentially make sure that a given player won the lottery.

So, in short we want to make sure that solely the executive is able to call that pickWinner function.

Inside the pickWinner function, we need to update the code shown below.

```
```solidity
modifier restricted() {
    require(msg.sender == executive);
    _;
}
```
```

# 9.11  SMART CONTRACT FILES

A final smart contract consists of many files associated with its deployment, testing, compilation, file containing installed dependencies, etc. For Lottery contract, we have five files, namely Lottery.sol file, this file contains set of rules/logic to handle the state of the asset stored in the smart contract. Then, we have Lottery.test.js file, this file contains all the test cases for our smart contract. Another files are package.json file, compile.js file, and deploy.js file. Detailed view of all these files is given in further section.

# 9.11.1  PACKAGE.JSON FILE

This file shows the complete information about the project, the installed dependencies, the start scripts, test scripts, and build scripts. This file gives an idea about the project and how to execute the project.