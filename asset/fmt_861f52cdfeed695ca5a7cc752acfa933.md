
Contextualizing explainability in AI literature and the NLP domain shows two forms of explanations—(i) plausible explanation and (ii) faithful explainability. The goal of plausible explanation is to provide human-understandable rationales for the model's behavior. The plausible explanation is subjective and requires human-in-the-loop to judge whether the explanation is justified and builds trust in the model. Faithful explainability is a more rigorous form of explanation and aligns more closely with the desired properties of transparency and interpretability and what the authors explore in their work. The goal of the technique is to quantify the correlation between the input (tokens/words) and the output (predictions) for a predictive task. One of the requisite for this form of explanation is that—model explanations are exclusive, i.e., a predictive model should exhibit one set of behavior for one reasoning process.

The authors lay the following three requirements for faithful explanations for attention mechanisms.

1. Attention mechanism should be a NECESSARY component for good model performance.
2. Attention distributions should be hard to manipulate, i.e., if any trained model can vary the distribution of attention weights and yet have similar predictions, they may not be suitable for the explanation. This directly corresponds to the exclusivity requisite for faithful explanations and will guide the search for adversarial models.
3. Attention distributions should work well in uncontextualized settings. Since the attention weights are typically learned on contextualized hidden layer outputs, to see the impact on input tokens, one needs to use uncontextualized settings to judge their usefulness.

### 7.4.2.1 Is attention necessary for all tasks?

The authors use the same three sets of tasks and six classification datasets using the `BiLSTM` model from the Jain and Wallace setting and create another model where the attention weights are uniform in distribution compared to the learned weights. Based on the F1 scores on all six classification datasets comparing the uniform and learned attention weights, the news datasets show no variations and hence are not used for the subsequent two analyses. The Stanford Sentiment Treebank (`SST`) is a borderline case and shows a small difference as compared to the MIMIC (III) and IMDB dataset.

### 7.4.2.2 Searching for adversarial models

To find attention weight distributions that mimic the base model predictions, the authors propose a model-consistent training protocol for finding adversarial attention distributions through a combined parameterization that holds for all training examples. The two measures they employ for the adversarial training are Total Variation Distance (`TVD`) and Jensen-Shannon Divergence (`JSD`).

Total Variation Distance (`TVD`) is used for comparing the class predictions from two models and is given by:

$$
\begin{array}{l} {\text{TVD}({\hat{y}}_{1},{\hat{y}}_{2}) = \frac{1}{2}{\sum\limits_{i = 1}^{|y|}|}{\hat{y}}_{1i} - {\hat{y}}_{2i}|} \\ \end{array}
$$

(7.22)

Jensen-Shannon Divergence (`JSD`) is used for comparing the two attention distributions and is given by:

$$
\begin{array}{l} {\text{JSD}(\alpha_{1},\alpha_{2}) = \frac{1}{2}\text{KL}\lbrack\alpha_{1}\|\overline{\alpha}\rbrack + \frac{1}{2}\text{KL}\lbrack\alpha_{2}\|\overline{\alpha}\rbrack\,\text{where}\,\overline{\alpha} = \frac{\alpha_{1} + \alpha_{2}}{2}} \\ \end{array}
$$

(7.23)

The adversarial training algorithm is first to train a base model(*M*[*b*]). Then train an adversarial model (*M*[*a*]) that minimizes the output prediction score from the base model yet maximizing the changes in the learned attention distribution from the base model using following instance-wide loss function:

$$
\begin{array}{l} {\mathcal{L}(M_{a},M_{b}) = \text{TVD}({\hat{y}}_{1}^{(i)},{\hat{y}}_{2}^{(i)}) - \lambda\text{KL}(\alpha_{a}^{(i)}\|\alpha_{b}^{(i)})} \\ \end{array}
$$

(7.24)

where *ŷ*^((*i*)) and *α*(i) denote predictions and attention distributions for an instance i, and *λ* controls the trade-off between the prediction distance and attention distribution changes.

For the diabetes dataset (and the anemia and the IMDB), they find it challenging to find adversarial weights that produce divergent attention weights and not losing the predictive performance, thus supporting the use of attention for the faithful explanation. On the contrary, Stanford Sentiment Treebank (`SST`) dataset shows no use of attention weights for the faithful explanation.

### 7.4.2.3 Attention Probing

为验证在无上下文环境下注意力分布的表现，将 `BiLSTM` 的注意力权重施加到使用词向量表示的未上下文训练 MLP 层上。因此，任务表现高意味着注意力分数能够捕捉输入与输出之间的关系。除 Stanford Sentiment Treebank (`SST`) 数据集外，所有任务和数据集均表现出 `BiLSTM` 训练的注意力权重优于 MLP 和均匀权重，表明注意力权重的有用性。

总之，研究提出了三个验证注意力机制有用性的基本组成部分以及三种量化方法，以实现可靠解释。注意力机制的有用性表现为任务依赖性。

## 7.5 量化注意力流

如前两节讨论，将注意力权重与输入关联用于解释简单 `BiLSTM`（在输出前仅有一个注意力层）的研究仍是一个开放课题。在具有自注意力、多头注意力以及编码器中多个注意力层的 Transformer 中，问题更为复杂。Abnar 和 Zuidema 在研究中提出了几种技术来解决此问题，即 **Attention Rollout** 和 **Attention Flow**，它们都计算从该层到输入 token（即 token attention）的注意力分数，用于可视化和解释 \[1！\]

### 7.5.1 信息流为有向无环图 (DAG)

Transformer 模型在任意层的注意力模块具有来自输入的残差连接，因此任意层 *l* + 1 的值 `V[l+1]` 由 `V[l]` + `W[att]`·`V[l]` 给出，其中 `W[att]` 为注意力矩阵。作者建议在残差连接上加上单位矩阵 `I`，并计算经残差调整的原始注意力：

$$
\begin{array}{l}
{A = 0.5 \cdot W_{att} + 0.5 \cdot I \cdot A}
\end{array}
$$

(7.25)

该公式可用于在 Transformer 模型的任意节点或层创建信息流图。研究建议使用以输入 token（或隐藏嵌入）为节点、原始注意力权重为边的有向无环图 (`DAG`)。

### 7.5.2 Attention Rollout

在已从 Transformer 模型构建的 DAG 之后，**Attention Rollout** 机制通过递归计算每条链路将信息传递至所有输入 token 的比例来量化注意力对输入 token 的影响。对于给定层 *i* 以及前序层的所有注意力权重，Attention Rollout 通过从输入层递归乘以注意力矩阵，直至层 *i*，可表示为：

$$
\begin{array}{l}
{\widetilde{A}(l_{i}) = \left\{ \begin{array}{l}
{A(l_{i})\widetilde{A}(l_{i - 1})\, if,\, i > j} \\
{A(l_{i})\, if,\, i = j}
\end{array} \right.}
\end{array}
$$

(7.26)

Fig. 7.5 展示了通过前序层注意力矩阵的递归乘法计算注意力滚动机制在输入 token（源）与输出之间的过程。

![Figure 7.5 Example of attention rollout mechanism between two nodes.](img/fig7_5.jpg)

Figure 7.5 Example of attention rollout mechanism between two nodes.

### 7.5.3 Attention Flow

在图论中，流网络是带有“容量”的每条边的有向图。最大流算法在给定源与汇之间找到最大可能的流值。本技术中，当 Transformer 的图映射为流网络时，边对应注意力权重；最大流算法即可计算从任意层的任意节点到输入 token（节点）的最大注意力流。

Fig. 7.6 展示了通过容量（最小权重）计算注意力流的过程，从输入 token（源）到输出。

![Figure 7.6 Example of attention flow mechanism between two nodes.](img/fig7_6.jpg)

Figure 7.6 Example of attention flow mechanism between two nodes.

研究表明，这两种方法提供互补的视角，与仅仅“关注”相比，它们在梯度基于方法和消除实验（ablation method）中与输入 token 重要性得分的相关性更高。

## 7.6 案例研究：使用可解释性技术的文本分类

### 7.6.1 目标

在医疗领域，机器学习模型的透明度和可解释性至关重要，这对其采用具有决定性影响。本节通过对最先进的 Transformer 进行可解释性技术的应用，展示其解释的价值。我们将比较传统可解释算法（如逻辑回归）与最新的 BERT 与临床 BERT（Clinical BERT），评估性能提升以及后验（post‑hoc）技术在解释黑盒模型中的应用。

### 7.6.2 数据、工具和库

医疗数据受 HIPAA 隐私法规限制，使用受限。为克服此限制，[MTSamples.com](http://MTSamples.com) 收集了四十种医学专科及工作类型的转录医疗报告样本来提升可及性。Kaggle 的医疗转录数据集及分类任务即基于此数据集。医学 NLP 项目进一步将数据转换为四个标签（Surgery、Medical Records、Internal Medicine、Other）以匹配医学分类体系。我们将使用转换后的数据集和分类任务进行案例研究。

我们使用 `pandas` 进行基本文本预处理和探索性数据分析；`Sklearn` 库用于传统 NLP 流水线和逻辑回归模型。我们采用 Huggingface 实现的 `BERT` 与 `Bio_ClinicalBERT` 作为 Transformer 实现。`Captum` 库用于通过梯度（saliency）方法进行输入归因。为理解和可视化 BERT 层和头的工作方式，我们使用 `exBERT` 可视化包。

### 7.6.3 实验、结果与分析

#### 7.6.3.1 探索性数据分析

我们进行基础 EDA，以从分布和语料角度了解数据。

Figs. 7.7 到 7.10 展示了词云、文档长度分布、高频词以及类别分布的有趣结果。词云（Fig. 7.7）和高频词统计图（Fig. 7.9）清晰显示出 *diagnoses*、*injury*、*chronic* 等术语的偏向，这些术语构成医疗转录和记录的基础语言。文档长度分布图（Fig. 7.8）呈现长尾分布，超过 25% 的文档长度超出 BERT 的最大序列长度。最后，将 40 类转换为 4 类（Fig. 7.10）后，类别分布几乎平衡，这有助于消除失衡对分类器比较的影响。

#### 7.6.3.2 实验

我们采用 90–10% 的训练‑测试划分，并额外构建 10% 的验证集用于调参和学习曲线。首先比较基础 `BERT` 与 `Bio_ClinicalBERT`，两者均在训练数据上微调并在测试数据上评估。

![Figure 7.7 Word cloud.](img/fig7_7.jpg)

Figure 7.7 Word cloud.

![Figure 7.8 Document length distribution.](img/fig7_8.jpg)

Figure 7.8 Document length distribution.

![Figure 7.9 Top words.](img/fig7_9.jpg)

Figure 7.9 Top words.

![Figure 7.10 Class distribution.](img/fig7_10.jpg)
