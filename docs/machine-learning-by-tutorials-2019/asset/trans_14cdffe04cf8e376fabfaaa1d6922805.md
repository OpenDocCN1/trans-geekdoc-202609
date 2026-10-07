
或 `.nameOrLexicalClass` 标签方案，标记器会分配 NLTag 值，指示这些标签在文本中如何被使用。例如，`.noun`、`.verb` 或 `.adjective`。请查阅文档获取可能的取值。

分词（Tokenization）是将文本拆分为更小单元的过程。它通常意味着将字符串分为单个单词和标点符号，但也可能意味着拆分成其他单元，如句子或字符。

你在本章中使用的所有类都会自动对输入进行分词，因此你不需要担心这个问题。然而，如果你以后需要自己动手，Natural Language 框架提供了 `NLTTokenizer` 来按单词、句子、段落或文档对文本进行分块。它使用特定语言的规则，这些规则通常很好，但可能并不完全符合你需要的。尽管如此，这是一个不错的选项，下次你需要对文本进行分词时至少应该考虑。

在下一章实现语言翻译时，你将使用 `NLTokenizer` 作为预处理步骤。同时，你可以查看 `projects/final/playgrounds` 文件夹下的 `NLExtras.playground` 来查看词性标记和分词的示例代码。

## 关键点

- Apple 新的 Natural Language 框架将利用快速、训练良好的机器学习模型进行 NLP。
- `NLLanguageRecognizer` 可以识别一段文本中使用的语言。
- `NLTagger` 和 `NLTagScheme` 允许你将文本分分为特定的、标记的类型。有几种内置的标记方案可用，你也可以指定自己的。
- `NLTokenizer` 可以将文本分解文档、段落、句子或单词。
- 使用 Create ML 和 `MLTextClassifier` 训练你的模型以对较大块的文本、句子、段落或文档进行分类。
- 使用 Create ML 和 `MLWordTagger` 训练模型在单词级别对文本进行分类。
- `NLModel` 将 Create ML 模型（如 `MLTextClassifier` 和 `MLWordTagger`）封装起来，确保输入在你的应用中的预处理方式与训练期间一致。它是与 `NLTagger` 配合使用的自定义标记方案所需的类型。

## 接下来去哪里？

本章涵盖了 Apple 通过 Natural Language 框架提供的大部分便利。你可以在章节资源 `projects/final/SMDB` 中找到该项目的完成版本。当你准备好后，请进入下一章，在那里你将学习如何实现涉及在 Keras 中创建自定义模型的更高级 NLP 特性。你将继续开发此应用，添加将西班牙语评论翻译成英语的能力。

## 第 15 章：自然语言转换，第一部分

作者 Chris LaPollo

**更新说明：** Apple 喜欢让我们等待。在编写此内容时，更新本章所需的 CoreML API 尚未完全就绪。随着 Apple 发布新 API，我们将继续更新本章。我们还会通知你并如何访问更新后的版本。

上一章展示了如何使用 Apple 的 Natural Language 框架执行一些实用的 NLP 任务。但 Apple 只涵盖了基础知识——还有许多你可能想对自然语言执行的操作。例如，你可能回答问题、总结文档或在语言之间进行翻译。

在本章中，你将学习一种名为**序列到序列 (sequence-to-sequence, seq2seq)** 的通用网络架构。你将将其添加到已构建的 SMDB 应用中，用它将电影评论从西班牙语翻译成英语，但相同的网络设计也用于许多类型的问题，从问题问答到生成图像描述。如果你还没有制作 SMDB，不要担心——如果你需要，我们会提供一个启动项目。但你可以暂时忘记 Xcode 了——seq2Seq 模型需要一个底层的框架，因此在本章的大部分内容中将使用 Python 和 Keras。

## 入门

此项目中的某些 Keras 代码最初基于 Keras GitHub 仓库 [github.com/keras-team/keras] 内部 **lstm_seq2seq.py** 文件中的示例。本章进行了风格上的修改，解释并扩展了代码，并展示了如何将构建的模型转换为 Core ML 并在应用中使用。

为了完成本章和下一章，你需要一个安装了 keras、各种工具和其他包的 Python 环境。为了确保安装了所有内容，请使用位于 `projects/notebooks` 的 `nlpenv-mac.yml` 创建一个新环境。如果你有 NVIDIA GPU，请取消注释 yml 文件中的 `tensorflow-gpu` 行以大幅提高训练速度。

后面的指令假设你已拥有此环境并将其命名为 `nlpenv`。如果你不确定如何从该文件创建环境，请回到第 4 章“开始使用 Python & Trie Create”。

一旦准备好 `nlpenv` 环境，请继续阅读以开始学习序列到序列模型。

## 序列到序列模型

在章节资源中，你会在 `projects/notebooks/data/` 找到一个名为 `spa.txt` 的文本文件。该文件来自 http://www.manythings.org/anki/ 的 manythings.org，它提供了许多不同语言的句子。这些句子摘自 www.tatoeba.org 的 Tatoeba Project 提供的更大的数据集。

该文件包含如下行：

| Go. | Ve. |
| :--- | :--- |
| Go. | Vete. |
| Go. | Vaya. |
| Go. | Vayase. |
| Hi. | Hola. |
| Run! | iCorre! |
| Run. | Corred. |

spa.txt 的前七行

每行都有一个英语句子——图像中并不是单单词行——后面是该句子的一种可能的西班牙语翻译。你将使用这些数据训练一个神经网络，处理西班牙语文本（如 "Corre!"）将其翻译成英语文本（如 "Run!"）。

注意：正如数据文件的示例所示，同一个短语可能会多次出现并带有不同的翻译。如果你正在训练一个从英语翻译到西班牙语的模型，这可能会让你困惑，迫使它只学习一种翻译。然而，你的模型将是从西班牙语翻译到英语，且文件中的重复西班牙语短语较少，所以这不会成为问题。

