
然而，当涉及对称密钥加密时，我们仍然面临密钥交换的问题。可以使用非对称密钥加密来解决这一问题。我们通过结合使用公钥和对称密钥加密来实现这一点。这种方法被称为混合密码系统。公钥可以用于保护对称密钥，从而避免任何人获取该对称密钥。此时的对称密钥有时被称为 `会话密钥`，因为它用于在两个系统之间的会话中加密数据。这种混合密码系统最常用于与 Web 服务器进行通信。

虽然可以使用 Diffie‑Hellman 来协商密钥派生，但在实际混合密码系统中并不常用。相反，双方中的任意一方会生成对称密钥。生成密钥后，公钥用于对其进行加密。在 Web 通信中，通常只有 Web 服务器持有公钥。这意味着客户端会生成会话（对称）密钥并将其发送给 Web 服务器，使用服务器的公钥对其进行加密。

### 非否认性

公钥加密的另一价值在于公钥和私钥分别属于个人或系统（取决于其最终用途）。我们可以利用已知个人的公钥。除了加密外，非对称密钥还可用于数字签名。消息使用某人的私钥进行签名，然后可以通过该人的公钥进行验证。此类情况下无需担心隐私，因为这仅是签名。它用于证明消息是由拥有私钥的个人生成的。证明消息来源于拥有私钥的所有者这一原则称为 `非否认性`。

公平地说，非否认性表示：当使用私钥发送消息时，私钥的所有者不能否认该消息来源于他们本人。这与前述表述的相反，但两种思考方式的含义相同，或至少产生相同的效果。术语 `非否认性` 的含义是：你不能通过声称消息不源自你自己而否定它。

这要求私钥必须得到保护。如果私钥没有任何方式保护而泄露，任何人都可以利用它。因此，保护密钥的意义各异。第一种是文件权限应仅允许文件所有者访问，这是保护的一部分，但并非全部。攻击者仍可能通过入侵该用户系统获取密钥。因此，使用密钥时需要密码。密码在密钥用于签名或签名失败之前会被请求。

### 椭圆曲线密码学

因素分解质数的方法长期被用于密钥生成，因为对这些巨大数字进行运算所需的时间和计算力是巨大的，但这并不是唯一生成密钥的方式。诸如因数分解质数等复杂问题被认为是不可解的，这意味着解决该问题所需的计算力是实质上难以企及的。大质数本身耗时，但随着计算能力的提升，解决这些问题变得更加容易，尤其是当计算成本大幅下降时。随着计算机变得显著更强大，使用多台机器同时处理复杂任务已不再困难。

椭圆曲线密码学（ECC）则采用不同的思路。它不依赖于因数分解质数等资源密集型计算，而是使用离散对数。人们认为，对随机椭圆曲线元素求离散对数在计算上不仅困难而且不可行。使用 ECC 时，密钥长度显著缩短，从而降低了加密和解密所需的计算资源。

椭圆曲线可以通过绘制多项式函数的图形来直观理解。例如，如 [Figure 13.4](#c13.xhtml#c13-fig-0004) 所示，函数 `y2 = x3 – x + 1` 的图形就是一个椭圆曲线的示例。对数是指数运算的逆运算，而离散对数是指使一个数值通过将另一个数值相乘得到目标值的指数。简单来说，它是索引。例如，若 `bk = a`，则 `k` 即为离散对数。因此，你选择曲线上的一个点，并求出对应的 `k` 值，这就是在 ECC 中使用的值。

```
![FIGURE 13.4 Elliptic curve](images/c13f004.png)
```

[**FIGURE 13.4**](#c13.xhtml#R_c13-fig-0004) 椭圆曲线

你可能会认为这并不困难。事实上，离散对数没有统一的计算方法。虽然存在某些特定情形下可以快速计算离散对数，但离散对数本身缺乏通用解法，给定离散对数 `x` 时，只有一种方式可以求解，这正是 ECC 的不可解性所在。与质数的因数分解不同，前者有已知的计算方法（尽管计算量大），而 ECC 之所以可行，是因为无法逆向求解。

或许更易理解的思路是：涉及大量变量多项式方程，不存在单一算法能够将曲线上的点逆转回原方程。缺乏能够解决（或逆向解决）所有方程的通用算法，使得该问题具有不可解性，从而能够创建难以破解的密钥。

你可以在前文的 Web 服务器扫描输出中看到 ECC 的使用。当在密码套件中看到 `ECDH` 时，指的是椭圆曲线 Diffie‑Hellman，这是一种利用椭圆曲线密码学的 Diffie‑Hellman 变体，用于密钥协商。

### 证书颁发机构与密钥管理

密钥是密码学的基石。没有密钥，我们就无法逆转加密过程。将可读文本转换为不可读内容很容易，而能够逆转的转换则是复<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> [content]...