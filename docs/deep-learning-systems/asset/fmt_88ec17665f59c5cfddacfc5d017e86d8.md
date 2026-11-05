
## Image Generation

The task of image generation requires modeling the distribution of images for a relative domain, such as written digits (the ultimate aspiration is modeling the distribution of all the natural images). Image generation is primarily an unsupervised learning task used in academia with some industry adoption for image deblurring, compression, and completion. The main types of algorithms used for image generation include auto-regressive and GAN models, specifically, `PixelRNN`, `PixelCNN`, `DCGAN`, `3D GAN`, `StackedGAN`, `StarGAN`, `SyleGAN`, and `Pix2pix`.

![image](images/fig3_17.png)

Figure 3.17: A `3D-GAN` generator takes a random vector `z` and generates a 3D image. Based on \[WZX+16\].

`PixelRNN` and `PixelCNN` are auto-regressive models that predict the pixels along both axes using recurrent and convolutional layers, respectively. These models generate a conditional distribution over the 256 possible values for each RGB image channel at each pixel location \[vKK+16\].

`DCGAN` and `3D GAN` combine `CNNs` and `GANs` to generate 3D objects, as shown in [Figure 3.17](#13_Chapter03.xhtml#fig3-17) \[RMC15, WZX+16\]. These GANs learn to generate high-quality objects by sampling from a low-dimensional space and passing those samples to the generator. `Stacked GANs` trains across multiple stacks of GANs, which results in higher quality image generation \[HLP+17\].

`StarGAN` and `StyleGAN` generate photorealistic images. For instance, they can generate human faces adjusting latent factors, such as freckles, hair color, gender, eyeglasses, and facial shape, when trained on a face dataset \[CCK+17, KLA19\].

`Pix2pix` is an adversarial network that learns a mapping from an input image to an output image and also learns a cost function to train this mapping. It can generate realistic images from labeled maps, colorize gray images, fill gaps in images, remove image backgrounds, and generate images from sketches \[IZZ+16\].

Other computer vision topologies that have been influential in the field, but do not currently have extensive commercial adoption are `FaceNet` for face recognition and verification, `SqueezeNet` and `ShuffleNet` for image classification on edge devices, `SENet` for high accuracy image classification, `SRGAN` for image super-resolution, and `SqueezeSegV2` for road-object segmentation from LiDAR point cloud \[SKP15, HSW+18, IHM+16, ZZL+17, HSA+19, LTH+16, WZZ+19\]. `OpenPose` is used for pose estimation and has some adoption; Wrnch.AI uses a modified proprietary model to detect kinematics from 2D video.

## 3.3 NATURAL LANGUAGE PROCESSING TOPOLOGIES

NLP has been considered an AI-complete problem (requiring human-level intelligence to solve) given the complexity required to understand language. NLP is a required step toward automatic reasoning, that is, using stored knowledge to generate additional knowledge \[Yam12\]. Academia and industry have made tremendous progress in recent years.

Traditional NLP systems often use a hidden Markov model (`HMM`) (do not worry if you are not familiar with `HMM`). An `HMM` requires language experts to encode grammatical and semantic rules, provide a detailed ontology, parse the data, tag words with the appropriate part-of-speech, and iteratively align inputs and outputs. Neural NLP models can learn a particular task using a lexicon or language vocabulary and a massive data corpus and without explicitly programming the language rules. A popular benchmark to assess the performance of NLP models is the General Language Understanding Evaluation (`GLUE`) benchmark \[SMH+18\].

Hyperscalers use NLP algorithms for NLU, speech recognition, speech generation, and speech-to-speech translation tasks. NLU tasks include language translation, sentiment analysis, automatic document summarization, image captioning, document clustering, and question & answering. Speech recognition and speech synthesis are used as part of an NLP system by AI assistants, such as Apple Siri, Amazon Alexa, Google Assistant, Microsoft Cortana, and Baidu DuerOS. Speech-to-speech translation is used to interpret speech between different languages either as three separate stages (speech-to-text, text translation, and text-to-speech) or as a combined model. NLP algorithms facilitate human-machine interactions, enhancing a machine’s ability to understand human language, and improve human-human communication, enabling communication between people without a common language.

### 3.3.1 NATURAL LANGUAGE UNDERSTANDING

NLU deals with machine reading comprehension. Neural machine translation (`NMT`) is the NLU task of mapping written text from a source to a target language using a `NN`. `NMT` topologies and techniques are also used for other NLU tasks with minor to no adaptations, such as sentiment analysis to categorize the sentiment of written product reviews, for question & answering systems, for document summarization, and for image captioning to “translate” a vector representation of the image into a description or caption.

Neural NLU models can be `RNN`-based, `CNN`-based, and transformer-based. They consist of an encoder that takes the source sentence and a decoder that outputs the target sentence. The decoder’s task is to predict the next output word (or subword) given the previous outputs and the inputs. During the decode stage, a target output word can be greedily chosen from the `softmax` output or using a *beam search* approach as follows: The top `n` candidate words from the `M` `softmax` outputs at time `t` are selected and used as inputs into the next timestep. This results in `nM` output candidates at `t` + 1. The top `n` are selected from this `nM` group, and the process iteratively repeats in each subsequent timestep. At the last timestep, one output is selected from the `nM` choices. A common choice is `n` = 10 to provide a compromise between speed and accuracy. [Figure 3.18](#13_Chapter03.xhtml#fig3-18) depicts a beam search of `n` = 2.

![image](images/fig3_18.png)

Figure 3.18: Beam search using a beam size of 2. Except for the initial decoder input at decoding timestep 0, every timestep uses the 2 most probable outputs (underlined) from the previous timesteps as inputs. At time `t` = 4, beam search results in the sentences: “I am playing the piano with …” and “I am playing the piano ‹eos› …,” where `‹eos›` is the end of sentence token.

The quality of the target sentence in machine translation is typically reported using the `BLEU` score, a measure of similarity between the machine’s translation and a professional human translation normalized by the sequence length. Other quality metrics have been proposed \[NDC+17\].

One implementation challenge during training is the variable sequence length. Using a constant sequence length to batch the sequences and either pad short sequences or truncate long sequences to the predetermined length so that each sample in a batch is of the same length mitigates this challenge.

The inputs to the `NN` are known as tokens. While earlier NLU topologies used words as tokens, most newer topologies use learned subwords \[SHB15\]. An algorithm segments words constrained to a fixed vocabulary size (the maximum number of subwords). These subwords are often interpretable, and the model can generalize to new words not seen during training using these subwords. Subwords are crucial for low-resource languages, that is, languages where the data corpus is small. The downside of using subwords rather than words is that a sequence has more tokens, which requires more computations.
