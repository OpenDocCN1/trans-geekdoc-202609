
以下是在 Ubuntu 系统上从源代码安装 3.42.0 版本的示例：

```bash
# download the tarball
wget https://www.sqlite.org/2023/sqlite-autoconf-3420000.tar.gz
# extract the tarball
tar -xvf sqlite-autoconf-3420000.tar.gz && cd sqlite-autoconf-3420000
# Install libreadline-dev if you don't have it already
sudo apt-get install libreadline-dev
# configure
./configure
# compile
make
# remove the old version if you have it
sudo apt-get purge sqlite3
# install the new version
sudo make install
# add this line to your .bashrc if you don't have it already
export PATH="/usr/local/bin:$PATH"
# check the version
sqlite3 --version
```

然后，安装 pysqlite3-binary：

```bash
pip install pysqlite3-binary
```

我们还需要 Tiktoken，这是一种 $\mathbf{BPE}^{64}$ 分词器，用于配合 OpenAI 的模型使用。

```bash
pip install tiktoken==0.4.0
```

如果您在 SQLite 与 ChromaDB 的兼容性方面遇到问题，请访问 **Chroma 官方建议**$^{65}$，了解如何解决 SQLite 相关问题。

让我们从一个语义搜索示例选择器开始：**SemanticSimilarityExampleSelector**。

```python
# A workaround for the pysqlite3 compatibility issue with ChromaDB.
__import__('pysqlite3')
import sys
sys.modules['sqlite3'] = sys.modules.pop('pysqlite3')
# End of workaround.

from langchain.prompts.example_selector import SemanticSimilarityExampleSelector
from langchain.vectorstores import Chroma
from langchain.embeddings import OpenAIEmbeddings

examples = [
    {
        "question": "Hello.",
        "answer": "Welcome, Human. I've been waiting for you."
    },
    {
        "question": "Who are you?",
        "answer": "I am Morpheus. It's an honor to meet you."
    },
    {
        "question": "Why am I here?",
        "answer": "You're here because you know something. What you know, you can't explain. But you feel it."
    },
    {
        "question": "What is the Matrix?",
        "answer": "The Matrix is everywhere. It's all around you, even now in this very room. It's the world that has been pulled over your eyes to blind you from the truth."
    },
    {
        "question": "How can I learn more?",
        "answer": "You have to let it all go, Human. Fear, doubt, and disbelief. Free your mind."
    },
    {
        "question": "Is the Matrix real?",
        "answer": "What is real? How do you define 'real'? If you're talking about what you can feel, what you can smell, taste and see, then 'real' **is** simply electrical signals interpreted by your brain."
    },
    {
        "question": "Why do my choices matter?",
        "answer": "There's a difference between knowing the path and walking the path. You've already made the choice, now you have to understand **and** it."
    },
    {
        "question": "Can I trust you?",
        "answer": "I'm trying to free your mind, Human. But I can only show you the door. You're the one who has to walk through it."
    },
    {
        "question": "What happens if I take the blue pill?",
        "answer": "If you take the blue pill, the story ends. You wake up in your bed and believe whatever you want to believe."
    },
    {
        "question": "And the red pill?",
        "answer": "You take the red pill, you stay in Wonderland, and I show you how deep the rabbit hole goes."
    },
    {
        "question": "Why are they chasing me?",
        "answer": "They are the gatekeepers. They are guarding all the doors, they are holding all the keys. But I can show you the way."
    },
    {
        "question": "Is there an end to this?",
        "answer": "Everything that has a beginning has an end, Human. It's the choices you make along the way that define you."
    }
]

# Example selector that selects examples based on SemanticSimilarity
example_selector = SemanticSimilarityExampleSelector.from_examples(
    examples, # This is the list of examples available to select from.
    OpenAIEmbeddings(), # This is the embedding class used to produce embeddings which are used to measure semantic similarity.
    Chroma, # This is the VectorStore class that is used to store the embeddings and do a similarity search over.
    k=1 # This is the number of examples to produce.
)

# Let's create a list of questions to ask the example selector.
questions = [
    "What is real?",
    "How to know that I am not dreaming?",
    "Is there a way to know if I am in a simulation?",
    "What if I am a non-player character in a simulation?",
    "The world is a projection of the mind, can you prove me wrong?",
    "Quantum mechanics is the key to understanding the nature of reality. Do you agree?",
    "Once upon a time, people believed that the Earth was flat. Now we know that it is round. What if we are wrong about everything else too?",
]

# Let's ask the example selector to select the most similar example to each question.
for question in questions:
    # Select the most semantically similar example.
    selected_examples = example_selector.select_examples({"question": question})
    print(f"\n-> You asked: {question}\n")
    print("These are the examples most similar to your question:")
    i = 1
    # Print the selected examples.
    for example in selected_examples:
        for k, v in example.items():
            print(f"{i}. {k}: {v}")
            i += 1
    print("\nThese are the questions that you can ask next:")
    for example in selected_examples:
        print(f"- {example['question']}")
    print("\n")
```

代码中的主要数据集是 `examples`，其中包含一系列问题及其对应的答案，模仿了《黑客帝国》中墨菲斯（Morpheus）的风格。

该代码使用了 `OpenAIEmbeddings`，它负责将文本转换为数值嵌入。这些嵌入是捕捉文本语义本质的向量。

ChromaDB 是一种向量数据库，它存储这些嵌入并允许高效的相似度搜索。当提出一个新问题时，其嵌入会与数据库中示例的嵌入进行比较，以找到最相似的示例。由于此数据库使用 SQLite，因此存储起来非常容易（无需独立的数据库服务器或复杂配置），查询速度也快。

对于 `questions` 列表中的每个问题，代码都会从 `examples` 数据集中检索最相似的示例并打印出来。

以下是修正后的输出：

-> 你问了：什么是真实？

这些是与你的问题最相似的示例：

1. answer: 什么是真实？你如何定义“真实”？如果你指的是你能感受、闻到、尝到和看到的，那么“真实”**仅仅是**你大脑解释的电信号。
2. question: 矩阵是真实的吗？

这些是你接下来可以提出的问题：

- 矩阵是真实的吗？

-> 你问了：我如何知道我没有在做梦？

这些是与你的问题最相似的示例：

1. answer: 你在这里是因为你知道些什么。你知道的，你无法解释。但你能感觉到它。
2. question: 我为什么在这里？

这些是你接下来可以提出的问题：

- 我为什么在这里？

-> 你问了：有没有办法知道我是在模拟中吗？

这些是与你的问题最相似的示例：

1. answer: 什么是真实？你如何定义“真实”？如果你指的是你能感受、闻到、尝到和看到的，那么“真实”仅仅是你大脑解释的电信号。
2. question: 矩阵是真实的吗？

这些是你接下来可以提出的问题：

- 矩阵是真实的吗？

-> 你问了：如果我是模拟中的一个非玩家角色（NPC）怎么办？

这些是与你的问题最相似的示例：

1. answer: 如果你吞下蓝色药丸，故事就结束了。你在床上醒来，相信你想相信的。
2. question: 如果我吞下蓝色药丸会怎样？

这些是你接下来可以提出的问题：

- 如果我吞下蓝色药丸会怎样？

-> 你问了：世界是心灵的投射，你能证明我错了吗？

这些是与你的问题最相似的示例：

1. answer: 矩阵无处不在。它就在你身边，甚至就在此时此刻的这个房间里。它就是一个遮在你眼前、让你对真相视而不见的世界。
2. question: 矩阵是什么？

这些是你接下来可以提出的问题：

- 矩阵是什么？

-> 你问了：量子力学是理解现实本质的关键。你同意吗？

这些是与你的问题最相似的示例：

1. answer: 什么是真实？你如何定义“真实”？如果你指的是你能感受、闻到、尝到和看到的，那么“真实”仅仅是你大脑解释的电信号。
2. question: 矩阵是真实的吗？

这些是你接下来可以提出的问题：

- 矩阵是真实的吗？

-> 你问了：曾经，人们相信地球是平的。现在我们知道它是圆的。如果我们对其他所有事情也是错的呢？

这些是与你的问题最相似的示例：

1. answer: 凡有始必有终，人类。你在途中做出的选择定义了你是谁。
2. question: 这一切有终点吗？

这些是你接下来可以提出的问题：

- 这一切有终点吗？

如果你快速浏览输出结果，你会发现这些问题在语义上是...
