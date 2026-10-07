
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

### 4.4. 讨论

我们展示了一个使用 Polygon 网络和 IPFS 构建的安全文档管理系统原型。我们通过在 Mumbai 测试网络和本地 IPFS 服务器上部署，成功地测试了文档的创建、验证和共享。

# 5. 结论与未来展望

## 5.1. 结论

在回顾了关于 Polygon、可用区块链技术以及应用层模块和包的各种论文和博客后，我们确定了一个对终端用户最方便的解决方案。对数据库和文件管理系统进行了深入研究，发现 IPFS 是所提方案的最佳替代方案。我们实现了具有生成、验证、共享和通知系统等功能的解决方案。

## 5.2. 未来展望

在未来，可以对所提的方案进行改进。在上传到 IPFS 网络之前可以对文档进行加密。此外，在请求文档时，可以将支持文件共享给审批者。此外，还可以构建应用程序用户界面使其更加用户友好。

# 参考文献

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
