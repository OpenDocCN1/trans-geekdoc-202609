
# Unstructured Data

Unstructured data is the most common and diverse type of data, encompassing information that doesn’t follow a predefined format or schema. This class of data is often rich in content but challenging to analyze and search. Unstructured data requires advanced AI techniques, such as `NLP` and computer vision, to extract meaningful insights.

These are examples of unstructured data:

*   Text files (e.g., Word documents)
*   Multimedia files (e.g., images, videos)
*   Social media content (e.g., tweets, posts)

# Information

Information bridges the gap between raw data and actionable knowledge. Derived from data, information provides a semantic element in the form of context and meaning, resulting in a transformation of disparate facts and figures into coherent, useful insights.

Information can be understood as data that has been processed, organized, or structured in a way that adds context and relevance. Unlike raw data, which is often unorganized and lacks inherent meaning, information is data presented in a format that is understandable and useful to its recipient(s). For example, a list of temperatures recorded at various times of the day is mere data; when these temperatures are organized into a table showing daily weather patterns, they become information.

The key characteristics of information are accuracy, relevance, completeness, and timeliness:

*   **Accuracy** — Information must be precise and free from errors to be valuable. Inaccurate information can lead to misguided decisions and outcomes.
*   **Relevance** — Information should be pertinent to the context or problem at hand. Irrelevant information, no matter how accurate, serves little purpose.
*   **Completeness** — Information must be comprehensive enough to provide a clear understanding without ambiguity. Incomplete information can result in incorrect conclusions.
*   **Timeliness** — Information is most useful when it is available at the right time. Outdated information can be as detrimental as inaccurate information.

In AI, information plays a critical role in training and refining algorithms. AI systems rely on vast amounts of data to learn and make predictions. This data is processed into information that adds context and aids in pattern recognition and decision-making.

For instance, in `NLP`, raw text data is processed to extract meaningful information, such as sentiment analysis or language translation. Similarly, in computer vision, images are analyzed to identify objects and patterns, turning visual data into actionable information.

# Knowledge

Knowledge represents a higher level of understanding that goes beyond mere data and information. It encompasses the insights, experiences, and contextual understanding that enable individuals and systems to make informed decisions, solve problems, and innovate.

Knowledge is derived from the synthesis and application of information. It involves recognizing patterns, understanding relationships, and drawing conclusions based on experience and context. Unlike data, which is raw and unprocessed, or information, which is organized and meaningful, knowledge embodies a deeper comprehension that guides action and thought.

The key characteristics of knowledge are contextuality, applicability, basis in experience, and dynamism.

*   **Contextuality** — Knowledge is deeply rooted in context. It involves understanding not just the facts but also the circumstances and nuances that surround them.
*   **Applicability** — Knowledge is practical. It involves the ability to apply information to real-world situations, making it actionable and relevant.
*   **Experience-based** — Knowledge is often gained through experience. It encompasses lessons learned, insights gained, and the wisdom accumulated over time.
*   **Dynamism** — Knowledge is ever-evolving. As new information becomes available and experiences accumulate, knowledge grows and adapts.

In AI, knowledge is crucial for developing systems that can derive inferences, learn, and adapt. AI systems rely on vast amounts of data and information to build knowledge bases that enable them to perform complex tasks and make intelligent decisions.

For example, expert systems in AI were designed to emulate human expertise in specific domains. These systems utilized knowledge bases that contained rules, facts, and relationships, allowing them to provide recommendations and solve problems. Similarly, `ML` algorithms use data and information to build models that capture knowledge about patterns and trends, enabling predictive analytics and decision-making.

# Understanding Machine Learning

`ML` is a subset of AI that allows computers to learn from existing information, *without being explicitly programmed*, and apply that learning to perform other similar tasks.

Without explicit programming, the machine learns from data and information it feeds. The machine picks up patterns, trends, or essential features from previous data and makes predictions on new data. This aspect of `ML`, i.e., a machine’s ability to learn *without being explicitly programmed*, is important and emphasizes the key difference between `ML` and classical programming.

Let’s say you are tasked by your manager to build a program that translates text from English to Italian. At a very high level, you could pursue a classical programming approach by manually coding rules and exceptions for lexicon, grammar, syntax, and vocabulary. This approach would be extremely complex and not scalable. Instead, with `ML`, you could leverage models that excel at understanding context, idioms, and nuances in both languages, which are essential for accurate translation. These `ML` models can continuously improve their translation capabilities with more data, adapting to new expressions, idioms, and evolving language usage.

A real-life `ML` application is in recommendation systems. For example, Amazon uses `ML` to recommend books to users based on users’ book categories selection and purchase history. Likewise, Spotify uses `ML` to recommend songs to users based on previously purchased songs and genres to their liking. In both cases, Amazon and Spotify use large amounts of data to train their `ML` models and derive meaningful inferences in the form or recommendations.

In the upcoming sections, the fundamental concepts of `ML` will be introduced. These concepts will form the basis you need to master each exam objective. Let’s start with the `ML` lifecycle.

## ML Lifecycle

First, you must have a holistic view of the entire `ML` lifecycle. Because `ML` is deeply grounded in science, it all starts by questions like “What is the business problem we are trying to solve?” and, most importantly, “How does machine learning address this business need?”

[Figure 1.2](#c001.xhtml#c01-fig-2) illustrates the `ML` lifecycle. These steps are generally followed in all `ML` projects, regardless of the cloud provider or the tools in use. Let’s review each step.

![FIGURE 1.2 Machine learning lifecycle.](images/c01f002.png)

[FIGURE 1.2](#c001.xhtml#rc01-fig-2) Machine learning lifecycle.

### Define ML Problem

Defining a `ML` problem is the critical first step in the development of any `ML` project. It involves understanding and clearly articulating the specific business challenge or question that needs to be addressed using data and `ML` techniques. This phase includes identifying the problem’s scope, the desired outcomes, and the feasibility of applying `ML` solutions. Crucially, it requires a detailed analysis of the available data, understanding the business context, and determining the performance metrics that will be used to evaluate success. By establishing a clear and well-defined problem statement, you can ensure that your efforts are focused and aligned with strategic goals, leading to more effective and impactful `ML` solutions.
