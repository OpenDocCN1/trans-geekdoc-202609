# 2014–2017: The VAE and GAN Era

The invention of the VAE in December 2013 can perhaps be thought of as the spark that lit the generative AI touchpaper. This paper showed how it was possible to generate not only simple images such as MNIST digits but also more complex images such as faces in a latent space that could be smoothly traversed. It was followed in 2014 by the introduction of the GAN, an entirely new adversarial framework for tackling generative modeling problems.

The following three years were dominated by progressively more impressive extensions of the GAN portfolio. In addition to fundamental changes to the GAN model architecture (DCGAN, 2015), loss function (Wasserstein GAN, 2017), and training process (ProGAN, 2017), new domains were tackled using GANs, such as image-to-image translation (pix2pix, 2016, and CycleGAN, 2017) and music generation (MuseGAN, 2017).

During this era, important VAE improvements were also introduced, such as VAE-GAN (2015) and later VQ-VAE (2017), and applications to reinforcement learning were seen in the “World Models” paper (2018).

Established autoregressive models such as LSTMs and GRUs remained the dominant force in text generation over this time. The same autoregressive ideas were also being used to generate images, with PixelRNN (2016) and PixelCNN (2016) introduced as new ways to think about image generation. Other approaches to image generation were also being tested, such as the RealNVP model (2016) that paved the way for later types of normalizing flow models.

In June 2017, a groundbreaking paper entitled “Attention Is All You Need” was published that would usher in the next era of generative AI, focused around Transformers.

# 2018–2019: The Transformer Era

At the heart of a Transformer is the attention mechanism that negates the need for the recurrent layers present in older autoregressive models such as LSTMs. The Transformer quickly rose to prominence with the introduction of GPT (a decoder-only Transformer) and BERT (an encoder-only Transformer) in 2018. The following year saw progressively larger language models being built that excelled at a wide range of tasks by treating them as pure text-to-text generation problems, with GPT-2 (2018, 1.5B parameters) and T5 (2019, 11B parameters) being standout examples.

Transformers were also starting to be successfully applied to music generation, with the introduction of, for example, the Music Transformer (2018) and MuseNet (2019) models.