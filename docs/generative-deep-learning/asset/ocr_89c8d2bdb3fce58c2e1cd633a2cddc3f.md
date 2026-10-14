While ChatGPT still has many limitations (such as sometimes “hallucinating” factually incorrect information), it is a powerful example of how Transformers can be used to build generative models that can produce complex, long-ranging, and novel output that is often indistinguishable from human-generated text. The progress made thus far by models like ChatGPT serves as a testament to the potential of AI and its transformative impact on the world.

Moreover, it is evident that AI-driven communication and interaction will continue to rapidly evolve in the future. Projects like Visual ChatGPT7 are now combining the linguistic power of ChatGPT with visual foundation models such as Stable Diffusion, enabling users to interact with ChatGPT not only through text, but also images. The fusion of linguistic and visual capabilities in projects like Visual ChatGPT and GPT-4 have the potential to herald a new era in human–computer interaction.

# Summary

In this chapter, we explored the Transformer model architecture and built a version of GPT—a model for state-of-the-art text generation.

GPT makes use of a mechanism known as attention, which removes the need for recurrent layers (e.g., LSTMs). It works like an information retrieval system, utilizing queries, keys, and values to decide how much information it wants to extract from each input token.

Attention heads can be grouped together to form what is known as a multihead attention layer. These are then wrapped up inside a Transformer block, which includes layer normalization and skip connections around the attention layer. Transformer blocks can be stacked to create very deep neural networks.

Causal masking is used to ensure that GPT cannot leak information from downstream tokens into the current prediction. Also, a technique known as positional encoding is used to ensure that the ordering of the input sequence is not lost, but instead is baked into the input alongside the traditional word embedding.

When analyzing the output from GPT, we saw it was possible not only to generate new text passages, but also to interrogate the attention layer of the network to understand where in the sentence it is looking to gather information to improve its prediction. GPT can access information at a distance without loss of signal, because the attention scores are calculated in parallel and do not rely on a hidden state that is carried through the network sequentially, as is the case with recurrent neural networks.

We saw how there are three families of Transformers (encoder, decoder, and encoder-decoder) and the different tasks that can be accomplished with each. Finally, we explored the structure and training process of other large language models such as Google’s T5 and OpenAI’s ChatGPT.