```
```python
from langchain.llms import OpenAI
from langchain.chat_models import ChatOpenAI

llm = OpenAI()
chat_model = ChatOpenAI()

llm_response = llm.predict(formatted_prompt)
print(llm_response)
```
```

The output should look like this:

Answer: The German Shepherd is a large-sized breed of dog that was originally bred for herding and guarding sheep. They have a strong sense of loyalty and possess a strong protective instinct. They are highly intelligent and are often used as working dogs in many fields such as police work, search and rescue, and military roles. They are also recognized as one of the most popular breeds of family pets. Read more here: https://dogbreeds.wiki/german-shepherd

This demonstrates that the prompt is functioning as anticipated.

# ## 16.7 - Chat Prompt Templates

A PromptTemplate can generate a sequence of messages, detailing not just the content but also the role and order of each message. Typically, a ChatPromptTemplate consists of several ChatMessageTemplates, each dictating the format, role, and content of the respective ChatMessage. Here is an example: