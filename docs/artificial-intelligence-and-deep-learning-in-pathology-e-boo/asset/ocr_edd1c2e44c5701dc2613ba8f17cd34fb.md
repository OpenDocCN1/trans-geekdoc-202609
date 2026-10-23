# Overview of advanced neural network architectures

Benjamin R. Mitchell, BA, MSE, PhD

Assistant Professor, Department of Computing Sciences, Villanova University, Villanova, PA, United States

# Introduction

The field of deep learning has expanded rapidly over the past few years, and modern practitioners now use a wide range of methods and techniques to achieve state-of-the-art performance. Many of the best performing systems now use architectures that are significantly more complex than the fully connected feed-forward networks used in the past. These techniques draw inspiration from a range of different fields, including statistical methods, time series analysis, game theory, information theory, operant conditioning, genetic evolution, and modern neuroscience (though for the last few it is worth a reminder that “inspired by” is not the same as “accurately modeling”).

This chapter will cover some of the most popular variations, including residual connections (ResNet), unsupervised pretraining (Autoencoders), transfer learning, generative models (GANs), recurrent networks (LSTMs), reinforcement learning, ensemble methods, and evolutionary algorithms. When reading this chapter, keep in mind that the methods presented are largely ways of modifying or expanding on the basic techniques presented in the previous chapter. This is done to address problems where those basic techniques are insufficient. The techniques described here can be used to address problems such as computational efficiency, classifier accuracy, and lack of large amounts of labeled training data.

# Network depth and residual connections

The “depth” of a deep neural network can be highly variable depending on the task. In the earliest days of artificial neural networks, most networks were “shallow,” meaning they did not have hidden layers. This was not because the early network designers did not want to have deeper networks; rather, it was because early researchers had no reliable method for training these deeper networks. As time progressed, developments in the field have allowed for the successful training of deeper and deeper networks. Today, some networks may have hundreds of hidden layers.