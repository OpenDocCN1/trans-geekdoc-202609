![](bbox=[0.15, 0.09, 0.24, 0.18])

This example is from the Tensor2Tensor GitHub repository, which contains a Colab notebook that allows you to play around with a trained encoder-decoder Transformer model and see how the attention mechanisms of the encoder and decoder impact the translation of a given sentence into German.

# GPT-3 and GPT-4

Since the original 2018 publication of GPT, OpenAI has released multiple updated versions that improve upon the original model, as shown in Table 9-2.

Table 9-2. The evolution of OpenAI's GPT collection of models

| Model | Date | Layers | Attention heads | Word embedding size | Context window | # parameters | Training data |
|---|---|---|---|---|---|---|---|
| GPT | Jun 2018 | 12 | 12 | 768 | 512 | 120,000,000 | BookCorpus: 4.5 GB of text from unpublished books |
| GPT-2 | Feb 2019 | 48 | 48 | 1,600 | 1,024 | 1,500,000,000 | WebText: 40 GB of text from outbound Reddit links |
| GPT-3 | May 2020 | 96 | 96 | 12,888 | 2,048 | 175,000,000,000 | CommonCrawl, WebText, English Wikipedia, book corpora and others: 570 GB |
| GPT-4 | Mar 2023 | - | - | - | - | - | - |

The model architecture of GPT-3 is fairly similar to the original GPT model, except it is much larger and trained on much more data. At the time of writing, GPT-4 is in limited beta—OpenAI has not publicly released details of the model's structure and size, though we do know that it is able to accept images as input, so crosses over into being a multimodal model for the first time. The model weights of GPT-3 and GPT-4 are not open source, though the models are available through a commercial tool and API.

GPT-3 can also be fine-tuned to your own training data—this allows you to provide multiple examples of how it should react to a given style of prompt by physically updating the weights of the network. In many cases this may not be necessary, as GPT-3 can be told how to react to a given style of prompt simply by providing a few examples in the prompt itself (this is known as few-shot learning). The benefit of fine-tuning is that you do not need to provide these examples as part of every single input prompt, saving costs in the long run.