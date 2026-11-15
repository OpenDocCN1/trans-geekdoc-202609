

## 前言

## 0.1 本书的目的

Does precision mean relevance? Can reasoning exist without data? For that matter, what is data?

精确性等同于相关性吗？推理可以不依赖数据存在吗？更何况，什么是数据？

With those questions in mind, this book serves an early course in mathematical thinking for data science. Because data science is interdisciplinary, students of data science come from a variety of disciplines. Interdisciplinary motivations are fueling the emergence of data science initiatives in various academic disciplines, with Business, Statistics, Computer Science, Economics, and Psychology among the departments offering studies in data science. For many students, data science is considered a means of insight into a particular field of interest, with the study of its discrete mathematics not a primary objective.

怀着这些问题，本书作为一门面向数据科学的数学思维入门课程。由于数据科学是一门跨学科专业，数据科学的学生来自各个不同的学科。跨学科的动机正在推动各学术领域中数据科学项目的涌现，商学、统计学、计算机科学、经济学和心理学等部门都在开设数据科学研究。对许多学生来说，数据科学被视为了解特定感兴趣领域的一种手段，而其离散数学的研究并非首要目标。

Courses in introductory data science and discrete mathematics tend to be ambitious. Introductory data science courses are seen requiring students to have prerequisite knowledge of statistics and computer programming, and a first course in discrete mathematics generally resembles a buffet of mathematical topics.

入门级数据科学和离散数学课程往往目标宏大。入门级数据科学课程被认为要求学生具备统计学和计算机编程方面的先修知识，而离散数学的第一门课程通常看起来像是一道数学主题的“自助餐”。

Students are often preoccupied with enough abstraction to miss the basic empirical essence of data science. This book aims to make these connections.

学生常常过分沉迷于抽象概念，而忽略了数据科学基本的实证本质。本书旨在建立这些联系。

In particular, those pursuing data engineering and high-performance computing for data science should be aware of the foundational aspects of data and computation present in this book.

特别是，那些从事数据工程和数据科学高性能计算的人应该了解本书中涉及的数据和计算的基础方面。

I wrote this book to give interdisciplinary students of data science a solid foundation in discrete mathematics for data science, connecting fundamental and abstract concepts for elementary problem solving.

我写这本书是为了给跨学科背景的数据科学学生提供数据科学离散数学的坚实基础，连接基础和抽象概念，以解决基础问题。

### 0.1.1 背景

It is imperative to respect the interdisciplinary backgrounds of data science practitioners, as domain expertise ensures that analysis is kept to relevant contexts.

必须尊重数据科学从业者的跨学科背景，因为领域专长确保分析保持在相关语境中。

![](img/ff796e63b14a88ab72583e78f3994e90_31_0.png)

图 1 跨学科数据科学背景。

Context is important for the classification of data, for determining which data values belong in a certain class and which do not. In this age of Big Data, much irrelevant data and noise can amount to a significant waste of computing resources, and a much higher cost when mistaken for relevant data.

背景对于数据分类非常重要，用于确定哪些数据值属于某个类别，哪些不属于。在大数据时代，大量无关数据和噪声会导致计算资源的显著浪费，如果误认为相关数据，成本将更高。

For example, the history data scientist decides to count battlefield casualties that include soldiers too wounded for further combat. The business data scientist counts only those sales transactions where the customer's payment has been received. The data engineer supports the domain specialists, filling voids and minimizing redundancies among maintained data sets.

例如，历史数据科学家决定统计包括过重伤无法继续作战的士兵在内的战场伤亡人数。商业数据科学家仅统计客户付款已收到的销售交易。数据工程师支持领域专家，填补维护数据集中的空白，并尽量减少冗余。

The classification of data requires details with respect to its source, type, organization, and sampling rate. These details are largely matters of domain expertise. In the process of data analysis, raw data must be ingested from a source and format, and computational results then generated and encoded for the next stage of analysis and eventually storage.

数据分类需要关于其来源、类型、组织和采样率的细节。这些细节在很大程度上属于领域专长范畴。在数据分析过程中，必须从源和格式中摄取原始数据，然后生成并编码计算结果，以便进行下一阶段的分析并最终存储。

Data scientists use programming tools for data conditioning, converting data to various formats. When data inconsistencies are encountered that the tools fail to process correctly, the data scientist is forced to become a student of low-level character encoding. Therefore, machine representations of numbers and text are considered important. Machine numbers, data types, and numerical representations are a few examples of discrete mathematics in practice.

数据科学家使用编程工具进行数据处理，将数据转换为各种格式。当遇到工具无法正确处理的数据不一致性时，数据科学家被迫成为低级字符编码的学生。因此，数字和文本的机器表示被认为很重要。机器数字、数据类型和数值表示是离散数学在实践中的几个示例。

Computers get information from the outside world in discrete periodic samples. These samples are usually incomplete representations of real world data, being limited to a sampling rate per second of continuous data or a data set sampled from a much larger population of data. Figure 2 depicts discrete samples of a continuous data waveform, such as from audio or video input. Each of those discrete samples in Figure 2 may be considered a snapshot in time, as conveyed by Figure 3.

计算机以离散周期采样的方式从外部世界获取信息。这些样本通常是现实世界数据的不完整表示，其限制是每秒连续数据的采样率，或者是从更大数据总体中抽取的数据集。图 2 描绘了连续数据波形的离散样本，例如来自音频或视频输入。图 2 中的每个离散样本可以被视为一个时间快照，如图 3 所示。

![](img/ff796e63b14a88ab72583e78f3994e90_33_0.png)

图 2 离散与连续信息。

![](img/ff796e63b14a88ab72583e78f3994e90_34_0.png)

图 3 连续现实的离散快照。

### 0.1.2 历史与人性

Formal courses in discrete mathematics for computer science first appeared in the U.S. university curricula in the late 1970s. The rationale was that students of computer science needed exercise in mathematics related to applications and architectures of digital computers. The curriculum was later codified by the Association for Computing Machinery in a joint effort with the Mathematical Association of America. Early topics generally included analysis of algorithms, counting, propositional logic, and set theory.

面向计算机科学的离散数学正式课程最早出现在20世纪70年代末的美国大学课程中。其理由是计算机科学学生需要进行与数字计算机应用和架构相关的数学训练。该课程后来由计算机协会（ACM）与美国数学协会（MAA）共同努力制定为标准。早期的主题通常包括算法分析、计数、命题逻辑和集合论。

Over the past forty years, topics in discrete mathematics textbooks have expanded as computing topics have burgeoned, with college textbooks for discrete math now including several more subjects than were initially codified by ACM.²

过去四十年来，随着计算主题的不断涌现，离散数学教科书的主题已有所扩展，如今大学阶段的离散数学教科书包含的主题比ACM最初制定的标准多出若干门。²

Expanded coverage includes: automata theory, theory of computation, cryptography, information theory, and graph theory with various heuristics.

扩展的覆盖内容包括：自动机理论、计算理论、密码学、信息论以及带有各种启发式方法的图论。

¹B. Marion, “Discrete mathematics: Support of and preparation for the study of computer science,” Journal of Computing Sciences in Colleges, vol. 16, pp. 190–199, 2000. DOI: https://dl.acm.org/doi/10.5555/357697.357730. ⤢

¹B. Marion，“离散数学：对计算机科学研究的支持与准备”，《计算机学院计算机科学杂志》，第16卷，第190–199页，2000年。DOI: https://dl.acm.org/doi/10.5555/357697.357730。⤢

²D. Stanat and D. McAllister, Discrete Mathematics in Computer Science. Prentice Hall Englewood Cliffs, N.J., 1977, vol. 16, pp. 190–199 (Stanat & McAllister's text may be considered the first definitive textbook on discrete mathematics.) ⤢

²D. Stanat 和 D. McAllister，《计算机科学离散数学》。Prentice Hall，Englewood Cliffs, N.J.，1977年，第16卷，第190–199页（Stanat & McAllister的教材可被视为第一本确定的离散数学教科书。）⤢

The situation for students new to data science is, perhaps, mired by introductory courses that expose advanced topics too early. For example, it is not uncommon to see in an introductory data science text such sophisticated topics as machine learning, including cluster analysis and neural networks. This presupposes that the underlying principles and algorithms are understood by students, who may have just had their first exposure to statistical regression. Keep in mind that students of data science coming from varied interdisciplinary backgrounds often do not have adequate experience with computational systems to boldly go about such problem solving.

对于初学者来说，数据科学的状况或许会因入门课程过早涉及高级主题而变得困难重重。例如，在入门级数据科学教材中，出现机器学习（包括聚类分析和神经网络）等复杂主题并不罕见。这预设了学生理解底层原理和算法，而这些学生可能刚刚第一次接触统计回归。请记住，来自不同跨学科背景的数据科学学生通常缺乏足够的计算系统经验，无法大胆地进行此类问题求解。

## 0.2 预修知识

This book assumes no prior background in computer programming or statistics. The student should be comfortable with algebra at the college level. Some prior knowledge of the Linux command-line terminal would be helpful as some example programs may be run from the command-line.

本书不假定读者具备计算机编程或统计学方面的背景。学生应熟练掌握大学水平的代数。具备一些Linux命令行终端的先验知识将会有所帮助，因为一些示例程序可能需要从命令行运行。

## 0.3 UNIX

This book refers from time to time to the Unix operating system. Internet servers hosting Big Data are overwhelmingly Linux/Unix systems. These, in turn, are accessed by analysts remotely through various types of application interfaces, including database connections and Internet browsers. Derived from Unix is Linux, the most ubiquitous operating system in the world today. Of the top 500 supercomputers in the world, all run the Linux operating system.³ Most Internet servers are also hosted on Unix or Linux.

本书不时提及Unix操作系统。托管大数据的互联网服务器绝大多数都是Linux/Unix系统。分析师通过各种应用程序接口远程访问这些系统，包括数据库连接和互联网浏览器。从Unix衍生出的Linux是当今世界上最普遍的操作系统。世界上前500强超级计算机全部运行Linux操作系统。³ 大多数互联网服务器也托管在Unix或Linux上。

More data is being both generated and stored in a Linux/Unix environment than people realize. But it is easy to take for granted the architecture of our programming environment. When “properly” coded, we expect our programs to work smoothly, often oblivious to the extraordinary yet beautiful complexity of the underlying system. Some low-level aspects of such system complexity are illuminated by this book, which should be of particular interest to students of data science planning to work in data engineering.

在Linux/Unix环境中生成和存储的数据比人们意识到的要多。但我们很容易理所当然地接受编程环境的架构。当代码编写得“恰当”时，我们期望程序运行顺畅，常常忽略底层系统非凡而又优美的复杂性。本书揭示了此类系统复杂性的一些低级方面，这对于计划从事数据工程工作的数据科学学生来说尤为感兴趣。

³See https://top500.org ↗️

³参见 https://top500.org ↗️

### 0.3.1 编码规范

Coding is used in this book as a vehicle for learning the subject matter. You can learn the streets of the big city by studying a map. You can additionally walk the streets yourself and learn your way around through experience. To program is to walk the streets. Likewise, programming a statistics routine is a _learning-by-doing_ approach that seems to be effective for many students.

本书将编程作为学习主题的载体。你可以通过研究地图来了解大城市的街道。你还可以亲自走遍街道，通过经验熟悉环境。编程就是走街串巷。同样，编写统计例程是一种_边做边学_的方法，似乎对许多学生都有效。

Coding allows us to condense otherwise verbose descriptions of concepts into a relatively compact, albeit abstract, perspective. For example, code that tests conditions is used to augment concepts of mathematical proof.

编程使我们能够将原本冗长的概念描述浓缩为相对简洁（尽管抽象）的视角。例如，用于测试条件的代码被用来丰富数学证明的概念。

To an extent, this book uses a Forth-like code called _epop_ for its compact, yet natural language structure. _epop_ is designed as a teaching tool to help students learn discrete math for data science, with data processing in mind. _epop_'s postfix notation allows fairly concise mathematical expressions, which leads to relatively compact syntax. More about this coding convention is presented in [Appendix A](#), as well as in the online resources noted in [Appendix C](#).

在某种程度上，本书采用一种名为 _epop_ 的类Forth代码，因其简洁而又自然的语言结构。_epop_ 被设计为一种教学工具，帮助学生以数据处理为目标学习数据科学离散数学。_epop_ 的后缀记法允许相当简洁的数学表达式，从而产生相对紧凑的语法。有关此编码规范的更多内容将在 [附录 A](#) 中介绍，以及在 [附录 C](#) 中列出的在线资源中介绍。

