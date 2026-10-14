The rapid rise of powerful Transformers for text generation and state-of-the-art diffusion models for image generation has meant that much of the focus of the last two years of generative AI development has been on multimodal models—that is, models that operate over more than one domain (for example, text-to-image models).

This trend was established in 2021 when OpenAI released DALL.E, a text-to-image model based upon a discrete VAE (similar to VQ-VAE) and CLIP (a Transformer model that predicts image/text pairs). This was followed by GLIDE (2021) and DALL.E 2 (2022), which updated the generative part of the model to use a diffusion model rather than a discrete VAE, with truly impressive results. This era also saw the release of three text-to-image models from Google: Imagen (2022, using Transformer and diffusion models), Parti (2022, using Transformers and a ViT-VQGAN model), and later MUSE (2023, using Transformers and VQ-GANs). DeepMind also released Flamingo (2022), a visual language model that builds upon their large language model Chinchilla by allowing images to be used as part of the prompt data.

Another important diffusion advancement introduced in 2021 was latent diffusion, where a diffusion model is trained within the latent space of an autoencoder. This technique powers the Stable Diffusion model, released as a joint collaboration between Stability AI, CompVis, and Runway in 2022. Unlike with DALL.E 2, Imagen, and Flamingo, the code and model weights of Stable Diffusion are open source, meaning anyone can run the model on their own hardware.

# The Current State of Generative AI

As we come to end of our journey through the history of generative AI, it is important to now reflect on where we stand in terms of current state-of-the-art applications and models. Let’s take a moment to assess our progress and key accomplishments in the field to date.

# Large Language Models

Generative AI for text is now almost entirely focused on building large language models (LLMs), whose sole purpose is to directly model language from a huge corpus of text—that is, they are trained to predict the next word, in the style of a decoder Transformer.

The large language model approach has been adopted so widely because of its flexibility and ability to excel at a wide range of tasks. The same model can be used for question answering, text summarization, content creation, and many other examples because ultimately each use case can be framed as a text-to-text problem, where the specific task instructions (the prompt) are given as part of the input to the model.

Let’s take GPT-3 as an example. Figure 14-2 shows how the same model can be used for text summarization and content creation.