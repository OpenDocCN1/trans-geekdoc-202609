# Table 1. The raw tomato leaf dataset

| Label | Category | Number | Leaf symptoms | Illustration |
|---|---|---|---|---|
| 1 | Corynespora leaf spot disease | 547 | Small brown spots appear, leaf spots have yellow halo. | See Figure 1 first row No.1-No.5 |
| 2 | Early blight | 405 | Black or brown spots appear, leaf spots often have yellow or green concentric ring pattern | See Figure 1 first row No.6-No.10 |
| 4 | Late blight | 726 | Watery ring pattern appears and rapidly enlarges to form purple-brown, oily-appearing blotches. | See Figure 1 second row No.1-No.5 |
| 5 | Leaf mold disease | 480 | Irregular yellow or green area appears. | See Figure 1 second row No.6-No.10 |
| 6 | Septoria leaf spot | 734 | Round spots, marginal brown, chlorotic yellow, appear. | See Figure 1 third row No.1-No.5 |
| 7 | Two-spotted spider mite | 720 | Show white or yellow spots, blade back netting. | See Figure 1 third row No.6-No.10 |
| 8 | Virus disease | 481 | Develop small yellow or green, slightly shrinking. | See Figure 1 forth row No.1-No.5 |
| 9 | Yellow leaf curl disease | 814 | Develop small and curl upwards and downwards, and marginal yellowing, bushy appearance. | See Figure 1 forth row No.6-No.10 |
| 3 | Health | 643 | | See Figure 1 fifth row |
| Total | | 5550 | | |

# Deep Learning Models

# AlexNet

AlexNet is the winner of ImageNet LargeScale Visual Recognition Challenge (ILSVRC) 2012, a deep convolutional neural network, which has 60 million parameters and 650,000 neurons [21]. The architecture of AlexNet utilized in this paper is displayed in Figure 3. Te AlexNet architecture consists of five convolutional layers (i.e., conv1, conv2, and so on), some of which are followed by maxpooling layers (i.e., pool1, pool2, and pool5), three fully connected layers (i.e., fc6, fc7, and fc8), and a liner layer with softmax activation in output. In order to reduce overftting in the fully connected layers, a regularization method called “dropout” is used (i.e., drop6, drop7) [21]. The ReLU activation function is applied to each of the first seven layers (i.e., relu1, relu2, and so on) [45]. In Figure 3, the notation m×m×n in each convolutional layer represents the size of the feature map for each layer, 4096 represents the number of neurons of the first two fully connected layers. The number of neurons of the final fully connected layer was modified to 9, since the classification problem in this work has 9 categories. In addition, the size of input images must be shaped to 227×227, which meets the input pixel size requirement of AlexNet.