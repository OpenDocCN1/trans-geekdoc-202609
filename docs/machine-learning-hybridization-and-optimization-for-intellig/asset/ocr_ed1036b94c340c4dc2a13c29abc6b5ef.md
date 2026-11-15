For evaluating the proposed BLTL framework’s source model, the metric chosen is ‘Accuracy’. It is believed that the higher the BLTL framework accuracy, the better the model in giving the classification output and caption generation.

# 5.4.3 EXPERIMENT RESULTS AND DISCUSSION

# 5.4.3.1 BLTL framework

The 25,000 imagenet dataset is used for feature learning at the source domain. The first source model of the BLTL framework consists of just five convolutional layers; then max pooling layers are used which in turn are followed by three dense layers. This proposed BLTL source CNN network, with adequate training and validation, results a in significant accuracy of 0.90, as demonstrated in Figure 5.3.

![](bbox=[0.18, 0.43, 0.8, 0.6])

FIGURE 5.3 Source domain classification results

In the present work, only the classification results of the source model of the BLTL framework are reported. Then the source domain–learned knowledge is in turn transferred to the BLTL framework’s target domain, which consists of a judicial law related dataset, as this is the basis for the development of the target domain. Then the resulting outcome features from the target domain of the BLTL framework will be transferred to the LSTM model, which classifies and translates the data and automatically generates law reports. The results of the target domain and the LSTM