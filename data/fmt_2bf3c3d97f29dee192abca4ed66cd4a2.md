
Figure 6.6 Decision Transformer architecture for offline RL. The first two time steps are shown. *E*[*R*], *E*[*S*], and *E*[*A*] represent the combined embedding layer positional encoding, and layer norm for the returns-to-go, states, and actions, respectively. The layer after GPT-2 contains three linear submodules for predicting the next element of the sequence. Next state, action, and return-to-go are predicted using different submodules.

Since the input tokens are a sequence of rewards-to-go, states, and actions, the multi-head self-attention mechanism computes attention between rewards, states, and actions. This includes the cross-attention between the input tokens and the partially generated output tokens, which are only actions. Chen et al. surmise that the attention mechanism is what makes Decision Transformer able to learn the relationship between states, actions, and rewards. Chen et al. also believe that Decision Transformer may be useful for online RL methods, where it could be used to generate diverse behavior. Decision Transformer achieves state-of-the-art on various RL benchmarks.

### 6.8 Case Study: Automatic Speech Recognition

#### 6.8.1 Goal

In this chapter, we looked at several applications of the transformer architecture. In this case study, we compare the transcription quality of Wav2vec 2.0 \[16\] to Speech2Text2 \[258\], and HuBERT \[120\], each of which is transformer-based and was discussed earlier in this chapter. We'll measure transcription quality with the word error rate and character error rate metrics.

#### 6.8.2 Data, Tools, and Libraries

![Listing 6.1 Python environment setup](img/comp6_1.jpg)

Listing 6.1 Python environment setup

We'll use Huggingface Transformers to load pre-trained models and Huggingface Datasets to load an automatic speech recognition (ASR) dataset, TIMIT \[93\]. After loading the necessary libraries in the environment, as shown in Listing 6.1, we can load the dataset

![Listing 6.2 Load dataset](img/comp6_2.jpg)

Listing 6.2 Load dataset

#### 6.8.3 Experiments, Results, and Analysis

##### 6.8.3.1 Preprocessing speech data

![](img/comp6_3.jpg)![Listing 6.3 Preprocess speech](img/comp6_3a.jpg)

Listing 6.3 Preprocess speech

##### 6.8.3.2 Evaluation

There are three types of errors we can make during transcription:

* substitution: swapping a correct word or character for an incorrect one
* deletion: removing a correct word or character
* insertion: inserting a word or character

We can compute the word error rate and character error rate metrics by summing the three kinds of errors and dividing by the number of words (or characters):

$$
\begin{array}{ll}
{WER} & {= \frac{S + D + I}{N}} \\
\end{array}
$$

(6.39)

$$
\begin{array}{ll}
{CER} & {= \frac{S + D + I}{N}} \\
\end{array}
$$

(6.40)

where *S* is the number of substitutions, *D* is the number of deletions, *I* is the number of insertions, and *N* is the number of words (or characters, for CER) in the transcript. The Huggingface datasets library has both metrics built-in, so we will use those instead of writing our own.

![Listing 6.4 Load WER and CER metric](img/comp6_4.jpg)

Listing 6.4 Load WER and CER metric

Now we load each model and then transcribe and compute quality metrics.

**Wav2vec 2.0** After running the listings up to and including Listing 6.5, we find that Wav2vec 2.0 achieves a WER of 0.09291(9.29%) and a CER of 0.02212(2.2%) on the TIMIT test set.

![](img/comp6_5.jpg)![Listing 6.5 Transcribe and evaluate with Wav2vec 2.0](img/comp6_5a.jpg)

Listing 6.5 Transcribe and evaluate with Wav2vec 2.0

**Speech2Text2** \[258\] is a transformer decoder model that can be used with *any* speech encoder, such as Wav2Vec2 or HuBERT \[120\]. We'll use a Speech2Text2 model of comparable size to the Wav2vec2 model used in Listing 6.5.

![](img/comp6_6.jpg)![Listing 6.6 Transcribe and evaluate with Speech2Text2](img/comp6_6a.jpg)

Listing 6.6 Transcribe and evaluate with Speech2Text2

In Listing 6.6, you'll notice that we are explicitly passing the attention mask to the model. This turns out to be important for Speech2Text2. If the attention mask is omitted, then the model may generate a transcription that is longer than the target. With a GPU with speed comparable to a K80, the listing should run in about 4 minutes. The Speech2Text2 model achieves a WER of 0.10283(10.28%) and a CER of 0.03624(3.62%) on the TIMIT test set.

**HuBERT** \[120\], short for Hidden-Unit BERT, is a transformer-based self-supervised speech representation learning model that is able to learn an acoustic model and a language model directly from labeled audio data.

![](img/comp6_7.jpg)![Listing 6.7 Transcribe and evaluate with HuBERT](img/comp6_7a.jpg)

Listing 6.7 Transcribe and evaluate with HuBERT

HuBERT achieves a WER of 0.11544(11.54%) and a CER of 0.2872(2.87%) on the TIMIT test set. For comparison, the WER and CER scores are gathered into Table 6.1, which shows Wav2vec 2.0 performs the best on TIMIT test, with Speech2Text2 in second place; HuBERT is in third.

TABLE 6.1 WER and CER metrics on the TIMIT test set for Wav2vec 2.0, Speech2Text2, and HuBERT. Best score is in boldface

| Model | WER | CER |
| --- | --- | --- |
| Wav2vec 2.0 | **0**.**09291** | **0**.**02212** |
| --- | --- | --- |
| Speech2Text2 | 0.10283 | 0.03624 |
| HuBERT | 0.11544 | 0.02872 |

# CHAPTER 7 解释性和可解释性技术在 Transformer 中

DOI: [10.1201/9781003170082-7](https://doi.org/10.1201/9781003170082-7)

在医疗、立法、执法或金融等关键领域的实际应用中，除了预测结果外，还需要从可解释性角度理解模型。遗憾的是，大多数最先进的 Transformer 模型和本文中涵盖的技术仍被视为“黑盒”，这会显著阻碍其采用。因此，有迫切的需求在从理解和诊断两个角度为这些复杂的最先进的模型构建可解释性。正如 Xie 等人所提议，我们将介绍能够提升可解释性的模型特性、影响可解释性的相关领域、针对基于 Transformer 和基于注意力系统的可解释方法的分类法，以及在使用不同可解释技术的电子健康记录系统中进行的详细案例研究，以获得实用的洞见 \[275\]。

## 7.1 可解释系统的特征

可解释系统的决定性目标之一是让系统的最终用户能够理解输入与输出之间的关系。因此，特征可以定义为用户可以评估和测量的系统属性。正如 Xie 等人所提议，必要的四个特征如下：

1. **置信度**。当最终用户（决策者）能够根据输入和输出将 Transformer-based 模型的处理过程与自己的思考过程对齐时，系统的置信度会提升。注意力热图在图像或文本上突出模型在决策（分类、识别、问答等）时认为重要的输入部分，输出模拟人类通过关注机制进行关联的形式，从而作为一种解释 \[106, 127, 154, 195, 254\]。

2. **安全**。在直接或间接影响人类生命的应用中，Transformer-based 模型应被认为是安全的。安全可以从以下几个方面衡量：(i) 行为一致且确定性，即相同的输入始终产生相同的输出；(ii) 在标准和异常条件下保持稳健可靠；(iii) 能够防止对社会整体产生负面影响的选择 \[191\]。

3. **信任**。可靠的模型不需要额外验证。已证明，预测置信度高的模型并不保证可信度 \[95, 189, 191, 291\]。Xie 等人提出了两个重要的可信度标准：(i) 满意的测试，即模型在训练数据上表现与在未见测试数据上的表现相似；量化上，当训练集和测试集的准确率、精确率等指标相近时，信任度提升。经验是一种更质性的评估，判断系统是否足以在不进行检查的情况下完成任务。真实部署中的数据和概念漂移会进一步降低系统的信任。近年来有许多研究探讨从模型预测角度对安全进行研究 \[5, 22, 134, 252\]。

4. **伦理**。如果模型的决策过程不违背最终用户设定的伦理原则，则可以视为在伦理层面上是可接受的。为伦理人工智能制定框架和指南的研究本身就是一个 rapidly growing 研究领域 \[20, 26, 59, 268\]。

## 7.2 影响可解释性的相关领域

Xie 等人指出四个与可解释性紧密相关且与前文定义的特征相呼应的领域：

* **学习机制**：能够提供模型训练过程的洞察有助于提升模型的置信度和信任度。模型达到的学习状态的形成过程可以通过以下方式进一步探讨：从滤波器、权重和激活的视角理解不同层在学习概念或统计模式上的演变；研究不同层在输入和权重影响下的收敛情况，并从记忆和统计力学角度分析网络的泛化特性 \[294, 301\]。对不同层的收敛性进行输入和权重分析，以及从记忆和统计力学角度分析网络的泛化属性 \[206\]。

* **模型调试**：类似于软件调试，模型调试指对模型架构、网络中数据处理以及训练和运行过程中引入的错误进行检查。常见的研究方法是构建辅助模型，作为诊断和检查的探针 \[140\]。Amershi 等人提出的 ModelTracker 允许对标记错误数据、缺失特征的识别、训练数据不足导致标签学习不足的洞察、异常影响、特征空间可视化、性能总结等进行可视化交互，是一种模型无关的调试方法 \[4\]。Fuchs 等人提出的神经听诊器（Neural stethoscopes）是另一种通用框架，通过量化重要因素的影响并通过促进/抑制信息来分析学习过程 \[90\]。

* **对抗攻击与防御**：对抗示例是人工工程的输入，用于检验模型的判别能力。构建对抗示例需要理解输入空间以及分类问题中类别边界。对抗攻击和防御是从可解释性和诊断角度探索模型的两种不同方式 \[291, 295\]。黑盒攻击和白盒攻击是两种主要的对抗攻击类型，用于生成误导模型的示例 \[76, 86, 233\]。最近的研究表明，在输入上加入不可感知的噪声会暴露模型的脆弱性 \[178\]。对抗防御是使模型对抗示例保持鲁棒的方法。两种常见的防御手段是：(i) 对抗训练，即在训练数据集中加入对抗示例以提升鲁棒性；(ii) 扰动消除，即模型识别并拒绝对抗示例 \[95, 218\]。
