# # USING THE GPU RUNTIME

To use the GPU runtime with Colab, select Runtime > Change Runtime Type in the menu and select GPU for the Hardware Accelerator (see figure 3.5).

![](bbox=[0.192, 0.166, 0.778, 0.494])

Figure 3.5 Using the GPU runtime with Colab

TensorFlow and Keras will automatically execute on GPU if a GPU is available, so there’s nothing more you need to do after you’ve selected the GPU runtime.

You’ll notice that there’s also a TPU runtime option in that Hardware Accelerator dropdown menu. Unlike the GPU runtime, using the TPU runtime with TensorFlow and Keras does require a bit of manual setup in your code. We’ll cover this in chapter 13. For the time being, we recommend that you stick to the GPU runtime to follow along with the code examples in the book.

You now have a way to start running Keras code in practice. Next, let’s see how the key ideas you learned about in chapter 2 translate to Keras and TensorFlow code.

# ## 3.5 First steps with TensorFlow

As you saw in the previous chapters, training a neural network revolves around the following concepts:

+   - First, low-level tensor manipulation—the infrastructure that underlies all modern machine learning. This translates to TensorFlow APIs:

+   - Tensors, including special tensors that store the network’s state (variables)

+   - Tensor operations such as addition, relu, matmul