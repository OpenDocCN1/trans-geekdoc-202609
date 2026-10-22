In some other cases, models were “found to be picking up on the text font that certain hospitals used to label the scans. As a result, fonts from hospitals with more serious caseloads became predictors of covid risk.”12

Both of these are examples of data leakage. Data leakage refers to the phenomenon when a form of the label “leaks” into the set of features used for making predictions, and this same information is not available during inference.

Data leakage is challenging because often the leakage is nonobvious. It’s dangerous because it can cause your models to fail in an unexpected and spectacular way, even after extensive evaluation and testing. Let’s go over another example to demonstrate what data leakage is.

Suppose you want to build an ML model to predict whether a CT scan of a lung shows signs of cancer. You obtained the data from hospital A, removed the doctors’ diagnosis from the data, and trained your model. It did really well on the test data from hospital A, but poorly on the data from hospital B.

After extensive investigation, you learned that at hospital A, when doctors think that a patient has lung cancer, they send that patient to a more advanced scan machine, which outputs slightly different CT scan images. Your model learned to rely on the information on the scan machine used to make predictions on whether a scan image shows signs of lung cancer. Hospital B sends the patients to different CT scan machines at random, so your model has no information to rely on. We say that labels are leaked into the features during training.

Data leakage can happen not only with newcomers to the field, but has also happened to several experienced researchers whose work I admire, and in one of my own projects. Despite its prevalence, data leakage is rarely covered in ML curricula.

# Cautionary Tale: Data Leakage with Kaggle Competition

In 2020, the University of Liverpool launched an Ion Switching competition on Kaggle. The task was to identify the number of ion channels open at each time point. They synthesized test data from training data, and some people were able to reverse engineer and obtain test labels from the leak.13 The two winning teams in this competition are the two teams that were able to exploit the leak, though they might have still been able to win without exploiting the leak.14

12 Will Douglas Heaven, “Hundreds of AI Tools Have Been Built to Catch Covid. None of Them Helped,” MIT Technology Review, July 30, 2021, https://oreil.ly/lg1b1.

13 Zidmie, “The leak explained!” Kaggle, https://oreil.ly/1lgLj.

14 Addison Howard, “Competition Recap—Congratulations to our Winners!” Kaggle, https://oreil.ly/wVUU4.