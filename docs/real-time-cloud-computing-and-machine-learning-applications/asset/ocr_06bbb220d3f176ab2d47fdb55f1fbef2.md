# 444 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoonon

# 5.1.11. Classification

Classification deals with the prediction of outcomes that are typically classes or categories. This means that the algorithm analyses a particular dataset with one or more variables, each belonging to a particular class and turn predicts the latter for a specific set of input. In simple terms, it assigns classes, also known as targets, labels or categories to either structured or unstructured data. In this section, two algorithms are detailed namely the K-Nearest Neighbour (KNN) algorithm and the Multilayer Perceptron (MLP) classification algorithm | [15,16]

The first step in classifying a set of values is the pre-labelling of data pushed to the cloud. Adding a category to the dataset can be categorical or numerical. In this case, the following states are allocated to the values registered to classify them by the type of traffic that they are more likely to be.

+   * Idle: The application is opened and kept idle without running other applications in the background. This means network parameters are mostly constant with few to no fluctuations which might occur in case of the reception of messages or notifications from social media applications.
* Browsing: Tasks such as web browsing and scrolling through social media like Facebook are performed while registering values. This type of traffic can be considered moderate.
* Streaming: Using the Twitch streaming or live videos on YouTube to watch videos while values are sent to the cloud. This means that the device is highly active in network usage.

A typical dataset with pre-labelled data such as the "laptopclassified" Cloudant database is as shown in Table 59.

| Key | Download Speed | Upload Speed | Packets Received | Packets Sent | Status |
|---|---|---|---|---||
| 12 | 2 | 1 | 9 | 5 | idle |
| 13 | 1 | 1 | 8 | 6 | idle |
| 325 | 158 | 54 | 330 | 281 | browsing |
| 1316 | 268 | 31 | 327 | 201 | browsing |
| 607 | 1310 | 26 | 954 | 428 | streaming |
| 608 | 1372 | 27 | 1003 | 447 | streaming |

# 5.1.11.1. Filling Cloud Databases

Since separate datasets are being used for the PC and Android devices, both of their values are pushed to their respective Cloud databases. Therefore, the Runnable threads for the local server, localAndroid and localServerPC, are modified to accommodate the credentials of the particular databases according to Table 5.1. To pre-label the data, "readings" JSONObject variable in Listings 5.6 and 5.7, it is used to add another column to the database using the put() method by