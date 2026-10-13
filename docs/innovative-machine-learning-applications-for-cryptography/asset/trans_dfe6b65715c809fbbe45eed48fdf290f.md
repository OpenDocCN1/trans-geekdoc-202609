
机器学习可用于利用 `DES` 等加密算法预测数据输入。使用支持向量机器学习，加密数据的第一个比特被更准确地预测的概率可能超过 50%，这比单纯猜测的预测效果更好。被认为是不可逆的单向函数的哈希函数的逆向工程，可以从机器学习中受益。该实验表明，我们猜测逆函数的准确率可超过 50%，这揭示了机器学习方法反转加密消息首个比特的效率高于猜测。尽管 `DES` 是一种较弱的加密方法，但该实验表明，尝试更复杂的方法（如用更强的加密标准 `AES` 替换 `DES`）可能是可行的。如果我们将相同的研究方法应用于更复杂的函数（如 `AES256`），我们可以以高于 50% 的准确率获得比猜测逆函数更好的结果。这引出了一个问题：预测两段加密数据的准确度能有多高？甚至更多？或者，机器学习算法能否正确预测完整的输入？换句话说，使用 `AES256` 或椭圆曲线加密等更强大的对称加密标准加密的单个加密数据片段，预测其准确度能有多高？

## 参考文献

*   Anees, A. (2022). Machine Learning and Applied Cryptography, Security and Communication networks. Wiley.
*   Armstrong, K. (2021). Applying machine learning to predict symmetric encryption algorithm inputs [Master Thesis]. Channel Islands, California State University.
*   AWS Dashboard. (n.d.). <https://awsacademy.instructure.com/>
*   Brownlee. (2021). Ensemble Learning Algorithms With Python. Academic Press.
*   Cui, X., Zhang, H., Fang, X., Wang, Y., Wang, D., Fan, F., & Shu, L. (2023). A Secret Key Classification Framework of Symmetric Encryption Algorithm Based on Deep Transfer Learning. Applied Sciences (Basel, Switzerland), 13(21), 12025. doi:[10.3390/app132112025](https://doi.org/10.3390/app132112025)
*   Dataoverhaulers. (n.d.). <https://dataoverhaulers.com/can-encrypted-data-be-hacked/>
*   Digital Guardian. (n.d.). <https://digitalguardian.com/blog/what-data-encryption>
*   Exchange, S. (n.d.). Hash Function on Finite Fields. <https://math.stackexchange.com/questions/1347240/how-to-attack-universal-hash-functio>
*   Github Code Resource. (n.d.). <https://github.com/kongfy/DES/blob/master/Riv85.txt>
*   Hitaj, Gasti, Ateniese, & Perez-Cruz. (2019). PassGAN: A Deep Learning Approach for Password Guessing. Academic Press.
*   MahmoodyM.MoranT.VadhanS. (2012). Publicly Verifiable Proofs of Sequential Work. Proceedings of the 4th Conference on Innovations in Theoretical Computer Science.
*   NgA.NotesL. (n.d.). <https://see.stanford.edu/materials/aimlcs229/cs229-notes3.pdf>
*   Open.edu. (n.d.). <https://www.open.edu/openlearn/science-maths-technology/computing-and-ict/systems-co>
*   Ouladj, M., & Guilley, S. (2021). Side-Channel Analysis of Embedded Systems: An Efficient Algorithmic Approach. Springer. doi:[10.1007/978-3-030-77222-2](https://doi.org/10.1007/978-3-030-77222-2)
*   Robin David. (n.d.). GITHUB python DES. <https://github.com/RobinDavid/pydes/blob/master/LICENSE.md>
*   Sectigostore. (n.d.). <https://sectigostore.com/blog/5-differences-between-symmetric-vs-asymmetric-encrypt>
*   Speciner, M., Perlman, R., & Kaufman, C. (2002). Network Security: Private Communications in a Public World. Prentice Hall PTR.
*   Tutorialspoint. (n.d.). <https://www.tutorialspoint.com/difference-between-private-key-and-public-key>
*   VTSCADA. (n.d.). <https://www.vtscada.com/help/Content/Scripting/Tasks/proEncryptionAnddecryption.htm>
*   Wang, L., & Machines, S. V. (2005). Theory and Applications. Springer.
*   YouTube. (n.d.). <https://youtu.be/Sy0sXa73PZA>

# 第 10 章

*   **Neethu Krishna**
    *   [![Orcid Image](i/orcid.svg)https://orcid.org/0000-0002-6061-9193](https://orcid.org/0000-0002-6061-9193)
    *   SCMS School of Engineering and Technology, Karukutty, India
*   **Kommisetti Murthy Raju**
    *   [![Orcid Image](i/orcid.svg)https://orcid.org/0000-0002-7576-4449](https://orcid.org/0000-0002-7576-4449)
    *   Shri Vishnu Engineering College For Women, India
*   **V. Dankan Gowda**
    *   [![Orcid Image](i/orcid.svg)https://orcid.org/0000-0003-0724-0333](https://orcid.org/0000-0003-0724-0333)
    *   BMS Institute of Technology and Management, India
*   **G. Arun**
    *   Erode Sengunthar Engineering College, India
*   **Sampathirao Suneetha**
    *   [![Orcid Image](i/orcid.svg)https://orcid.org/0009-0005-2714-6442](https://orcid.org/0009-0005-2714-6442)
    *   Andhra University College of Engineering, Andhra University, India

## 摘要

在密码学中，在不先解密的情况下对加密材料执行计算长期以来一直是一个愿望。这正是**同态加密（`HE`）**所实现的功能。通过允许对加密数据进行计算，相关敏感信息的隐私和安全性达到了前所未有的高度。本章深入探讨了 `HE` 广阔而复杂的领域、其基本理论以及对机器学习的深远影响。由于机器学习所基于的数据具有敏感性，隐私和安全问题经常出现。在这方面，允许算法从加密数据中学习并进行预测的同态加密，成为一种潜在的万能药。因此，作者在本章中旨在为更深入地理解这种协同效应奠定基础，展示它是如何存在的，以及未来将走向何方。

## 1. 同态加密简介

存在一类称为**同态加密（`HE`）**的加密方式，对象可以直接在密文上进行计算。解密后，结果与直接对明文应用这些操作所获得的结果完全相同。由于这一特殊属性，`HE` 成为安全数据处理的有效工具——敏感信息甚至在计算过程中也保持加密状态。同态 `HE` 的原理意味着结构在加密和计算之间前后存在且保持不变。例如，如果您有两个明文数字——比如 2 和 3——并希望以加密形式将它们相加，`HE` 允许您首先将它们转换为密文，然后在各自的加密形式上执行加法运算。解密结果将得到 5，这确实等于这两个原始数字的和。

### 历史背景与发展

同态加密的概念可以追溯到 `RSA`（1978 年发明）作为一种具有同态特性的算法的构想。但这仅限于特定操作。突破发生在 2009 年，当时斯坦福大学博士生 Craig Gentry 在其博士论文中首次开发了一种全同态加密方案。这是一个转折点，因为它证明了可以在加密数据上执行任意计算。

其最初的构建提案基于基于格的密码学（Suryawanshi and Abhay Chaturvedi, 2022）。它提出了一种加密方案，能够同态地评估其自身解密函数的电路。尽管这一首个方案具有革命性，但由于速度太慢且过于复杂而不切实际。但它为该领域的后续研究奠定了基础。
