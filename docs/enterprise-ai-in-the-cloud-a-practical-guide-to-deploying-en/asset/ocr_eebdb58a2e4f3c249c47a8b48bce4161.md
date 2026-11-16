# TABLE 24.5: Differences Between GANs, VAEs, and Diffusion Models

| GENERATIVE GANS MODEL | VAES | DIFFUSION MODELS |
|---|---|---|
| **Working Principle** | Two neural networks competing in a zero-sum game to generate new data that closely resembles the training dataset | A type of neural network that learns to encode and decode data by mapping it to a latent space | Adding noise to the original image and then removing the noise gradually to create a range of new images depending on the noise with which the recovery process started |
| **Applications** | • Image to image translation<br>• Scenes and people<br>• Realistic human faces<br>• Artwork<br>• Photorealistic photos of objects | • Image and video generation<br>• Data compression<br>• Anomaly detection | • Text-to-image<br>• Text-to-video<br>• Text-to-3D<br>• Text-to-tasks |
| **Examples** | • StyleGAN<br>• BigGAN | • Beta-VAE<br>• VQ-VAE | • DALL-E<br>• CLIP |

DALL-E and CLIP are two diffusion-type models from OpenAI. DALL-E can generate images from text descriptions, while CLIP can understand both text and images and can relate them to each other. For example, you can ask DALL-E to create an orange in the form of an apple, and DALL-E will precisely do that to create a novel image that was never seen before.

Diffusion models are not without their challenges because they can be very computationally intensive and slower than GANs. Despite their challenges, diffusion models are fascinating and extend the limits of virtual reality and what's possible with Gen AI.

# IMPLEMENTING GENERATIVE AI AND ChatGPT

Given its many risks, implementing generative AI and ChatGPT for your company is not a trivial task. Moreover, it is a constantly evolving space; you must keep close tabs on what's happening out there. Having said that, consider the different options you have when implementing generative AI or ChatGPT. Your options will span between buying off-the-shelf solutions and building them on your own. Figure 24.9 shows the different options laid out in front of you.

# From Packaged Software to Pretraining Models

Consider these build versus buy options that are available when implementing generative AI:

+   - **Out-of-the-box options:** You already use the out-of-the-box option when you use ChatGPT for various natural language processing tasks such as summarizing, answering questions, translation, and so on. The issue with that approach is that you need to figure out how your data is going to be leveraged by those companies.
+   - **Consuming APIs:** When you use APIs, cost is a critical factor because you are charged based on the tokens, you use both as a query to the API and the response you get back. It is therefore important to exercise controls over the amount of data input to the API as well as the amount of data generated from the API.
+   - **Prompt engineering:** The other option is prompt engineering, which has been gaining much attention lately. We are already seeing innovations in this space in the form of new models such as