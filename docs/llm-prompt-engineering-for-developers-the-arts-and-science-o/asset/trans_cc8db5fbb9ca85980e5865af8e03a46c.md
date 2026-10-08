

改写以下提示词：

- 对您个人而言，“优雅老去”意味着什么？
- 为什么“优雅老去”这一话题在当今社会中如此重要？

## 13 - ReAct：推理 + 行动

### 13.1 - 它是什么？

ReAct（推理 + 行动）框架代表了大语言模型领域的一种方法。

你可以把 ReAct 想象成一位厨师，他不仅一步步告诉你食谱，还会不时走出厨房去获取新鲜食材。

在这种情况下，ReAct 的“推理”部分就像厨师在解释每个步骤。它允许模型制定计划，必要时进行调整，并解决意外出现的问题。

“行动”部分则是我们的厨师去获取食材的时候。这代表了模型与外部数据库或工具通信以收集新数据或见解的能力，确保其回答准确且保持最新。当 ReAct 结合这两项能力（推理和行动）时，它以一种协调的方式进行，就像厨师根据现有食材调整食谱一样。

这种创新的结合使 ReAct 在任务执行上表现出色，产生既拟人又易于理解解决方案，最终增强了我们对模型能力的信心。

在一篇题为*《ReAct：协同语言模型中的推理与行动》* [49]（Yao, S., Zhao, J., Yu, D., Du, N., Shafran, I., Narasimhan, K., & Cao, Y. (2022)）的研究论文中，作者研究了如何通过结合推理（如逐步思考）和行动（如制定计划）来提高大语言模型的有效性。他们没有分别研究这两者，而是将二者交织在一起。

[49] https://arxiv.org/pdf/2210.03629.pdf

语言模型在推理（例如思维链提示）和行动（例如 WebGPT、SayCan、ACT-1）方面正在变得更好，但这两个方向一直保持不变。

这意味着模型可以逐步思考其步骤，调整其计划，甚至从外部来源收集更多数据。他们称这种方法为“ReAct”。他们在各种任务上测试了 ReAct，例如回答问题和验证事实，并且表现非常出色。例如，当被要求回答问题和验证事实时，ReAct 可以通过使用维基百科 API 来避免常见错误。它还在如在线购物等任务上比其他方式表现更好，展示了其在不同情境下的有效性和适应性。

在两个交互式决策基准（ALFWorld 和 WebShop）上，ReAct 分别比模仿和强化学习方法高出 34% 和 10% 的绝对成功率，同时仅用一个或两个上下文示例进行提示。

我们将通过查看一个实际例子来更好地理解 ReAct。

### 13.2 - 使用 LangChain 进行 ReAct

假设我们要向模型提出以下问题：

```
# 问题 1
Roden Cutler House 由一家电力基础设施公司所有，该公司由澳大利亚新南威尔士州政府所有，请问它成立于哪一年？
```

```
# 问题 2
Alan Paton 和 Jaroslav Seifert 谁出生得更早？
```

```
# 问题 3
Anna Popplewell 在一部跟随时事发展的剧集中饰演了 Lady Lola，这部电视剧跟随时事发展指的是什么？
```

这些问题是从 [hotpotqa.github.io](https://hotpotqa.github.io/) [50] 数据集中随机选取的。

为了将额外信息纳入推理过程，我们将使用维基百科 Python 库来获取有用信息。我们还将使用配备 OpenAI 作为 LLM 的 LangChain。

**如果您不熟悉使用 LangChain 进行提示，本指南中有一章对此进行了详细说明。在这种情况下，我们建议您在阅读完该章后再回来查看这个示例。**

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

现在，让我们看看该代理如何使用第一个问题：“Roden Cutler House 由一家电力基础设施公司所有，该公司由澳大利亚新南威尔士州政府所有，请问它成立于哪一年？”

![](img/ee54af4a0c9d9a4beda42d94caa5229b_126_0.png)

#### 使用 LangChain 进行 ReAct

该代理首先搜索“Roden Cutler House”，发现它由 Ausgrid 所有。然后它搜索“Ausgrid”，发现它成立于 2011 年。然后它使用这些信息来回答问题。
这是该代理生成的文本：

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

让我们用第二个问题测试：“Alan Paton 和 Jaroslav Seifert 谁出生得更早？”

#### 使用 LangChain 进行 ReAct

![](img/ee54af4a0c9d9a4beda42d94caa5229b_128_0.png)

这是该代理生成的文本：

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

最后，让我们用第三个问题测试：“Anna Popplewell 在一部跟随时事发展的剧集中饰演了 Lady Lola，这部电视剧跟随时事发展指的是什么？”

