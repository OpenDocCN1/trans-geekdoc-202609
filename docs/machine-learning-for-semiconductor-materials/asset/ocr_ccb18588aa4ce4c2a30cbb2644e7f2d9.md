The random forest model got better at sorting things out when we trimmed down the data to just the key bits, using SVC to pick what mattered most. Looking at the results in an obvious way showed that the model was good at telling pass from fail, which means the SVC way of choosing what to look at made the model work better. By spotting the most important things to consider, this method produced predictions you could count on more.

Similarly, using logistic regression to pick features worked well. The random forest classifier did an excellent job after training on the chosen features. The confusion matrix showed some wrong guesses, both false positives and negatives, but overall, the classification was pretty accurate. This tells us that while logistic regression was good, we might be able to make it work even better to catch subtler patterns in the data.

The decision tree method of picking features gave us another helpful view. It ranked features based on how important they were, which helped the random forest classifier do well. The confusion matrix showed that the decision tree was good at spotting key aspects. It had a nice balance between correct positive and negative classifications.

Looking at the outcomes of these different methods sheds light on the upsides of each feature selection approach. SVC-based feature selection did a fantastic job of refining the dataset, while decision trees and logistic regression brought their own benefits to the table. Each technique revealed areas that could use some tweaking to boost performance but also showed its strengths in making the classification more accurate. Down the road, researchers should focus on exploring new ways to select features and fine-tune algorithms to achieve even better accuracy.

# 3.12 CONCLUSION

The study of feature selection methods paired with random forest classification for the SECOM dataset showed big improvements in spotting defects. SVC, logistic regression, and decision trees each played a key role in boosting the model's effectiveness. SVC provided a refined dataset with high classification accuracy, while logistic regression and decision trees also produced satisfactory results, each with its own strengths and weaknesses. Concisely, the research highlights how important it is to pick the right feature selection method to get the best model performance. Comparing different approaches gives insights that show how well feature selection works to improve fault detection systems. Looking ahead, future work should focus on making current methods better and exploring new ones to achieve even higher accuracy and reliability in semiconductor manufacturing.

# REFERENCES

+   1. J. Shim, S. Cho, E. Kum, and S. Jeong, “Adaptive fault detection framework for recipe transition in semiconductor manufacturing,” Computers & Industrial Engineering, vol. 161, 2021.

+   2. S. Mitra, and C. Koley, “Real-time robust bearing fault detection using scattergram-driven hybrid, CNN-SVM,” Electrical Engineering, pp. 1–11, 2023.