![](bbox=[0.143, 0.082, 0.857, 0.363])

Figure 4-3. Defeating prompt injection with added structure

# Adversarial Training

In AI security, *adversarial* refers to deliberate attempts to deceive or manipulate a machine learning model to produce incorrect or harmful outcomes. *Adversarial training* aims to fortify the LLM against prompt injections by incorporating regular and malicious prompts into its training dataset. The objective is to enable the LLM to identify and neutralize harmful inputs autonomously.

Implementing adversarial training for an LLM against prompt injection involves these key steps:

+   **1. Data collection**
+   Compile a diverse dataset that includes not just normal prompts but also malicious ones. These malicious prompts should simulate real-world injection attempts to trick the model into revealing sensitive data or executing unauthorized actions.

+   **2. Dataset annotation**
+   Annotate the dataset to label normal and malicious prompts appropriately. This labeled dataset will help the model learn what kind of input it should treat as suspicious or harmful.

+   **3. Model training**
+   Train the model as usual, using the annotated dataset with the additional adversarial examples. These examples serve as “curveballs” to teach the model to recognize the signs of prompt injections and other forms of attacks.