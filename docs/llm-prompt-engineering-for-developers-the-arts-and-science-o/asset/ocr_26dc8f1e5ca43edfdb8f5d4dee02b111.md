# 12 - Perplexity as a Metric for Prompt Optimization

# 12.1 - Avoid Surprising the Model

Language models, when given prompts, can tackle a wide array of tasks with little to no prior examples. However, their effectiveness hinges greatly on the selected prompt. The reasons for this variation aren’t entirely clear. Some researchers have delved into the factors causing this discrepancy and proposed an idea: the better the model recognizes the language in the prompt, the more effectively it performs. Essentially, prompts that are more familiar or “natural” to the model yield better outcomes.

In simpler terms, prompts that are more common in the training data tend to perform better. This is because familiar sequences help the model understand and provide relevant information. However, it’s challenging to gauge this precisely since many language models are trained on vast data, and we don’t always have access to this data, as in the case of OpenAI GPT models.

This hypothesis was studied in the paper “Demystifying Prompts in Language Models via Perplexity Estimation” (Gonen, H., Iyer, S., Blevins, T., Smith, N. A., & Zettlemoyer, L. (2022)). We are not going to delve deep into the details of the paper, but the authors stated that over a wide range of tasks, the lower the perplexity of the prompt (i.e., closer to zero) is, the better the prompt is able to perform the task.

Instead of considering the training data, the paper proposes the perplexity of the prompt as a proxy used to gauge how often it might appear in the data. This method helps bypass the issue of finding an exact match and considers similar versions of the prompt. It’s also beneficial because we