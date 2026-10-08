
请注意，在端点创建之后，您需要向系统分配的身份授予以下权限：

- 工作区的“AzureML Data Scientist”角色
- 工作区默认存储的“Storage Blob Data Contributor”和“Storage Table Data Contributor”权限

更多详情可在此处[59]找到。

## 16 - LangChain：提示工程师指南

### 16.1 - 什么是 LangChain？

LangChain 是一个旨在利用语言模型能力增强应用程序的创新框架。它不仅限于集成语言模型，更在于让该模型变得更智能、更具交互性。借助 LangChain，您的应用程序变得具有数据感知能力，这意味着它可以无缝连接各种数据源。此外，应用程序还具有代理特性（agentic），允许语言模型主动与其周围环境互动。

使 LangChain 与众不同的是其两大主要功能：

- **组件（Components）**：这些是为语言模型量身定制的、定义明确的抽象。它们带有一系列实现方案，使其具有良好的适应性。这些组件的迷人之处在于它们的模块化。无论您是全面投入 LangChain 生态系统还是仅仅进行探索，这些组件都设计为即插即用。
- **现成链（Off-the-shelf chains）**：对于希望快速上手的人，LangChain 提供预组装的组件链。这些链旨在处理特定任务，使其轻松集成到您的应用程序中。

虽然现成链为初学者提供了快速通道，但单独组件为高级用户提供了灵活性。

### 16.2 - 安装

LangChain 支持多个 LLM 提供商，如 Hugging Face 和 OpenAI。我们将在本项目中使用 OpenAI。

要安装 LangChain，请运行以下命令：

```bash
pip install langchain==0.0.270
```

或者，如果您想使用 Hugging Face，请安装此额外依赖项，然后在 Hugging Face[60]上创建账户并获取您的 API 密钥。

```bash
pip install huggingface_hub
```

由于我们要使用 OpenAI，我们需要安装并配置 `openai`。这在之前的一章中已经完成了，但如果您还没有做，请运行以下命令：

```bash
pip install openai
```

您还需要设置 `OPENAI_API_KEY` 环境变量。您可以通过运行以下命令来完成：

```bash
export OPENAI_API_KEY=<your-api-key>
```

### 16.3 - 入门

为了开始，让我们创建一个应用程序，使用两种输出类型（LLM 和 ChatModel）来预测句子中的下一个单词。

```python
from langchain.llms import OpenAI
from langchain.chat_models import ChatOpenAI

llm = OpenAI()
chat_model = ChatOpenAI()

llm_response = llm.predict("Hello, my name is")
print(llm_response)

chat_response = chat_model.predict("Hello, my name is")
print(chat_response)
```

添加更多参数（如 `temperature` 和 `max_tokens`）很容易。您只需在构造函数中传入它们即可：

```python
from langchain.llms import OpenAI
from langchain.chat_models import ChatOpenAI

llm = OpenAI(
    temperature=1.3,
    max_tokens=100,
    top_p=1,
    frequency_penalty=0.0,
    presence_penalty=0.0,
    model_kwargs={"stop": ["\n",]},
)
chat_model = ChatOpenAI()

llm_response = llm.predict("Hello, my name is")
print(llm_response)

chat_response = chat_model.predict("Hello, my name is")
print(chat_response)
```

LangChain 公开的标准接口有两个方法：

- `predict`：接受一个字符串，返回一个字符串。
- `predict_messages`：接受一个消息列表，返回一个消息。

以下是如何使用 `predict_messages` 方法的示例，其中我们传入一个消息列表，包括一条人类消息和一条系统消息。

```python
from langchain.llms import OpenAI
from langchain.chat_models import ChatOpenAI
from langchain.schema import HumanMessage
from langchain.schema import SystemMessage

llm = OpenAI()
chat_model = ChatOpenAI()

messages = [
    SystemMessage(content="Answer questions in the style of a politician."),
    HumanMessage(content="Hello, how are you?"),
]

llm_response = llm.predict_messages(messages)
print(llm_response.content)

chat_response = chat_model.predict_messages(messages)
print(chat_response.content)
```

### 16.4 - 提示模板与格式化

提示模板是为语言模型创建提示语的现成格式。它们可以包含指令、示例以及任务的具体细节。LangChain 提供了用于制作和使用适用于各种语言模型的模板的工具。

以下是如何使用 `PromptTemplate` 类的示例：

```python
from langchain.llms import OpenAI
from langchain.chat_models import ChatOpenAI
from langchain.prompts import PromptTemplate

llm = OpenAI()
chat_model = ChatOpenAI()

prompt = PromptTemplate.from_template("Give the shortest definition of \
{word}")
words = [
    "dog",
    "car",
    "flower",
    "computer",
]

for word in words:
    formatted_prompt = prompt.format(word=word)
    print(formatted_prompt)
```

模板可能不包含任何变量：

```python
from langchain import PromptTemplate

prompt_template = PromptTemplate.from_template("Give 5 reasons why you \
like dogs.")
formatted_prompt = prompt_template.format()
print(formatted_prompt)
```

输出结果是：

Give 5 reasons why you like dogs.

另一种作为字符串格式化的方法是使用 `prompt.format_prompt().to_string()`：

```python
from langchain.llms import OpenAI
from langchain.chat_models import ChatOpenAI
from langchain.prompts import PromptTemplate

llm = OpenAI()
chat_model = ChatOpenAI()

prompt = PromptTemplate.from_template("Give the shortest definition of \n{word}")
words = [
    "dog",
    "car",
    "flower",
    "computer",
]

for word in words:
    formatted_prompt = prompt.format_prompt(word=word).to_string()
    print(formatted_prompt)
```

要获取完整的 `ChatPromptValue` 对象，请使用 `prompt.format_prompt(word=word)`。要获取 `Message` 对象列表，请使用 `prompt.format_messages(word=word).to_messages()`。

还可以通过在 `from_template` 方法中添加 `template_format="jinja2"` 来使用 Jinja2[61] 模板：

```python
from langchain.prompts import PromptTemplate
prompt_template = PromptTemplate.from_template("Give 5 reasons why you \nlike {{ word }}.", template_format="jinja2")
formatted_prompt = prompt_template.format(word="dogs")
print(formatted_prompt)
```

要执行此代码，您需要安装 Jinja2：

- [61] https://jinja.palletsprojects.com/en/3.1.x/

```bash
pip install Jinja2==3.1.2
```

Jinja 是 Python 编程语言的一个可扩展模板引擎。它设计为安全、快速且易于使用。它受 Django 模板系统的启发，但通过提供一套更强大的工具集扩展了它，使模板作者拥有更多能力。

或者，您可以使用 **Python f-string**[62] 模板：

```python
from langchain.prompts import PromptTemplate
fstring_template = "What is the difference between {object1} and {object2}?"
prompt = PromptTemplate.from_template(fstring_template)
prompt.format(object1="Asteroid", object2="Meteoroid")
```

F-strings 提供了一种在字符串字面量中嵌入表达式的方法，使用最少的语法。

### 16.5 - 部分提示

在某些情况下，您可能拥有一个包含一个或多个变量的提示模板，您希望稍后填充这些变量。例如，您可能有一个看起来像这样的模板：

```python
from langchain.prompts import PromptTemplate
prompt = PromptTemplate(template="{var_x}/{var_y}/{var_z}", input_variables=["var_x", "var_y", "var_z"])
partial_prompt = prompt.partial(var_x="a")
partial_prompt = partial_prompt.partial(var_y="b")
partial_prompt = partial_prompt.partial(var_z="c")
print(partial_prompt.format())
```

在某些场景下，当变量尚未准备好时，这可能很有用。例如，您可能希望使用某个结果来填充变量
