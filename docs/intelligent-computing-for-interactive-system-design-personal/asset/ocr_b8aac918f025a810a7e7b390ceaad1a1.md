# 9.3.7 Q7: What Happens When the Classifier Is Wrong?

Again, because the purpose of developing these models is for research, rather than for a production system, the cost of a wrong classification is fairly low in an immediate sense. However, the answer to Q5 clearly shows that if we are not careful with how the classifier is used, it could end up exposing information that the user did not want to be exposed. This risk, combined with the relatively low likelihood that tie strength and life facet will change suggests that one strategy for dealing with wrong classifications is to make it easy for the user to confirm that a classification is correct, or to correct it if it is wrong. Because it is unlikely to change frequently, correcting wrong classifications manually takes a relatively small amount of effort.

# 9.3.8 How Well Do the Classifiers Perform?

Now that we've considered these questions, how do the classifiers perform?

# 9.3.8.1 Life Facet Classification

To evaluate the life facet classification, we built a model with SVMs (polynomial kernel; d = 2). Since an SVM is originally a binary classifier, we composed three pairwise SVMs (family-vs.-work, family-vs.-social, and work-vs.-social) and combined their outputs with a maximum voting method. We also compared the result with two different models using WEKA [Hall et al. 2009]: a rule-based model (decision tree C4.5) and probabilistic model (naïve Bayes [NB]).
We also split the data into three different categories and trained models for each dataset:

+   - all includes all contacts on the 70-person list
+   - contactlist includes only contacts from the 70-person list who appear in the user's phonebook
+   - somecomm includes only contacts from the 70-person list with at least one logged SMS or call

For the 70-contact list data set, the SVMs showed 65.5% accuracy with survey features and increased to 81.0% when using all features (see Table 9.5). Note that half of the contacts in the 70-contact list were online friends, that is, the profile and mobile-communication features did not contain their data. Nevertheless, this approach achieves a 13.2% improvement in accuracy in using the survey feature. The SVMs yielded 68.5% accuracy on the in-phonebook list using the profile and mobile-communication features together. Accuracy went up to 88% for contacts that users actually communicated with (the communication list set).