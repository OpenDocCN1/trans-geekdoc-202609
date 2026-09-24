
# 2021 第四届电子器件与机械工程国际会议 (ICEDME) (中国广州 2021.3.19-2021.3.21)

## 摘要

“华泰美诉同道开发”案由杭州互联网法院于2018年3月15日审理。法院判决华泰胜诉，并判处4,000元金赔偿。此案被视为区块链作为数字证据形式使用的先驱案例之一。该案通过经验证的无线秘密通信方案进行认证，以满足法律要求，确保数字证据安全地存储在区块链上，并由相关部门负责人激活设备。

《民事诉讼法》允许使用数字证据，因为任何使用的证据都应当是真实的、与案件相关的且通过合法途径获得的。许多人不愿接受数字证据，因为很难证明数字证据的真实性。

**关键词**——区块链；电子证据；司法鉴定；带外链聊天机器人

## I. 引言

大视宝（快报）是浙江省杭州的一份区域性报纸。华泰美是一家在杭州注册的公司。2013年7月24日，快报与华泰美签署了一份独家许可合同。该合同授予了快报在互联网上发布帖文文章的权利，以及在案件中起诉损害赔偿的权利。

2019年，人民法院发布了关于数字证据的指导意见。该意见明确列出了数字证据的形式以及检查数字证据是否真实的规则。

“华泰美诉同道开发”案发生在新指导意见发布之前。然而，该案的裁决直到现在仍为区块链如何作为证据提供启示。值得注意的是法院是如何处理此案的。

2017年，法学家们也写了一篇文章，法院判决也于7月24日发布。同一天，该文章在互联网上被转贴。总部位于广东省深圳的同道开发（TDD）是该网站的注册所有者。

法院考虑了三个因素：证据存储平台的资质、工具的可靠性以及基于区块链的证据的可信度。其推理与人们回答问题时的逻辑相似：人可以信任吗？他们有足够的工具吗？会交付产品吗？

转贴是在没有华泰美许可的情况下进行的。华泰美声称同道开发侵犯了其知识产权并起诉索赔。该案由杭州互联网法院于2018年3月15日审理。

法院首先查看是哪家公司运营证据存储平台。其股东与华泰美不同，其运营独立于华泰美和快报，作为一个第三方数字证据存储平台 [2]。

## II. 协议

### A. 保护协议

保护协议为客户提交的证据生成的哈希证据函数代码提供服务。证据协议下文描述并如图1所示。

#### 1) 初始化

客户端和服务器可以为自己生成不同的ID，为了符合法律要求，客户端需要通过合法服务器、合法服务器的预共享密钥获取其当前位置（`LOC`）。形式上，初始化过程如下：

- 客户端持有证据标识 `ID_c` 和 `LC`。
- 服务器持有标识 `ID_s` 和预设的证据有效期（`VP`）。
- 客户端持有要在区块链中保护的证据数据（`ED`）。
- 客户端和服务器共享 `K_c`。
- 客户端（`C`）生成随机值 `R_c` 并通过 `HTTPS` 发送给服务器（`S`）：

```
$M_1 = (LOC, R_c)$
```

- 服务器（`S`）生成 `EM` 并通过带外链通道发送给客户端（`C`）：

```
$M_2 = (ID_s, VP)$
```

- 客户端（`C`）生成证据标记 `EM` 并通过 `HTTPS` 发送给服务器（`S`）：

```
$M_3 = (ID_c, ED)$
```

- 服务器（`S`）生成随机值 `R_s` 并发送给客户端（`C`）：

```
$M_4 = (EM, R_s)$
```

- 客户端（`C`）计算哈希值 `H` 并通过 `HTTPS` 发送给服务器（`S`）：

```
$M_5 = (H, R_c, ED)$
```

- 服务器（`S`）验证哈希值并存储证据：

```
$H = H$
```

图1. 保护协议

### B. 验证协议

验证协议用于确认证据是否合法记录在区块链上。验证协议下文描述并如图2所示。

#### 1) 初始化

通常，某些实体（合法或非法）想要证明其持有证据数据（`ED'`）以验证（`V`）：

```
$M_1 = (ED', EM')$
```

该实体持有经过验证的信息：(`ED`, `EM`)。

#### 2) 验证阶段

- 实体（`E`）通过 `HTTPS` 通道向 `V` 发送 `M_1`：
  - `E → V; M_1 = (ED', EM')`。
- `V` 通过 `HTTPS` 通道向 `S` 发送 `M_2`：
  - `V → S; M_s = (ED', EM')`。
- 接收 `M_2` 后，`S` 使用 `EM` 在区块链上查找信息。如果 (`EM'`, `ID`, `IDs`， `TS`, `ET`, `NC`， `C_c`, `H`)，`S` 从 `NTSC` 获取时间戳（`TS`）：
  - 区块链：`S → (EM'`, `ID`, `IDs`, `TS`, `ET`, `LC`, `R_c`, `H_s)`；
  - `NTSC → S; TS`。
  - `S → V; VR = "错误的标记."`
- `S` 验证 `ET < TS`；`S` 通过 `HTTPS` 通道向 `V` 返回 `VR` 并终止协议：
  - `S → V; VR = "标记已过期."`
- `S` 使用 `NTSC` 验证 `ID` 是否有效。如果无效，`S` 通过 `HTTPS` 通道向 `V` 返回 `VR` 并终止协议：
  - `S → V; VR = "时间戳."`
- 接收到 `ID` 和 `H` 后，`S` 找到 (`ID_c`, `C_c`) 并验证 `ED`：`Hash(C_c) || R_c || IDs || ID || ED = ED`。
  - 如果等式失败，`S` 通过 `HTTPS` 通道向 `V` 返回 `VR` 并终止协议：
    - `S → V; VR = "已验证."`
  - 否则，`S` 通过 `HTTPS` 通道向 `V` 返回 `VR` 并终止协议：
    - `S → V; VR = "验证失败."`

## III. 结论

杭州互联网法院于 2018 年 3 月 15 日审理了华泰悦美诉腾高开发案。法院判决华泰胜诉，并判赔 金4000 元。这被视为区块链作为数字……形式的案例之一。在本案中，提出了一种基于位置的区块链保护方案，以安全地存储数字证据。

## 参考文献

- [1] M. Pourabjad et al., "Digital Forensics Architecture for Evidence Collection Preservation in IoT Environment Using Blockchain and Blockchain," in IEEE Access, 2019, pp. 15339–15349.
- [2] P. Rudy, "Internetropol review of digital evidence 2016 - 2019," in International Conference and Security Symposium, vol. 28, pp. 49980–49992.
- [3] R. Zhang, X. Xu, and J. Li, "Security and Privacy of Blockchain," in ACM Comput. Serv., vol. 53, no. 3, 1–34, 2020.
- [4] A et al., "Blockchain-based bitcoin payment system for digital evidence," IEEE Access, vol. 7, pp. 49906–49915, 2021.
- [5] M. Li, A. Xu, N. Wang, X. Huang, and J. Sheng, "Efficient Bitcoin Transaction in Public Transport System: A First Implementation Based on Blockchain," in 12th IEEE International Conference on Computer and Security, Suzhou, China, 2018.
- [6] N. Liu, L. Xing, J. Huang, and J. Poster, "A Framework for Identity Representation on Blockchain," in 12th IEEE International Conference on Security and Communications (Guangzhou), Guangzhou, Oct 10-12, pp. 751–754, 2016.
- [7] J. Cai and Y. Huang, "Unlinking Privacy-Preserving Identity Authentication Without Cost," in IEEE Access, vol. 6, pp. 18570–18581, 2018.
- [8] J. Zhang, X. Wang, and W. Yi, "Unlinking Privacy-Preserving Identity Authentication and Key Management for Disaster Scenarios," in IEEE International Journal of Things, vol. no. 1, pp. 878–890, 2020.
- [9] J. Zhang, N. Wang, and X. Xu, "A secure privacy system for network-based blockchain," IEEE Access, vol. 4, pp. 9259–9260, 2016.
- [10] D. Rachmaniev, J. Targaran, and A. B. Chen, "Comparative analysis of Blockchain and Smart Contract based applications," International Journal of Physics: Conference Series. Vol. 978. No. 1. IOP Publishing, 2018.
- [11] A. Khu, H. Al-Ahmed, and F. Taher, "Medical image protection and sharing using Blockchain and Smart Contracts," 2017, 26th IEEE International Conference on Electronics, Circuits and Systems (ICCS), Batumi, Georgia, pp. 397–400, 2017.
- [12] N. Liu and Y. Liu, “Access System for Intelligent Buildings,” in Proc. 9th IEEE International Conference on Mobile Communications Applications, Xi’an, China, pp. 11–17, 2016.
- [13] N. Xu, C. Jiang, X. Huang and D. Lu, "Role-Based Access Control System for Intelligent Buildings," 11th International Conference on Network and Security Science, Helsinki, 710–712, 2017.
