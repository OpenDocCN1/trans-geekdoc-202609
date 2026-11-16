
y 其他软件专业人士) 在编写任何代码之前。如果该过程涉及从面向对象的角度分析和设计您的系统，则称为**面向对象分析与设计（OOAD）过程。**像 Python 这样的语言是面向对象的。用这种语言编程，称为**面向对象编程（OOP）**，允许您将面向对象的设计实现为工作系统。

## 1.3 PYTHON

Python 是一种面向对象的脚本语言，于 1991 年公开发布。它由阿姆斯特丹国家数学与计算机科学研究所的 Guido van Rossum 开发。

Python 已迅速成为世界上最流行的编程语言之一。它目前在教育和科学计算领域特别流行，² 并且最近已超越编程语言 R，成为最流行的数据科学编程语言。³,⁴, ⁵ 以下是 Python 流行且每个人都应该考虑学习它的一些原因：⁶, ⁷, ⁸

- 2. https://www.oreilly.com/ideas/5-things-to-watch-in-python-in-2017.
- 3. https://www.kdnuggets.com/2017/08/python-overtakes-r-leader-analytics-data-science.html.
- 4. https://www.r-bloggers.com/data-science-job-report-2017-r-passes-as-but-python-leaves-them-both-behind/.
- 5. https://www.oreilly.com/ideas/5-things-to-watch-in-python-in-2017.
- 6. https://dbader.org/blog/why-learn-python.
- 7. https://simpleprogrammer.com/2017/01/18/7-reasons-why-you-should-earn-python/.
- 8. https://www.oreilly.com/ideas/5-things-to-watch-in-python-in-2017.

- 它是开源的、免费的且广泛可用，拥有庞大的开源社区。
- 它比 C、C++、C# 和 Java 等语言更容易学习，使新手和专业开发人员能够快速上手。
- 它比许多其他流行的编程语言更易读。
- 它在教育领域广泛使用。⁹

⁹ Tollervey, N., 《教育中的 Python：教学、学习、编程》（O’Reilly Media, Inc., 2015）。

- 它通过广泛的标准库和第三方开源库提高开发人员的生产力，因此程序员可以更快地编写代码，并用最少的代码执行复杂任务。我们将在第 1.4 节中详细介绍这一点。
- 有大量免费的开源 Python 应用程序。
- 它在 Web 开发中很受欢迎（例如，Django、Flask）。
- 它支持流行的编程范式——过程式、函数式和面向对象。0 我们将从第 4 章开始介绍函数式编程特性，并在后续章节中使用它们。

0 https://en.wikipedia.org/wiki/Python_(programming_language).

- 它简化了并发编程——使用 asyncio 和 async/await，您可以编写单线程并发代码 1，极大地简化了编写、调试和维护该代码这一本质上复杂的过程。2

1 https://docs.python.org/3/library/asyncio.html.

2 https://www.oreilly.com/ideas/5-things-to-watch-in-python-in-2017.

- 有许多可以提升 Python 性能的功能。
- 它用于构建从简单脚本到拥有大量用户的复杂应用程序的任何东西，例如 Dropbox、YouTube、Reddit、Instagram 和 Quora。3

3 https://www.hartmannsoftware.com/Blog/Articles_from_Software_Fans/Famous-Software-Programs-Written-in-Python.

- 它在人工智能领域很受欢迎，人工智能正在爆炸式增长，部分原因是它与数据科学的特殊关系。
- 它在金融界广泛使用。4

4 Kolonovic, M. and R. Krishnamachari, Big Data and AI Strategies: Machine Learning and Alternative Data Approach to Investing (J.P. Morgan, 2017).

- 许多学科中 Python 程序员的就业市场非常广阔，尤其是在面向数据科学的职位上，Python 工作也是所有编程工作中薪酬最高的工作之一。5 6

5 https://www.infoworld.com/article/3170838/developer/get-paid-10-programming-languages-to-learn-in-2017.html.

6 https://medium.com/@ChallengeRocket/top-10-of-programming-

- R 是一种用于统计应用和可视化的流行开源编程语言。Python 和 R 是两种最广泛使用的数据科学语言。

## Anaconda Python Distribution

我们使用 Anaconda Python 发行版，因为它在 Windows、macOS 和 Linux 上易于安装，并支持最新版本的 Python、IPython 解释器（在第 1.5.1 节中介绍）和 Jupyter Notebooks（在第 1.5.3 节中介绍）。Anaconda 还包括其他常用于 Python 编程和数据科学的软件包和库，让您可以专注于 Python 和数据科学，而不是软件安装问题。IPython 解释器 7 具有帮助您探索、发现和尝试 Python、Python 标准库以及大量第三方库的功能。

7 https://ipython.org/.

## Zen of Python

我们遵循 Tim Peters 的 The Zen of Python，它总结了 Python 创建者 Guido van Rossum 为该语言制定的设计原则。此列表可以在 IPython 中使用命令 import this 查看。The Zen of Python 在 Python 增强提案（PEP）20 中定义。“PEP 是一份向 Python 社区提供信息的设计文档，或描述 Python 或其流程或环境的新功能。” 8

8 https://www.python.org/dev/peps/pep-0001/.

## 1.4 IT’S THE LIBRARIES!

在本书中，我们专注于使用现有库来帮助您避免“重新发明轮子”，从而发挥您的程序开发工作的优势。通常，与其开发大量原创代码——一个昂贵且耗时的过程——不如只需创建预先存在的库类的一个对象，这只需要一条 Python 语句。因此，库将帮助您使用少量代码完成重要任务。在本书中，您将使用广泛的 Python 标准库、数据科学库和第三方库。

### 1.4.1 Python Standard Library

Python 标准库为文本/二进制数据处理、数学、函数式编程、文件/目录访问、数据持久化、数据压缩/归档、加密、操作系统服务、并发编程、进程间通信、网络协议、JSON/XML/其他 Internet 数据格式、多媒体、国际化、GUI、调试、性能分析等提供了丰富的功能。下表列出了我们在示例中使用的一些 Python 标准库模块。

### Some of the Python Standard Library modules we use in the book

| Module | Description |
|---|---|
| collections | 除列表、元组、字典和集合之外的其他数据结构。 |
| csv | 处理逗号分隔值文件。 |
| datetime, time | 日期和时间操作。 |
| decimal | 定点和浮点算术，包括货币计算。 |
| doctest | 通过在文档字符串中嵌入验证测试和预期结果来进行简单的单元测试。 |
| json | 用于与 Web 服务和 NoSQL 文档数据库配合使用的 JavaScript 对象表示法 (JSON) 处理。 |
| math | 常见数学常数和运算。 |
| os | 与操作系统交互。 |
| queue | 先进先出数据结构。 |
| random | 伪随机数。 |
| re | 用于模式匹配的正则表达式。 |
| sqlite3 | SQLite 关系型数据库访问。 |
| statistics | 均值、中位数、众数和方差等数学统计函数。 |
| string | 字符串处理。 |
| sys | 命令行参数处理；标准输入、标准输出和标准错误流。 |
| timeit | 性能分析。 |

### 1.4.2 Data-Science Libraries

Python 在许多领域拥有庞大且快速增长的开源开发者社区。Python 流行的最大原因之一是其开源社区开发的开源库范围非凡。我们的目标之一是创建示例和实现案例研究，为您提供引人入胜、充满挑战且有趣的 Python 编程入门，同时让您参与实践数据科学、关键数据科学库等。您将惊讶于只需几行代码就能完成的大量任务。下表列出了各种流行的数据科学库。在学习我们的数据科学示例时，您将使用其中许多库。对于可视化，我们将使用 Matplotlib、Seaborn 和 Folium，但还有更多。有关 Python 可视化库的良好摘要，请参见 `http://pyviz.org/`。

