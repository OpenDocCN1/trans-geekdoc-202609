# ## 2 Methodology

In robotics typically high-dimensional sensory data with application specific configurations are in use. To make an anomaly detection component reusable without expensive adaptions from specialists, it is desirable to base on a flexible architecture (one or many input channels) and not to use much domain knowledge about the data. This and the need to work with streaming data to find anomalous subsequences instead only single outliers, quantifiable by a score, exclude many anomaly detection methods available in the literature.

On the other side, artificial neuronal networks in general have been used to solve a large range of problems in the field of robotics processing [2] particularly, deep-learning networks are identified as the leading breakthrough technique in the field of mobile robots [3]. They might be used to overcome important challenges in perception and control of mobile robots. For example in [5, 6] a novelty detection in visual data to analyze the robot’s environment is described.

In [13] we have shown that a specific deep neural network (DNN) based autoencoder allow for a robust and easily expandable implementation of anomaly detection in kinematic data but which architecture should we use?

There are several approaches. A common way is to train a neuronal network with non anomalous data to be able to predict the next few time frames in the timeseries, based on the current and past values. Then the test data can be compared with the predicted data and the prediction error gives an indication of anomaly [4].

A further class of unsupervised methods combines recurrent neural networks with an encoder/ decoder used as a reconstruction model, where some form of reconstruction error is used, as a score measure of anomaly. The so called autoencoders are trained to reconstruct the normal time-series and it is assumed, that such a model would do badly to reconstruct anomalies, having not seen during training [4].

A newer variant of the autoencoder architecture is the variational autoencoder (VAE) introduced in [7, 8] and amongst others used for anomaly detection [9]. It is based on a reconstruction probability instead a reconstruction error, which should be a more objective anomaly measure. To take into account the temporal structure of timeseries in such an architecture, an additional LSTM [11] layer can be preceded.

# ## 3 Concept

The bigger aim of the project behind this paper is to make the usage of mobile robots more robust and flexible by dynamic adaptions to a changing environment. This paper extends the work in [13], which describes in detail the kinematics of the commercially available mobile platform Mir-100 during overrun of a cable channel as a model for an environmental anomaly. Takeoffs are happening particular strong for the rear wheels as a product of the front and the drive wheels already past the cable channel and therefore pulling is more