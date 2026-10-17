
本节包含一个代码示例，展示了在 NLTK 中定义的多种分词器。[Listing 6.16](#ch06.xhtml#list6.16) 显示了 `nltk_tokenizers.py` 的内容，阐释了如何对句子中的单词进行多种分词。

***LISTING 6.16: nltk_tokenizers.py***

```python
import nltk
text = "I love deep dish pizza. Mainly from Chicago. Also with beer."
sents = nltk.sent_tokenize(text)
words = nltk.word_tokenize(text)
tokens = nltk.wordpunct_tokenize(text)
tags = nltk.pos_tag(words)
print("text: ", text)
print("sents: ", sents)
print("words: ", words)
print("tokens:", tokens)
print("tags: ", tags)
```

[Listing 6.16](#ch06.xhtml#list6.16) 初始化变量 `text` 为字符串，随后创建了多种 NLTK 分词器的实例。`print()` 语句块显示每个分词器生成的 token。在 [Listing 6.16](#ch06.xhtml#list6.16) 中运行代码，会得到如下输出：

`text: I love deep dish pizza. Mainly from Chicago. Also with beer.`  
`sents: ['I love deep dish pizza.', 'Mainly from Chicago.', 'Also with beer.']`  
`words: ['I', 'love', 'deep', 'dish', 'pizza', '.', 'Mainly', 'from', 'Chicago', '.', 'Also', 'with', 'beer', '.']`  
`tokens: ['I', 'love', 'deep', 'dish', 'pizza', '.', 'Mainly', 'from', 'Chicago', '.', 'Also', 'with', 'beer', '.']`  
`tags: [('I', 'PRP'), ('love', 'VBP'), ('deep', 'JJ'), ('dish', 'JJ'), ('pizza', 'NN'), ('.', '.'), ('Mainly', 'RB'), ('from', 'IN'), ('Chicago', 'NNP'), ('.', '.'), ('Also', 'RB'), ('with', 'IN'), ('beer', 'NN'), ('.', '.')]`

下面的链接包含了前面输出中各项词汇及其对应的词性：

*[https://cs.nyu.edu/grishman/jet/guide/PennPOS.html](https://cs.nyu.edu/grishman/jet/guide/PennPOS.html)*

接下来的章节提供了使用 NLTK 库查找命名实体的另一个示例。

## **NLTK and Context-Free Grammars (Optional)**

简言之，上下文无关语法（CFG）是一组用于生成字符串模式的规则或“生产”。这些规则通常是递归的，涉及终端符号集合、非终端符号集合以及结束符号。还有一个开始符号，它是非终端符号，出现在 CFG 生成的初始字符串中。根据 CFG 的复杂程度，生产中也可能出现正则表达式。

前面的段落可能显得晦涩或甚至无用，但实际上你已经接触过 CFG：许多流行的编程语言（如 C、C++、Java，但不包括 Fortran）都是上下文无关语法。例如，C 语言的完整生产规则集长约五页。

下面是一个表示包含任意组合的算术运算符 `*`, `/`, `+`, `-`（以及作为操作数的数值）的简单语法示例：

`<expression> --> number <expression> --> ( <expression> ) <expression> --> <expression> + <expression> <expression> --> <expression> - <expression> <expression> --> <expression> * <expression> <expression> --> <expression> / <expression>`

虽然这段描述可能显得抽象，NLTK 库其实提供了对 CFG 的支持。[Listing 6.17](#ch06.xhtml#list6.17) 展示了 `nltk_grammar.py` 的内容，说明如何指定一个简单的上下文无关语法的生产规则。注意，通常在 CFG 中会用单个字母 N、V、P 代替名词、动词和介词：后者只是为了展示你可以在 CFG 的生产规则中更具表现力。

***LISTING 6.17: nltk_grammar.py***

```python
import re import nltk
from nltk.parse import RecursiveDescentParser

# Define a CFG (Context Free Grammar):
mygrammar = nltk.CFG.fromstring(""" S -> NP VP NP -> Art Noun | Art Noun PP VP -> Verb | Verb NP | Verb NP PP PP -> Prep NP Art -> 'a' | 'an' | 'the' Noun -> 'boy' | 'ball' | 'apple' | 'hot' | 'dog' Verb -> 'ate' | 'ran' | 'studied' Prep -> 'in' | 'with' """)

# a top-down parser:
rdstr = RecursiveDescentParser(mygrammar)
str1 = "the boy with the ball ate a hot dog"
str2 = "the boy ate an apple with the ball"

#display the grammar trees:
print("grammar trees for str1:")
for tree in rdstr.parse(str1.split()):
    print("tree:", tree)
print("------------------------")
print("grammar trees for str2:")
for tree in rdstr.parse(str2.split()):
    print("tree:", tree)
```

[Listing 6.17](#ch06.xhtml#list6.17) 初始化变量 `mygrammar`，包含 8 条生产规则，用于判断文本字符串是否符合给定语法。随后代码实例化 `RecursiveDescentParser` 类的对象 `rdstr`，并定义两个字符串 `str1` 与 `str2`。其中一条能够根据语法解析，另一条不能。

这两个字符串非常相似，肉眼区分难度较大。代码中包含两个循环分别显示 `str1` 与 `str2` 的解析树。可以看到只有 `str2` 有解析树，因为 `str1` 不属于定义的语法。

运行 [Listing 6.17](#ch06.xhtml#list6.17) 后，会看到：

`grammar trees for str1: ------------------------ grammar trees for str2: tree: (S (NP (Art the) (Noun boy)) (VP (Verb ate) (NP (Art an) (Noun apple) (PP (Prep with) (NP (Art the) (Noun ball)))))) tree: (S (NP (Art the) (Noun boy)) (VP (Verb ate) (NP (Art an) (Noun apple)) (PP (Prep with) (NP (Art the) (Noun ball)))))`

## **What is Gensim?**

Gensim 是一种基于 Python 的开源 NLP 库，用于执行文本处理、词向量嵌入和主题建模等 NLP 任务，其官方主页位于：*[https://gensim.readthedocs.io/en/latest/index.html]*

Gensim 支持无监督的主题建模，并采用现代统计机器学习方法。它还基于 Cython（除了 Python 之外）实现。Gensim 支持词向量模型，如 Word2Vec 和 FastText，同时也支持 LDA 和 LSI 用于主题建模。此外，Gensim 与 scipy 和 NumPy 兼容，并提供从 NumPy 数组到模型和反之的转换函数。

Gensim 可处理单个文本文档或文档集合（语料库）。它使用向量表示文档中的词汇，模型是一种将向量从一种表示转换为另一种表示的算法。

此外，Gensim 可以创建 BoW 语料库、tf‑idf 模型、word2vec 模型以及 n‑grams。它还能计算相似度度量。下面我们来看一个使用 gensim 与 tf‑idf 的示例（在下一节中讨论）。

### **Gensim and tf‑idf Example**

Gensim 同样支持单个文本文档或文档集合。[Listing 6.18](#ch06.xhtml#list6.18) 展示了 `gensim_tfidf.py` 的内容，说明如何将 gensim 与 tf‑idf 结合使用。

