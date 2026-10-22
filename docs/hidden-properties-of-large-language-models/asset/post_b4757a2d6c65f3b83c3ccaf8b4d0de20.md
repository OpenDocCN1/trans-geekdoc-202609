
Dedicated to my parents, Honglei Hu and Hong Sun

## Contents
- 1 Introduction 1
- 1.1 Thesis Organization ................................ 2
- 2 Background 5
- 2.1 Definition ................................ 5
- 2.2 Architecture ................................ 5
- 2.3 Training ................................ 8
- 2.4 Inference ................................ 9
- 3 A Simple and Effective Pruning Approach for Large Language Models 11
- 3.1 Overview ................................ 11
- 3.2 Introduction ................................ 11
- 3.3 Preliminaries ................................ 13
- 3.4 Approach ................................ 13
- 3.5 Experiments ................................ 17
- 3.5.1 Zero-Shot Tasks ................................ 17
- 3.5.2 Language Modeling ................................ 18
- 3.5.3 Speedup Evaluation ................................ 19
- 3.6 Analysis ................................ 20
- 3.7 Related Work ................................ 23
- 3.8 Additional Results ................................ 24
- 3.8.1 Image Classifiers ................................ 24
- 3.8.2 Previous LLMs ................................ 24
- 3.8.3 Additional Baselines ................................ 27
- 3.8.4 Number of Calibration Samples ................................ 28
- 3.8.5 Robustness Analysis ................................ 29
- 3.8.6 Higher Sparsity ................................ 29
- 3.8.7 Few-shot Results on MMLU ................................ 30
- 3.8.8 Fine-tuning ................................ 31
- 3.8.9 Zero-Shot Tasks ................................ 31
- 3.9 Conclusion ................................ 36

- 4.36 Average attention probability over all heads in intermediate layers of Phi-2. The input prompt is “William Shakespeare was a famous writer from England who wrote plays and poems. He is considered one of the best writers ever.\n His works include famous plays like ‘Romeo and Juliet’ and ‘Hamlet’.” . . . . . . . 64
- 4.37 Activation trajectory in the attention LayerNorm of LLaMA2-7B and Phi-2, where the LayerNorm input contains massive activations. Note that LLaMA2-7B uses a variant of layer normalization: RMSNorm [176] and Phi-2 uses the default LayerNorm [31]. . . . . . . . . . . . . . . . . . . . . . . . . . . . . 64
- 4.38 Value updates ∑_{i∈C} p_i^k v_i at layer 3 of LLaMA2-7B, with four input sequences. . 65
- 4.39 Value updates ∑_{i∈C} p_i^k v_i at layer 15 of LLaMA2-7B, with four input sequences. 65
- 4.40 Value updates ∑_{i∈C} p_i^k v_i at layer 30 of LLaMA2-7B, with four input sequences. 66
- 4.41 Attention distribution in default GPT-2 and GPT-2 with explicit attention bias. . 67
- 4.42 Ten largest activation magnitudes at each layer in three GPT-2 models. . . . . . . 68
- 4.43 Example images. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 68
- 4.44 Illustration of massive activations in CLIP ViT-L for the 4 images shown in Figure 4.43. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 69
- 4.45 Illustration of massive activations in DINOv2 ViT-L for the 4 images shown in Figure 4.43. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 69
- 4.46 Illustration of massive activations in DINOv2 ViT-G for the 4 images shown in Figure 4.43. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 69
- 4.47 Layer-level analysis for ViTs in MAE and CLIP. . . . . . . . . . . . . . . . . . 70
- 4.48 Layer-level analysis for ViTs in DINOv2. . . . . . . . . . . . . . . . . . . . . 71
- 4.49 Layer-level analysis for ViTs in DINOv2-reg. . . . . . . . . . . . . . . . . . 71
- 5.1 Our framework for studying idiosyncrasies in Large Language Models (LLMs). We show that each LLM is unique in its expression. In the example shown here on ChatGPT, Claude, Grok, Gemini, and DeepSeek, a neural network classifier is able to distinguish them with a near-perfect 97.1% accuracy. 76
- 5.2 Ablations on input length of text embedding models. Classification accuracies improve as the text embedding models capture more context. Performance begins to saturate beyond an input sequence length of 256. Note that the three lines represent different groups of LLMs and are not directly comparable. . . . . . . 81
- 5.3 Different numbers of training samples. Our sequence classifiers benefit from more training samples. The classification performance converges when using about 10K training samples. . . . . . . . . . . . . . . . . . . . . . . . . . . . . 83
- 5.4 Example responses from ChatGPT and Claude, showcasing their idiosyncrasies: characteristic phrases (left) and unique markdown formatting (right). For clarity, we highlight each characteristic phrase with underline and model-specific color. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 84
- 5.5 Frequencies of words and letters. The top 20 most frequently used words of LLMs (left) exhibit distinct patterns for each model, but their letter frequencies (right) are very similar. Results are on the chat API models. . . . . . . . . . . 85
- 5.6 **Characteristic phrases.** We train a logistic regression model on TF-IDF features of chat APIs’ outputs and extract the top 10 phrases for each LLM based on the coefficients of these features. We remove common words shared across these LLMs. 86
- 5.7 **First word.** We analyze the distribution of the first word in chat APIs’ responses, with the top 10 most frequent words for each model. These differences in first-word usage explain the non-trivial accuracy with only the first word in Figure 5.2. 87
- 5.8 **Markdown formatting elements.** Each LLM has a distinctive distribution of markdown formatting elements. 88
- 5.9 **Results of our open-ended language analysis on ChatGPT and Claude.** ChatGPT features descriptive language, sophisticated markdown formatting, and in-depth details, while Claude highlights straightforward tone, minimal structure, and summarized content. 89
- 5.10 **Inferring model similarity.** We consider 6 LLMs, including 5 chat API models and Phi-4. In each subfigure, we evaluate a five-way classifier on outputs from the excluded LLM and present the distribution of predicted model origins. There is a strong tendency for LLM outputs to be predicted as ChatGPT. 91
- 5.11 Prompts in our open-ended language analysis. 93
- 5.12 Confusion matrices for N-way classifiers on three groups of LLMs: chat APIs, instruct LLMs, and base LLMs. 94
- 5.13 Word and letter frequencies in instruct and base LLMs. 94
- 5.14 Characteristic phrases for instruct and base LLMs. 95
- 5.15 Distribution of first word choices in instruct and base LLMs. 95
- 5.16 Markdown formatting elements for chat APIs (top) and instruct LLMs (bottom). 96
- 5.17 Results of our open-ended language analysis on ChatGPT and Claude with different LLM judges. 97
- 5.18 Additional results of our open-ended language analysis on chat APIs (top) and instruct LLMs (bottom). 101

## Chapter 1
### Introduction

Large Language Models (LLMs) are a class of machine learning models trained with self-supervision on enormous amounts of text. The origin of LLMs began with the Transformer [1] model introduced in 2017. This model removed recurrence, used purely self-attention, and was originally designed for neural machine translation. In 2019, GPT-2 [2] was released by OpenAI, which brought widespread attention to LLMs. By design, GPT-2 is a decoder-only Transformer and trained with an auto-regressive objective on large corpora. Although small in size compared to today’s models, GPT-2 showed strong performance on various tasks, such as translation, summarization and simple question answering. More importantly, its simple design made it easy to scale and to perform inference with prompt-based natural language inputs. Since then, the development of LLMs has followed scaling laws, where larger models trained on more data generally perform better. Later models, such as GPT-3 [3] in 2020 and GPT-4 [4] in 2023, continue to showcase amazing capabilities achievable by LLMs.

To date, LLMs have made a substantial impact on our daily lives. Chatbots based on LLMs, like ChatGPT [5] and DeepSeek [6], are now being widely used all around the world. They have also spurred various applications, such as Cursor and Manus, that are aimed to significantly improve the human workflow. Even more, the goal of achieving Artificial General Intelligence (AGI) feels closer than ever, thanks to ever-increasing performance of LLMs. For researchers in machine learning and deep learning, the success of LLMs has led to a paradigm shift - from training supervised models to large-scale self-supervised representation learning. Another important lesson learnt from the development of LLMs is the importance of scaling laws - simple and scalable methods coupled with more compute and data, which continue to shape progress in AI beyond language domain, e.g., Sora [7] and Whisper [8].

While the impact of LLMs is undeniable, our primary mode of interaction and even much academic research on these models remain frustratingly superficial. In most real-world applications, users interact with these models through black-box APIs – providing a question as input and receiving an answer from APIs or chatbots in return. While this interface is convenient, there is little visibility into the internal processes behind generating these responses. In academic research, much of the focus on LLMs remains at the black-box level, examples include fine-tuning models for better performance [24, 134], developing new prompting strategies [9, 11, 33], and building evaluation benchmarks for new tasks [12, 35]. While these efforts are necessary and important, they offer limited insight into how LLMs actually function. Beyond performance, a scientific
