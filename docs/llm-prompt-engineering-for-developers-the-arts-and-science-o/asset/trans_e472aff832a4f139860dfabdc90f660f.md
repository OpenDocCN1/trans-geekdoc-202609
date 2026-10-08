

cally similar to the examples.
例如，以下问题：

世界是心智的投影，你能证明我错了吗？

与以下示例相似：

矩阵无处不在。它就在你周围，甚至就在你眼前的这个房间里。它就是为了遮蔽你的双眼、让你看不见真相的世界。

让我们将选择器用在链中：

```python
# A workaround for the pysqlite3 compatibility issue with ChromaDB.
__import__('pysqlite3')
import sys
sys.modules['sqlite3'] = sys.modules.pop('pysqlite3')

from langchain.prompts.example_selector import SemanticSimilarityExampleSelector
from langchain.vectorstores import Chroma
from langchain.embeddings import OpenAIEmbeddings
from langchain.prompts.few_shot import FewShotPromptTemplate
from langchain.prompts.prompt import PromptTemplate

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
        "answer": "What is real? How do you define 'real'? If you're talking about what you can feel, what you can smell, taste and see, then 'real' is simply electrical signals interpreted by your brain."
    },
    {
        "question": "Why do my choices matter?",
        "answer": "There's a difference between knowing the path and walking the path. You've already made the choice, now you have to understand it."
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

example_selector = SemanticSimilarityExampleSelector.from_examples(
    examples, # This is the list of examples available to select from.
    OpenAIEmbeddings(), # This is the embedding class used to produce embeddings which are used to measure semantic similarity.
    Chroma, # This is the VectorStore class that is used to store the embeddings and do a similarity search over.
    k=1 # This is the number of examples to produce.
)

example_template = """
Human: {question}
AI: {answer}
"""

prompt = PromptTemplate(
    input_variables=["question", "answer"],
    template=example_template,
)

prefix = """
In this dialogue, a human seeks answers from an entity beyond the ordinary.
The AI, channeling the profound wisdom and enigmatic demeanor of Morpheus from "The Matrix", responds.
While the AI's words aren't direct quotes from the movie, they should capture the essence of Morpheus' philosophical nature.
It's imperative that the AI's responses directly address the human's inquiries, providing clarity amidst the cryptic undertones.
"""

suffix = """
Human: {question}
AI: """

question = input("Human: ")

prompt = FewShotPromptTemplate(
    example_selector=example_selector, # ExampleSelector used to select examples instead of using all examples.
    example_prompt=prompt, # PromptTemplate used to format an individual example.
    prefix=prefix, # A prompt template string to put before the examples.
    suffix=suffix, # A prompt template string to put after the examples.
    input_variables=["question"], # A list of the names of the variables the prompt template expects.
    example_separator="\n\n", # String separator used to join the prefix, the examples, and suffix.
)

from langchain.chat_models import ChatOpenAI
from langchain.chains import LLMChain

# initialize the model
llm = ChatOpenAI(
    temperature=1.2,
)

# get the response
chain = LLMChain(
    llm=llm,
    prompt=prompt,
)

print("AI: " + chain.run(question))
```

在本示例中，我们使用了`SemanticSimilarityExampleSelector`。然而，LangChain 提供了其他示例选择器。我们将探讨其中的一些。

### 16.11.1 - NGram 重叠示例选择器

`NGramOverlapExampleSelector` 根据输入与示例之间重叠的 n-gram 数量来选择示例。

> n-gram 重叠分数是一个度量指标，用于通过比较两个文本序列之间重叠的 n-gram 来衡量它们的相似性。n-gram 是指给定文本或语音中 n 个连续项目（例如单词、字符）的序列。此指标常用于文本相似度、抄袭检测和机器翻译评估等任务。

例如，考虑句子“I love cats”的 2-gram（或 bigrams）：
- I love
- love cats
- love ice-cream

https://python.langchain.com/docs/modules/model_io/prompts/example_selectors/ngram_overlap
https://en.wikipedia.org/wiki/N-gram

- ice-cream
- cream lover

要计算两个文本之间的 n-gram 重叠分数：
- 提取两个文本中的所有 n-gram。
- 统计两个文本之间共享的 n-gram 数量。
- 将共享 n-gram 的数量除以两个文本中所有唯一 n-gram 的总数。

得出的分数将在 0 到 1 之间，1 表示两个文本共享所有 n-gram，而 0 表示没有共享的 n-gram。

### 16.11.2 - 最大边际相关性示例选择器

`MaxMarginalRelevanceExampleSelector` 是一种旨在选择兼顾相关性和多样性示例的方法。

主要目标是找到与给定输入最相似的示例。这是通过测量示例和输入的嵌入之间的余弦相似度来完成的。

> 余弦相似度是一种度量指标，用于衡量两个嵌入在向量空间中的方向接近程度。较高的余弦相似度表示更大的相似性。想象你在空间中拥有两个向量（嵌入）。余弦相似度衡量的是这两个向量之间夹角的余弦值。如果向量相同，夹角为 0°，余弦值为 1。如果向量完全不同，夹角为 90°，余弦值为 0。

虽然相关性很重要，但如果只关注相关性，我们可能会得到一组非常相似的示例。为了避免这种情况，该选择器还会确保所选示例的多样性。在选择最相关的示例后，它会惩罚那些与已选示例过于相似的其他示例。这确保了下一个被选中的示例不仅与输入相关，而且与之前已选取的示例有所不同。

### 16.11.3 - 基于长度的示例选择器

`LengthBasedExampleSelector` 根据示例的长度进行选择，确保其不超过语言模型允许的最大长度或上下文窗口。

构建的提示词的总长度受用户输入和添加到其中的示例两者的影响。根据用户输入的长度，选择器将调整其包含在提示词中的示例数量。例如，如果用户输入较长，选择器将选择较少的示例，以确保总长度不超过模型的上下文窗口。相反，如果用户输入较短，选择器可以包含更多的示例，充分利用上下文窗口中的可用空间。

该选择器确保包含用户输入和所选示例的构建提示词始终保持在模型限制之内。

> GPT-3 等语言模型对每个提示词都有一个最大标记限制。如果提示词超过此限制，模型将无法处理它。

### 16.11.4 - 自定义示例选择器

如果现有的示例选择器都不满足您的需求，您可以通过继承 `BaseExampleSelector` 并实现 `select_examples` 方法来创建自己的自定义示例选择器。

