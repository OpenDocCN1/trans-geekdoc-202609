Following is a list of some current research that supports the use of deep learning with tabular data. Compared to the thousands of research papers published on deep learning with nontabular data, including text and images, only a tiny number of papers have been published on deep learning with tabular data.

In addition to making an argument for deep learning with tabular data, the following introduce libraries for deep learning with tabular data. These libraries offer convenient ways to apply deep learning to tabular datasets. We will be using some of these libraries in chapter 8 when we go through additional examples of applying deep learning to tabular data and examine alternatives to the Keras-based approach that was used in this chapter for the Airbnb NYC problem.

+   - SAINT: Improved Neural Networks for Tabular Data via Attention and Contrastive Pre-Training (https://arxiv.org/abs/2106.01342). We will examine this framework in more detail in a later chapter.

+   - TabNet: Attentive Interpretable Tabular Learning (https://arxiv.org/abs/1908.07442). This paper introduces another framework for deep learning with tabular data that we will explore in more detail in a later chapter.

+   - PyTorch: A Framework for Deep Learning with Tabular Data (https://arxiv.org/abs/2104.16368). This paper introduces a library based on PyTorch, and it is one that we will revisit in a later chapter.

+   - fastai: Aed API for Deep Learning (https://arxiv.org/abs/2002.04688). This paper introduces fastai, a high-level framework built on top of PyTorch. This framework includes support for tabular data.

+   - DANETs: Deep Abstract Networks for Tabular Data Classification and Regression (https://arxiv.org/abs/2112.02962).

Each of these papers that we can exercise to validate the robustness of the libraries and, more importantly, determine the ability to solve real-world tabular data problems with deep learning, we need to assess whether the libraries are easy to use and work with current deep learning frameworks. Figure 3.15 shows the relative popularity of some of these libraries based on the number of citations their papers received along with the number of stars received by their peers.

The popularity of libraries matters. If a library is widely used, it is more likely to work in a variety of environments. We cannot take it for granted that a library will work in every environment. As we will see in chapter 8, some libraries do not work in Colab, for example, which means it is difficult to assess them. Also, if you use a library that hundreds or thousands of other machine learning practitioners are using, you are more likely to find answers to questions and resolutions to problems. If you are one of a handful of people using a library, you could end up being the first person who