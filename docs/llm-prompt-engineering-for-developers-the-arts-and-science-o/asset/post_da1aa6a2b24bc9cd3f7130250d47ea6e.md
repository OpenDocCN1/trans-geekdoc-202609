
Felix: Hi there. I am Felix, the chatbot. Let's play a game. Name an animal, and I'll tell you if it's a mammal or not.
You: cow
Felix: A cow is also a mammal. It is a large domesticated ungulate animal that is raised as livestock for meat, milk, and other dairy products. Cows give birth to live young and produce milk to feed their offspring.
You: Exit
Felix: Goodbye!

## 6.5 - Limitations of Few-Shot Learning

Let's consider an example where we want the AI to answer with "X" if the input is an odd number and "Y" if the input is an even number. We can use the following code that uses a few-shot learning technique:

```python
import os
import openai
import click

openai.api_key = os.getenv("OPENAI_API_KEY")

@click.command()
def chat_with_felix():
    """Chat with Felix, the chatbot."""
    print("Felix: Hi there. I am Felix, the chatbot. Let's play a game.\n")

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
                {"role": "assistant", "content": "X"},

                {"role": "user", "content": "2"},
                {"role": "assistant", "content": "Y"},

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

This is an execution example:

```text
Felix: Hi there. I am Felix, the chatbot. Let's play a game.
You: 1
Felix: X
You: 2
Felix: I'm sorry, but I'm not sure what you're referring to with "2." Could you please provide more context or clarify your question?
You: 3
Felix: Z
You: 4
Felix: Z
You: 5
Felix: Z
```

This is not the expected behavior! In order to solve this problem, we can use a different prompt, such as the following:

```python
import os
import openai
import click

openai.api_key = os.getenv("OPENAI_API_KEY")

@click.command()
def chat_with_felix():
    """Chat with Felix, the chatbot."""
    print("Felix: Hi there. I am Felix, the chatbot. Let's play a game.")

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
                {"role": "assistant", "content": "1 is an odd number so the answer is X."},


                {"role": "user", "content": "2"},
                {"role": "assistant", "content": "2 is an even number so the answer is Y."},


                {"role": "user", "content": "3"},
                {"role": "assistant", "content": "3 is an odd number so the answer is X."},


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

This is an execution example:

```text
Felix: Hi there. I am Felix, the chatbot. Let's play a game.
You: 10
Felix: 10 is an even number so the answer is Y.
You: 22
Felix: 22 is an even number so the answer is Y.
You: 44
Felix: 44 is an even number so the answer is Y.
You: 12
Felix: 12 is an even number so the answer is Y.
You: 13
Felix: 13 is an odd number so the answer is X.
You: 19
Felix: 19 is an odd number so the answer is X.
```

This is the expected behavior.

What we did to solve the problem was to provide a reasoning for the answer. This is a common technique used in few-shot learning to bypass some of the few-shot learning limitations. The few-shot learning technique can return incorrect answers if the prompt is complex. By providing a reasoning for the answer, or what we call a “Chain of Thoughts”, we can help the AI to understand the problem better and provide the correct answer.

## 7 - Chain of Thought (CoT)

According to “When do you need Chain-of-Thought Prompting for ChatGPT?”31 (Chen, J., Chen, L., Huang, H., & Zhou, T. (2023)), simply adding a CoT instruction can improve GPT-3’s accuracy from 17.7% to 78.7%. This is a significant improvement, but not every query requires a CoT instruction.

In fact, a CoT instruction is only necessary when the query is complex and the AI needs more information to understand the problem.

CoT is a technique that allows us to provide reasoning for the answer. This technique is used in combination with few-shot learning to bypass some of the limitations of few-shot learning.

Consider this example:

```python
import os
import openai
import click

openai.api_key = os.getenv("OPENAI_API_KEY")

@click.command()
def chat_with_felix():
    """Chat with Felix, the chatbot."""
    print("Felix: Hi there. I am Felix, the chatbot. Let's play a game.\n")

    while True:
        message = input("You: ")

        if message.lower() in ['exit', 'quit']:
            print("Felix: Goodbye!")
            break

        response = openai.ChatCompletion.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "system", "content": "You are a smart and helpful assistant."},
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

Then ask the following question:

When James was 2 years old, his sister was 2*2 years old. James is now 30 years old. How old is his sister?

This is how the dialog looks like:

Felix: Hi there. I am Felix, the chatbot. Let's play a game.
You: When James was 2 years old, his sister was 2*2 years old. James is now 30 years old. How old is his sister?
Felix: If James was 2 years old, then his sister was 2*2 = 4 years old. Since James is now 30 years old, his sister would be 30 - 2 = 28 years old.

As you can see, the answer is partially correct, which means that gpt-3.5-turbo was able to understand the age difference but didn't guess the correct age of the sister.

Even after asking a different question, the answer is still incorrect:

Felix: Hi there. I am Felix, the chatbot. Let's play a game.
You: When Harry was 25 years old, his sister was 29 years old. Harry is now 30 years old. How old is his sister?
Felix: If Harry is now 30 years old, then his sister is 29 years old, assuming their age difference remains constant.

A CoT instruction should improve the answer.

```python
import os
import openai
import click

openai.api_key = os.getenv("OPENAI_API_KEY")

@click.command()
def chat_with_felix():
    """Chat with Felix, the chatbot."""
    print("Felix: Hi there. I am Felix, the chatbot. Let's play a game.\n")

    while True:
        message = input("You: ")

        if message.lower() in ['exit', 'quit']:
            print("Felix: Goodbye!")
            break

        response = openai.ChatCompletion.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "system", "content": "You are a smart and helpful assistant."},
                {"role": "user", "content": "When James was 2 years old, his sister was 2*2 years old. James is now 30 years old. How old is his sister?"},
                {"role": "assistant", "content": "When James was 2 years old, his sister was 4 years old. There's 2 year differences between them and the sister is older than James. When James is 30 years old, his sister should be 32 years old."},
                {"role": "user", "content": "When Harry was 25 years old, his sister was 29 years old. Harry is now 30 years old. How old is his sister?"},
                {"role": "assistant", "content": "When Harry was 25 years old, his sister was 29 years old. There's 4 year differences between them and the sister is older than Harry. When Harry is 30 years old, his sister should be 34 years old."},
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
            print("Felix: Sorry, a problem occurred. Please try again.")
```
