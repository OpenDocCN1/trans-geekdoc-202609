

## 15

1.  [15.](#chapter11.xhtml#notes-ch11_15) 这里，我演示的是“跳字模型”（skip-gram）的一个版本，该方法是 Mikolov 等人在论文《Efficient Estimation of Word Representations in Vector Space》中提出的两种方法之一。

2.  [16.](#chapter11.xhtml#notes-ch11_16) 同上。

3.  [17.](#chapter11.xhtml#notes-ch11_17) 我使用了 bionlp-[www.utu.fi/wv\_demo/](http://www.utu.fi/wv_demo/) 上的 word2vec 演示（使用“English GoogleNews Negative300”模型）来获得这些结果。

4.  [18.](#chapter11.xhtml#notes-ch11_18) 其思路是在向量运算问题 `man − woman = king − x.` 中求解 `x`。要相加或相减两个向量，只需相加或相减它们对应的元素即可；例如，(3, 2, 4) − (1, 1, 1) = (2, 1, 3)。

5.  [19.](#chapter11.xhtml#notes-ch11_19) bionlp-[www.utu.fi/wv\_demo/](http://www.utu.fi/wv_demo/)。

6.  [20.](#chapter11.xhtml#notes-ch11_20) R. Kiros 等人，“Skip-Thought Vectors”，载于《Advances in Neural Information Processing Systems》第 28 卷（2015 年），3294–302。

7.  [21.](#chapter11.xhtml#notes-ch11_21) 引自 H. Devlin，“Google a Step Closer to Developing Machines with Human-Like Intelligence”，《Guardian》，2015 年 5 月 21 日，[www.theguardian.com/science/2015/may/21/google-a-step-closer-to-developing-machines-with-human-like-intelligence](http://www.theguardian.com/science/2015/may/21/google-a-step-closer-to-developing-machines-with-human-like-intelligence)。

8.  [22.](#chapter11.xhtml#notes-ch11_22) Y. LeCun，“What’s Wrong with Deep Learning?”，讲义幻灯片，第 77 页，2018 年 12 月 14 日访问，[www.pamitc.org/cvpr15/files/lecun-20150610-cvpr-keynote.pdf](http://www.pamitc.org/cvpr15/files/lecun-20150610-cvpr-keynote.pdf)。

9.  [23.](#chapter11.xhtml#notes-ch11_23) 例如，参见 T. Bolukbasi 等人，“Man Is to Computer Programmer as Woman Is to Homemaker? Debiasing Word Embeddings”，载于《Advances in Neural Information Processing Systems》第 29 卷（2016 年），4349–57。

10. [24.](#chapter11.xhtml#notes-ch11_24) 例如，参见 J. Zhao 等人，“Learning Gender-Neutral Word Embeddings”，载于《Proceedings of the 2018 Conference on Empirical Methods in Natural Language Processing》（2018 年），4847–53，以及 A. Sutton、T. Lansdall-Welfare 和 N. Cristianini，“Biased Embeddings from Wild Data: Measuring, Understanding, and Removing”，载于《Proceedings of the International Symposium on Intelligent Data Analysis》（2018 年），328–39。

## 12: Translation as Encoding and Decoding

1.  [1.](#chapter12.xhtml#notes-ch12_1) Q. V. Le 和 M. Schuster，“A Neural Network for Machine Translation, at Production Scale”，《AI Blog》，Google，2016 年 9 月 27 日，ai.googleblog.com/2016/09/a-neural-network-for-machine.html。

2.  [2.](#chapter12.xhtml#notes-ch12_2) W. Weaver，“Translation”，载于 W. N. Locke 和 A. D. Booth 编，《Machine Translation of Languages》（New York: Technology Press and John Wiley & Sons, 1955），15–23。

3.  [3.](#chapter12.xhtml#notes-ch12_3) 这是 Google Translate 对大多数语言所采用的方法。撰写本文时，Google Translate 尚未对某些不太常见的语言切换到神经网络。

4.  [4.](#chapter12.xhtml#notes-ch12_4) 更多详情，请参见 Y. Wu 等人，“Google’s Neural Machine Translation System: Bridging the Gap Between Human and Machine Translation”，arXiv:1609.08144（2016 年）。

5.  [5.](#chapter12.xhtml#notes-ch12_5) 在 Google 的神经机器翻译系统中，词向量是作为整个网络训练的一部分来学习的。

6.  [6.](#chapter12.xhtml#notes-ch12_6) 更具体地说，解码器网络的输出是网络词汇表中（此处为法语）每个可能单词的概率。更多详情请参见 Wu 等人，“Google’s Neural Machine Translation System”。

7.  [7.](#chapter12.xhtml#notes-ch12_7) 撰写本文时，Google Translate 和其他翻译系统的工作方式是一次翻译一个句子。关于超越逐句翻译的研究示例，请参见 L. M. Werlen 和 A. Popescu-Belis，“Using Coreference Links to Improve Spanish-to-English Machine Translation”，载于《Proceedings of the 2nd Workshop on Coreference Resolution Beyond OntoNotes》（2017 年），30–40。

8.  [8.](#chapter12.xhtml#notes-ch12_8) S. Hochreiter 和 J. Schmidhuber，“Long Short-Term Memory”，《Neural Computation》9，第 8 期（1997 年）：1735–80。

9.  [9.](#chapter12.xhtml#notes-ch12_9) Wu 等人，“Google’s Neural Machine Translation System”。

10. [10.](#chapter12.xhtml#notes-ch12_10) 同上。

11. [11.](#chapter12.xhtml#notes-ch12_11) T. Simonite，“Google’s New Service Translates Languages Almost as Well as Humans Can”，《Technology Review》，2016 年 9 月 27 日，[www.technologyreview.com/s/602480/googles-new-service-translates-languages-almost-as-well-as-humans-can](http://www.technologyreview.com/s/602480/googles-new-service-translates-languages-almost-as-well-as-humans-can)。

12. [12.](#chapter12.xhtml#notes-ch12_12) A. Linn，“Microsoft Reaches a Historic Milestone, Using AI to Match Human Performance in Translating News from Chinese to English”，《AI Blog》，Microsoft，2018 年 3 月 14 日，blogs.microsoft.com/ai/machine-translation-news-test-set-human-parity。

13. [13.](#chapter12.xhtml#notes-ch12_13) “IBM Watson Is Now Fluent in Nine Languages (and Counting)”，《Wired》，2016 年 10 月 6 日，[www.wired.co.uk/article/connecting-the-cognitive-world](http://www.wired.co.uk/article/connecting-the-cognitive-world)。

14. [14.](#chapter12.xhtml#notes-ch12_14) A. Packer，“Understanding the Language of Facebook”，EmTech Digital 视频讲座，2016 年 5 月 23 日，events.technologyreview.com/video/watch/alan-packer-understanding-language。

15. [15.](#chapter12.xhtml#notes-ch12_15) DeepL Pro，新闻稿，2018 年 3 月 20 日，[www.deepl.com/press.html](http://www.deepl.com/press.html)。

16. [16.](#chapter12.xhtml#notes-ch12_16) K. Papineni 等人，“BLEU: A Method for Automatic Evaluation of Machine Translation”，载于《Proceedings of the 40th Annual Meeting of the Association for Computational Linguistics》（2002 年），311–18。

17. [17.](#chapter12.xhtml#notes-ch12_17) Wu 等人，“Google’s Neural Machine Translation System”；H. Hassan 等人，“Achieving Human Parity on Automatic Chinese to English News Translation”，arXiv:1803.05567（2018 年）。

18. [18.](#chapter12.xhtml#notes-ch12_18) Google Translate 对“餐厅”故事的法语翻译：Un homme est entré dans un restaurant et a commandé un hamburger, cuit rare. Quand il est arrivé, il a été brûlé à un croustillant. La serveuse s’arrêta devant la table de l’homme. “Est-ce que le hamburger va bien?” Demanda-t-elle. “Oh, c’est génial,” dit l’homme en repoussant sa chaise et en sortant du restaurant sans payer. La serveuse a crié après lui, “Hé, et le projet de loi?” Elle haussa les épaules, marmonnant dans son souffle, “Pourquoi est-il si déformé?”

19. [19.](#chapter12.xhtml#notes-ch12_19) Google Translate 对“餐厅”故事的意大利语翻译：Un uomo andò in un ristorante e ordinò un hamburger, cucinato raro. Quando è arrivato, è stato bruciato per un croccante. La cameriera si fermò accanto al tavolo dell’uomo. “L’hamburger va bene?” Chiese lei. “Oh, è semplicemente fantastico,” disse l’uomo, spingendo indietro la sedia e uscendo dal ristorante senza pagare. La cameriera gli urlò dietro, “Ehi, e il conto?” Lei scrollò le spalle, mormorando sottovoce, “Perché è così piegato?”

20. [20.](#chapter12.xhtml#notes-ch12_20) Google Translate 对“餐厅”故事的中文翻译：一名男子走进一家餐厅, 点了一个罕见的汉堡包. 当它到达时, 它被烧得脆脆. 女服务员停在男人的桌子旁边. “汉堡好吗” 她问. “哦, 这太好了,” 那男人说, 推开椅子, 没有付钱就冲出餐厅. 女服务员大声喊道：“嘿, 账单呢?” 她耸了耸, 低声嘀咕道, “他为什么这么弯腰?”

21. [21.](#chapter12.xhtml#notes-ch12_21) 关于 Google Translate 缺乏理解所带来问题的深入讨论，请参见 D. R. Hofstadter，“The Shallowness of Google Translate”，《The Atlantic》，2018 年 1 月 30 日。

