

以及我们生成的证书的 CID，即数据的加密哈希值。通过此 CID，我们可以从 IPFS 获取原始证书，并使用 "pdf-lib" npm 包获取所有数据字段。如果匹配，我们可以验证该证书已通过验证；否则，该证书未通过验证且不可信。

## 3.4. 证书共享与其他功能

经过身份认证的用户拥有一个仪表板（Dashboard）页面，他们可以在那里查看所有已生成的证书，并带有分享选项。通过该功能，用户可以选择允许系统中的特定用户（无论是另一个用户还是证明者）访问其文档，访问持续时间由用户定义。需要证书的用户需要输入接收者的邮箱地址和共享的天数。之后，另一个用户可以在其仪表板上与自己的证书一起看到这此证书。

由于安全存储在区块链上的文档 CID 是与接收者共享的，而不是文档本身，这确保了文档的安全性。为了提高用户体验，我们实现了一个通知系统。相关通知将展示给经过身份认证的用户。

## 4. 仿真与结果结果

本节描述了我们获得的实验结果。该实现分为三个模块：第一个模块是证书生成，第二模块重点介绍验证过程，第三个模块是证书共享。我们使用了 IPFS、React.js、Node.js、Express.js 和 Polygon (Matic) 作为区块链。智能合约用 Solidity 编写。

## 4.1. 软件规范

- 前端开发：ReactJS, Semantic UI
- 后端开发：NodeJS, IPFS, Polygon (Matic, 区块链网络)
- 软件包管理器：Node Package Manager (NPM)

## 4.2. Web门户界面

![](img/d513d62f05793611c13a01e05574c355_6_0.png)

图 1(a) 显示了申请者创建证书的步骤。从可用证书和表单选择要生成的证书。提交后，申请者将被重定向到仪表板，新证书将以待处理状态添加到其中。

图 1(b) 描绘了证书的审批流程。在申请新证书时，证书会出现在审批者的仪表板上，审批者可以批准或拒绝该证书。审批者可以点击“查看”按钮查看文档详情。Shikhar Sarang 等人 / Procedia Computer Science 215 (2022) 340–349，在批准或拒绝后，申请者会收到其仪表板上的通知，状态也会随改变。

![](img/d513d62f05793611c13a01e05574c355_7_0.png)

图 2. (a) 证明者在审批前的证书视图和 (b) 证书视图

为了验证身份，在证书被批准之前，证明者可以如图 2(a) 所示查看证书。用户可以在验证页面上通过上传任何现有证书来使用证书验证功能，如图 2(b) 所示。

![](img/d513d62f05793611c13a01e05574c355_7_1.png)

图 3. 证书共享

用户可以使用已批准证书的共享功能。如图 3 所示，一旦证书被共享，接收者就会在其仪表板上收到一条通知。

## 4.3. 智能合约实现

实现的合约：IdentificationCertificateContract.sol, PassportCertiContract.sol, BirthCertificateContract.sol, Dashboard.sol,ShareCertificateContract.sol, Login.sol, NotificationContract.sol

下面列出了一些重要的函数：

```solidity
function newIdentificationCertificate(string memory accName, string memory _name, _number, string memory _ipsfHash, string memory _description)
public {
    IdentificationCertificate memory c;
    c.ipsfHash = _ipsfHash;
    c.description = _description;
    c.name = _name;
    c.number = _number;
    c.state = 0;
    c.accName = _accName;
    IdentificationCertificates[accName] = c;
    IdentificationQueue memory b;
    b.state = 0;
    b.accName = accName;
    enqueueIdentificationCertificate(b);
}
```

```solidity
function approveIdentificationCertificate(string memory accName) {
    IdentificationCertificate memory c = IdentificationCertificates[accName];
    if(c.state != 0) return;
    c.state = 2;
    IdentificationCertificates[accName] = c;
    updateIdentityCard();
}
```

```solidity
function getIdentificationCertificate(string memory accName) public view
(IdentificationCertificate memory) {
    return IdentificationCertificates[accName];
}
```

```solidity
function shareCertificate(string memory sharerAccName, string memory sharedToAccName, uint typeCert, uint time, string memory timeSharing) public {
    uint userId = accountName[sharerAccName];
    uint viewerId = accountName[sharedToAccName];
    require(userId >= 1, "User not found");
    require(viewerId >= 1, "Viewer not found");
    require(userId != viewerId, "You can't share with yourself");
    SharedCertificate memory b;
    b.sharerAccName = sharerAccName;
    b.timeSharing = timeSharing;
    b.time = time;
    b.typeCert = typeCert;
    userHasAccessCertificate[sharedToAccName].push(b);
}
```

```solidity
function getSharedCertificate(string memory accName) public view
(SharedCertificate memory b) {
    b = userHasAccessCertificate[accName];
}
```

## 4.4. 讨论

我们展示了一个使用 Polygon 网络和 IPFS 构建的安全文档管理系统原型。我们通过在 Mumbai 测试网络和本地 IPFS 服务器上部署，成功地测试了文档的创建、验证和共享。

## 5. 结论与未来展望

### 5.1. 结论

在回顾了关于 Polygon、可用区块链技术以及应用层模块和包的各种论文和博客后，我们确定了一个对终端用户最方便的解决方案。对数据库和文件管理系统进行了深入研究，发现 IPFS 是所提方案的最佳替代方案。我们实现了具有生成、验证、共享和通知系统等功能的解决方案。

### 5.2. 未来展望

在未来，可以对所提的方案进行改进。在上传到 IPFS 网络之前可以对文档进行加密。此外，在请求文档时，可以将支持文件共享给审批者。此外，还可以构建应用程序用户界面使其更加用户友好。

## 参考文献

- [1] "India reported 18% rise in cyber crime in 2020; 578 incidents of 'fake news on social media:'" The Hindu, Sep. 2021. 访问于 04.10.2021.
- [2] NCR, Crime in India 2020.
- [3] "Blockchain technology: principles and applications;" Sep. 2015.
- [4] M. Miluni, W. He, and M. Kanwal, "Proof of luck: An efficient consensus protocol," in 11th Workshop on Software Engineering for Trusted Systems, pp. 1–6, 2016.
- [5] G. Meiklelein, M. Portile, G. Skelen, D. McCoy, G. Voeler, and S. Savage, "A fistful of bitcoins: characterizing payments," pp. 127–140, 2013.
- [6] "Performance and scalability of blockchain networks and smart contracts," 2017.
- [7] "Smart Contracts Implementation, Applications, Benefits, and Limitations," Journal of Information and Applications, Oct. 2019.
- [8] "What Are DApps? The Decentralized Future," May 2019. 访问于 03.12.2021.
- [9] "Introducing LEGITDOC;" 访问于 04.10.2021.
- [10] "Introducing Blockchain." 访问于 04.10.2021.
- [11] "Hyperledger - Open Source Blockchain Technologies;" 访问于 04.10.2021.
- [12] "More Virtual Alternatives to Ethereum: A Handy Guide -- Blog," Apr. 2020. 访问于 03.12.2021.
- [13] "Ethereum vs Polygon: Which One Is Better for NFT?" Feb. 2022. Section: NFT.
- [14] "Solana and Polygon: A Detailed Comparison," Feb. 2022. 访问于 16.03.2022.
- [15] "What is MongoDB? A definition from Whabs.com." 访问于 16.03.2022.
- [16] "InterPlanetary File System," Mar. 2022. Page Version ID: 107559789.
- [17] "IPFS: Distributed File System." 访问于 16.03.2022.
- [18] "Will Blockchain Replace MySQL and SQL?" Wiredelta,” 访问于 16.03.2022.
- [19] "BigchainDB: The blockchain database..." 访问于 16.03.2022.

