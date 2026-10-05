# Theoretical foundations for recommender systems 21

# 2.3.3.4 Amazon product data

Amazon product data [58] is an extensive dataset gathered from Amazon website. The dataset contains 143.7 million product reviews and ratings, and metadata of products in the form of product name, categories, price, brand, and image feature. Moreover this dataset also contains information of other items purchased and other links viewed by the same user. Some visual features of products have also been extracted using deep convolutional networks and have been made available in the dataset.

# 2.3.3.5 Yahoo Webscope datasets

Yahoo Webscope [59] is a library of several datasets that have been made available by Yahoo for noncommercial purposes. Some of these datasets specifically address the areas of recommendations and classifications. A brief description of some such datasets is given as:

+   - Yahoo! Music rating
This dataset contains preferences of Yahoo music community and contains over 717 million ratings of 136,000 songs by 1.8 million users. The details of songs including artist, album, and genre are also available in the dataset.
- Yahoo Delicious
Delicious is a bookmarking website for storing online bookmarks. Yahoo Delicious dataset contains 100,000 URLs that were bookmarked on website by its users. Each URL has been bookmarked at least 100 times.
- Yahoo! Movies rating
This dataset contains movie preferences of Yahoo users, rated on a scale of A+ to F. Users in this dataset are anonymous. However, detailed information is available about movies that include cast, crew, synopsis, genre, average ratings, and awards. This dataset is a good candidate for both CF and content-based filtering.

The next section ends the chapter with a brief overview about the problems and challenges that the RSs face nowadays.

# 2.4 Problems related to RSs

Although RSs are extremely powerful tools on the web these days, yet have some problems and challenges which they face every now and then. These challenges are discussed in detail by [8], [6], [60], and [61] and have been summarized in the following subsections.

# 2.4.1 Data sparsity problem

Data sparsity problem arises in RSs as time progresses. This problem is caused by a drastic increase in the number of users and items. As not many of the users are rating the items they very frequently, the utility matrix becomes sparse, which results in degradation of recommendation quality.