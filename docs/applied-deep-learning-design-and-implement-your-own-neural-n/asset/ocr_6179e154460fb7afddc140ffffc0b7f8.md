Stage-II generator along with the text description, which helps to generate high-resolution images with fine details, and sharp colors looking more realistic.

Table 8.8 shows the inputs, outputs, and aims of generator and discriminator networks in stack-GAN:

| Stack GAN | Input | Output | Aim |
|---|---|---|---|
| Generator Stage-I | Noise Vector (z) and Text description | Low-resolution images | To generate realistic images |
| Generator Stage-II | Low-resolution output from Stage-I and Text Description | High-resolution images | To generate realistic images |
| Discriminator (DI) | Real and generated samples of Stage-I | Probability score to identifying real or fake samples of stage-I | Correctly identify between real or fake sample of Stage-I |
| Discriminator (DII) | Real and generated samples of Stage-II | Probability score to identifying real or fake samples of Stage-II | Correctly identify between real or fake sample of Stage-II |

Table 8.8: Inputs, outputs, and aims of generator and discriminator networks in stack-GAN

Since the invention of the original GAN by Ian Goodfellow, the area of generative adversarial networks has remained an active area of research. GAN has shown scope in many different areas ranging from medical images, audio, video, image synthesis, 3-D imaging, and so on. So, lots of research is going on in this area, and a large number of GANs variants have been suggested by various researchers in different areas over the years. While writing this chapter, more than 400 GAN variants exist right now. It is clear from the increasing GAN count that it is not at all possible to cover all those GANs here. So, we have discussed only some of the important GANs with their contributions to the field. The list is very long; still, we have listed some variants in table 8.9, suggested over the years in different fields.

# Applications of GAN

In this section, a large number of different interesting GAN applications have been highlighted to give an idea of the type of problems in which GAN is gaining success. Some of these are to generate photographs of human faces and cartoon characters, text-to-image translation, image-to-image translation, semantic-image-to-photo translation, photos-to-emojis, face aging, photo blending, photograph editing, super-resolution, clothing translation, photo in-painting, 3Dobject generation, video prediction, and many more. Refer to table 8.9 to get an idea of the various available GANs across different fields: