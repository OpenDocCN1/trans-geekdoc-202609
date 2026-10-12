

![Remember](images/remember.png) `.sol` 扩展名用于表示 Solidity 源文件。有关 Solidity 的更多信息，请参阅 [第 9 章](#c09.xhtml)。

![Tip](images/tip.png) 随时单击窗口左侧工具栏上垂直排列的“双页”图标，即可返回到“文件浏览器”浏览器窗格。

### 4. 将以下代码输入到新创建的 `NFTFD.sol` 文件中：

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

![Warning](images/warning.png) `import "[...]/ERC721URIStorage.sol";` 这行代码必须包含在单行中，不能有换行。

![Tip](images/tip.png) 直接从 [`www.seoyoungkim.com/nftfdcode.html`](http://www.seoyoungkim.com/nftfdcode.html) 复制并粘贴此代码，以避免拼写错误。

![Remember](images/remember.png) Solidity 区分大小写，因此在编译时 `ERC721URIStorage` 和 `erc721uristorage` 不会被视为相同。

### 5. 要编译刚才输入的源代码，请单击最左侧导航窗格中的 Solidity 编译器图标。

![Tip](images/tip.png) 你可以在“文件浏览器”双页图标的正下方找到 Solidity 编译器图标。

### 6. 在 Solidity 编译器浏览器窗格中，单击“编译 NFTFD.sol”按钮。

![Technicalstuff](images/technicalstuff.png) 该合约的编译详细信息显示在“编译 NFTFD.sol”按钮下方。这一次，当你单击出现的“合约”下拉菜单（如 [图 11-1](#c11.xhtml#c11-fig-0001) 所示）时，除了 `NFTFD` 之外，还会出现以下合约名称：

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

![图 11-1：Remix 上的 NFTFD 和基础合约编译详情。](images/9781119843313-fg1101.png)

[图 11-1：](#c11.xhtml#rc11-fig-0001) Remix 上的 NFTFD 和基础合约编译详情。

![Technicalstuff](images/technicalstuff.png) 如果你仔细查看第 4 步中让你输入的源代码，会注意到这一行：`contract NFTFD is ERC721URIStorage {`。它告诉你 `NFTFD` 合约直接*派生*自预构建的基础合约 `ERC721URIStorage`（从 [`https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/extensions/ERC721URIStorage.sol`](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/extensions/ERC721URIStorage.sol) 导入），而后者又派生自 `ERC721` 基础合约，后者本身又派生自前面列表中的其他接口和合约。

### 逐步解析

以下是你用于代币合约的 `NFTFD.sol` 代码的分块解释。我们还提供了一些提示，说明你是否可以轻松自定义代码元素，而不会意外破坏某些功能。

`pragma solidity ^0.8.0;`

**I.** 此 Solidity 版本编译指令仅允许在 0.8.x 版本下编译源代码（包括 0.8.0 及后续版本，但严格早于 0.9.0 版本）。

`import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/extensions/ERC721URIStorage.sol";`

**II.** 下一行代码指示编译器从 OpenZeppelin 的智能合约库导入 `ERC721URIStorage` 合约。该合约作为基础合约，我们从中派生出自己的代币合约。

如果你访问这个特定的 URL 查看 `ERC721URIStorage.sol` 文件中的代码，你会注意到 `ERC721URIStorage` 本身派生自 OpenZeppelin 的 `ERC721` 实现，后者从 [`https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/ERC721.sol`](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/ERC721.sol) 导入。`ERC721URIStorage` 合约通过增加一种为每个代币设置和存储额外代币特定信息 *(tokenURI)* 的方式，增强了 `ERC721` 的功能。

`contract NFTFD is ERC721URIStorage {`

**III.** 接下来，我们定义自己的合约 `NFTFD`。此处的代码通过关键字 `is` 指定我们的新合约派生自一个基础合约 `ERC721URIStorage`，该合约包含在上一行代码导入的 `.sol` 文件中。此功能称为*继承*。Solidity 允许多重继承。一个合约可以间接或直接继承多个其他合约：

*   **间接继承：** 如果我们自己的 `NFTFD` 合约直接继承自 `ERC721URIStorage`，它也会间接继承自 `ERC721`，后者是 `ERC721URIStorage` 的“父级”。
*   **直接继承：** 你可以通过提供一个逗号分隔的列表，列出你想让你的合约继承的所有基础合约，来指定直接继承。

![Tip](images/tip.png) 你可以为你的代币合约输入一个不同于 NFTFD 的名称（这是我们选择的），而无需更改说明或代码的其他元素以符合你选择的合约名称。

`address public founder;`

**IV.** 此行声明了一个类型为 `address` 的公共状态变量 `founder`。在后续代码中，该变量被赋值为代币创始人的账户地址，并用于确保只有创始人的账户有能力铸造新代币。

`constructor() ERC721("NFTs For Dummies", "NFTFD") {`

**V.** 此代码块声明了特殊的 `constructor()` 函数，该函数仅在合约初始化时执行一次。请注意声明中的附加语句：`ERC721("NFTs For Dummies", "NFTFD")`。此部分指定了分别用于 `ERC721` 的 `constructor` 函数中的名称和代号。

![Tip](images/tip.png) 你可以将代币的名称和代号自定义为任何你想要的内容，而无需担心与代码的其他部分保持兼容。只需在前面的 `constructor()` 声明中用字符串替换 "NFTs For Dummies" 和 "NFTFD" 即可。

`founder = msg.sender;`

**VI.** 转到 `constructor()` 函数的内容，函数定义花括号内的第一行代码将存储在 `founder` 状态变量中的地址初始化为 `msg.sender`，后者包含发起交易的账户地址。具体来说，`msg` 是一个包含当前交易信息的全局变量，而 `sender` 是该对象的一个成员（在 Solidity 中称为*结构体*）。因为这段代码是 `constructor()` 函数的一部分，所以这行代码本质上将部署代币合约的账户地址存储在 `founder` 状态变量中。

```
for (uint tokenID = 1; tokenID <= 5; tokenID++) {
    _mint(founder, tokenID);
    _setTokenURI(tokenID, "NFTFD Limited Edition Initial Release");
}
```

**VII.** 下一个代码块实现了一个 `for` 循环，迭代创建编号为 1、2、3、4 和 5 的新代币。

![Tip](images/tip.png) 你可以通过简单地更改定义 `for` 循环的代码中 `tokenID <= 5` 部分的数字“5”来自定义创建多少个代币。*小心！* 选择一个大数字会显著增加部署代币合约所需的时间和 Gas 费。

