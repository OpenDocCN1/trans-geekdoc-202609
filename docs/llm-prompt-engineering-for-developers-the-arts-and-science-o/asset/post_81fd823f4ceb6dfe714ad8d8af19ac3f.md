
Paraphrase the following prompts:

- What does aging gracefully mean to you personally?
- Why is the topic of aging gracefully so important in today's society?

## 13 - ReAct: Reason + Act

### 13.1 - What Is It?

The ReAct (Reason + Act) framework represents an approach in the field of Large Language Models.

Think of ReAct like a chef who not only tells you the recipe step-by-step but also occasionally steps out to get fresh ingredients.

In this case, the “reasoning” part of ReAct is like the chef explaining each step. It allows the model to formulate plans, adjust them when necessary, and tackle unexpected issues.

The “act” part is when our chef fetches the ingredients. This represents the model’s ability to communicate with external databases or tools to gather new data or insights, ensuring its responses are accurate and up-to-date. When ReAct combines these two capabilities, reasoning and acting, it does so in a coordinated manner, much like a chef adjusting a recipe based on the available ingredients.

This innovative blend allows ReAct to perform exceptionally well on tasks, producing solutions that are both human-like and easily understood, ultimately boosting our confidence in the model’s abilities.

In a research paper titled *ReAct: Synergizing Reasoning and Acting in Language Models* [49] (Yao, S., Zhao, J., Yu, D., Du, N., Shafran, I., Narasimhan, K., & Cao, Y. (2022)), the authors studied how Large Language Models can be made more effective by combining reasoning (like thinking through steps) and acting (like making plans). Instead of studying them separately, they interweave the two.

[49] https://arxiv.org/pdf/2210.03629.pdf

Language models are getting better at reasoning (e.g., chain-of-thought prompting) and acting (e.g., WebGPT, SayCan, ACT-1), but these two directions have remained separate.

This means the model can think through its steps, adjust its plans, and even gather more data from outside sources. They named this approach “ReAct.” They tested ReAct on various tasks, like answering questions and verifying facts, and it performed very well. For example, when tasked with answering questions or verifying facts, ReAct could avoid common mistakes by using a Wikipedia API. It also performed better than other methods on tasks like online shopping, demonstrating its effectiveness and adaptability in different situations.

On two interactive decision-making benchmarks (ALFWorld and WebShop), ReAct outperforms imitation and reinforcement learning methods by an absolute success rate of 34% and 10% respectively, while being prompted with only one or two in-context examples.

We are going to better understand ReAct by looking at a practical example.

### 13.2 - React Using LangChain

Let’s say we want to ask the model the following questions:

```
# Question 1
Roden Cutler House is owned by an electricity infrastructure company that is owned by the Government of New South Wales, Australia, and was formed in what year?
```

```
# Question 2
Who was born first, Alan Paton or Jaroslav Seifert?
```

```
# Question 3
Anna Popplewell played Lady Lola in a series that follows what ?
```

These questions were randomly picked from the [hotpotqa.github.io](https://hotpotqa.github.io/) [50] dataset.

To incorporate additional information into the reasoning, we are going to use the Wikipedia Python library to fetch useful information. We are also going to use LangChain with OpenAI as an LLM.

**If you are not familiar with prompting using LangChain, there is a chapter in this guide that explains it in detail. In this case, we recommend you come back to this example after reading that chapter.**

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

# Initialize the agent
react = initialize_agent(
    tools, # List of tools this agent has access to.
    llm, # Language model to use as the agent.
    agent=AgentType.REACT_DOCSTORE, # Agent type to use. If None and agent_path is also None, will default to AgentType.ZERO_SHOT_REACT_DESCRIPTION.
    verbose=True # Print out the agent's actions
)

question = input("Ask a question: ")
react.run(question)
```

Now, let’s see the agent in action with the first question: “Roden Cutler House is owned by an electricity infrastructure company that is owned by the Government of New South Wales, Australia, and was formed in what year?”

![](img/ee54af4a0c9d9a4beda42d94caa5229b_126_0.png)

#### ReAct using LangChain

The agent first searches for “Roden Cutler House” and finds that it is owned by Ausgrid. It then searches for “Ausgrid” and finds that it was formed in 2011. It then uses this information to answer the question.
This is the text generated by the agent:

> Entering new AgentExecutor chain...
>
> Thought: I need to search Roden Cutler House, find the electricity infrastructure company that owns it, then find the year it was formed.
>
> Action: Search[Roden Cutler House]
>
> Observation: Roden Cutler House is a skyscraper in Sydney, New South Wales, Australia. It consists of 19 floors primarily office/commercial space. Construction finished in 1975 and it is located at 24 Campbell Street, Sydney. The Antenna height is 112m and the structure height is 108 m. The building is owned by Ausgrid and the lower floors house the City South substation.
>
> The building is named after Sir Roden Cutler, the longest-serving Governor of New South Wales and a Victoria Cross recipient. Roden Cutler won the Victoria Cross in the 1941 Syrian campaign where he was wounded, requiring the amputation of a leg.[1]
>
> Thought: Roden Cutler House is owned by Ausgrid. I need to find the year it was formed.
>
> Action: Search[Ausgrid]
>
> Observation: Ausgrid is an electricity distribution company which owns, maintains and operates the electrical networks supplying 1.8 million customers servicing more than 4 million people in Sydney, the Central Coast and Hunter regions of New South Wales, Australia. It was formed in 2011 from the previously state-owned energy retailer/distributor, EnergyAustralia, when the retail division of the company, along with the EnergyAustralia brand, was sold by the Government of New South Wales, and the remainder renamed Ausgrid.
>
> Thought: Ausgrid was formed in 2011. So the answer is 2011.
>
> Action: Finish[2011]
>
> Finished chain.

Let’s test with the second question: “Who was born first, Alan Paton or Jaroslav Seifert?”

#### ReAct using LangChain

![](img/ee54af4a0c9d9a4beda42d94caa5229b_128_0.png)

This is the text generated by the agent:

```
> Entering new AgentExecutor chain...
Thought: I need to search Alan Paton and Jaroslav Seifert, and find who was born first.
Action: Search[Alan Paton]
Observation: Could not find [Alan Paton]. Similar: ['Alan Paton', 'David Paton', 'Sunday Times CNA Literary Awards', 'Lost in the Stars', 'The Alan Parsons Project', 'Deaths in 1988', 'Cry, the Beloved Country', 'Jonny Steinberg', 'Fred Khumalo', 'Liberalism in South Africa']
Thought: Alan Paton was born on January 11, 1903. I need to search Jaroslav Seifert next and find its date of birth.
Action: Search[Jaroslav Seifert]
Observation: Jaroslav Seifert (Czech: [jarošláv sajfrt] (listen); 23 September 1901 – 10 January 1986) was a Czech writer, poet and journalist. Seifert was awarded the 1984 Nobel Prize in Literature "for his poetry which endowed with freshness, sensuality and rich inventiveness provides a liberating image of the indomitable spirit and versatility of man".
Thought: Jaroslav Seifert was born on September 23, 1901. 1903 (Alan Paton) < 1901 (Jaroslav Seifert), so Jaroslav Seifert was born first.
Action: Finish[Jaroslav Seifert]
> Finished chain.
```

Finally, let's test with the third question: "Anna Popplewell played Lady Lola in a series that follows what?"
