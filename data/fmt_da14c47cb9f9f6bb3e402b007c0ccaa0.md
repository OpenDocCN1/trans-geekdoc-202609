
Even some of the world’s most important ML problem requires access to confidential data. Such data that is being crowd-sourced or outsourced has a problem of data leaks among themselves.

In crowd-sourced data, the concern lies with the data of one user being exposed to the other users, leading to the possibility of data leakage among the peers of the crowd-sourced data.

In outsourced data, the privacy of the users, whose data is present in the firm’s database is a risk.

只有将数据本身匿名化是不够的，无法使其保持私密性。实时实例显示，研究人员将 Netflix 推荐挑战的匿名用户数据与 IMDb 用户评论数据相结合，进行去匿名化处理（Arvind et al., 2008）。

## Literature review

已发表的若干工作涉及在两种数据类型—— crowd-sourced 和 outsourced——上训练机器学习算法时的隐私保护发展，部分工作还涉及该领域中除这两类主要数据类型之外的一般性问题。

Abadi et al. (Martin et al., 2016) 提出了一种基于微分隐私方案的 `DP-SGD`（差分隐私随机梯度下降）方法，该方法侧重于模型训练过程中的隐私损失量。微分隐私关注单个用户数据在数据集中的存在对结果的影响。机制 `M` 在模型训练过程中的隐私损失可以表示为 Equation 1。

$$
\log\frac{{\mathbb{P}}(M(D) \in S)}{{\mathbb{P}}\left( {M\left( D^{\prime} \right) \in S} \right)}
$$

其中 `D` 和 `D'` 是仅在一条记录上的差异的数据集，`S` 是结果的集合。

目标是尽可能降低隐私损失的值。作者提出通过对每个计算步骤的随机梯度下降进行优化，以最小化隐私损失值。这可以通过剪切最大梯度范数来实现，从而限制基于信息的学习并降低隐私损失。随后，对数据进行噪声添加，以引入随机性。最大梯度范数和噪声的值被视为超参数，并进行调整以限制隐私损失。该算法被应用于两个数据集 `MNIST` 和 `CIFAR-10`，以展示结果。

Papernot et al. (2016) 提出了 `PATE`（private aggregate of teacher ensembles），该方法通过引入集群学习者的概念来改进 `DP-SGD`。在 `DP-SGD` 中，噪声已添加以保护隐私。然而，存在模型是否记忆了数据或仅从整体趋势中学习的歧义。因此，在 `PATE` 中，从原始数据集中导出了独立的训练数据集，然后分别训练多个模型，最后通过最大投票确定最终结果。这确保了每个模型都从整体模式中学习，而非记忆具体数据。

为了使每个学习者的投票结果私密，添加了拉普拉斯噪声，拉普拉斯噪声表示为 Equation 2。

$$
Lap\left( \frac{1}{\gamma} \right)
$$

Papernot et al. (2018) 进一步改进了 `PATE`，使其能够处理大规模数据。该工作通过修改原始 `PATE` 架构中的噪声最大计算来实现改进。

经典的拉普拉斯最大计算如下 Equation 3：

$$
f(x) = \arg\max\limits_{j}
$$

- Abadi et al. (2016) 提出了一种基于差分隐私的 SGD，它具有显著优势，包括在隐私约束下训练深度神经网络的先驱性算法，这对隐私保护机器学习领域是一项重要贡献。此外，该论文引入了基于差分隐私的精细隐私成本评估框架，提升了我们在模型训练中确保数据隐私的能力。这些创新在图像分类和语言表征等领域具有多种应用，在不牺牲模型实用性的前提下提供了增强的隐私保护。此外，该论文提出的技术在医疗、金融和政府等大量数据存在的领域中，也有望保护敏感信息。此外，它们在推荐系统、欺诈检测和自动驾驶等数据隐私至关重要的关键领域中，也为隐私保护机器学习解决方案打开了大门。然而，需要承认隐私保护与模型质量之间存在固有的权衡，并且在敏感应用中，由于深度神经网络表示的解释复杂以及可能的细粒度数据编码，需要进行严格的评估和风险评估。

Papernot et al. (2018) 提出的 `PATE` 方法在隐私保护机器学习领域具有显著优势。其显著优势之一是通过引入教师答案的选择性和较不噪声的聚合机制，增强了隐私保护。这种稳健的方法能够提供强差分隐私保障，有效保护涉及敏感数据的个人隐私。然而，需要考虑的潜在缺点是可能出现实用性权衡。与许多隐私保护技术一样，`PATE` 可能导致学生模型准确率下降，可能需要增加计算资源和更长的训练时间。这在模型准确性至关重要的应用中可能是一个问题。尽管如此，`PATE` 方法在处理敏感数据的任务中的广泛适用性是一个重要优势，例如个人消息或医疗记录，它能够在保护个人数据隐私的同时提取有价值的洞察，并通过创新的聚合机制提高模型准确性。

Hwanjo et al. (2006) 讨论的技术具有显著优势。首先，它在保护数据隐私的同时仍能提供准确结果，在隐私和安全问题至关重要的情况下尤为宝贵。其次，它特别适用于水平分区数据的场景，能够在保持强隐私保护的同时促进分布式知识发现。然而，也有需要考虑的潜在缺点。一个重要限制是它在与传统 SVM 方法相比时的相对计算效率较低。这种效率低下是由于额外的隐私措施（如加密和解密）造成的，可能增加处理时间和资源需求。在应用领域，该技术在需要安全数据处理的医疗诊断、金融分析和欺诈检测等多个领域都有前景，它能够在保护敏感数据的同时进行隐私意识的数据挖掘和机器学习任务。

Vaidya et al. (2005) 讨论的技术具有显著优势。首先，它在保护数据源隐私的同时，能够在严格保护敏感信息的前提下进行数据挖掘。此外，它还具有经过验证的安全属性，确保在挖掘过程中数据的机密性。该论文介绍了高效的协议，用于从持有相同个体私有信息的不同各方生成关联规则，从而实现协作数据挖掘并保护隐私。此外，它提出了一个灵活的工具包，用于隐私保护的数据挖掘方法，可能提高隐私意识的数据挖掘技术的适应性。然而，也有需要考虑的显著限制。该技术可能受到各方串通的影响，从而损害数据隐私保护。在完全恶意环境中，某些各方可能主动试图破坏隐私保护措施，这使得在迭代数据挖掘场景中，维护安全属性变得具有挑战性。论文还有一个开放性问题，即在数据出现小幅变化后重新运行算法，这可能影响其实用性。该技术在隐私保护的关联规则挖取中表现出实用性，能够安全计算分布式集合的交集基数，从而实现协作关联规则挖取。它也暗示了在构建决策树、EM 聚类和管理两个参数之间的关联规则方面的潜在用途，表明它可以作为创建支持各种隐私意识数据挖掘技术的综合工具的基础组成部分。

The privacy-preserving outsourced SVM (`POS`) technique (Fang et al. 2015) offers a robust solution for safeguarding individual privacy while enabling collaborative operations on encrypted and outsourced data. 它的多功能性体现在其能够在各种数据分区方案（包括水平、垂直和任意分区）中保持数据隐私，从而适应广泛的场景。然而，该论文未明确处理所有潜在隐私问题，特别是在云环境中安全处理和存储加密和外包数据的问题，留下了在其范围之外的额外隐私考虑。在应用领域，`POS` 特别适合于在外包和加密数据上进行安全支持向量机器学习（SVM）分类。其多功能性使其适用于医疗、金融和社交网络等数据隐私至关重要的领域。此外，它与其他隐私保护 SVM 方法相辅相成，特别适用于分布式模型的情境，强调在协作数据分析和分类任务中保持用户数据的保密性、完整性和可审计性，提供了一种安全且保护隐私的机器学习方法。

Samanthula et al. (2014) introduces a k-NN protocol with several notable advantages. Firstly, it provides robust data confidentiality and privacy protection, ensuring the security of user input queries. Additionally, the protocol incurs negligible computation costs on the end-user, enhancing its efficiency and user-friendliness. However, there are several challenges and concerns to consider. The protocol differs from existing privacy-preserving classification techniques by hosting encrypted data on the cloud, potentially introducing unique operational challenges. While it aims to address accuracy issues that can arise in existing methods due to the introduction of statistical noise, it may also face challenges in mitigating data access pattern leakage. In terms of applications, the proposed k-NN protocol holds relevance in data mining contexts, with specific use cases mentioned in fraud detection in the financial sector and tumor cell level prediction in healthcare. This suggests practical applications in domains where data privacy and classification accuracy are paramount considerations.

Ping et al. (2017) introduces multi-key privacy-preserving deep learning schemes with several notable advantages. These schemes effectively safeguard sensitive data, intermediate results, and the training model, ensuring robust privacy measures. A security analysis included in the paper further validates the effectiveness of these techniques, assuring users of their data’s confidentiality. Moreover, their versatility and adaptability make them suitable for a wide range of ML tasks within the same privacy-preserving setting. However, there are certain limitations to consider. Implementing these schemes may incur additional computational and communication costs compared to traditional deep learning methods due to encryption and decryption processes, potentially impacting efficiency. Additionally, the dependency on trusted third parties for secure key management could pose practical challenges in some scenarios. In terms of applications, the schemes find valuable use in cloud computing, especially in collaborative learning scenarios involving multiple data owners with different datasets. One specific application highlighted in the paper is privacy-preserving face recognition, a prominent biometric authentication technique used in real-life scenarios. Furthermore, the generic nature of the proposed solutions allows for their application in various other ML tasks that share the same privacy-preserving setting and requirements.

The paper provides a concise review of several works and research done in the field of PPML to the readers. Several works focusing on privacy concerns in different environments of data flow are presented in their paper. Modifications into several existing algorithms like SVM, kNN, and neural networks are also highlighted. A few techniques based on DP were discussed that focused on the privacy of data while the training of the model, followed works that focused on the privacy of distributed and outsourced data.

These models however developed and proposed, there is still a scope for them to make easy to use for several consultancy firms as well as several general freelancing users in order to achieve the goal of PPML. A part of it can be achieved by making libraries in commonly used programming languages like python in popular ML libraries like sckit-learn. The existing works focus on modifying existing algorithms to achieve privacy, however, a lot of room exists for the development of specific models having the capability of achieving the goal of privacy.

* Abadi, M., Andy, C., Ian, G., Brendan McMahan, H., Ilya, M., Kunal, T., and Li, Z. (2016). Deep learning with differential privacy. Proc. 2016 ACM SIGSAC Conf. Comp. Comm. Sec., 308–318.

* Dan, B., Eu-Jin, G., and Kobbi, N. (2005). Evaluating 2-DNF formulas on ciphertexts. Theory Cryptograp. Second Theory Cryptograp. Conf., TCC 2005, Cambridge, MA, USA, February 10-12, 2005. Proceedings 2, 325–341.

* Zvika, B., Gentry, C., and Vaikuntanathan, V. (2014). Leveled fully homomorphic encryption without bootstrapping. ACM Trans. Comput. Theory (TOCT), 6(3), 1–36.
