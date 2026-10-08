```
from langchain.prompts.chat import (
    ChatPromptTemplate,
    SystemMessagePromptTemplate,
    HumanMessagePromptTemplate,
)

system_template = "You are a smart bot specialized in answering questions about {topic}."
system_message_prompt = SystemMessagePromptTemplate.from_template(system_template)

human_template = "{text}"
human_message_prompt = HumanMessagePromptTemplate.from_template(human_template)

chat_prompt = ChatPromptTemplate.from_messages([system_message_prompt, human_message_prompt])

formatted_chat_prompt = chat_prompt.format_messages(topic="dogs", text="How to train a dog to sit?")
print(formatted_chat_prompt)
```

The final prompt appears like this:

```
[SystemMessage(content='You are a smart bot specialized in answering questions about dogs.', additional_kwargs={}), HumanMessage(content='How to train a dog to sit?', additional_kwargs={}, example=False)]
```

Here is another example where we share an initial chat sequence with the model: