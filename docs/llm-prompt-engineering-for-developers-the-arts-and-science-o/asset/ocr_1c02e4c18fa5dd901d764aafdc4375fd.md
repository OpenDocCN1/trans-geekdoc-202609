These questions were randomly picked from the [hotpotqa.github.io](https://hotpotqa.github.io/)<sup>50</sup> dataset.

To incorporate additional information into the reasoning, we are going to use the Wikipedia Python library to fetch useful information. We are also going to use LangChain with OpenAI as an LLM.

**If you are not familiar with prompting using LangChain, there is a chpter in this guide that explains it in detail. In this case, we recommend you come back to this example after reading that chapter.**

```
```python
from langchain import OpenAI, Wikipedia
from langchain.agents import initialize_agent, Tool
from langchain.agents import AgentType
from langchain.agents.react.base import DocstoreExplorer

# Wikipedia is the docstore that the agent will use to answer questions
docstore=DocstoreExplorer(Wikipedia())

# Tools are the functions that the agent can use to answer questions
tools = [
    Tool(
        name="Search",
        func=docstore.search,
        description="useful for when you need to ask with search"
    ),
    Tool(
        name="Lookup",
        func=docstore.lookup,
        description="useful for when you need to ask with lookup"
    )
]

# Define the agent that will be used to answer questions
llm = OpenAI(temperature=0, model_name="text-davinci-002")
```
```