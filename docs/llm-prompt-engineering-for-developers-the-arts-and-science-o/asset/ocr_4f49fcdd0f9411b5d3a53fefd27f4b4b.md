tional nature. Traditional LMs usually generate text in a unidirectional manner, predicting the next word based on previous words. BERT’s bidirectional nature makes it excellent for tasks like understanding and classifying existing text but less suited for generating coherent and fluent sequences of new text.

BERT is a high-capacity model designed to **understand** sophisticated text.

# ### 2.7.2 - Generative pre-trained transformer (GPT)

GPT is a language model that can generate text based on a given prompt. It is trained on a large amount of text and can generate text that is similar to the text it was trained on.

GPT-3 and GPT-4 are the latest versions of GPT. They are powerful language models with many parameters. They are built on the same architecture as [GPT-2](https://github.com/openai/gpt-2)\(^9\) but with some changes. GPT-3 and GPT-4 use a mix of dense and sparse attention patterns in their layers, which helps the model process information efficiently.

Unlike BERT, GPT is a high-capacity model designed to **generate** sophisticated text.

Prompt engineering is highly relevant to GPT-based models, as it can be used to guide the model’s output and produce more relevant and coherent text. When we talk about prompt engineering, we typically refer to the manipulation of the initial sequence to guide the GPT’s output. This involves carefully crafting the input to elicit a specific type of response or to steer the model’s behavior in a desired direction. The better the prompt, the more accurate and contextually relevant the output from GPT tends to be.

As GPT models, especially GPT-3 and GPT-4, have grown in size and capability, the importance of effective prompt engineering has also increased. This is because these models have a vast amount of knowledge and potential responses, so guiding them effectively can be the difference between a generic answer and a highly specific, relevant one. Moreover,