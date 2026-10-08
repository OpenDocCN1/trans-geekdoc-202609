```
emplate)

chat_prompt = ChatPromptTemplate.from_messages([system_message_prompt, \
human_message_prompt])

openai_chat = ChatOpenAI()

chain = LLMChain(
    llm=openai_chat,
    prompt=chat_prompt,
)

output = chain.run(topic="dogs", text="How to train a dog to jump over \\
a fence?")
print(output)
```

To create an initial chat sequence, we can use the ChatPromptTemplate class as we did in one of the previous examples:

```
from langchain.prompts import ChatPromptTemplate
from langchain.prompts.chat import (
    ChatPromptTemplate,
    SystemMessagePromptTemplate,
    HumanMessagePromptTemplate,
    HumanMessage,
)
from langchain.chains import LLMChain

template = ChatPromptTemplate.from_messages([
    SystemMessagePromptTemplate.from_template("You are a smart assistant\\
t, specialized in answering questions about {topic}."),
    HumanMessage(content="Hi there, how are you?"),
    SystemMessagePromptTemplate.from_template("Hey there, my name is {n\\
ame}"),
    HumanMessage(content="Great! I'm going to ask you some questions. I\\
'd like to have a conversation with you."),
```