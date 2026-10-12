
![Remember](images/remember.png) The `.sol` extension is used to indicate a Solidity source file. For more on Solidity, see [Chapter 9](#c09.xhtml).

![Tip](images/tip.png) At any time, click the Double Page icon, located on the toolbar running down the left side of the window, to return to the File Explorer browser pane.

### 4. Type the following code into the newly created `NFTFD.sol` file:

```
pragma solidity ^0.8.0;
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
contract NFTFD is ERC721URIStorage {
    address public founder;
    constructor() ERC721("NFTs For Dummies", "NFTFD") {
        founder = msg.sender;
        for (uint tokenID = 1; tokenID <= 5; tokenID++) {
            _mint(founder, tokenID);
            _setTokenURI(tokenID, "NFTFD Limited Edition Initial Release");
        }
    }
    function mintNFT(
        address to,
        uint256 tokenID,
        string memory tokenURI
    ) public {
        require(msg.sender == founder, "not an authorized minter");
        _mint(to, tokenID);
        _setTokenURI(tokenID, tokenURI);
    }
}
```

![Warning](images/warning.png) The `import "[...]/ERC721URIStorage.sol";` code line must be contained on a single line with no line breaks.

![Tip](images/tip.png) Avoid typos by directly copying and pasting this code from [`www.seoyoungkim.com/nftfdcode.html`](http://www.seoyoungkim.com/nftfdcode.html).

![Remember](images/remember.png) Solidity is case sensitive, so `ERC721URIStorage` and `erc721uristorage` aren't treated identically at compilation.

### 5. To compile the source code you just typed, click the Solidity-Compiler icon, located in the Navigation pane to the far left.

![Tip](images/tip.png) You can find the Solidity Compiler icon just below the File Explorers Double Page icon.

### 6. From the Solidity Compiler browser pane, click the Compile NFTFD.sol button.

![Technicalstuff](images/technicalstuff.png) The compilation details for this contract appear underneath the Compile NFTFD.sol button. This time, when you click the Contract drop-down menu that appears (as shown in [Figure 11-1](#c11.xhtml#c11-fig-0001)), the following contract names appear in addition to `NFTFD`:

*   `ERC721URIStorage`
*   `ERC721`
*   `IERC721`
*   `IERC721Receiver`
*   `IERC721Metadata`
*   `Address`
*   `Context`
*   `Strings`
*   `ERC165`
*   `IERC165`

![FIGURE 11-1: NFTFD and base contract compilation details on Remix.](images/9781119843313-fg1101.png)

[FIGURE 11-1:](#c11.xhtml#rc11-fig-0001) NFTFD and base contract compilation details on Remix.

![Technicalstuff](images/technicalstuff.png) If you take a closer look at the source code we have you type in Step 4, you notice the line `contract NFTFD is ERC721URIStorage {`. It tells you that the `NFTFD` contract is directly *derived* from the prebuilt base contract — `ERC721URIStorage` (imported from [`https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/extensions/ERC721URIStorage.sol`](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/extensions/ERC721URIStorage.sol)) — which is derived from the `ERC721` base contract, which itself is derived from the other interfaces and contracts in the preceding list.

### The play-by-play

The following is a chunk-by-chunk explanation of the `NFTFD.sol` code you use for your token contract. We also provide tips for whether you can easily customize elements of the code and not accidentally break something.

`pragma solidity ^0.8.0;`

**I.** This Solidity version pragma allows the source code to be compiled only under versions 0.8.x (including and following version 0.8.0 but strictly preceding version 0.9.0).

`import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/extensions/ERC721URIStorage.sol";`

**II.** The next line of code directs the compiler to import the `ERC721URIStorage` contract from OpenZeppelin's smart-contract library. This contract serves as the base from which we derive our own token contract.

If you visit this particular URL to take a peek at the code in the `ERC721URIStorage.sol` file, you notice that `ERC721URIStorage` is itself derived from OpenZeppelin's `ERC721` implementation, which is imported from [`https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/ERC721.sol`](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/ERC721.sol). The `ERC721URIStorage` contract provides enhanced functionality to `ERC721` by adding a means to setting and storing additional token-specific information *(tokenURI)* for each token.

`contract NFTFD is ERC721URIStorage {`

**III.** Next, we define our contract, `NFTFD`. The code here, through the keyword `is`, specifies that our new contract is derived from a base contract, `ERC721URIStorage`, which is contained in the `.sol` file we imported in the prior line of code. This feature is known as *inheritance*. Solidity permits multiple inheritance. A contract can inherit numerous other contracts either indirectly or directly:

*   **Indirectly:** If our own `NFTFD` contract directly inherits from `ERC721URIStorage`, it also indirectly inherits from `ERC721`, a "parent" to `ERC721URIStorage`.
*   **Directly:** You can specify direct inheritance by providing a comma-separated list of all base contracts you want your contract to inherit from.

![Tip](images/tip.png) You can type a name for your token contract that's different from NFTFD, which we've chosen, without having to alter other elements of the instructions or code to conform to your chosen contract name.

`address public founder;`

**IV.** This line declares a public state variable, `founder`, of type `address`. In the code the follows, this variable is assigned the account address of the token's founder, and is used to ensure that only the founder's account has the ability to mint new tokens.

`constructor() ERC721("NFTs For Dummies", "NFTFD") {`

**V.** This block of code declares the special `constructor()` function, which is executed just once at contract initiation. Notice the additional statement in the declaration: `ERC721("NFTs For Dummies", "NFTFD")`. This portion specifies the name and ticker, respectively, to be used in the `ERC721`'s `constructor` function.

![Tip](images/tip.png) You can customize the name of, and ticker for, your token to whatever you want without having to worry about remaining compatible with other parts of the code. Simply type a name and ticker to replace the strings "NFTs For Dummies" and "NFTFD" in the preceding `constructor()` declaration.

`founder = msg.sender;`

**VI.** Turning to the contents of the `constructor()` function, the first line of code (within the function's defining curly brackets) initializes the address being stored in the `founder` state variable as `msg.sender`, which contains the address of the account that has initiated the transaction. Specifically, `msg` is a global variable that contains information about the current transaction, and `sender` is a member of this object (known as a *struct* in Solidity). Because this code is part of the `constructor()` function, this line of code essentially stores the address of the account from which the token contract is deployed in the `founder` state variable.

```
for (uint tokenID = 1; tokenID <= 5; tokenID++) {
    _mint(founder, tokenID);
    _setTokenURI(tokenID, "NFTFD Limited Edition Initial Release");
}
```

**VII.** The next block of code implements a `for` loop that iteratively creates new tokens, numbered: 1, 2, 3, 4, and 5.

![Tip](images/tip.png) You can customize how many tokens to create by simply changing the number "5" in the `tokenID <= 5` portion of the code defining the `for` loop. *Be careful!* Selecting a large number dramatically increases the time and gas required to deploy your token contract.
