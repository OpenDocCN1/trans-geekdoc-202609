
# LLM Prompt Engineering

## For Developers

The Art and Science of Unlocking LLMs' True Potential

Aymen EL Amri

![](img/ee54af4a0c9d9a4beda42d94caa5229b_0_0.png)

This book is for sale at http://leanpub.com/LLM-Prompt-Engineering-For-Developers

This version was published on 2024-04-22

![](img/ee54af4a0c9d9a4beda42d94caa5229b_1_0.png)

Published by FAUN.

At FAUN, we empower developers by keeping them at the forefront of what truly matters in the ever-evolving tech landscape.

© Aymen EL AMRI - www.faun.dev

## Contents

- Preface ... 1
- What Are You Going to Learn? ... 3
- To Whom is This Guide For? ... 5
- Join the Community ... 5
- About the Author ... 5
- The Companion Toolkit ... 6
- Your Feedback Matters ... 7
- **From NLP to Large Language Models** ... 9
  - What is Natural Language Processing? ... 9
  - Language Models ... 9
  - Statistical Models (N-Grams) ... 10
  - Knowledge-Based Models ... 11
  - Contextual Language Models ... 12
  - Neural Network-Based Models ... 12
  - Feedforward Neural Networks ... 12
  - Recurrent Neural Networks (RNNs) ... 13
  - Long Short-Term Memory (LSTM) ... 14
  - Gated Recurrent Units (GRUs) ... 14
  - Transformer Models ... 15
  - Bidirectional Encoder Representations from Transformers (BERT) ... 16
  - Generative pre-trained transformer (GPT) ... 17
  - What’s Next? ... 18
- **Introduction to Prompt Engineering** ... 19
- **OpenAI GPT and Prompting: An Introduction** ... 23
  - Generative Pre-trained Transformers (GPT) Models ... 23
  - What Is GPT and How Is It Different from ChatGPT? ... 23
  - The GPT models series: a closer look ... 24
  - GPT-3.5 ... 25
  - GPT-4 ... 26
  - Other Models ... 26
  - API Usage vs. Web Interface ... 26
  - Tokens ... 27
  - Costs, Tokens, and Initial Prompts: How to Calculate the Cost of Using a Model ... 29
  - Prompting: How Does It Work? ... 30
  - Probability and Sampling: At the Heart of GPT ... 34
  - Understanding the API Parameters ... 35
  - Temperature ... 36
  - Top-p ... 36
  - Top-k ... 38
  - Sequence Length (max_tokens) ... 38
  - Presence Penalty (presence_penalty) ... 38
  - Frequency Penalty (frequency_penalty) ... 39
  - Number of Responses (n) ... 39
  - Best of (best_of) ... 40
  - OpenAI Official Examples ... 40
  - Using the API without Coding ... 41
  - Completion (Deprecated) ... 42
  - Chat ... 44
  - Insert (Deprecated) ... 44
  - Edit (Deprecated) ... 45
- **Setting Up the Environment** ... 47
  - Choosing the Model ... 47
  - Choosing the Programming Language ... 47
  - Installing the Prerequisites ... 47
  - Installing the OpenAI Python library ... 49
  - Getting an OpenAI API key ... 49
  - A Hello World Example ... 49
- **Interactive Prompting** ... 52
  - Interactive Prompting with Multiline Prompt ... 54
- **Few-shot Learning and Chain of Thought** ... 57
  - What Is Few-Shot Learning? ... 57
  - Zero-Shot vs Few-Shot Learning ... 57
  - Approaches to Few-Shot Learning ... 57
  - Prior Knowledge about Similarity ... 58
  - Prior Knowledge about Learning ... 58
  - Prior Knowledge of Data ... 58
  - Examples of Few-Shot Learning ... 59
  - Limitations of Few-Shot Learning ... 63
- **Chain of Thought (CoT)** ... 68
- **Zero-shot CoT Prompting** ... 74
- **Auto Chain of Thought Prompting (AutoCoT)** ... 78
- **Self-Consistency** ... 80
- **Transfer Learning** ... 88
  - What Is Transfer Learning? ... 88
  - Inductive Transfer ... 89
  - Transductive Transfer ... 89
  - Inductive vs. Transductive Transfer ... 90
  - Transfer Learning, Fine-Tuning, and Prompt Engineering ... 92
  - Fine-Tuning with a Prompt Dataset: A Practical Example ... 93
  - Why Is Prompt Engineering Vital for Transfer Learning and Fine-Tuning? ... 100
- **Perplexity as a Metric for Prompt Optimization** ... 103
  - Avoid Surprising the Model ... 103
  - How to Calculate Perplexity? ... 104
  - A Practical Example with Betterprompt ... 107
  - Hack the Prompt ... 114
- **ReAct: Reason + Act** ... 116
  - What Is It? ... 116
  - React Using Langchain ... 117
- **General Knowledge Prompting** ... 123
  - What Is General Knowledge Prompting? ... 123
  - Example of General Knowledge Prompting ... 123
- **Introduction to Azure Prompt Flow** ... 132
  - What Is Azure Prompt Flow? ... 132
  - Prompt Engineering Agility ... 133
  - Considerations before Using Azure Prompt Flow ... 134
  - Creating Your First Prompt Flow ... 137
  - Deploying the Flow for Real-Time Inference ... 143
- **LangChain: The Prompt Engineer’s Guide** ... 146
  - What is LangChain? ... 146
  - Installation ... 146
  - Getting Started ... 147
  - Prompt Templates and Formatting ... 149
  - Partial Prompting ... 152
  - Composing Prompts Using Pipeline Prompts ... 154
  - Chat Prompt Templates ... 162
  - The Core Building Block of LangChain: LLMchain ... 166
  - Custom Prompt Templates ... 168
  - Few-Shot Prompt Templates ... 170
  - Better Few-Shot Learning with Example Selectors ... 174
  - NGram Overlap Example Selector ... 187
  - Max Marginal Relevance Example Selector ... 188
  - Length-Based Example Selector ... 188
  - The Custom Example Selector ... 189
  - Few-Shot Learning with Chat Models ... 196
  - Using Prompts from a File ... 203
  - Validating Prompt Templates ... 207
- **A Practical Guide to Testing and Scoring Prompts** ... 208
  - How and What to Evaluate in a Prompt ... 208
  - Testing and Scoring Prompts with promptfoo ... 212
