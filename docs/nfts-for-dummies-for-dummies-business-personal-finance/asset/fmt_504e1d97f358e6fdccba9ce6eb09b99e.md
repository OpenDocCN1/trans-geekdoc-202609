
```solidity
pragma solidity 0.8.6;
contract LittleBear {
    event LogMsg(string message);
    string public storedMsg;
    constructor() {
        storedMsg = "Hello Little Bear (a.k.a. Maddie)!";
        emit LogMsg(storedMsg);
    }
    function updateMsg(string memory newMsg) public {
        storedMsg = newMsg;
        emit LogMsg(storedMsg);
    }
}
```

![Tip](images/tip.png) To avoid typos, you can copy-and-paste this snippet directly from [`www.seoyoungkim.com/nftfdcode.html`](http://www.seoyoungkim.com/nftfdcode.html).

![Warning](images/warning.png) Solidity is case sensitive, so `LogMsg` and `logmsg` aren't treated identically at compilation.

The remainder of this section explains the code, chunk by chunk.

This first line of code is the Solidity version pragma, which specifies the allowable version(s) of the Solidity compiler to be used at compilation. In this case, the version pragma allows the source code to be compiled only under version 0.8.6:

`pragma solidity 0.8.6;`

Next, you define the contract, `LittleBear` — Solidity is a *curly-bracket* language, which means it uses curly brackets to open and close blocks of code:

`contract LittleBear {`

The following line declares an event, `LogMsg`, that accepts a single argument of type `string`:

`event LogMsg(string message);`

The next line declares a public state variable, `storedMsg`, of type `string`. The latest content of `storedMsg` is retained in contract storage, even as the contract and its functions lie dormant between calls:

`string public storedMsg;`

The following block of code declares the special `constructor()` function, which is executed just once, at contract initiation. The first line of this function initializes the text being stored in the `storedMsg` state variable; the second line triggers the `LogMsg` event, passing the contents of `storedMsg` to be written to the contract's event log:

```solidity
constructor() {
    storedMsg = "Hello Little Bear (a.k.a. Maddie)!";
    emit LogMsg(storedMsg);
}
```

The following block of code declares a public function, `updateMsg()`, that accepts a single argument of type `string`. This parameter is defined by the name `newMsg` within this function and is declared as a memory variable, which means its contents aren't retained after the iteration of this function is complete. Without explicitly declaring the keyword `memory`, function parameters are, by default, memory variables as opposed to state variables:

```solidity
function updateMsg(string memory newMsg) public {
    storedMsg = newMsg;
    emit LogMsg(storedMsg);
}
```

The first line of this `updateMsg()` function replaces the text being stored in the `storedMsg` state variable with the text that was passed to this function when it was called. The second line triggers the `LogMsg` event so that the latest contents of `storedMsg` can be written to the contract's event log.

Finally, we complete the block of contract code with a closing curly bracket:

`}`

### Compiling before takeoff

After you prepare your `LittleBear.sol` file and add the necessary code, you can compile that code by following these steps:

1.  **Click the Compiler icon located in the navigation pane on the left, as shown in** [Figure 9-4](#c09.xhtml#c09-fig-0004)**.**

2.  **In the Solidity Compiler pane that appears, click the Compile LittleBear.sol button, as shown in** [Figure 9-5](#c09.xhtml#c09-fig-0005)**.**

    The compilation details for this contract appear underneath the Compile button, as shown in [Figure 9-6](#c09.xhtml#c09-fig-0006).

Excellent! You're now ready to deploy your smart contract.

![Remember](images/remember.png) After you deploy your smart contract, you can't go back and change any of the code. If you want to make corrections, you have to deploy a new smart contract with the updated code.

![FIGURE 9-4: LittleBear.sol source code, ready for compilation on Remix.](images/9781119843313-fg0904.png)

[FIGURE 9-4:](#c09.xhtml#rc09-fig-0004) LittleBear.sol source code, ready for compilation on Remix.

![FIGURE 9-5: Solidity Compiler on Remix.](images/9781119843313-fg0905.png)

[FIGURE 9-5:](#c09.xhtml#rc09-fig-0005) Solidity Compiler on Remix.

### Deploying

Before you get to the real thing, practice deploying this contract on your local Ganache environment (which we discuss in [Chapter 8](#c08.xhtml)).

1.  **Click the Ethereum icon in the navigation pane on the left (the icon beneath the Compiler icon).**

    This step opens the Deploy & Run Transactions pane, shown in [Figure 9-7](#c09.xhtml#c09-fig-0007).

    ![FIGURE 9-6: Accessing compilation details on Remix.](images/9781119843313-fg0906.png)

    [FIGURE 9-6:](#c09.xhtml#rc09-fig-0006) Accessing compilation details on Remix.

    ![FIGURE 9-7: Deploy & Run Transactions on Remix.](images/9781119843313-fg0907.png)

    [FIGURE 9-7:](#c09.xhtml#rc09-fig-0007) Deploy & Run Transactions on Remix.

2.  **Select the Injected Web3 option from the Environment drop-down menu.**

    Make sure to also

    1.  Sign in to the MetaMask browser extension by clicking the Fox icon on the browser toolbar. (See [Figure 9-8](#c09.xhtml#c09-fig-0008).)

    2.  Connect to the Handsomely-Vessel custom network.

    3.  Select one of your imported local Ganache accounts. In our case, we're choosing Ganache HV1.

    ![Remember](images/remember.png) You must also have the Ganache desktop application open and running the appropriate workspace — in this case, the Handsomely-Vessel workspace.

3.  **Select the LittleBear–LittleBear.sol contract from the Contract drop-down menu and then click the Deploy button. (See** [Figure 9-8](#c09.xhtml#c09-fig-0008)**.)**
    ![FIGURE 9-8: Deploying the LittleBear contract to the Handsomely-Vessel workspace in Ganache.](images/9781119843313-fg0908.png)

    [FIGURE 9-8:](#c09.xhtml#rc09-fig-0008) Deploying the LittleBear contract to the Handsomely-Vessel workspace in Ganache.

4.  **In the MetaMask notification pop-up that appears (see** [Figure 9-9](#c09.xhtml#c09-fig-0009)**), review the transaction details and click Confirm.**

    Clicking Confirm submits a transaction containing the compiled bytecode (without specifying a destination address), which generates a contract account with its own address for future access. If you realize that you're not ready to deploy your contract, simply click Reject.

    ![FIGURE 9-9: Confirming contract account creation on the Handsomely-Vessel workspace.](images/9781119843313-fg0909.png)

    [FIGURE 9-9:](#c09.xhtml#rc09-fig-0009) Confirming contract account creation on the Handsomely-Vessel workspace.

    You can now view and interact with this contract under the Deployed Contracts heading, as shown in [Figure 9-10](#c09.xhtml#c09-fig-0010):

    *   Click the `storedMsg` button to see what's currently stored in this state variable.
    *   Click the `updateMsg` button to call the function that updates the stored text in `storedMsg`, as shown in [Figure 9-11](#c09.xhtml#c09-fig-0011).

    ![FIGURE 9-10: Viewing deployed contracts on Remix.](images/9781119843313-fg0910.png)

    [FIGURE 9-10:](#c09.xhtml#rc09-fig-0010) Viewing deployed contracts on Remix.

    ![FIGURE 9-11: Interacting with deployed contracts on Remix.](images/9781119843313-fg0911.png)

    [FIGURE 9-11:](#c09.xhtml#rc09-fig-0011) Interacting with deployed contracts on Remix.

    ![Remember](images/remember.png) Executing the `updateMsg` function is a transaction on the EVM that requires gas, whereas simply viewing the contents of the `storedMsg` variable doesn't require gas. You notice a MetaMask notification pop-up, requiring confirmation every time you attempt to execute the `updateMsg` function.

Now that you've gotten your feet wet in the local Ganache environment, it's time to deploy our `LittleBear` contract to the Ropsten Testnet. Follow these steps:

1.  **Click the Fox icon in your browser toolbar to open MetaMask.**
