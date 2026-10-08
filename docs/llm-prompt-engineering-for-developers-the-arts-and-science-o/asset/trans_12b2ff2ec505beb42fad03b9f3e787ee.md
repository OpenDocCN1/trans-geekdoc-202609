

## 5 - 环境搭建

### 5.1 - 选择模型

由于 OpenAI GPT 模型是最受欢迎且使用最广泛的模型，并且可以通过 OpenAI API 轻松访问，我们将在本指南中使用它们。但是，要将本指南中讨论的概念和技术应用于其他模型，在几乎大多数情况下，你都可以使用相同的方法，无需进行重大更改。

我们的目标是理解提示工程背后的概念和技术，以及如何将它们应用于不同的模型。我们不会关注每个模型的技术细节。

### 5.2 - 选择编程语言

OpenAI API 官方支持 Python 和 Node.js[^20]。Azure OpenAI 库[^21] 可用于 .NET、Java、JavaScript 和 Go。其他社区库[^22] 也适用于其他语言，例如 Rust、PHP 等。

我们将使用 Python 作为本指南的编程语言，因为它是 AI 和机器学习中最受欢迎的语言。即使你不是 Python 开发者，使用 Python 入门也非常容易。

[^20]: https://platform.openai.com/docs/libraries/libraries
[^21]: https://platform.openai.com/docs/libraries/azure-openai-libraries
[^22]: https://platform.openai.com/docs/libraries/community-libraries

### 5.3 - 安装先决条件

为了避免与你机器上其他 Python 项目发生冲突，我们将为本指南创建一个 Python 虚拟环境。

要创建虚拟环境，你可以使用 Virtualenv、Virtualenvwrapper 或其他工具。我们将使用 [Virtualenvwrapper](https://github.com/python-virtualenvwrapper/virtualenvwrapper) 用于本指南。

首先安装 pip 和 virtualenvwrapper：

```bash
sudo apt install python3-pip
sudo pip3 install virtualenvwrapper
```

如果你使用的是 Windows，你可以使用 [Chocolatey](https://chocolatey.org/) 安装 pip 和 virtualenvwrapper：

```bash
choco install pip
pip install virtualenvwrapper-win
```

不过，我建议使用 [Multipass](https://multipass.run/) 或任何其他虚拟化工具在 Windows 上使用 Ubuntu 虚拟机。或者，你可以使用 DigitalOcean 或 AWS 等云服务。

我们的开发环境还将使用 Python 3.9。你应该已经安装了 Python 3.9。请按照此链接[安装 Python 3.9](https://www.python.org/downloads/)。

接下来，使用 Python 3.9 创建一个名为 pe（prompt engineering 的缩写）的虚拟环境：

```bash
mkvirtualenv pe --python=$(which python3.9)
```

在 Windows 上，你可以使用以下命令：

```bash
mkvirtualenv pe --python=<path to python.exe>
```

记得将 `<path to python.exe>` 替换为你机器上 python.exe 的实际路径。

创建虚拟环境后，它将自动激活。确保你正在使用 Python 3.9：

```bash
python --version
```

### 5.4 - 安装 OpenAI Python 库

OpenAI Python 库可在 PyPI 上获取[^27]。你可以使用 pip 安装它：

```bash
pip install openai==0.27.8
```

### 5.5 - 获取 OpenAI API 密钥

要使用 OpenAI API，你需要获取一个 API 密钥。你可以通过注册 OpenAI[^28]，然后在此处[^29]创建新的 API 密钥来获取。

请注意，API 的使用是收费的。但是，对于本指南来说，总成本不会超过 10 美元。可能甚至只有这个的一半。

别忘了将 API 密钥导出为环境变量：

```bash
export OPENAI_API_KEY=<your API key>
```

[^27]: https://pypi.org/project/openai/
[^28]: https://platform.openai.com/
[^29]: https://platform.openai.com/account/api-keys

### 5.6 - 一个 Hello World 示例

让我们从创建一个简单的 Python 脚本开始，以测试我们的安装。

在过去，OpenAI API 有像“Completion”和“Edit”这样的端点，现在这些端点已弃用。新 API 有一个名为“ChatCompletion”的单一端点，几乎适用于所有情况。该公司建议用户采用 Chat Completions API，该 API 已被证明功能强大，能够以更高的灵活性和特异性处理大多数用例。这就是我们将在此示例中使用的端点。

创建一个名为 app.py 的文件，并添加以下代码：

```python
# Import necessary libraries
import os          # Used for accessing environment variables
import openai      # OpenAI's Python client library

# Retrieve the OpenAI API key from environment variables
openai.api_key = os.getenv("OPENAI_API_KEY")

# Print an initial greeting message from Felix, the chatbot
print("Felix: Hi there. I am Felix, the chatbot. How can I help you today?")

# Get the user's message/input
user_message = input("You: ")

# Use the OpenAI API to generate a response based on the user's message
response = openai.ChatCompletion.create(
    model="gpt-3.5-turbo",  # Specify the model to be used
    messages=[
        # System message to set the behavior of the assistant
        {
            "role": "system",
            "content": "You are smart and helpful assistant."
        },
        # Initial user message (this is hardcoded and not used for any dynamic interaction)
        {
            "role": "user",
            "content": "Hi there."
        },
        # Initial assistant's response to the hardcoded user message
        {
            "role": "assistant",
            "content": "Hi there. \n\nI am Felix, the chatbot.\nHow can I help you today?"
        },
        # Actual user's message that was inputted earlier
        {
            "role": "user",
            "content": f"{user_message}"
        }
    ],
    # Parameters to guide the generation of the response
    temperature=1,         # Controls randomness. Higher values make output more random.
    max_tokens=256,        # Maximum number of tokens (words/characters) in the response
    top_p=1,               # Nucleus sampling parameter. Controls diversity of the output.
    frequency_penalty=0,   # Controls the penalty for using frequent tokens. 0 means no penalty.
    presence_penalty=0     # Controls the penalty for using new tokens. 0 means no penalty.
)

# Try to print the generated response
try:
    print("Felix: " + response.choices[0].message.content)
    # If there's an error (e.g., API error, network issues), print an error
except:
    print("Felix: Sorry, a problem occurred. Please try again later.")
```

这段代码使用 OpenAI API 设置了一个简单的聊天机器人交互。用户提供一条消息，聊天机器人（名为 Felix）根据给定的消息和先前硬编码的对话上下文进行响应。如果 API 调用出现任何问题，它将优雅地处理错误并通知用户。

### 5.7 - 交互式提示

为了使聊天机器人具有交互性，我们将使用 Click 创建一个命令行界面（CLI）。Click[^30] 是一个第三方 Python 包，允许以可组合的方式创建命令行界面，并且代码量尽可能少。它被称为“命令行界面创建工具包”。

使用 pip 安装 Click：

```bash
pip install click==8.1.7
```

接下来，更新 app.py 中的代码以使用 Click：

```python
import os
import openai
import click

openai.api_key = os.getenv("OPENAI_API_KEY")

@click.command()
def chat_with_felix():
    """Chat with Felix, the chatbot."""
    print("Felix: Hi there. I am Felix, the chatbot. How can I help you today?")
    while True: # This will keep the chat session active
        message = input("You: ")
        # Exit the loop (and the program) if the user types 'exit' or 'quit'
        if message.lower() in ['exit', 'quit']:
            print("Felix: Goodbye!")
            break
        response = openai.ChatCompletion.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "system", "content": "You are smart and helpful assistant."},
                {"role": "user", "content": "Hi there."},
                {"role": "assistant", "content": "Hi there. \nI am Felix, the chatbot.\n\nHow can I help you today?"},
                {"role": "user", "content": f"{message}"},
            ],
            temperature=1,
            max_tokens=256,
            top_p=1,
            frequency_penalty=0,
            presence_penalty=0
        )
        try:
            print("Felix:", response.choices[0].message.content)
        except:
            print("Felix: Sorry, a problem occurred. Please try again later.")

if __name__ == '__main__':
    chat_with_felix()
```

[^30]: https://palletsprojects.com/p/click/

