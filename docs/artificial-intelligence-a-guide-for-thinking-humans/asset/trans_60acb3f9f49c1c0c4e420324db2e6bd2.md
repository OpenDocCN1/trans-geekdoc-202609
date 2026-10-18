

1990年代到2000年代的统计机器翻译系统通常计算大量概率表，用于关联源语言和目标语言中的短语。当输入一个新句子时，例如英语句子“A man went into a restaurant”，系统会将句子拆分为“短语”（“A man went”、“into a restaurant”），并在概率表中查找这些短语在目标语言中的最佳翻译。这些系统还有额外步骤，以确保翻译后的短语能够作为一个句子协同工作，但翻译的主要驱动力是从训练数据中学习到的短语概率。尽管统计机器翻译系统对两种语言的句法了解甚少，但总体而言，这些方法产生的翻译比早期的基于规则的方法更好。

Google Translate——可能是最广泛使用的自动翻译程序——从2006年推出到2016年一直采用这种统计机器翻译方法，2016年，Google研究人员开发出一种基于深度学习的、据称更优的翻译方法，称为神经机器翻译。不久之后，神经机器翻译被采用于所有最先进的机器翻译程序中。

## Encoder, Meet Decoder

[Figure 38](#chapter12.xhtml#fig38) 描绘了使用 Google Translate（以及其他当代机器翻译程序）时内部的工作原理，这里是从英语翻译成法语。^()

[figure 38](#chapter12.xhtml#fig38) 的上半部分展示了一个循环神经网络（一个 `encoder network`），与我在上一章中描述的类似。英语句子“A man went into a restaurant”在七个时间步内被编码。我使用白色矩形来表示对该句子进行编码的网络；我将稍后讨论矩形内部的网络实际长什么样。在编码阶段，每个时间步将句子中的一个词以词向量的形式输入网络，类似于我上面描述的那些词向量。^() ![FIGURE 38: Sketch of an “encoder-decoder” pair of networks for language translation. The white rectangles represent the encoder and decoder networks, operating over successive time steps. The input words—for example, `man`—are first turned into word vectors—for instance, `wordvec(man)`—before being given to the network.](images/Figure38.jpg)

FIGURE 38: Sketch of an “encoder-decoder” pair of networks for language translation. The white rectangles represent the encoder and decoder networks, operating over successive time steps. The input words—for example, `man`—are first turned into word vectors—for instance, `wordvec(man)`—before being given to the network.

在最后一个时间步，编码器网络接收一个特殊的 END 符号，此时隐藏单元的激活值即为句子的 `encoding`。编码器的这些最终隐藏单元激活值随后作为输入提供给第二个网络，即 `decoder network`，它将生成句子的翻译版本。解码器网络如 [figure 38](#chapter12.xhtml#fig38) 的下半部分所示，它只是另一个循环网络，但其输出是代表构成翻译后句子的单词的数字——这些数字中的每一个也会在下一个时间步被反馈回网络。^()

请注意，法语句子有七个单词，而英语句子有六个。这种编码器-解码器系统原则上可以将任意长度的句子翻译成任意其他长度的句子。^()

> My mother said that the cat that flew with her sister to Hawaii the year before you started at that new high school is now living with my cousin.

谁正和我表妹住在一起？答案可能会影响某些语言中动词 `is` 和 `living` 的翻译方式。人类处理这类复杂句子的能力相当不错，但循环神经网络很容易丢失上下文。当网络试图将整个句子编码为一组隐藏单元激活值时，事情就会变得混乱。

在1990年代末，瑞士的一个研究小组提出了一种解决方案：循环神经网络中的单个单元应具有更复杂的结构，带有专门的权重，用于确定在下一个时间步传递哪些信息以及哪些信息可以被“遗忘”。这些研究人员将这些更复杂的单元称为“长短期记忆”(`LSTM`)单元。^()

深度学习时代的自动机器翻译是大数据和快速计算的胜利。要创建一对用于从英语到法语等语言进行翻译的编码器-解码器网络，这些网络需要在超过三千万对人工翻译的句子上进行训练。由 LSTM 单元组成并在大型数据集上训练的深度循环神经网络已成为现代自然语言处理系统的基石，不仅用于 Google Translate 使用的编码和解码网络，还用于语音识别、情感分类，以及我们将在下文中看到的问答系统。这些系统通常包含多种技巧来提高性能，例如同时正向和反向输入原始句子，以及在不同时间步关注句子不同部分的机制。^()

## Evaluating Machine Translation

Google Translate 在 2016 年推出神经机器翻译后，该公司声称新方法正在“缩小人类与机器翻译之间的差距”。^()

总的来说，此类声明部分源于科技公司之间向其他公司销售各种 AI 服务的竞争，而语言翻译是一项具有高利润潜力的主要产品。虽然 Google Translate 等网站为少量文本提供免费翻译，但如果你是一家公司，需要翻译大量文档或为网站上的客户提供翻译，你可以找到许多收费的机器翻译服务，它们都基于相同的编码器-解码器架构。

我们应在多大程度上相信机器实际上在学习“语义含义”或机器翻译正在迅速接近人类准确度水平的说法？要回答这个问题，让我们更仔细地查看这些说法所依据的实际结果。特别是，让我们看看这些公司如何衡量机器或人类翻译的 `quality`。衡量翻译质量绝非易事；给定文本可以有多种正确的翻译方式（以及更多错误的方式）。由于翻译给定文本没有单一的正确答案，因此很难设计一种自动方法来计算系统的准确性。

机器翻译中关于“人类平准”和“缩小机器与人类之间差距”的说法基于两种评估翻译结果的方法。第一种是自动方法——一个计算机程序——将机器的翻译与人类的翻译进行比较并输出一个分数。第二种方法聘请双语人类手动评估翻译。对于第一种方法，几乎所有机器翻译评估中使用的程序都称为双语评估替代研究，或 `BLEU`。^()

