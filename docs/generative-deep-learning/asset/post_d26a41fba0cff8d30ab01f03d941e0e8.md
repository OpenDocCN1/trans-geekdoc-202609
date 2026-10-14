
## Text-to-Image Models

State-of-the-art image generation is currently dominated by large multimodal models that convert a given text prompt into an image. Text-to-image models are highly useful as they allow users to easily manipulate generated images via natural language. This is in contrast to models such as StyleGAN, which, while extremely impressive, does not have a text interface through which you can describe the image that you want to be generated.

Three important text-to-image generation models that are currently available for commercial and personal use are DALL.E 2, Midjourney, and Stable Diffusion.

DALL.E 2 by OpenAI is a pay-as-you-go service that is available through a web application and API. Midjourney provides a subscription-based text-to-image service through its Discord channel. Both DALL.E 2 and Midjourney offer free credits to those joining the platform for early experimentation.

![](img/f0f0f5d89818fdddf117bbe758ac8143_428_0.png)

### Midjourney

Midjourney is the service used to create the illustrations for the stories in Part II of this book!

Stable Diffusion is different because it is fully open source. The model weights and code to train the model are available on GitHub, so anyone can run the model on their own hardware. The dataset used to train Stable Diffusion is also open source. This dataset, called LAION-5B, contains 5.85 billion image-text pairs and is currently the largest openly accessible image-text dataset in the world.

An important corollary of this approach is that the baseline Stable Diffusion model can be built upon and adapted to different use cases. An excellent demonstration of this is ControlNet, a neural network structure that allows fine-grained control of the output from Stable Diffusion by adding extra conditions. For example, output images can be conditioned on a Canny edge map of a given input image, as shown in Figure 14-6.

![](img/f0f0f5d89818fdddf117bbe758ac8143_429_0.png)

Figure 14-6. Conditioning the output of Stable Diffusion using a Canny edge map and ControlNet (source: Lvmin Zhang, ControlNet)

ControlNet contains a trainable copy of the Stable Diffusion encoder, alongside a locked copy of the full Stable Diffusion model. The job of this trainable encoder is to learn how to handle the input condition (e.g., the Canny edge map), whilst the locked copy retains the power of the original model. This way, Stable Diffusion can be fine-tuned using only a small number of image pairs. Zero convolutions are simply 1 × 1 convolutions where all weights and biases are zero, so that before training, ControlNet does not have any effect.

![](img/f0f0f5d89818fdddf117bbe758ac8143_430_0.png)

Figure 14-7. The ControlNet architecture, with the trainable copies of the Stable Diffusion encoder blocks highlighted in blue (source: Lvmin Zhang, ControlNet)

Another advantage of Stable Diffusion is that it is able to run on a single modestly sized GPU with only 8 GB of VRAM, making it possible to run on edge devices, rather than through calls to a cloud service. As text-to-image services are included in downstream products, the speed of generation is becoming increasingly more important. This is one reason why the size of multimodal models is generally trending downward (see Figure 14-3).

Example outputs for all three models can be seen in Figure 14-8. All of these models are exceptional and are able to capture the content and style of the given description.

A unicorn leaping over a magnificent river, beautiful oil painting, stunning natural scenery, award-winning art, golden lighting, intricate detail

![](img/f0f0f5d89818fdddf117bbe758ac8143_431_0.png)

![](img/f0f0f5d89818fdddf117bbe758ac8143_431_1.png)

![](img/f0f0f5d89818fdddf117bbe758ac8143_431_2.png)

Figure 14-8. Outputs from Stable Diffusion v2.1, Midjourney, and DALL.E 2 for the same prompt

A summary of some of the most powerful text-to-image models in existence today is shown in Table 14-2.

Table 14-2. Text-to-image models

| Model | Date | Developer | # parameters | Open source |
|---|---|---|---|---|
| DALL.E 2 | Apr 2022 | OpenAI | 3,500,000,000 | No |
| Imagen | May 2022 | Google | 4,600,000,000 | No |
| Parti | Jun 2022 | Google | 20,000,000,000 | No |
| Stable Diffusion | Aug 2022 | Stability AI, CompVis, and Runway | 890,000,000 | Yes |
| MUSE | Jan 2023 | Google | 3,000,000,000 | No |

Part of the skill of working with text-to-image models is creating a prompt that both describes the content of the image you want to generate and uses keywords that encourage the model to produce a particular style or type of image. For example, adjectives such as stunning or award-winning can often be used to improve the quality of the generation. However, it is not always the case that the same prompt will work well across different models—it depends on the contents of the specific text-image dataset used to train the model. The art of uncovering prompts that work well for a particular model is known as prompt engineering.

## Other Applications

Generative AI is rapidly finding applications across a variety of novel domains, from reinforcement learning to other kinds of text-to-X multimodal models.

For example, in November 2022 Meta published a paper on *CICERO*, an AI agent trained to play the board game *Diplomacy*. In this game, players represent different countries in Europe before World War I and must negotiate with and deceive each other in order to gain control of the continent. It is a highly complex game for an AI agent to master, not least because there is a communicative element where players must discuss their plans with other players in order to gain allies, coordinate maneuvers, and suggest strategic goals. To achieve this, CICERO contains a language model that is able to initiate dialogue and respond to messages from other players. Crucially, the dialogue is consistent with the agent’s strategic plans, which are generated by another part of the model to adapt to the constantly evolving scenario. This includes the ability for the agent to bluff when conversing with other players—that is, convince another player to co-operate with the agent’s plans, only to then enact an aggressive maneuver against the player in a later turn. Remarkably, in an anonymous online *Diplomacy* league featuring 40 games, CICERO’s score was more than double the average of the human players and it ranked in the top 10% of participants who played multiple games. This is an excellent example of how generative AI can be successfully blended with reinforcement learning.

The development of embodied large language models is an exciting area of research, further exemplified by Google’s *PaLM-E*. This model combines the powerful language model PaLM with a Vision Transformer to convert visual and sensor data into tokens that can be interleaved with text instructions, allowing robots to execute tasks based on text prompts and continuous feedback from other sensory modalities. The PaLM-E website showcases the model’s abilities, including controlling a robot to arrange blocks and fetch objects based on text descriptions.

*Text-to-video* models involve the creation of videos from text input. This field, which builds on the concept of text-to-image modeling, has the additional challenge of incorporating a time dimension. For example, in September 2022 Meta published *Make-A-Video*, a generative model that is able to create a short video given only a text prompt as input. The model is also able to add motion between two static images and produce variations of a given input video. Interestingly, it is trained only on paired text-image data and unsupervised video footage, rather than text-video pairs directly. The unsupervised video data is enough for the model to learn how the world moves; it then uses the text–image pairs to learn how to map between text image modalities, which are then animated. The *Dreamix model* is able to perform video editing, where an input video is transformed based on a given text prompt while retaining other stylistic attributes. For example, a video of a glass of milk being poured could be converted to a cup of coffee being poured, while retaining the camera angle, background, and lighting elements of the original video.
