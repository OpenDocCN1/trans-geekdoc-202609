
使用以下命令执行脚本：

```python
python app.py
```

你会发现聊天机器人现在可以进行交互了。你可以输入一条消息，聊天机器人会做出回应。你还可以输入“exit”或“quit”来结束交互。

## 5.8 - 使用多行提示词进行交互式输入

在某些情况下，我们可能会使用如下所示的提示词：

```text
写一个关于一个机器人试图学习如何成为人类的故事。
```

```text
这个机器人叫托伯（Tobor）。一旦托伯获得了说话的能力，他
就开始学习如何像人类一样思考。他首先学习如何思考并
培养创造性的想象力。
```

在这种情况下，我们需要接受来自用户的多行输入。我们可以使用以下代码来实现：

```python
import os
import openai
import click

openai.api_key = os.getenv("OPENAI_API_KEY")

@click.command()
def chat_with_felix():
    """Chat with Felix, the chatbot."""
    print("Felix: Hi there. I am Felix, the chatbot. How can I help you
today?")
    while True:  # This will keep the chat session active
        print("You: (Type your message. When done, type 'END' on a new line)")
        lines = []
        while True:
            line = input()
            if line == "END":
                break
            lines.append(line)
        message = '\n'.join(lines)

        # Exit the loop (and the program) if the user types 'exit' or 'quit'
        if message.lower() in ['exit', 'quit']:
            print("Felix: Goodbye!")
            break

        response = openai.ChatCompletion.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "system", "content": "You are a smart and helpful assistant."},
                {"role": "user", "content": "Hi there."},
                {"role": "assistant", "content": "Hi there. \n\nI am Felix, the chatbot.\nHow can I help you today?"},
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

## 6 - 少样本学习与思维链

### 6.1 - 什么是少样本学习？

少样本学习，有时也称为低样本学习，是一种允许模型仅凭少数几个示例就能做出准确预测的方法，从而减少数据收集和计算的成本。这项技术已应用于各个领域，例如：

- 计算机视觉（字符识别、目标跟踪、分类）
- NLP（文本补全、翻译、分类）
- 音频处理（声音克隆、转换）

### 6.2 - 零样本学习与少样本学习

诸如 GPT-4、PaLM 2、Llama 2 等大型语言模型是在海量数据集上训练而成的，它们在各种任务上都能表现良好。因此，通常在没有示例的情况下提示它们。这就是我们所说的零样本学习。然而，当任务复杂时，模型需要针对少量示例进行训练才能表现良好，这时就引入了少样本学习技术。

尽管如此，提高提示词的质量并采用最佳实践仍有助于你在零样本学习中取得更好的结果（上下文、连贯性、人设等）。

事实上，零样本学习是大多数情况下的首选方法。它更快、更容易。

### 6.3 - 少样本学习的途径

少样本学习有几种不同的途径，包括使用：

#### 6.3.1 - 关于相似性的先验知识

在训练期间，我们开发嵌入（embeddings），使其能够区分不同的类别，即使这些类别之前从未被见过。

可以把这想象成教 AI 识别猫和狗的区别，方法是给它看很多图片。即使后来它看到了以前没见过的猫或狗的品种，它仍然能猜得正确，因为它已经学会了猫和狗的一般区别概念。这有点像玩一个匹配相似物品的游戏，AI 会随着时间的推移变得更好。

#### 6.3.2 - 关于学习的先验知识

我们利用现有知识来引导学习算法选择那些不仅拟合数据良好，而且能有效泛化的参数。这有助于防止过拟合，特别是在处理有限数据时。

想象一下你在教某人骑滑板车。如果不是从头开始，如果他们以前骑过自行车，你可以利用这些知识帮助他们学得更快。同样，在教 AI 时，我们利用它已经知道的东西来帮助它学习新事物，而不会犯常见的错误。

#### 6.3.3 - 关于数据的先验知识

通过利用我们对数据固有结构和变化的理解，即使只提供少数几个示例，我们也能有效地训练 AI。这种知识为更高效的学习奠定了基础。

假设你正在教某人了解不同种类的水果。如果他们已经知道苹果和橙子，你可以利用这些知识来解释橘子（就像小橙子一样！）。同样，在教 AI 时，如果它对你要提供的信息（或数据）类型有所了解，它就能更轻松地学习新事物。

### 6.4 - 少样本学习的示例

让我们从这个简单的例子开始：

```python
import os
import openai
import click

openai.api_key = os.getenv("OPENAI_API_KEY")

@click.command()
def chat_with_felix():
    """Chat with Felix, the chatbot."""
    print("Felix: Hi there. I am Felix, the chatbot. Let's play a game. Give me a number and I'll tell you if it's even or odd.")

    while True:
        message = input("You: ")

        if message.lower() in ['exit', 'quit']:
            print("Felix: Goodbye!")
            break

        response = openai.ChatCompletion.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "system", "content": "You are a smart and helpful assistant."},
                {"role": "user", "content": "1"},
                {"role": "assistant", "content": "1 is an odd number because it is not divisible by 2."},
                {"role": "user", "content": "2"},
                {"role": "assistant", "content": "2 is an even number because it is divisible by 2."},
                {"role": "user", "content": "3"},
                {"role": "assistant", "content": "3 is an odd number because it is not divisible by 2."},
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

与 AI 交互：

1. 在这个例子中，我们使用少样本学习技术来教 AI 识别奇数和偶数，并以自定义方式做出回答。

另一个示例如下：

```python
import os
import openai
import click

openai.api_key = os.getenv("OPENAI_API_KEY")

@click.command()
def chat_with_felix():
    """Chat with Felix, the chatbot."""
    print("Felix: Hi there. I am Felix, the chatbot. Let's play a game. Name an animal, and I'll tell you if it's a mammal or not.")

    while True:
        message = input("You: ")

        if message.lower() in ['exit', 'quit']:
            print("Felix: Goodbye!")
            break

        response = openai.ChatCompletion.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "system", "content": "You are a smart and helpful assistant."},
                {"role": "user", "content": "dog"},
                {"role": "assistant", "content": "A dog is a mammal because it gives birth to live young and has fur."},
                {"role": "user", "content": "fish"},
                {"role": "assistant", "content": "A fish is not a mammal because it lays eggs and lives in water."},
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

与 AI 交互：
