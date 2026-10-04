# CHAPTER 8 Getting started with deep learning with tabular data

In this chapter, we will review a set of deep learning stacks (low-level framework, high-level API, and deep learning for tabular data library) and use three of these stacks—fastai, PyTorch with TabNet, and Lightning Flash—to solve the Airbnb NYC problem. We will solve the problem three times, with each stack. The goal is to illustrate both the general form of the deep learning approach and to highlight the unique characteristics of the three tools we've selected.

# 8.1 The deep learning with tabular data stack

Before we examine the stacks that are available for deep learning with tabular data in general, let's look at a specific example: the Keras-based deep learning solution for the Airbnb price prediction problem from chapter 3.

# The Keras solution, vs the XGBoost solution

The code that is distinct, for the Keras solution is contained in the training notebook. In particular, the key differences between the Keras solution and the XGBoost solution described in chapter 3 include

+   - Model definition—The Keras model has a large function to define the layers that make up the model, with each class (continuous, categorical, and text) getting a specific set of layers.
- Model training—The Keras model includes additional code to define the callbacks required to make the training process efficient, a callback to stop the training process early if the training is no longer making the model better and a callback to ensure the optimal model is saved during the training process.

The Keras solution that we examined in chapter 3 gives us a concrete baseline with to compare the other stacks we will examine in this chapter. In this chapter, we will exercise a set of other stacks so you can see the pros and cons of each choice.

We will also discuss an additional set of stacks that we weren't able to exercise and explain what this tells us about choices. It is important to understand the stack choices and the pros and cons of the choices that you can select a deep learning with tabular data stack that works best for your requirements.

We briefly review the Keras solution from chapter 3. Figure 8.1 shows the files that make up the Keras solution, with the training notebook highlighted.

The training notebook contains the code that varies between the Keras solution and the other solutions that we will explore in this chapter. The other files stay consistent across all the deep learning solutions, with the exception of some settings in the training config file.

Figure 8.2 shows the components that make up the stack for this solution. The components are used in the training notebook.

In this stack the underlying, low-level deep learning framework is TensorFlow. Since Keras is delivered as part of the TensorFlow distribution and is the recommended