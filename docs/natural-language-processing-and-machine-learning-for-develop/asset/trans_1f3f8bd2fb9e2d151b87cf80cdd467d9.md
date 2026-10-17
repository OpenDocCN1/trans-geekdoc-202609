
BLEU 是“双语评估研究”（bilingual evaluation understudy）的缩写，是一个众所周知的 NLP 指标。BLEU 分数涉及直接计算，并且由于 BLEU 分数通常与 NLP 模型一起发布，因此其包含已成为常规做法。

然而，BLEU 是为了衡量机器翻译而创建的，它在整个语料库上计算时最可靠，而不是按句子逐句计算。BLEU 分数的流行可能导致一种副作用，即将 BLEU 分数用于其他测量工具能够产生更准确结果的 NLP 任务。

BLEU 存在一些显著局限性：它不考虑句子结构，而句子结构在不同语言之间可能有很大差异（参见第 [3](#ch03.xhtml) 章节关于“词尾”的部分），也不考虑句子的含义。

在简化的说法中，BLEU 分数涉及精确率、n-gram 和与参考句子的完全匹配。BLEU 检查输出中有多少个 n-gram 也出现在参考翻译中。然而，BLEU 不能识别同义词，这意味着使用相近但不同的动词的句子对被视为不相似。例如，使用动词“drink”、“imbibe”和“consume”的三个句子在日常对话中可能被视为等价，但 BLEU 并不将它们视为相同。

### **ROUGE 分数：BLEU 的替代方案**

简要而言，ROUGE 分数是一种变体的 BLEU，它使用 *recall*（BLEU 使用 *precision*）并且统计参考翻译中出现的 n-gram 与输出中出现的 n-gram 的数量（BLEU 则相反）。关于 ROUGE 的更多信息请参见：

*[https://www.aclweb.org/anthology/N03-1020/](https://www.aclweb.org/anthology/N03-1020/)*

此外，还有与 BLEU 无关的技术，如困惑度（perplexity）、词误率（WER）和 F1 分数，这些都在附录中讨论。使用关键词“BLEU 分数替代方案”进行在线搜索即可找到许多讨论 BLEU 替代方案的文章。

## **总结**

本章首先快速概述了语言模型、文本编码技术以及两种词语境概念，随后介绍了词嵌入，它们在 NLP 中非常有用。你还学习了距离度量，例如余弦相似度（用于衡量两个向量之间的距离）和文档相似度。此外，你还了解了向量空间模型（VSM）和主题建模的概念。

# CHAPTER 5

# ALGORITHMS AND TOOLKITS (I)

本章包含上一章介绍的若干 NLP 相关概念的 Python 代码示例。你将看到一系列代码示例，涉及正则表达式、Python 库 BeautifulSoup、Scrapy，以及使用 SpaCy 库的各种 NLP 相关 Python 代码示例。

作为快速提醒，本章还有一个专门讨论正则表达式的附录（附录 C）以及另一个专门讨论 Sklearn Python 库的附录（附录 F），它们对本章中的一些代码示例具有相关性。

本章的第一部分包含一些使用正则表达式进行数据清洗的示例。第二部分包含一些关于 BoW（袋状词）、单热编码和 Sklearn 中词嵌入的基本示例。

第三部分介绍 BeautifulSoup，这是一个用于抓取 HTML 网页的 Python 模块。该部分包含一些 Python 代码示例，展示如何从 GitHub 代码仓库中抓取并操作 HTML 网页的内容。该部分还简要介绍了 Scrapy，这是一个基于 Python 的库，提供网页抓取功能以及多种其他 API。

第四部分介绍 spaCy，这是一个用于 NLP 的 Python 库，并附带展示 spaCy 各种特性的 Python 代码示例。

## **使用正则表达式清洗数据**

本节提供了使用正则表达式在需要清洗数据时能够实现的简单预览。如果你对正则表达式不熟悉，可以阅读附录 C，该附录专门讨论该主题。本节中用于本节代码示例的主要概念列表如下：

*   \[A-Z\] 匹配任何大写字母

*   \[a-z\] 匹配任何小写字母

*   \[a-zA-Z\] 匹配任何小写或大写字母

*   \[^a-zA-Z\] 匹配除小写或大写字母之外的任何字符

[Listing 5.1](#ch05.xhtml#list5.1) 显示了 `text_clean_regex.py` 的内容，该文件说明了如何从文本字符串中删除所有非字符符号。

***LISTING 5.1: text_clean_regex.py***

```python
import re # this is for regular expressions
text = "I have 123 apples for sale. Call me at 650-555-1212 or send me email at apples@acme.com."
print("text:")
print(text)
print()
# replace the '@' symbol with the string ' at ':
cleaned1 = re.sub('@', ' at ',text)
print("cleaned1:")
print(cleaned1)
# replace non-letters with ' ':
cleaned2 = re.sub('[^a-zA-Z]', ' ',cleaned1)
print("cleaned2:")
print(cleaned2)
# replace multiple adjacent spaces with a single ' ':
cleaned3 = re.sub(' +', ' ',cleaned2)
print("cleaned3:")
print(cleaned3)
```

[Listing 5.1](#ch05.xhtml#list5.1) 包含导入语句，以便在后续代码中使用正则表达式。之后初始化变量 `text` 为一段句子并显示其内容，然后定义变量 `cleaned1`，其中将“@”符号替换为包含空格的字符串“ at ”（注意“at”前后各有一个空格）。接下来，变量 `cleaned2` 被定义，其中将除字母以外的所有字符替换为空格。最后，变量 `cleaned3` 被定义，其中将连续的多个空格压缩为单个空格。运行 [Listing 5.1](#ch05.xhtml#list5.1) 中的代码，你将看到以下输出：

text: I have 123 apples for sale. Call me at 650-555-1212 or send me email at apples@acme.com. cleaned1: I have 123 apples for sale. Call me at 650-555-1212 or send me email at apples at acme.com. cleaned2: I have apples for sale Call me at or send me email at apples at acme com cleaned3: I have apples for sale Call me at or send me email at apples at acme com 

[Listing 5.2](#ch05.xhtml#list5.2) 显示了 `text_clean_regex2.py` 的内容，该文件说明了如何从文本字符串中删除 HTML 标签。

***LISTING 5.2: text_clean_regex2.py***

```python
import re # this is for regular expressions
# \[^>\]: matches anything *except* a '>' 
# <\[^>\]: matches anything after '>' *except* a '>' tag
tagregex = re.compile(r'<\[^>\]+>')
def remove_html_tags(doc):
    return tagregex.sub(':', doc)
doc1 = "<html><head></head></body><p>paragraph1</p><div>div element</div></html>"
print("doc1:")
print(doc1)
print()
doc2 = remove_html_tags(doc1)
print("doc2:")
print(doc2)
```

[Listing 5.2](#ch05.xhtml#list5.2) 包含导入语句，随后是变量 `tagregex`，它是一个正则表达式，匹配左角括号“<”，后跟任意非右角括号“>”的字符。随后定义函数 `remove_html_tags()`，该函数通过正则表达式将所有 HTML 标签替换为冒号“:”。代码随后初始化变量 `doc1` 为一个 HTML 字符串并显示其内容，最后调用 `remove_html_tags()` 方法对 `doc1` 进行清理并打印结果。运行 [Listing 5.2](#ch05.xhtml#list5.2) 中的代码，你将看到以下输出：

doc1: <html><head></head></body><p>paragraph1</p><div>div element</div></html> doc2: :::::paragraph1::div element:: 
```
