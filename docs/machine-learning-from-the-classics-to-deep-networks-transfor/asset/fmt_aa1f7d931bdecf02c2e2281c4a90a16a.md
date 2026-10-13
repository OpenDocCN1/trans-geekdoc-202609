
## 5. Exercise 19.9

**(e)** During training and every 20 epochs, visualize the generated images created by the generator and comment on the evolution of the learning process.

**(f)** Play with all the various parameters that have been suggested above and see the effect on the training.

## 3. Exercise 19.10

This exercise helps to familiarize with transformer architectures and explore the impact of positional encoding. The focus is on the language translation NLP task, and more specifically on German-to-English translation, following the PyTorch tutorial: <https://pytorch.org/tutorials/beginner/translation_transformer.html>.

In the tutorial, the setup of the data sets, the transformer and the training procedure are described in detail. A simple qualitative evaluation is provided at the end by translating the German sentence “Eine Gruppe von Menschen steht vor einem Iglu,” which in English means “A group of people stands in front of an igloo.”

### 1. (a)

Experiment with various transformer hyperparameters, namely:

*   **`EMB_SIZE`** (dimensionality of the embedding space, $d_m$). Start with `EMB_SIZE=512`.
*   **`NHEAD`** (number of heads). Start with `NHEAD=8`.
*   **`FFN_HID_DIM`** (hidden layer dimensionality of the two-layer FCN module). Start with `FFN_HID_DIM=512`.
*   **`NUM_ENCODER_LAYERS`** (number of encoder blocks). Start with `NUM_ENCODER_LAYERS=3`.
*   **`NUM_DECODER_LAYERS`** (number of decoder blocks). Start with `NUM_DECODER_LAYERS=3`.

How much one can compress the architecture (i.e., reduce the aforementioned values) without sacrificing performance?

### 2. (b)

Tweak the `PositionalEncoding` class in order to remove the effect of the positional encoding. You can add an argument that controls whether positional encoding is added to the token embedding or not. Specifically, you can modify the `PositionalEncoding` class to have an extra argument `use_pos_encoding`.

### 3. Note

Note that dropout of this `PositionalEncoding` layer may affect performance, so for this experiment set the dropout value to zero. Note that this `Seq2SeqTransformer` definition has a dropout argument, where you can set `dropout=0`. Evaluate the performance of the transformer without positional embedding on the previous German sentence. Comment on the obtained results with respect to the functionality of positional encoding.

## 5. Exercise 19.11

This exercise serves as an introduction to self-supervised methods, focusing on implementing SimCLR, Section 19.6.5, on the MNIST data set. SimCLR applies contrastive learning during pretraining, while it involves various implementation details and hyperparameters that affect downstream performance during fine-tuning.

### 1. (a) Implementation details

*   **Augmentations**: Create a dataloader providing two augmented versions for each image. Use the following sequence of transformations: `RandomHorizontalFlip()`, `RandomResizedCrop(size=28, scale=(0.2, 1.))`, `ToTensor()`, `Normalize((0.5,), (0.5,))`.
*   **Encoder**: Design a sequence of three convolutional layers with output channels: 32, 64, and 128 respectively. Use `kernel size` 3, `stride` 1, and `padding` 1. Apply batch normalization, ReLU activation, and max pooling after each convolutional layer. Use `kernel size` 2 and `stride` 2 for `max pooling`, with `padding` 1 for the last operation.
*   **Projector**: A projector head should be applied on the output of the encoder. Use a linear layer that maps the output dimension of the encoder to an 128-dimensional feature space.

### 2. (b) Pretrain

Implement the InfoNCE loss function by using the cross-entropy loss function from PyTorch. Think of InfoNCE as a binary cross entropy loss over the feature similarities. Train the encoder and its projection head for 100 epochs with a temperature of 0.07 and a batch size of 64. Use the Adam optimizer with a `learning rate` of 0.003 and `weight decay` of 0.003.

### 3. (c) Downstream performance

In order to evaluate your network, use your encoder (not the projector) to extract for all train and test images the corresponding feature vectors. Use these vectors as a new data set and train three different classifiers: (i) a linear layer, (ii) logistic regression, and (iii) a $k$-NN to evaluate downstream performance.

### 4. (d) Role of the batch size

Try different batch sizes for the pretraining stage. How does the performance change as the batch sizes grow larger? Comment on the results.

### 5. (e) Role of the temperature

Pretrain with different `temperature values`, namely 0.07, 0.2, 0.5, and 1. How does temperature affect downstream performance?

### 6. (f) Role of the projection head

A projector head should be applied at the output of the encoder. Use a linear layer that maps the output dimension of the encoder to an 128-dimensional feature space. $\ell_2$ normalization should be applied on the output features. Investigate the impact on downstream performance of pretraining (i) without the projection head and (ii) using a two-layer MLP with one ReLU activation as the projector. Assess the importance of the projector.

### 7. (g) Role of the number of epochs

Explore the impact of extending pretraining duration (e.g., 200, 300, 400 epochs) on downstream performance metrics.

## 6. Exercise 19.12

The focus of this exercise is on diffusion models, using DDPMs based on the `Diffusers` package from `HuggingFace`, which is written in PyTorch. The source code is here: <https://github.com/huggingface/diffusers>. The exercise comprises the following steps:

### 1. (a)

Load a pretrained Stable Diffusion model from the `HuggingFace` model hub, namely `Stable Diffusion v2`. In PyTorch, this can be done by using the `stable-diffusion-2` pretrained model from the `StableDiffusionPipeline` module of the `diffusers` package.

### 2. (b)

Remove few self-attention and cross-attention layers, and generate images after each modification to analyze their impact on image coherence and relevance. This can be done by applying the function `param.fill_(0)` to the parameters of any attention layer of the U-Net backbone.

### 3. (c)

Vary the number of diffusion steps (e.g., reducing by half, doubling) and observe changes in image quality and generation time. Use the DPM-Solver++ scheduler (`DPMSolverMultistepScheduler` module of the `diffusers` package).

### 4. (d)

In working with classifier-free guidance, examine how the model performs when we tune the model toward stronger or weaker prompt-conditioning. Tune the `guidance_scale` model's parameter; `guidance_scale = 1` corresponds to no guidance.

### 5. (e)

Modify the noise schedule used in the diffusion process. Evaluate its impact on the smoothness and realism of the generated images. Tune the `DPMSolverMultistepScheduler` module's parameters `beta_start` and `beta_end`, which are the starting and final beta value of inference, and define `beta_schedule` either as linear or `scaled_linear`.

## References
