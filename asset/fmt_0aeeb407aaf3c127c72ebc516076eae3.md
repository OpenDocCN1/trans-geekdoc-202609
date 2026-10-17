
## 参考文献

15. D. Boneh, X. Boyen, and H. Shacham, “Short group signatures,” in *Annual International Cryptology Conference*, 2004, pp. 41–55.

16. C. Delerablée, “Identity-based broadcast encryption with constant size ciphertexts and private keys,” in *International Conference on the Theory and Application of Cryptology and Information Security*, 2007, pp. 200–215.

17. M. Abdalla, M. Bellare, and P. Rogaway, “DHAES: An encryption scheme based on the Diffie-Hellman problem,” *Cryptology ePrint Archive*, Report 1999/007, <https://eprint.iacr.org/1999/007>.

18. J. Groth, and A. Sahai, “Efficient non-interactive proof systems for bilinear groups,” in *Annual International Conference on the Theory and Applications of Cryptographic Techniques*, 2008, pp. 415–432.

19. M. Bellare, and A. Palacio, “The knowledge-of-exponent assumptions and 3-round zero-knowledge protocols,” in *Annual International Cryptology Conference*, 2004, pp. 273–289.

20. D. Boneh, and M. Franklin, “Identity-based encryption from the Weil pairing,” in *Annual International Cryptology Conference*, 2001, pp. 213–229.

21. M. H. Ameri, M. Delavar, J. Mohajeri, and M. Salmasizadeh, “A key-policy attribute-based temporary keyword search scheme for secure cloud storage,” IEEE Trans. Cloud Comput., vol. 8, no. 3, pp. 660–671, 2020, [`doi.org/10.1109/TCC.2018.2825983`](https://doi.org/10.1109/TCC.2018.2825983).

22. M. Backes, D. Fiore, and R. M. Reischuk, “Verifiable delegation of computation on outsourced data,” in *Proceedings of the 2013 ACM SIGSAC Conference on Computer & Communications Security*, 2013, pp. 863–874.

23. D. Boneh, and X. Boyen, “Efficient selective-ID secure identity-based encryption without random oracles,” in *International Conference on the Theory and Applications of Cryptographic Techniques*, 2004, pp. 223–238.

24. D. Boneh, X. Boyen, and E.-J. Goh, “Hierarchical identity based encryption with constant size ciphertext,” in *Annual International Conference on the Theory and Applications of Cryptographic Techniques*, 2005, pp. 440–456.

25. C. Delerablée, and D. Pointcheval, “Dynamic threshold public-key encryption,” in *Annual International Cryptology Conference*, 2008, pp. 317–334.

26. C. Gentry, “Practical identity-based encryption without random oracles,” in *Annual International Conference on the Theory and Applications of Cryptographic Techniques*, 2006, pp. 445–464.

# 第 5 章 公钥设置下的可搜索加密

与对称密钥设置相比，**公钥设置下的可搜索加密**提供了灵活性，因为用户之间不需要复杂的密钥共享过程，这使其适用于多用户共享云存储环境。由于存储成本优化、数据管理便捷以及随时随地访问等特性，云存储在组织中变得非常流行，并逐渐成为一种必需品。然而，由于安全顾虑，组织在采用该平台时感到有些犹豫。如果数据以明文形式原样存储在第三方云服务器上，则可能不安全。为解决信任问题，建议以加密形式存储数据。这解决了问题；然而，数据的选择性访问变得不可行。一个简单的解决方案是先下载所有数据并在本地解密，但在这种情况下，如果一切都要手动完成，为什么还要使用云存储？用户必须能够从存储在云服务器上的加密数据中仅检索所需数据。检索所需数据的首要要求是在加密数据上执行搜索的能力。可搜索加密技术在此场景中发挥着关键作用。众所周知，可搜索加密可以使用对称密钥或公钥设置来开发。使用对称密钥设置为共享云存储环境创建可搜索加密方案，在云用户之间共享密钥方面可能会导致大量复杂性。随着用户数量的增加，内部密钥分发过程也变得困难。因此，首选公钥设置。在本章中，我们将讨论公钥设置下可搜索加密方案的各个方面。

## 5.1 系统定义与系统模型

在本节中，我们将通过引入可搜索加密方案中涉及的不同算法来正式定义可搜索加密，并利用第 4 章中给出的概率定义，为可搜索加密方案提供正确性条件。此外，我们将讨论可搜索加密系统的架构，并解释系统中各实体的角色。

### 5.1.1 系统定义

与任何加密方案一样，可搜索加密方案也由四个基本算法组成：密钥生成、索引生成、陷门生成和搜索。这些算法源自加密方案中的算法，我们将在此讨论每个算法与任何标准公钥加密（`PKE`）方案中算法的相似性和关系。

*   `[K_pub, K_pri] ← GenKey(1^n)`：此处的密钥生成算法与任何标准 `PKE` 方案中的相同。该算法也接受安全参数（一元格式）并输出公钥和私钥对，就像任何 `PKE` 方案一样。

*   `C_j ← GenIndex(K_pub, w_j)`：索引生成算法与任何 `PKE` 方案中的加密算法相同。它也接受公钥，并使用该公钥加密与数据文件关联的关键词。通常，在 `PKE` 方案中，我们使用公钥加密消息，此处消息等同于关键词。关键词密文的集合有时称为加密索引，因为云服务器默认实现直接或倒排索引方法来存储加密数据文件及其关联的加密关键词。因此，在可搜索加密的背景下，该算法称为索引生成算法；否则，它仅仅是一个加密算法。

*   `T_i ← GenTrap(K_pri, w_i)`：陷门生成算法在输入方面（即用户的私钥）与 `PKE` 方案中的解密算法相似。但在此步骤不接受密文，可搜索加密方案将其保留用于搜索步骤。通常，密钥用于解密，但这里我们希望使用该密钥将搜索能力委托给云服务器，同时不泄露它。此处，对于我们要搜索的每个关键词，我们生成一种该关键词的密钥，在密码学界，这称为搜索陷门，有时也称为搜索令牌。搜索陷门就像普通的计算机陷门一样，便于云服务器在加密数据上执行搜索。

*   `0/1 ← Search(T_i, C_j)`：搜索算法是针对 `PKE` 方案的新算法。该算法使用关键词的陷门，搜索每个密文以查找该关键词。如果找到匹配项则返回 1，否则返回 0。有时方案会明确显示返回与该关键词关联的数据文件引用；否则，隐含假设相关数据文件将提供给生成陷门的用户。

```
Pr[[K_pub, K_pri] ← GenKey[1^n]; C ← GenIndex[K_pub, w]; T ← GenTrap[K_pri, w]: 1 ← Search[T, C]] = 1
```

(5.1)

公式 5.1 表明，我们进行了一个实验：生成了一对公私钥，使用公钥适当加密一个关键词以获得其密文，并使用相应的私钥为同一关键词生成陷门。之后，将密文和搜索陷门同时提供给搜索算法。如果搜索算法以概率 1 返回二进制值 1，则称我们的方案始终正确。

### 系统定义变体

这是我们讨论过的一个综合系统定义；然而，在文献中存在该定义的一些变体，具体取决于开发可搜索加密方案所使用的方法类型和底层技术。可搜索加密方案既可以使用底层加密方案的核心进行设计（如我们上面刚讨论的），也可以使用一种将底层加密方案转换为可搜索加密的变换方法。使用变换方法开发的可搜索加密方案的系统定义如下：

*   `[PK[SE], SK[SE]] ← GenKey(1^n, W)`：该算法类似于上述的密钥生成算法。但这里还额外接受一个参数——关键词空间。关键词空间用于将其映射到身份空间（如果使用基于身份的加密（`IBE`）方案作为底层方案）或属性空间（如果使用基于属性的加密（`ABE`）方案作为底层方案）。该算法只是使用合适的映射运行底层加密方案的建立算法。底层加密方案的公共参数 `PP` 被用作可搜索加密方案的公钥 `PK[SE]`（除了底层加密方案的公共参数外，它可能还包含一些其他参数，例如用于映射目的的哈希函数），而主密钥 `MSK` 被用作可搜索加密方案中相应的私钥 `SK[SE]`。

*   `T[i] ← GenTrap(SK[SE], w[i])`：该算法内部调用底层加密方案的密钥生成算法；关键词在通过某个哈希函数映射后作为输入。例如：如果使用 `IBE` 作为底层方案，则使用哈希函数 `H`，它将每个关键词映射到身份空间中的唯一身份，`T[i] ← GenKey(MSK[IBE], H(w[i]))`。

*   `C[i] ← GenIndex(PK[SE], w[i])`：该算法内部调用底层加密方案的加密算法。以 `IBE` 方案为例，该算法调用 `Enc(PP[IBE], H(w[i]), m[i])`，该算法接受应用哈希函数后的关键词（将关键词映射到身份）并随机选择一条消息 `m[i]` 进行加密。

*   `0/1 ← Search(PK[SE], T[i], C[i])`：该算法内部调用底层方案的解密算法。以 `IBE` 方案为例，该算法调用 `Dec(PP[IBE], T[i], C[i])`，如果解密算法正确输出加密消息 `m[i]`，则输出二进制值 1；否则返回 0。

上述步骤展示了基于开发可搜索加密方案所用方法论类型的可搜索加密定义变体。接下来，我们将讨论另一种基于所用底层方案类型的变体。这里，我们将考虑使用 `ABE` 作为底层方案，并讨论关于 `ABE` 的相应可搜索加密方案的定义。为了联合表述，令 `I[K]` 表示密钥生成算法 `GenKey` 的输入，`I[E]` 表示生成索引算法 `GenIndex` 的输入。在 `KP-ABE` 中，`I[K]` 和 `I[E]` 分别是访问策略和属性集合。在 `CP-ABE` 中，`I[K]` 和 `I[E]` 分别是属性集合和访问策略。

*   `(PP, MSK) ← Setup(1^n, W, Att)`：建立算法接受属性全集 `Att = {att[1], att[2], ..., att[|Att|]}` 和关键词空间 `W = {w[1], w[2], ..., w[|W|]}`，除了安全参数 `1^n` 外，输出公共参数 `PP` 和主密钥 `MSK`。

*   `SK[u] ← GenKey(PP, MSK, I[K])`：该算法接受 `MSK` 和用户 `u` 的凭证 `I[K]`，并生成其对应凭证的私钥，即 `SK[u]`。

*   `C[i] ← GenIndex(PP, w[i] ∈ W, I[E])`：该算法使用 `I[E]` 和 `PP` 加密关键词 `w[i]`，并输出密文 `C[i]`。

*   `T[i] ← GenTrap(SK[u], w[i] ∈ W)`：该算法使用用户 `u` 的私钥 `SK[u]` 为关键词 `w[i]` 生成陷门。

*   `0/1 ← Search(PP, C[i], T[i])`：只有当 `I[K]` 和 `I[E]` 之间满足可满足性条件时，才会执行该算法。如果可满足性条件成立，该算法通过逐个搜索所有密文来查找陷门中包含的关键词，如果找到匹配则返回 1，否则返回 0。

### 5.1.2 系统模型

在可搜索加密系统中，涉及不同的实体，每个实体执行系统定义中解释的算法之一。这些实体的描述及其角色通常称为系统模型，如下图 图 5.1 所示。

![图 5.1 PKE 设置下 SE 的通用系统模型](img/fig5_1.jpg)

**图 5.1** PKE 设置下 SE 的通用系统模型。

如果使用标准可搜索加密方案，则假设每个云用户拥有一对公钥和私钥 `[K[pub], K[pri]]`，由密钥生成中心生成；这些可能是完全随机的密钥，与 `IBE` 或 `ABE` 基础的 `SE` 方案中的人员身份或用户凭证无关。如果使用 `IBE` 或 `ABE` 方案作为底层方案，则在密钥生成中会采集与个人身份或凭证（属性/访问策略）相关的信息来生成用户的私钥。在 图 5.1 中，我们在一个图中展示了标准 `SE` 或基于 `ABE` 的 `SE` 的系统模型，具体说明如下：

*   **可信机构**：可信机构（`TA`）是在使用 `ABE` 作为底层方案开发可搜索加密方案时发挥作用的实体。当新用户向 `TA` 注册时，`TA` 将验证其凭证并使用 `GenKey` 算法生成其私钥。该算法嵌入与该用户关联的访问策略（`KP-ABE`）或属性（`CP-ABE`）。`TA` 还通过执行 `Setup` 算法初始化系统，该算法生成公共参数 `PP` 和主密钥 `MSK`，其中 `PP` 可供每个云用户使用。

*   **数据拥有者**：数据拥有者（`DO`）是希望将其数据共享给多个用户的实体。`DO` 首先通过调用 `GenIndex` 算法加密数据和相关关键词。如果使用标准 `SE`，该算法使用 `K[pub]` 加密关键词 `w[i]`；否则，如果使用 `ABE`，该算法使用 `PP` 以及访问策略（如果使用 `CP-ABE`）或属性（如果使用 `KP-ABE`）加密关键词 `w[i]`。然后数据拥有者将加密数据上传到云服务器。

*   **数据用户**：数据用户（`DU`）是希望检索数据拥有者存储在云服务器上的数据的实体。由于数据是加密形式，且 `DU` 希望云服务器在加密数据上执行搜索，因此数据拥有者必须将其搜索功能委托给云服务器。数据拥有者通过执行 `GenTrap` 算法，使用其私钥生成搜索陷门。

*   **云服务器**：云服务器（`CS`）由第三方拥有，用于提供存储等服务。它存储加密数据，并使用 `DU` 提供的搜索陷门对这些数据执行搜索。如果使用标准 `SE`，则搜索算法仅接受密文和关键字的陷门；否则，如果使用 `ABE` 方案，可能还需要 `PP`，或者如果使用某种转换方法，则需要 `PK[SE]`。`PK[SE]` 表示转换后的可搜索加密方案的公钥。

### 5.1.3 SE 系统中各参与方之间的信息流

`IBE` 型 `SE` 系统中各参与方之间的信息流通过以下步骤进行解释，如 图 5.2 所示。

*   **i)** `DO` 使用 `GenIndex(K[pub], w[i])` 算法，在接收者的公钥 `K[pub]` 下，发送数据及其关联的关键词的加密形式。生成的加密数据及其索引存储在远程服务器上，以便与其他用户共享。

*   **ii)** `DU` 使用 `GenTrap(K[pri], w[i])` 算法生成与该特定文件关联的关键词的陷门。生成的陷门将使云服务器能够执行搜索，前提是它是由数据预期的用户生成的，即陷门是使用生成索引时所用公钥对应的同一用户的私钥生成的。

*   **iii)** `CS` 使用 `DU` 发送的搜索陷门 `T[j]`，通过 `Search(C[i], T[j])` 算法对加密数据 `C[i]` 执行搜索操作。云服务器代表 `DU` 执行搜索操作。如果找到与搜索陷门对应的关键词，则云服务器返回二进制输出 1；否则输出 0。

![Figure 5.2 Flow of information in an IBE-based SE system.](img/fig5_2.jpg)

**图 5.2** 基于 IBE 的 SE 系统中的信息流。

`ABE` 型 `SE` 系统中各参与方之间的信息流通过以下步骤进行解释，如 图 5.3 所示。

*   **i)** `TA` 使用 `Setup(λ)` 算法初始化系统，该算法以安全参数 `λ` 作为输入。此外，它使用 `KeyGen(MSK)` 算法向云用户颁发必要的凭证，该算法以主密钥作为输入。

*   **ii)** 数据所有者是指希望将其数据集合连同一些关键词外包给云服务器以实现共享的一方。考虑到数据的机密性，数据以加密形式存储。为了将数据上传到云服务器，数据所有者使用 `GenIndex(PP, w[i])`，该算法以公共参数 `PP` 和与数据文件关联的元数据项 `w[i]` 作为输入，生成 `w[i]` 的密文 `C[i]`。一旦数据上传到云服务器，授权用户即可对其进行搜索。
