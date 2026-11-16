The second step involves training the model in Amazon Personalize to make real-time personalization recommendations. In this step, you use three types of data.

+   - Event data, such as the items the user clicks on, purchases, or browses
+   - Item data, such as the price, category, and other information in the catalog
+   - Data about the users, such as the user's age, location, and so on

The next step is to feed this data into the Amazon Personalize service and get a personalized private model hosted for you through the Amazon API Gateway. You can then use this API to feed the recommendations to your users in your business application.

NOTE To train a personalized model, you must gather event data, item data, and user data.