```
```
llm = ChatOpenAI()
# get the response
response = llm(messages)
# print the response of the model
print(f"- ai: {response.content}")
```
```

It is also possible to pass an instance of `MessagePromptTemplate` or `BaseMessage` to the `ChatPromptTemplate`, respectively `SystemMessage` and `HumanMessagePromptTemplate`:

```
```
messages = template.format_messages(
    topic="personal finance",
    name="Theo the bot",
    user_input="What is the best way to save money?",
)
```
```

```
```
from langchain.chat_models import ChatOpenAI
# initialize the model
llm = ChatOpenAI()
```
```

```
```
# get the response
```
```