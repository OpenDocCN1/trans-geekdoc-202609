max V(D) = E_{X~P_data(x)}[log D(x)] + E_{z~P_z(z)}[log(1 - D(G(z)))]
D
(6.3)

To keep the GAN-MLC stable while training, many techniques are used, including replacing deterministic spatial pooling function layers and using strided convolution layers in the discriminator to make it learn the spatial downsampling function while training. Also in the generator, fractional-strided convolution layers are used to enable learning on the upsampling function. Batch normalization is used for the input to all intermediate layers to have zero means and unit variance, except for the last layer of the generator and the input layer of the discriminator.

# ALGORITHM 1: GAN-MLC TRAINING PROCESS

+   1. for each iteration do
+   2. Generator draw M noise samples {(z^1, y_g), ..., (z^M, y_g)} from noise prior p_g(z), where y_g = [0, ..., 0_classes];
+   3. Draw m examples {(x^1, y^1), ..., (x^m, y^m)} from data generating distribution P_d(x);
+   4. Perform gradient descent on the parameters of D with regard to the negative likelihood of D on minibatch;
+   5. Generator draw M noise samples {(z^1, y_g), ..., (z^M, y_g)} from noise prior p_g(z), where y_g = [0, ..., 0_classes];
+   6. Perform gradient descent on the parameters of G with regard to the negative likelihood of G on minibatch of noise sample;

# 6.3.1 Diagnostic Report Generation

The description generation model consists of a CNN followed by an RNN model, modelled as an encoder and decoder network. While training, the overall goal is to maximize the likelihood of labels provided with training-embedded images. LSTM layers further take a sequence of encoded inputs and learn to decode them to sequence one word after another. Figure 6.2 depicts the architecture designed for generating the descriptions for the X-ray images.

The overall objective for the description generator is given by Equation 6.4, to maximize the probability of correct description, where I is an encoded image and S is the target description sentence. Since S is a sentence, a sequence of maximum length N will be expanded to S_0, S_1, ... S_{N-1}, and the objective function is given, as shown in Equation 6.5.

θ* = arg max_θ Σ log p(S|I, θ) (6.4)

log p(S|I, .) = Σ_{T=0}^{N} log p(S_T | I, S_0, S_1, ..., S_T - 1) (6.5)