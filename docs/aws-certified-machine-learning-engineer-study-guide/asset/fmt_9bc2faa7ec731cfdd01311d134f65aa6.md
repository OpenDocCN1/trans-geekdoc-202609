
# 16. B
AWS IAM enables access control by securely managing identities and access to AWS services and resources. AWS KMS provides encryption keys and manages their lifecycle, ensuring data and model security through encryption at rest and in transit.

# 17. C
Encrypting data at rest and in transit ensures that sensitive data remains secure, even if accessed without proper authorization.

# 18. B
Log transformation reduces skewness in data, making distributions more Gaussian-like, which can improve model performance and interpretation.

# 19. B
Dropout is a technique that prevents overfitting in neural networks. It works by randomly deactivating a percentage of neurons during training. This forces the remaining neurons to compensate, which prevents any one neuron from becoming too dependent on others.

# 20. C
Amazon SageMaker Clarify detects and measures bias in machine learning models, both before and after deployment, helping to ensure fair and unbiased predictions.

# 21. C
`P3.2xlarge` provides GPU acceleration, which is essential for models requiring high computational power for inference, ensuring optimal performance.

# 22. C
Amazon SageMaker Multi-Model Endpoints allows you to deploy multiple models on a single endpoint, effectively managing different model versions and improving resource utilization, leading to cost savings and simplified deployment management.

# 23. D
Amazon SageMaker with Endpoint Variants and Auto Scaling allows you to deploy multiple versions of a model with Auto Scaling to handle different traffic loads, providing high performance and scalable inference for real-time image processing.

# 24. A
Baseline constraints and statistics help ensure that the input data remains consistent with the training data and the model’s predictions continue to meet the required accuracy and compliance standards.

# 25. B
Role templates simplify the assignment of appropriate permissions based on common Amazon SageMaker tasks, ensuring that users have the necessary access while adhering to security best practices and reducing the complexity of role management.

# Chapter 1: Introduction to Machine Learning

![](images/chaptersquare.png)

Machine learning (ML) has become ubiquitous in our digital world. Whether you need to book a flight, visit your doctor, make an online purchase, pay a bill, or check the weather forecast, behind the scenes any of these actions has started (or is a part of) a process that collects large amounts of data, processes the data, and performs some ML task.

ML is a branch of artificial intelligence (AI) that enables systems to learn and improve from experience without being explicitly programmed.

The integration of ML into various domains has revolutionized industries by enhancing efficiency, accuracy, and decision-making capabilities.

This chapter will provide the ML foundations you need to know for the exam. To better understand ML, we need to set the context where ML originated, which is AI.

## Understanding Artificial Intelligence

AI is a branch of computer science whose main focus is to develop systems capable of performing tasks that typically require human intelligence. These tasks include (but are not limited to) recognizing speech, making decisions, solving problems, identifying patterns, and understanding languages. AI systems leverage techniques such as ML, natural language processing (NLP), deep learning, and computer vision to simulate cognitive functions like learning, reasoning, and self-correction. The field of AI is rapidly evolving, with applications spanning various industries, from healthcare and finance to autonomous vehicles and smart cities. Understanding AI involves exploring its fundamental concepts, its historical development, and the ethical implications of its widespread adoption.

AI systems ingest data, such as human-level knowledge, and emulate natural intelligence. ML is a subset of AI, where data and algorithms continuously improve the training model to help achieve higher-quality output predictions. Deep learning is a subset of ML. It is an approach to realizing ML that relies on a layered architecture, simulating the human brain to identify data patterns and train the model.

[Figure 1.1](#c001.xhtml#c01-fig-1) illustrates this hierarchy. It all starts with data and how data can be used to extract relevant information, which ultimately produces knowledge.

![FIGURE 1.1 Deep learning, machine learning, and AI.](images/c01f001.png)

[FIGURE 1.1](#c001.xhtml#rc01-fig-1) Deep learning, machine learning, and AI.

### Data, Information, and Knowledge

Data, information, and knowledge form the foundation of understanding and applying AI. `Data` is the raw, unprocessed facts and figures collected from various sources. When data is organized and processed, it transforms into `information`, which provides context and meaning. `Knowledge` is derived from the synthesis of information, enabling comprehension and informed decision-making.

In AI, data serves as the essential input that fuels ML algorithms, enabling the training of models to recognize patterns and make predictions. Information, structured from the data, helps refine these models by offering insights and context. Ultimately, knowledge empowers AI systems to emulate human-like reasoning, enhancing their ability to perform complex tasks, adapt to new situations, and provide valuable solutions across various domains.

#### Data

Data is defined as a value or set of values representing a specific concept or concepts. Data is the most critical asset of the digital age, fueling advancements in technology and shaping the way we understand and interact with the world. To harness its full potential, it’s essential to recognize the different classes of data: structured, semi-structured, and unstructured. Each class has unique characteristics and applications, particularly in the context of AI.

Understanding these classes of data and their peculiarities is crucial for leveraging AI’s full potential. Structured data provides the foundation for organized analysis, semi-structured data offers flexibility in handling complex information, and unstructured data unlocks a wealth of untapped insights. Together, they enable AI systems to learn, adapt, and deliver transformative solutions across various domains. Let’s review each class in more detail.

##### Structured Data

Structured data is highly organized and easily searchable in databases. This type of data adheres to a fixed schema, meaning it follows a predefined format with specific fields and records. For example, a spreadsheet containing customer information, such as names, addresses, and purchase histories, is structured data. It allows for efficient querying and analysis, making it invaluable for business intelligence and data-driven decision-making.

These are examples of structured data:

*   Relational databases (e.g., SQL databases)
*   Spreadsheets (e.g., Excel files)
*   Financial records (e.g., transaction logs)

##### Semi-Structured Data

Semi-structured data lacks the rigid structure of structured data but still contains some organizational elements, such as tags or markers, that provide context and hierarchy. This class of data is often used for storing and transmitting complex information that doesn’t fit neatly into a table format. Semi-structured data is more flexible than structured data, allowing for greater adaptability in handling diverse data types.

These are examples of semi-structured data:

*   `JavaScript Object Notation (JSON)` files
*   `Extensible Markup Language (XML)` documents
*   Email messages (headers, body text, attachments)

##### Unstructured Data
