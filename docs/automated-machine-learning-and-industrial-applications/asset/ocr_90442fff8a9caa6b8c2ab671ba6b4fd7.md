# 7.4 Experimentation and Results

Python language was used in the implementation of code in the Jupyter notebook provided by Google Colab.

# 7.4.1 Performance Metrics

The system of measurement used in the evaluation process were precision, recall, and F1-score. Precision is the ratio of the count of properly detected instances of sentiment polarity to the total number of detected instances. Recall is the fraction of count of correctly detected instances of sentiment polarity to the actual count of correct instances. F1-score is the geometric mean of precision and recall, which serves to achieve balance between the precision and recall.

# 7.4.2 Data Collection

The data required for model evaluation was obtained through the crawling of tweets on social media using the application programming interface (API) provided by Twitter. The steps involved in data collection from tweets using Python are presented below:

+   Step 1: Create a Twitter developer account and design an app.
+   Step 2: Install a Python library named Tweepy to access the API.
+   Step 3: Authenticate the requests to the Twitter API.
+   Step 4: Lift off the tweets using Tweepy.
+   Step 5: Refine the tweets based on specific keywords like chatbots and bots, or filter by hashtags or product/service terms.

Using the above steps, tweets were collected under two sectors, namely, fashion and telecommunications. Table 7.6 below shows the dataset summary.

| Sector | Number of tweets collected |
|---|---|
| Fashion | 810 |
| Telecommunication | 428 |