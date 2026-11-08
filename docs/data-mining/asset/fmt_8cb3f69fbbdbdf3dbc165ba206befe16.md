
3. C. The loss function you will use to train your model.
4. D. The learning algorithm you will use to train your model.
5. E. The technique(s) you will use to address overfitting.
6. F. The hyperparameters for the model and learning algorithm that you need to select, and how you will select them.
7. G. Design a baseline method to compare your method against, which is not a deep neural network.
Be sure to clearly justify your choices.
Bonus question: Extend your model to account for the user’s relative stances (e.g., if two users in a thread express disagreement with each other, they are likely to be on opposite sides of the issue).
* 11.18 Which was the first of the DeepMind “Alpha” models to avoid using any supervised learning?
1. A. AlphaZero
2. B. AlphaGo
3. C. AlphaGo Zero
* 11.19 Which model can play shogi (“Japanese chess”) better than humans and other AI?
1. A. AlphaZero
2. B. AlphaGo
3. C. AlphaGo Zero
# Chapter 12 Beyond supervised and unsupervised learning
## Abstract
In many practical applications, labeled data is rare or costly to obtain. “Semisupervised” learning exploits unlabeled data to improve the performance of supervised learning. We first discuss how to combine clustering with classification; more specifically, how mixture model clustering using expectation maximization can be combined with Naïve Bayes to blend information from both labeled and unlabeled data. Next, we discuss how a generative approach for learning from unlabeled data, such as the one based on fitting a mixture model, can be combined with discriminative learning from labeled data. Following that, we consider the “cotraining” method for semisupervised learning, which can be applied when two different views are available for the same data. These two views normally correspond to two distinct sets of attributes for the same instances. Finally, we see how cotraining can be combined with expectation maximization in the so called “co-EM” method to yield further improvements in predictive performance in some scenarios. In addition to semisupervised learning, this chapter also discusses sophisticated techniques for multiinstance learning, which improve on the simple methods presented in [Chapter 4](#Ch004_91-164_B9780443158889000054.xhtml#Ch004_91-164_B9780443158889000054), “Algorithms: the basic methods.”
### Keywords
Semisupervised learning; combining clustering and classification; expectation maximization; combining generative and discriminative modeling; cotraining; co-EMmulti-instance learning
## Chapter Outline
* 12.1 **Semisupervised Learning** [**474**](#Ch013_473-484_B9780443158889000133.xhtml#s0010)
  * [Clustering for Classification](#Ch013_473-484_B9780443158889000133.xhtml#s0015) 474
  * [Cotraining](#Ch013_473-484_B9780443158889000133.xhtml#s0020) 476
  * [EM and Cotraining](#Ch013_473-484_B9780443158889000133.xhtml#s0025) 477
  * [Neural Network Approaches](#Ch013_473-484_B9780443158889000133.xhtml#s0030) 477
* 12.2 **Multi-Instance Learning** [**478**](#Ch013_473-484_B9780443158889000133.xhtml#s0035)
  * [Converting to Single-Instance Learning](#Ch013_473-484_B9780443158889000133.xhtml#s0040) 478
  * [Upgrading Learning Algorithms](#Ch013_473-484_B9780443158889000133.xhtml#s0045) 480
  * [Dedicated Multi-Instance Methods](#Ch013_473-484_B9780443158889000133.xhtml#s0050) 481
* [12.3 **Further Reading and Bibliographic Notes**](#Ch013_473-484_B9780443158889000133.xhtml#s0055) **482**
* [12.4 **WEKA Implementations**](#Ch013_473-484_B9780443158889000133.xhtml#s0060) **483**
* [12.5 **Exercises**](#Ch013_473-484_B9780443158889000133.xhtml#s0065) **484**
Modern machine learning embraces scenarios that transcend the classic dichotomy of supervised vs unsupervised learning. For example, in many practical applications labeled data is very scarce but unlabeled data is plentiful. “Semisupervised” learning attempts to improve the accuracy of supervised learning by exploiting information in unlabeled data. This sounds like magic, but it can work! This chapter reviews several well-established approaches to semisupervised learning, such as applying EM-style clustering to classification, combining generative and discriminative methods, and cotraining. We will also see how cotraining and EM-based semisupervised learning can be merged into a single algorithm.
Another nonstandard scenario with many practical applications is multi-instance learning. Here, each example is a bag of instances, each of which describes an aspect of the object to be classified, but there is still only one label for the entire example. Learning from such data poses serious algorithmic challenges, and some heuristic ingenuity may be necessary to make it practical. We will look at three different approaches: converting multi-instance data to single-instance data by aggregating the information in each bag of instances into a single instance, upgrading single-instance algorithms to be able to deal with bags of data, and dedicated approaches to multi-instance learning that do not have a single-instance equivalent.
## 12.1 Semisupervised Learning
When introducing the machine learning process in [Chapter 2](#Ch002_43-66_B9780443158889000030.xhtml#Ch002_43-66_B9780443158889000030), “Input: concepts, instances, attributes,” we drew a sharp distinction between supervised and unsupervised learning. Recently researchers have begun to explore territory between the two, sometimes called *semisupervised learning*, in which the goal is classification but the input contains both unlabeled and labeled data. You cannot do classification without labeled data, of course, because only the labels tell what the classes are. But it is sometimes attractive to augment a small amount of labeled data with a large pool of unlabeled data. It turns out that the unlabeled data can help you learn the classes. How can this be?
First, why would you want it? Many situations present huge volumes of raw data, but assigning classes is expensive because it requires human insight. Text mining provides some classic examples. Suppose you want to classify Web pages into predefined groups. In an academic setting you might be interested in faculty pages, graduate student pages, course information pages, research group pages, and department pages. You can easily download thousands, or millions, of relevant pages from university Web sites. But labeling the training data is a laborious manual process. Or suppose your job is to use machine learning to spot names in text, differentiating between personal names, company names, and place names. You can easily download megabytes, or gigabytes, of text but making this into training data by picking out the names and categorizing them can only be done manually. Cataloging news articles, sorting electronic mail, learning users’ reading interests—applications are legion.
Leaving text aside, suppose you want to learn to recognize certain famous people in television broadcast news. You can easily record hundreds or thousands of hours of newscasts, but again labeling is manual. In any of these scenarios it would be enormously attractive to be able to leverage a large pool of unlabeled data to obtain excellent performance from just a few labeled examples, particularly if you were the graduate student who had to do the labeling!
### Clustering for Classification
