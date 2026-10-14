
A sort of neural network in which two models com-pete against after other. The generator and discrimi-nator are two neural networks that compete against each other to generate and identify real and fake data. The two models interact with each other, and the generator improves over time at producing data that is accurate.

### b Variational autoencoders (VAEs)

VAEs are a type of neural network that can compress data into a smaller, hidden space, and then decompress it back to the original data. The latent space is a space with fewer dimensions that captures the data’s basic characteristics. After learning to represent data in the space known as the latent space, the VAE can be used to produce new data by sampling points from the latent space and decoding these again into the data that was originally collected space.

### c Recurrent neural networks (RNNs)

RNNs are a type of neural network system that is capable of processing sequential data. As a result, they are well-suited for generating text, music, and other sorts of data with a periodic order.

The various approaches needed to build a GAI system will vary depending on the application. GANs, for instance, are frequently used to produce images, but VAEs are frequently used to generate text. The following are some of the steps involved in developing a GAI system:

1.  **Data collection:** The initial step involves gathering an extensive array of data pertinent to the intended application. For instance, if the goal is to create cat photographs, the initial task entails amassing a dataset comprising images of cats.

2.  **Dataset pre-processing**: Before the data can be employed for model training, it might necessitate pre-processing. This step could encompass tasks such as data cleansing, noise reduction, and normalization.

3.  **Algorithm choice:** Multiple models exist for constructing a GAI system. The selection of an appropriate model hinges on the specific application and the quantity of available data.

4.  **Model training:** The algorithm is subjected to a training process using a dataset. The duration of this process can vary based on the dataset’s size and the desired precision of the model, sometimes spanning a considerable timeframe.

5.  **Generate fresh data:** Following the completion of model training, it becomes feasible to employ the model for generating novel data. The approach employed in this process is contingent on the specific framework being used and dictates the manner in which the new data is crafted.

While GAI systems are currently in their nascent stages of research, they hold immense potential to revolutionize various industries we may anticipate seeing more cutting-edge and significant uses of GAI in the upcoming years thanks to the ongoing development of this technology ([Singh et al., 2019](#ch9.xhtml#ref9_11); Jovanović et al., 2022; [Samant et al., 2022](#ch9.xhtml#ref9_3))。

## II. Evolution of GAI

The advent of GAI signifies resulted in substantial advances in ML and AI. In the following sections, a timeline of how generative AI has progressed is discussed.

### a Beginning principles (1950–1990s)

During the early years of AI research, the underlying principles of GAI were established. In domains such as natural language processing and music creation, researchers investigated rule-based systems and symbolic representations to generate content.

### b The rebirth of neural networks in the 2000s

The “deep learning revolution,” or the resurrection of artificial neural networks, was critical in the creation of generative artificial intelligence. Neural networks with deep learning revealed the ability to learn data hierarchies, allowing for the development of higherlevel and more intricate outputs (Davies et al., 2021).

### c Variational autoencoders (VAEs) (2013)

VAEs pioneered a probabilistic approach to generative modeling. To construct a latent space representation of data, they incorporated aspects from both generative and recognition models. VAEs enabled seamless interpolation and manipulation of latent space data points.

### d Generative adversarial networks (GANs) (2014)

GANs, suggested by Ian Goodfellow and colleagues, represented a significant development in generative AI. GANs are made up of the discriminator and generator, two distinct neural networks that compete with one another in a manner akin to a game. While the discriminator seeks to distinguish between genuine and produced data, the generation process aims to provide data that is as realistic as possible.

### e Visualizing the future era (2014–current)

During this period, GAN gained prominence due to their ability to create high-resolution images that closely resemble authentic photographs. Renowned GAN architectures like deep convolutional GAN (DCGAN), StyleGAN, and BigGAN elevated the caliber and diversity of the generated images to new heights ([Guo et al., 2022](#ch9.xhtml#ref9_6)).

### f Text and language making (2015–current)

Progress in the realm of natural language process-ing and deep learning has yielded the creation of text and language generative frameworks. Innovations like long- short- term memory (LSTM) networks and transformers have empowered the generation of logically connected and contextually fitting textual content (Sathish et al., 2023).

### g Music and audio production (2016–current)

Generative algorithms have been used to compose music and synthesize audio. Melodies, harmonies, and even full music recordings have been generated using recurrent neural networks along with different sequence-to-sequence algorithms. WaveGAN and other approaches have also showed promise in producing realistic signals for audio.

### h Applications in healthcare and science (2010–current)

GAI has been used in healthcare since 2010s for a variety of purposes, including image interpretation, drug development, and personalized medicine. GANs and VAEs have found use in creating artificial medical images to improve diagnostic accuracy and expand small datasets ([Figure 9.1](#ch9.xhtml#fig9_1)) (Rebecca [Perkins et al., 2022](#ch9.xhtml#ref9_7)).

![Figure 9.1 Overview of GAI](images/fig9_1_C.jpg)

[Figure 9.1 Overview of GAI](#ch9.xhtml#R_fig9_1)

### i Concerns about ethics and racism (2010–current)

Concerns regarding ethical issues and biases arose as AI that generates gained prominence. The potential for AI-generated content to propagate disinformation, produce offensive content, or reproduce biases existing in training data sparked debate over ethical implementation and mitigating techniques.

### j Ongoing exploration and advancement (current and beyond)

Researchers are working on ways to improve the quality of generated content by making it more realistic, diverse, and controllable. Hybrid models that combine different GAI techniques are being developed to improve the performance of models. Creative applications of GAI are being explored in areas such as art, music, and video games. Interdisciplinary collaborations between researchers from different fields are helping to advance the state of GAI research.

Advances in deep learning architectures, computational power, and the availability of massive datasets have driven the development of GAI. As technological advancements continue, AI with generative capabilities has the potential to impact a wide range of persistence, from entertainment and art to healthcare and scientific research in this system ([Cai et al., 2019](#ch9.xhtml#ref9_9)).

## III. Construction

Designing and training a neural network architecture to produce data that corresponds to the dataset being studied is the first step in building a generative AI system. In the following sections, the stages below outline the general technique for developing a generative artificial intelligence system.

### a Select a generative approach
