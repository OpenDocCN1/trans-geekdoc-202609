
![](img/f0f0f5d89818fdddf117bbe758ac8143_285_0.png)

This example is from the Tensor2Tensor GitHub repository, which contains a Colab notebook that allows you to play around with a trained encoder-decoder Transformer model and see how the attention mechanisms of the encoder and decoder impact the translation of a given sentence into German.

## GPT-3 and GPT-4

Since the original 2018 publication of GPT, OpenAI has released multiple updated versions that improve upon the original model, as shown in Table 9-2.

Table 9-2. The evolution of OpenAI's GPT collection of models

| Model | Date | Layers | Attention heads | Word embedding size | Context window | # parameters | Training data |
|---|---|---|---|---|---|---|---|
| GPT | Jun 2018 | 12 | 12 | 768 | 512 | 120,000,000 | BookCorpus: 4.5 GB of text from unpublished books |
| GPT-2 | Feb 2019 | 48 | 48 | 1,600 | 1,024 | 1,500,000,000 | WebText: 40 GB of text from outbound Reddit links |
| GPT-3 | May 2020 | 96 | 96 | 12,288 | 2,048 | 175,000,000,000 | CommonCrawl, WebText, English Wikipedia, book corpora and others: 570 GB |
| GPT-4 | Mar 2023 | - | - | - | - | - | - |

The model architecture of GPT-3 is fairly similar to the original GPT model, except it is much larger and trained on much more data. At the time of writing, GPT-4 is in limited beta—OpenAI has not publicly released details of the model's structure and size, though we do know that it is able to accept images as input, so crosses over into being a multimodal model for the first time. The model weights of GPT-3 and GPT-4 are not open source, though the models are available through a commercial tool and API.

GPT-3 can also be fine-tuned to your own training data—this allows you to provide multiple examples of how it should react to a given style of prompt by physically updating the weights of the network. In many cases this may not be necessary, as GPT-3 can be told how to react to a given style of prompt simply by providing a few examples in the prompt itself (this is known as few-shot learning). The benefit of fine-tuning is that you do not need to provide these examples as part of every single input prompt, saving costs in the long run.

An example of the output from GPT-3, given a system prompt sentence, is shown in Figure 9-15.

Write me a short story about a unicorn who defeats an evil dragon.

Luna was out for a leisurely stroll through the forest when she heard a loud, ferocious roar. She immediately knew it was a dragon and ran as fast as she could in the opposite direction.

As she ran, she could feel the dragon's hot breath on her back and knew she wouldn't be able to outrun it for long. She had to think of a plan, and fast.

Just as the dragon was about to snatch her up in its teeth, Luna turned around and stabbed it in the eye with her horn. The dragon screeched in pain and flew into a rage, but Luna was ready for it.

She dodged its fire breath and claws until she finally had an opportunity to strike. She impaled the dragon with her horn and it fell to the ground with a thud, dead.

Luna breathed a sigh of relief and trotted away, knowing that she had saved the forest from the evil dragon.

Figure 9-15. An example of how GPT-3 can extend a given system prompt

Language models such as GPT benefit hugely from scaling—both in terms of number of model weights and dataset size. The ceiling of large language model capability has yet to be reached, with researchers continuing to push the boundaries of what is possible with increasingly larger models and datasets.

## ChatGPT

A few months before the beta release of GPT-4, OpenAI announced ChatGPT—a tool that allows users to interact with their suite of large language models through a conversational interface. The original release in November 2022 was powered by GPT-3.5, a version of the model that was more powerful than GPT-3 and was fine-tuned to conversational responses.

Example dialogue is shown in Figure 9-16. Notice how the agent is able to maintain state between inputs, understanding that the attention mentioned in the second question refers to attention in the context of Transformers, rather than a person's ability to focus.

What is a Transformer model and how is it used in generative deep learning? Can you give a short ~100 word summary?

A Transformer model is a type of deep learning model used in natural language processing tasks such as language translation and text generation. It utilizes an attention mechanism to enable the model to focus on different parts of the input sequence during processing, allowing it to capture long-range dependencies and better model context.

In generative deep learning, a Transformer model can be used as a language model to generate new text that is similar to the input data it was trained on. This can be achieved by using the model's output at each time step as input to the next time step, and sampling from the output probability distribution to generate the next word in the sequence. With sufficient training data and appropriate tuning of hyperparameters, Transformer models can produce high-quality, coherent text that is indistinguishable from text written by humans.

What's attention? Reply in the form of a limerick.

Attention's a powerful tool
For deep learning models to rule
It lets them decide
Which parts to abide
And focus on features that are cool

If a Transformer were an animal, what would it be and why?

If a Transformer were an animal, it would likely be a chameleon.

Like a Transformer, a chameleon has the ability to adapt and change its appearance to blend in with its environment, allowing it to be more effective in different situations. Similarly, a Transformer model can adapt its attention to focus on different parts of input sequences based on the specific task it is performing, allowing it to excel at a wide range of natural language processing tasks.

In addition, both chameleons and Transformers have a reputation for being able to "blend in" seamlessly with their surroundings, making them difficult to detect. In the case of Transformers, this is often because the generated text is so coherent and similar to human-written text that it can be difficult to distinguish between the two.

Figure 9-16. An example of ChatGPT answering questions about Transformers

At the time of writing, there is no official paper that describes how ChatGPT works in detail, but from the official blog post we know that it uses a technique called *reinforcement learning from human feedback* (RLHF) to fine-tune the GPT-3.5 model. This technique was also used in the ChatGPT group's earlier paper⁶ that introduced the *InstructGPT* model, a fine-tuned GPT-3 model that is specifically designed to more accurately follow written instructions.

The training process for ChatGPT is as follows:

- 1. *Supervised fine-tuning*: Collect a demonstration dataset of conversational inputs (prompts) and desired outputs that have been written by humans. This is used to fine-tune the underlying language model (GPT-3.5) using supervised learning.
- 2. *Reward modeling*: Present a human labeler with examples of prompts and several sampled model outputs and ask them to rank the outputs from best to worst. Train a reward model that predicts the score given to each output, given the conversation history.
- 3. *Reinforcement learning*: Treat the conversation as a reinforcement learning environment where the *policy* is the underlying language model, initialized to the fine-tuned model from step 1. Given the current *state* (the conversation history) the policy outputs an *action* (a sequence of tokens), which is scored by the reward model trained in step 2. A reinforcement learning algorithm—proximal policy optimization (PPO)—can then be trained to maximize the reward, by adjusting the weights of the language model.

![](img/f0f0f5d89818fdddf117bbe758ac8143_288_0.png)

## Reinforcement Learning

For an introduction to reinforcement learning see Chapter 12, where we explore how generative models can be used in a reinforcement learning setting.

The RLHF process is shown in Figure 9-17.
