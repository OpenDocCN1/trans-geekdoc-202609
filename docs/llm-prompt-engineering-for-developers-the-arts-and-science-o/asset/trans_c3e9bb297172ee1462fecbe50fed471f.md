
("role", role_prompt),
("instructions", instructions_prompt),
("examples", example_prompt)
]

# 创建流水线提示词
pipeline_prompt = PipelinePromptTemplate(final_prompt=full_prompt, pipe\
line_prompts=input_prompts)

# 打印最终组合后的提示词
role_description = "你是一个非常聪明的机器人，专门回答有关狗品种的问题。"

instruction_details = """
写出以下犬种的特征："德国牧羊犬"。
"""

examples = """- 金毛寻回犬是一种大型犬，被培育用作枪犬，用于在狩猎和射击聚会中找回被击落的水禽（如鸭子）和陆禽。它们被称为“寻回犬”是因为它们有能力完好无损地找回被击中的猎物。在这里阅读更多：
https://dogbreeds.wiki/golden-retriever
- 罗威纳犬是一种家犬品种，通常被视为中大型或大型犬。在德国，这些狗被称为 Rottweiler Metzgerhund，意为罗特韦il屠夫犬，因为它们的主要用途是驱赶牲畜并将装满屠宰肉的马车拉往市场。在这里阅读更多：
https://dogbreeds.wiki/rottweiler
"""

formatted_prompt = pipeline_prompt.format(
    role_description=role_description,
    instruction_details=instruction_details,
    examples=examples
)

```python
from langchain.llms import OpenAI
from langchain.chat_models import ChatOpenAI

llm = OpenAI()
chat_model = ChatOpenAI()

llm_response = llm.predict(formatted_prompt)
print(llm_response)
```

输出应该如下所示：

回答：德国牧羊犬是一种大型犬，最初被培育用于牧羊和看管羊群。它们具有强烈的忠诚感，并拥有强烈的保护本能。它们非常聪明，经常被用作许多领域的工犬，例如警务、搜救和军事角色。它们也被认为是最受喜爱的家庭宠物品种之一。在这里阅读更多：https://dogbreeds.wiki/german-shepherd

这证明了该提示词按预期运行。

## 16.7 - 聊天提示词模板

PromptTemplate 可以生成一系列消息，不仅详细说明内容，还详细说明了每条消息的角色和顺序。通常，ChatPromptTemplate 由几个 ChatMessageTemplate 组成，每个模板规定相应 ChatMessage 的格式、角色和内容。以下是一个示例：

```python
from langchain.prompts.chat import (
    ChatPromptTemplate,
    SystemMessagePromptTemplate,
    HumanMessagePromptTemplate,
)

system_template = "你是一个非常聪明的机器人，专门回答关于{topic}的问题。"
system_message_prompt = SystemMessagePromptTemplate.from_template(system_template)

human_template = "{text}"
human_message_prompt = HumanMessagePromptTemplate.from_template(human_template)

chat_prompt = ChatPromptTemplate.from_messages([system_message_prompt, human_message_prompt])

formatted_chat_prompt = chat_prompt.format_messages(topic="dogs", text="如何训练狗坐下？")
print(formatted_chat_prompt)
```

最终提示词看起来像这样：

```
[SystemMessage(content='你是一个非常聪明的机器人，专门回答关于狗的问题。', additional_kwargs={}), HumanMessage(content='如何训练狗坐下？', additional_kwargs={}, example=False)]
```

以下是另一个示例，其中我们与模型共享初始聊天序列：

```python
from langchain.prompts import ChatPromptTemplate

template = ChatPromptTemplate.from_messages([
        ("system", "你是一个非常聪明的助手，专门回答关于{topic}的问题。")
        ,
        ("human", "嗨，你好吗？"),
        ("ai", "嗨，我的名字是{name}"),
        ("human", "太棒了！我要问你一些问题。我想和你进行对话。"),
        ("ai", "当然，我在这里为你解答关于{topic}的问题。"),
        ("human", "{user_input}"),
    ])

messages = template.format_messages(
    topic="personal finance",
    name="机器人Theo",
    user_input="节省钱的最好方法是什么？",
)

# 打印 messages 变量
print(f"Messages: {messages}\n")

# 打印内容
print(f"System message: {messages[0].content}\n")

# 打印对话
print(f"- human: {messages[1].content}")
print(f"- ai: {messages[2].content}")
print(f"- human: {messages[3].content}")
print(f"- ai: {messages[4].content}")
print(f"- human: {messages[5].content}")

from langchain.chat_models import ChatOpenAI
# 初始化模型
llm = ChatOpenAI()
# 获取响应
response = llm(messages)
# 打印模型的响应
print(f"- ai: {response.content}")
```

还可以将 `MessagePromptTemplate` 或 `BaseMessage` 的实例分别传递给 `ChatPromptTemplate`，即 `SystemMessage` 和 `HumanMessagePromptTemplate`：

```python
messages = template.format_messages(
    topic="personal finance",
    name="机器人Theo",
    user_input="节省钱的最好方法是什么？",
)

from langchain.chat_models import ChatOpenAI
# 初始化模型
llm = ChatOpenAI()

# 获取响应
response = llm(messages)
# 打印模型的响应
print(response.content)
```

## 16.8 - LangChain 的核心构建模块：LLMChain

LangChain 应用程序的基本组件之一是 LLMChain，它整合了三个主要元素：

- LLM：这作为主要的认知机制。
- 提示词模板：这些引导语言模型的响应。
- 输出解析器：这些将 LLM 的初始输出转换为更用户友好的格式，促进进一步的处理或利用。

以下是如何使用 LLMChain 的示例：

```python
from langchain.chat_models import ChatOpenAI
from langchain.prompts.chat import (
    ChatPromptTemplate,
    SystemMessagePromptTemplate,
    HumanMessagePromptTemplate,
)
from langchain.chains import LLMChain

system_template = "你是一个非常聪明的机器人，专门回答关于{topic}的问题。"
system_message_prompt = SystemMessagePromptTemplate.from_template(system_template)

human_template = "{text}"
human_message_prompt = HumanMessagePromptTemplate.from_template(human_t\
emplate)

chat_prompt = ChatPromptTemplate.from_messages([system_message_prompt, \
human_message_prompt])

openai_chat = ChatOpenAI()

chain = LLMChain(
    llm=openai_chat,
    prompt=chat_prompt,
)

output = chain.run(topic="dogs", text="如何训练狗跳过\\
栅栏？")
print(output)
```

要创建一个初始聊天序列，我们可以像在前面的示例中那样使用 ChatPromptTemplate 类：

```python
from langchain.prompts import ChatPromptTemplate
from langchain.prompts.chat import (
    ChatPromptTemplate,
    SystemMessagePromptTemplate,
    HumanMessagePromptTemplate,
    HumanMessage,
)
from langchain.chains import LLMChain

template = ChatPromptTemplate.from_messages([
    SystemMessagePromptTemplate.from_template("你是一个非常聪明的助手\\
，专门回答关于{topic}的问题。"),
    HumanMessage(content="嗨，你好吗？"),
    SystemMessagePromptTemplate.from_template("嗨，我的名字是{n\\
ame}"),
    HumanMessage(content="太棒了！我要问你一些问题。我想\\
和你进行对话。"),
    SystemMessagePromptTemplate.from_template("当然，我在这里为你解答 \
关于{topic}的问题。") , 
    HumanMessagePromptTemplate.from_template("{user_input}" ) ,
]
)

messages = template.format_messages( topic="personal finance", name="机器人Theo", user_input="节省钱的最好方法是什么？" ,
)

from langchain.chat_models import ChatOpenAI
# 初始化模型
llm = ChatOpenAI()

# 获取响应
chain = LLMChain( llm=llm, prompt=template ,
)

# 将输入作为字典传递给 chain.run() 方法
input_dict = {
    'topic': "personal finance",
    'name': "机器人Theo" ,
    'user_input': "节省钱的最好方法是什么？"
}

print(chain.run(input_dict))
```

## 16.9 - 自定义提示词模板

StringPromptTemplate 类是一个字符串提示词，它公开了 format 方法，返回一个提示词。它是 BasePromptTemplate 和 ABC 的子类。
