Google's Science Journal app (https://play.google.com/store/apps/details?id=com.google.android.apps.forscience.whistlepunk). You can use this to collect data from many sensors, not just accelerometer. Some questions to guide your exploration of phone placement:

+   - How much sensor data do you need to collect and label before you can train an accurate model for phone placement?
+   - How do the places that you keep your phone match up with the places we identified through our surveys and interviews?
+   - Can you get your classifier to perform better if you merge some labels together (e.g., like we did with enclosed/not enclosed)?
+   - Can you add other features, such as time of day or location, to improve your model?
+   - How does your model perform when you train it on your data and also test it on your own data? How does that compare to training it with your data and testing it with a friend or classmate?
+   - Can you purposefully trick the classifier into thinking you put your phone somewhere that you didn't?

Training classifiers for tie strength from just your own data is challenging for all of the reasons described in Section 9.3.6, and asking somebody else for their data can be problematic from a privacy perspective. However, one interesting possibility is to use your own data to classify life facet. You could start by labeling just a couple of your contacts to see how it performs on the remaining unlabeled contacts. There are apps in the app store that will let you download your communication data in a file. You can also get access to some of your own data by downloading it from social networking sites (e.g., Facebook lets you download some of your own data).

+   - How much training data do you need in order to classify life facets using your own data?
+   - What features do you think will be most useful given our results?
+   - Since you are *the* expert on your own social relationships, what features would you change or add to improve these models? Do they improve the inference? Do you think they will work on other peoples' data as well?

# Acknowledgments

My thanks to my coauthors and collaborators who contributed to the projects described in this chapter: A.J. Brush, Sauvik Das, Jason Hong, Jun-Ki Min, Scott