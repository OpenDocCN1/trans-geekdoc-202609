Machine Learning Math:

All You Need to Know Immediately About Math If You Want Spark In Deep Learning, Artificial Intelligent and Machine Learning.

  

1.  Table of Contents

Introduction

1.  Induction and Deduction
2.  Decision Trees

3.  Types of Artificial Intelligence and Machine Learning

4.  Stacked Denoising Autoencoders
5.  Robotics

6.  Reinforcement Learning

7.  Linear Algebra

8.  How Companies Use Big Data to Increase Sales

9.  What Is Supervised Machine Learning

10.  How To Build A Predictive Model

11.  Data Preprocessing With Machine Learning

12.  Machine Learning and Robotics

13.  How AI Is Revolutionizing Industry

Conclusion

  

# Introduction

Machine learning is one such discipline that focuses on how to improve the performance of systems through computation, experience, and a little more experience. In computer systems, an experience usually exists in the form of data. Therefore, the main content of the machine learning algorithm is an algorithm for generating a model from data on a computer. With the learning algorithm, we provide empirical data to it, and it can generate models based on that data; in the face of a new situation, the model will give us corresponding judgments. If computer science is the study of programs, machine learning is the study of algorithms.  

## Dataset  

To do machine learning, you need data. Suppose we collect a collection of data on watermelons, such as (green in color; curled at the base; dull tapping), (dark in color; slightly curled at the base; dull tapping), (pale in color; stiff at the base; crisp tapping). Each pair of parentheses contains a record.   

This collection of records is called a dataset, where each record is a description of an event or object called an instance or sample. Something that reflects the behavior or nature of an event or object in some way such as color, root, and tap are called attribute or feature. Values on attributes such as green and black are called attribute values. The spaces where attributes are stretched are called attribute space, sample space, or input space. Since each point in space corresponds to a coordinate vector, we also refer to it as a feature vector. 

## Hypothesis  

The process of learning a model from data is called learning or training and is accomplished by performing a learning algorithm. The data used in the training process is called training data, where each sample is called a training sample, and the set of training samples is called the training set. The learning model corresponds to an underlying law of data and is therefore called a hypothesis; the underlying law itself is called a "truth" or "ground-truth", and the learning process is designed to find or approximate the truth. The model is sometimes referred to as a learner, an instantiation of a learning algorithm on a given data and parameter space. 

If you want to learn a model that can help you decide if it is a good result, the sample data are not enough. To establish such a "prediction" model, we need to obtain the "result" information of the training sample, such as (color green; curling; ringing) 

## Classification   

If we want to predict discrete values, such as "good melon" and "bad melon", this type of learning task is called "classification". If you want to predict a continuous value, such as watermelon maturity 0.95 or 0.37, this type of learning task is called regression. For a "binary classification" task involving only two classes, one is usually called a "positive class" and the other a "negative class"; when multiple classes are involved, it is called a "multi-class classification" task.  

## Testing  

After learning the model, the process of using it to make predictions is called testing, and the predicted samples are called sample testing. For example, after learning, the test case can get its prediction mark.   

We can also "cluster" watermelons, which will be divided into several groups, each group called a "cluster"; these automatically formed clusters may correspond to some of the underlying concepts, such as "light-colored", "dark-colored", or even "local". This learning process can help us understand the inherent law of data and establish the basis for further analysis of data. It should be noted that the concepts of "light-colored melon" and "native melon" are unknown to us in cluster learning, and the training samples used in the learning process usually do not possess the labeled information.   

As said before, after a careful understanding of all the resources available in detail, you can interpret whether a model uses supervised learning or unsupervised learning by a little brainstorming. Classification and regression are the representatives of the former, while clustering is the representatives of the latter.   

Note that the goal of machine learning is to make the learned model work well with "new samples" and not just training samples; even for unsupervised learning tasks such as clustering, we also hope that the cluster partition can be applied to the samples, not in the training set. The reason why training samples can work well in the whole sample space is that it has generalizability. Generalizability is defined as the ability to use the mastered model in new samples. The beauty of machine learning is, even though training set being a small sample, it can reflect its characteristics quite well in the sample space. Thus, generalizability is an important concept that leads machine learning to a new trend with its simplicity in complexness. It is usually assumed that all samples in the sample space are subject to an unknown "distribution" D, and each sample we obtain is independently sampled from that distribution, i. e. independent and identically distributed (IID). In general, the more training samples we have, the more information we get about. 

# 1.Induction and Deduction  

Induction and deduction are two basic means of scientific reasoning. The "generalization" process from the special to the general, that is, from the concrete facts to the general law, and the latter is the "specialization" process from the general to the special, that is, to deduce the concrete situation from the basic principles. For example, in a mathematical axiom system, it is deductive to derive a theorem corresponding to it based on a set of axioms and inference rules, while "learning from examples" is an inductive process; hence it is also called "inductive learning". 

   

Inductive learning can be divided into a narrow sense and a broad sense, which is roughly equivalent to learning from a sample, while a narrow sense requires learning concepts from training data, which is also called "concept learning" or "concept formation". It is very difficult to learn the concept with good generalization performance and clear semantic meaning. However, an understanding of concept learning helps to understand some of the basic ideas of machine learning. The most basic concept learning is Bourg concept learning, that is, learning the target concepts such as "yes" and "no", which can be expressed as 0/1 Boolean values.   

Learning is known for hypothesis amidst of all discover and model analysis that goes on the background. The goal of the search is to find the fit hypothesis, that is, the correct one. Once the representation of a hypothesis is established, the size of the hypothetical space and its size are determined.   

There are many strategies for searching this assumption space such as top-down, general to special, or bottom-up. During the search process, you can continuously delete the hypothesis inconsistent with the positive example and/or the hypothesis consistent with the negative example. Eventually, we will get the same assumption as the training set that all the training samples are correctly judged, and this is what we learn.   

## Inductive Preference  

Any effective machine learning algorithm must have its inductive preference; otherwise, it will be confused by the hypothesis of "equivalent" in the training set in the hypothesis space and cannot produce definite learning results. It is conceivable that, if there were no preferences, our watermelon learning algorithm would generate a model that randomly selects the equivalent assumptions on the training set each time it makes prediction Learning models, which sometimes tell us it is good and sometimes bad do not make sense.   

Inductive preferences correspond to the learning algorithm's assumptions about what model is better. In practical problems, whether this assumption is true or not, that is, whether the algorithm's inductive preference matches the problem itself most of the time, directly determines whether the algorithm can achieve good performance.   

Due to its complex patterns dealing with deep learning, it is easy to "over-fit" if there are few data samples; such a complex model, such as large data sample, cannot be solved without powerful computing equipment. It is accurate because humans have entered the "big data era"; data storage and computing devices have developed, making connectionism learning technology spring again. Interestingly, neural networks became popular in the mid-1980s. It is related to the increase of computing power and data access efficiency caused by the wide application of Intel X86 microprocessor and memory strip technology. 

Deep learning in this situation is very similar to the neural networks of that time. In the past two decades, the ability of human beings to collect, store, transmit, and process data has increased rapidly, and huge amounts of data have accumulated in every corner of human society. There is an urgent need for computer algorithms that can effectively analyze and utilize data. Machine learning has responded to this urgent need of the Great Age, so it is natural that the field has grown enormously and gained widespread attention.   

Computer science has excelled in this decade exponentially due to a large number of researchers voluntarily dedicating their valuable time to academia. Apart from that, machine learning has also helped researchers to speed up their research process. Now, machine learning is almost in every nook and corner of the world with its infinite number of applications that are serving mankind. From facial recognition to autopilot cars to Internet marketing to bioinformatics that uses protein synthesis. A lot of fields are now actively involved in the development of artificial intelligence with all their strength. In coming years, it is believed that machine learning will expand its horizons in a way that no one ever imagined. 

Bioinformatics research involves the whole process from "life phenomena" to "law discovery", which necessarily includes data acquisition, data management, data analysis, simulation experiments, and so on. Data analysis is the arena for machine learning, where machine learning technologies are already thriving. Machine learning provides data analytics capabilities. Cloud computing provides data processing capabilities. Crowdsourcing provides data tagging capabilities.   

## Overfitting and Underfitting 

   

In the process of model evaluation and adjustment, we often encounter "overfitting" or "underfitting" situation. How to effectively identify the "overfitting" and "underfitting" phenomena and adjust the model is the key to improve the machine learning model. Especially in the actual project, it is the domain knowledge that the algorithm engineer should have to adopt many methods to reduce the risk of "overfitting" and "underfitting".  

When trying to define these two, remember that if a model fits with the training samples well but gives a very bad percentage of accuracy, it is called overfitting. On the other hand, if the training sample did not fit well in the model and if was not accurate too in effect to the prediction, it is called underfitting. 

The cost is an index to measure the conformity between the model and the training sample. Simply put, the cost is for all the training samples, the model fit out of the true value of the training samples of the average error. And the cost function is the function relation between the cost and the model parameter. The process of model training is to find the appropriate model parameters to minimize the value of the cost function. The cost function is recorded as j (), representing the model parameters.  

The cost of the test data set, Jtest (), is the most intuitive indicator of the accuracy of the model. The smaller the Jtest () value means the smaller the difference between the predicted value and the actual value of the model, and the better the prediction accuracy of the new data. Special attention is needed due to the fact that the test data set used to test the accuracy of the model must be "unheard of" data for the model.   

## Ways to Reduce the Risk of Overfitting 

1.  Start with the data and get more training data. 

Using more training data is the most effective way to solve the overfitting problem because more samples can make the model learn more effective features and reduce the impact of noise. Of course, it is usually difficult to add experimental data directly, but some rules can be adapted to expand training data. For example, in the problem of image classification, the data can be expanded by means of image translation, rotation, scaling, and so on. 

2.  Reduce model complexity. 

The main factor of overfitting is that the model is too complex when the data is less. Reducing the model complexity properly can avoid too much sampling noise. For example, the network layer and the number of neurons are reduced in the neural network model, and the depth of the tree is reduced and the tree is pruned in the decision tree model. 

3.  Integrate learning method. 

Ensemble learning is the integration of multiple models to reduce the overfitting risk of a single model, such as bagging method. 

## Ways to Reduce Risk of Underfitting  

1.  Add new features. 

When the feature is not enough or the correlation between the existing feature and the sample label is not strong, the model is easy to be underfitted. By mining new features such as "context feature", "ID class feature" and "combination feature", better results can be obtained. In the deep learning trend, there are many models that can help to complete feature engineering, such as factorization machine, gradient lifting decision tree, deep-crossing, etc. 

2.  Increase model complexity. 

The learning ability of the simple model is poor, and the model has a stronger fitting ability by increasing the complexity of the model. For example, the linear model adds higher order terms in the neural network model to increase the number of network layer or the number of neurons.  

3.  Reduce the regularization coefficient. 

Regularization is used to prevent overfitting; but when the model appears underfitting, it is necessary to reduce the regularization coefficient.  

## Datasets and Examples 

It is generally accepted that machine learning is the main way to realize artificial intelligence, which is gradually realized by human beings based on machine learning and a huge amount of data, and deep learning is a branch of machine learning. If the three ranges are represented by concentric circles, then AI is the outermost circle and deep learning is the innermost circle. Artificial intelligence is the ability of machines to make decisions that humans can make in less than a second, and those machines can make decisions that one hundred thousand people can make in a second at the same time.  

Learning from training samples with concept markers (classifications) to label (classify) the data outside the training sample set as far as possible. Here, all the tags (classifications) are known. Therefore, the ambiguity of training samples is low. Learn a training sample without conceptual markers (classifications) to discover the structural knowledge in the training sample set. Here, all the tags (classifications) are unknown. Therefore, the ambiguity of training samples is high. Clustering is typical unsupervised learning.   

·          Accuracy and Recall 

Two basic indexes are said to be important in the information retrieval and other processes like recognition. These indexes are important for a better understanding of the topic. 

In the problem that goes on with the accuracy and recall, there are four scenarios that can be used. Out of which the first one is true positive, which means an instance is perfectly true. The second one is called false positive, meaning it is not true but been predicted as true by the machine. The third one is called true negative, which means it is absolutely false and the system has guessed it right. The last one is called false negative that is not false but predicted as false by the machine for various reasons that need to be monitored. 

Datasets 

Datasets and algorithms are as essential as butter and bread, and in many cases, data is more important than algorithms. The examples in this book are primarily based on open-source datasets collected over many years and partially desensitized test data.   

·          HTTP Dataset: The HTTP dataset CSIC 2010 contains a large number of labeled 36,000 normal requests for web services and 25,000 requests for attacks of SQL injection, buffer overflow, information leakage, file containment, XSS, etc.  It is widely used in the functional evaluation of WAF products.  

·          Alexa Dataset: Alexa is a website that publishes world rankings. Founded by search engine, Alexa in April 1996 (USA), it aims to enable Internet users to share virtual world resources and participate more in the organization of Internet resources. Alexa collects more than 1,000 GB of information on the web every day, not only giving links to as many as one billion websites but also ranking each one of them. It can be said that Alexa currently has the largest number of URLs, ranking the most detailed information published website. Alexa rankings are one of the most frequently cited metrics used to measure the number of visits to a website. Alexa rankings are based on users who download and install the Alexa tools bar embedded in browsers such as IE and Firefox to monitor the websites they visit, so their ranking data is not necessarily authoritative. But it provides a comprehensive ranking, visitors ranking, page traffic ranking, and other evaluation index information; it is difficult to have more scientific and reasonable evaluation reference. Alexa offers download of the TOP one million web domains in the world in CSV format.   

·          Movie Review Dataset: The movie review dataset contains different movie-related data that can be used for various analysis and testing purposes. This is widely used all around the world due to its simple implementation and easy instructions. 

## Text Data Extraction 

In machine learning, feature extraction is considered as a kind of manual work. Some people call it "feature engineering", which shows how much work it takes. In feature extraction, digital and text feature extraction is the most common. Digital features can be used as features directly, but for a multi-dimensional feature, the range of values of one feature is very large, which may lead to the influence of other features on the results being ignored. At this time, we need to pre-process the digital features. 

Text data extraction features are much more complex than digital features. They are essentially word segmentation. Different words are used as a new feature. 

Word set model: A set of words in which each element has only one word, that is, each word in the word set has only one word.   

Word bag model: If a word appears more than once in a document, count the number of times it appears (frequency).  

The essential difference between the two is that the word bag increases the frequency dimension based on the word set: the word set only concerns with and without, and the word bag also concerns with several. When processing data, CSV is the most common format, with each line of the file recording a vector, with the last column marked. TensorFlow provides a very convenient way to read data sets from CSV files.   

# 2.Decision Trees 

The first algorithm we are going to take a look at with supervised machine learning is the decision trees. These are nice to work with because they are efficient data tools any time that you would like to look at the different scenarios that are provided, and then pick out the right options for these for your business. Once the decision tree is able to present you with a few options, you can see the outcomes and the possibilities that come with them. And all of this information can be used in order to help you make predictions that are the most accurate and helpful for your needs.  

It is also possible to use these decision trees for either continuous random variables, or when you want to work with categorical variables. However, most of the time, when you decide to work with these decision trees, you are working with classification problems.  

In order for a programmer to make a good decision tree, it is important to take all of the data and split it up into domains, and then you will split it up into a minimum of two sets, even though you will often get more, of similar data. These data sets are going to be sorted out with the help of their independent variables because it will make it easier to distinguish the different sets that you are working with as well.  

So, we have talked about these a bit here, but it is time to get a better idea of how this works. For this example, we are going to assume that there are 60 people in the group. Out of these people in the group, there are going to be three independent variables to consider including their gender, which class they are in, and their heights.  

When we take a look at all of these people in the group, we know from the start that half of them, or 30 people, like to spend some of their time playing soccer. So, with this knowledge, we decide to work on a model that will help us to better figure out which of the students are soccer players and enjoy playing this sport, and which ones aren’t.  

To help us to figure this out, we need to work on a decision tree, one that is able to look at the people in the group and divide them up based on their similarities and more. We would use the three variables that we talked about before. If the decision tree works out the way that we would like, or hope is that we are going to find a set of students that can end up homogenous when it is all said and done.  

Of course, there are some other algorithms that you are able to use to figure this one out. And some of them are going to work well with the decision tree to ensure that you can accurately split up the data that you have. This is to ensure that you are going to end up with two subsets at a minimum and that the outcomes of both of these subsets are going to end up homogenous. It is possible to have more of these, but since we are just trying to figure out whether we have a person in the group who likes to play soccer or not, right now we are just going to work on dividing the students up into two groups, whether they play soccer or not.  

Decision trees can be a great option for you to work with when it comes to supervised machine learning. This is because these decision trees will allow you to take the data and split them up. Then, with this data split up and ready to go, you can look it over and make some decisions. It is a great way to ensure that you are making the best decisions for your business and for yourself, because all of the information is going to be in front of you, sorted out and easy to read, rather than having to look at all of the conflicting information and make an educated guess in the process.  

## Random forests 

There are a lot of situations where you are able to use the decision tree to make some of the decisions and to sort the data that you want. But there are also times when it just isn’t going to do the work the right way. If you are looking at your data and you know that the decision tree isn’t the right option for you, then you may find that the random forest is a bit better to work with.  

These random forests can be popular to use, and if you plan to do a lot of work in the field of data science, then you definitely will want to learn more about these and how you can use them in your needs. Since these algorithms are well-known in the industry and popular, you will find that many people use them to solve out various problems that come up. For example, if you would like to work on a task that will explore through all the data you have, such as dealing with some of the values that may have gone missing, or dealing with any of the information outliers that show up, these random forests are going to be there to help you get it all done.  

Now, you may find that as you work on machine learning, there will be some times when you will use them because they seem to be the perfect option for giving you great results, results that other algorithms are just not able to do. Some of the different advantages that you are able to get when it comes to these random forests will include:

1.  When you decide to create some of your own training sets and to work on these, you may find that all of the objects that are inside that set will be generated in a random manner. You will be able to replace this if your random tree works the right way, and can help you to sort through the information based on your needs.  
2.  If there are M input variable amounts, then m<M is going to be specified from the beginning, and it will be held as a constant. The reason that this is so important because it means that each tree that you have is randomly picked from their own variable using M.  
3.  The goal of each of your random trees will be to find the split that is the best for the variable m.  
4.  As the tree grows, all of these trees are going to keep getting as big as they possibly can. Remember that these random trees are not going to prune themselves.  
5.  The forest that is created from a random tree can be great because it is much better at predicting certain outcomes. It is able to do this for you because it will take all prediction from each of the trees that you create and then will be able to select the average for regression or the consensus that you get during classification.  

You may find that it is great to work with random forests any time that you are doing things in data science, and there are going to be quite a few advantages to working with a random forest rather than some of the other algorithms, even though it isn’t going to be perfect each time. just because the random variable can provide you with a lot of the results that you would like, you do have to know when it can be useful and when it should be avoided. With that said, there are some advantages to its use.  

First, these random forests are good to use because they can work with regression and classification problems that you have. Many other algorithms are not able to work with both of these. In addition, you may find that random forests are a good option to go with if you are handling large amounts of data because you can add in hundreds of data points and variables, and the random forest will still be able to handle this.  

One thing to consider when you are working with this is that while the random forest is able to handle a lot of regression problems, they will have some issues when it comes to making predictions. Random forests are not going to be limited in this because they are not able to go past any of the ranges that you provide to them so there may be times when your accuracy is not going to be as high as you would like.  

## The KNN algorithm 

The third type of supervised machine learning algorithm that you are able to work with is known as the KNN algorithm. This one is also known as the k-nearest neighbor's algorithm. When you decide to use this algorithm, it is going to be helpful to take all of your data, the data that you have for k most similar examples of any instance of data that you are working on. Once you see some success with this, the KNN algorithm will then be able to go through all of your data points and can provide you with a summary of all the results. Many companies and programmers are able to use this to help them look through the results and make some good predictions.  

Any time that you plan to work with this KNN algorithm model, you will be able to see it as a form of competitive learning. This is going to work well because the different elements will end up competing against one another. This may sound like a bad thing, but when the elements start to compete against one another, they become better at making predictions that are successful.  

As you can imagine, this one is going to work a bit different than the other algorithms that we have talked about in this guidebook so far. There are some programmers who don’t like to use it because they think that KNN is more of a lazy learning process. This is because while it can be effective at providing you with some results, it isn’t going to help you out by creating any models until you specifically ask it for a brand-new prediction. This can be good sometimes, but it will depend on the case. Some people want it to make new predictions automatically, and some like that they will have the most relevant information for the task at hand.  

There are different benefits that can come when you decide to work with this KNN algorithm. When you choose to go with this algorithm, you can cut through a lot of the noise that is found inside your specific set of data. This is because the KNN algorithm is going to rely more on a competitive method to sort through all of the data that you see. This algorithm is going to be great when you want to handle a lot of data, so it is definitely one that you should consider if your data is pretty large. At the same time, it works well if you need some help sorting through all of this data.  

Now, you could have someone go through and look at all this information, providing you with some estimations and predictions for you as well. But this is not that efficient with really large forms of data. Sure, it can be done, but it can take a long time, often so long that new data is coming in and the predictions you have will be too old to work with. It can also lead to more mistakes as someone could miss information or misread it as well. The KNN algorithm can solve this problem by taking out the human error and sorting through any amount of data that you would like.  

One of the biggest problems that you are going to see when you decide to work with the KNN algorithm is that the costs of computing the information are going to be pretty high, especially when you try to compare it to some of the algorithms that are there. This is because this kind of algorithm is meant to take a look at all of the data points that you have, each and every one before it sends out the prediction that you want. This sometimes provides more accurate predictions and information, but the computational costs may be too high for some people.  

# 3.Types of Artificial Intelligence and Machine Learning 

Artificial intelligence is occasionally divided into types based on the characteristics of artificial intelligence (and, indirectly, the intentions of the artificially intelligent software). This approach to artificial intelligence allows computer scientists to create AI programs along with a pattern of capabilities, while it also allows non-science people to understand how AI of certain type functions. The three main types of artificial intelligence in this common division are listed below: 

Analytical artificial intelligence 

Humanized artificial intelligence 

Human-inspired artificial intelligence 

 The first of these types is referred to as analytical artificial intelligence, and it includes the cognitive capabilities of artificial intelligence (as opposed to the task-driven types of AI). Research in analytical artificial intelligence would involve studying how artificially intelligence machines can create cognitive representations of the world and use these basic representations to engage in learning. 

Another type of artificial intelligence is the so-called humanized artificial intelligence, which incorporates types of intelligence outside of cognition. This would include social intelligence and emotional intelligence, meaning those aspects of intelligent action that are based on capabilities apart from relatively straightforward receiving information and processing it in various ways. Human beings are able to show sympathy and feel empathy for other human beings, which are aspects of emotional intelligence. A potential application of this in the context of artificial intelligence might include a computer program or a robot that recognizes when it needs to show sympathy. For example, a program may wish someone a happy birthday, express sorrow at the loss of a family member or other tragedy, or it may give some other sign (like a change in a robotic facial expression) that represents that the AI is aware that an event of import has occurred and a display of some kind is warranted or expected. 

Social intelligence involves the ways that humans use self-awareness and group awareness to interact effectively in the social environment. Self-awareness, in this case, does not necessarily mean the consciousness that some people associate with the implicit dangers of artificial intelligence, but it refers to having an understanding of oneself, including understanding how aspects of oneself may be singular or different from other people. Social intelligence in the context of artificial intelligence may include a machine’s ability to recognize a group dynamic and also to interact successfully with human beings in a social setting. 

Advances in humanized artificial intelligence capabilities have clear implications in business, finance, and medicine. One potential application that has already been attempted is the ability of artificial intelligence programs to engage in dialogue with human beings or create scripts for human beings to follow for interaction with other human beings. Some websites have AI that interacts with people that visit the website, while in the future robots would use this type of AI to be able to successfully interact with human beings without appearing “robotic”. 

Advancements in robotics are a clear use for humanized AI as well as a related type of artificial intelligence, the so-called human-inspired artificial intelligence. Human-inspired artificial intelligence is similar to humanized artificial intelligence, but with a focus on cognitive intelligence and emotional intelligence. A human-inspired artificial intelligence program or robot would be able to process information, learn, and recognize human emotion and respond appropriately, but this type of program would not necessarily be able to understand human social relationships and have an individual awareness in the way that a program with humanized AI would. 

## Will Artificial Intelligence Resemble Human Intelligence? 

A discussion of humanized artificial intelligence leads naturally into the predictive question of whether artificial intelligence in the future will resemble human intelligence or simply “humanness.” If the universe is conceived as an essentially good creation (or simply a thing that exists) and human beings are also conceived as being good along with other forms of life, then there is no reason to believe that artificial intelligence poses an essential danger to humans. 

But if the universe is perceived as being something equivocal, a creation that is neither good nor bad and in which good or bad things interact with one another occasionally to the detriment of one or the other then artificial intelligence becomes something potentially dangerous. If we truly live in a “dog eat dog” world then the dangers of creating something more intelligent than we are and immune from many of our weaknesses are obvious. If human beings mistreat the creatures under their stewardship as individuals at the top of the food chain then how can we say that we too will not be mistreated by machines? 

What this sort of questions accomplish is to imbue the artificial intelligence debate with a philosophical bend that is often ignored. Although the issue with artificial intelligence seems to be whether or not we as human beings can trust machines enough to imbue them with powers greater than our own, it is really a question about human nature itself. The tacit assumption underlying AI fears is that artificial intelligence will eventually become like humans and that this eventuality is something frightening. 

Fictional portrayals of artificial intelligence will be explored in more detail later in the book, but it is important to mention them in passing here. In movies like The Terminator, artificially intelligent robots (and the artificially intelligent programs that direct them) are perceived as thinking in the way that human beings think. In other words, the idea that human beings are dangerous to the environment or to the universe itself and therefore should be eliminated is a human-type logic. This type of logic says: “This thing is bad, we should get rid of it.” But it is difficult for us to say just how conscious machines (thinking machines using artificial intelligence) would perceive human beings. 

A human being may remove all the weeds from a garden because it understands that the weeds are dangerous to flowers or crops, or a human being may hunt foxes and wolves because the danger that these animals pose to farm animals and livestock. This does not mean necessarily that an artificially intelligent machine would behave the same way. If a sugar cane plantation is run by an artificially intelligent program and the goal is to increase production, the AI program may reach the same conclusion that a human being would: this particular thing is dangerous to the plantation, it should be removed. But perhaps the program reaches the conclusion that the sugar plantation itself is unnecessary: that sugary products are not necessary at all and that we should move away from growing them. Or perhaps the machine would have an understanding of where to grow things that we as human beings do not have. 

Human beings have eradicated plant and animal species in order to create farmland or as places of settlement. We recognize that there are problems in the way that we interact with the environment and many AI theorists assume that artificial intelligence would reach the same conclusion. Perhaps they would, but they might have suggestions or even solutions that human beings have not thought of. Just as human beings created new food sources for human beings to partake of over a period of tens of thousands of years, artificial intelligence agents may come up with new food sources or new ways of growing food that solves many problems that human beings are faced with today. 

In the film The Matrix, the machines that rule the Earth eventually decide that human beings are a perfect source of energy, and the machines keep human beings in a collective delusion in order to pacify and sedate them. But this portrayal of machines implies that machines would have the same sort of motivations that human beings would have. For example, the relationship of human beings with other species on the planet is characterized by a reduction of habitats and the number of competing species for the specific intention of advancing human interest. A film like The Matrix assumes that machines would interact with human beings and other species in this self-interested way. 

In reality, this perception that artificial intelligence would behave in this somewhat maleficent human way – hunting human beings to extinction or turning us into fodder – assumes that thinking machines would be motivated by the same essential motivations that drive apex species in the animal kingdom. As much as we as human beings may have a perception of our superiority and sanctity as a species, human beings essentially behave in a very animalistic way. We do it so successfully that we have gained a position of dominance over the other species in our environment. 

For example, a human family moves into a forested area in which a bear resides. After several episodes in which the bear breaks into the human residence, attracted by the smell of food or whatever else, the family decides to have something done about the bear. Similarly, after deer numbers explode in a rural area for a number of human-related reasons, the state or county department of natural resources decides to start culling deer numbers because of fears of accidents caused by deer, deer intrusion into human habitats, et cetera. What underlies all of these interactions is the reality that human interest is also believed to supersede the interests of other species. Instead of the family moving to avoid the bear, they decide that the easiest thing to do is to remove the bear. As human beings, our intentions are generally not guided by a desire for equilibrium with our environments, but to advance our interests in the environment to the greatest extent that we can. 

Though we may design artificial intelligence with the goal of making it human-like or humanized, we assume that fully conscious artificial intelligence – artificial intelligence of exceeding its programming and acting independently of human beings – would behave similarly to how we behave. Perhaps it would not. Perhaps artificial intelligence would be able to achieve homeostasis with the global environment that human beings are not able to achieve. 

The purpose here is not to advocate for artificial intelligence as being somehow better than human beings, but to raise the philosophical question of what would be the motivations of artificially intelligent life. When we assume that artificial intelligence would have the same self-centered motivations that we as human beings have, we assume that we are the ideal species on Earth and that any competitor of ours would naturally resemble us in some way. This is not necessarily true. 

Although artificial intelligence could (and likely will) develop the intellectual capabilities that human beings possess, this does not mean that they would think as we think and reach the same conclusions that we reach. When we as human beings say that artificially intelligent machines could potentially eliminate the human race what we are basically saying is that if we as human beings had the capabilities that machines will have then we would wipe out human beings. 

Existentially-speaking, there needs to be more discussion on what forms machine consciousness is likely to take. Although artificial neural networks may be based on the neural connections of human beings, assuming that artificial intelligence that is conscious would naturally think and behave the way that a human being behaves is a massive leap in reasoning. We do not know how machines are likely to think and we need to explore this area. Recall the AI programs that had a conversation that no one understood on social media. Human beings did not understand it. Why not? Because we did not understand how they were using language and, also (and not less importantly), we did not understand what motivations underlie the conversation. 

## Artificial Intelligence and Machine Learning 

The applications of artificial intelligence are numerous and many of these are based on machine learning. Machine learning, like deep learning, is one of the concepts that must be defined in order to understand artificial intelligence and the direction that it has been taking and is likely to take. Machine learning has been defined in different ways, just as learning has. Machine learning can be summarized as the changes in machine programming or data that occurs in order to improve machine performance. In this fashion, machine learning is essentially tied to how machines store data (including in .dat files and other extensions), and these tasks are closely affiliated with concepts of artificial intelligence. 

Artificial intelligence, especially in its human-inspired and humanized forms, is often conceptualized in terms of tasks that machines complete that human beings would otherwise complete. The idea of using machines to reason and learn in ways that humans are not able to do (at least rapidly) is a more modern development. 

Thinking about artificial intelligence in terms of machine learning may help the reader to conceptualize AI in a basic (and effective) way. The machine or agent is able to perceive its environment and form a model. A model is a sort of representation of the environment. Human beings also form various types of models, some of which may be very abstract. Artificial neural networks allow machines or agents to perceive and model their environments. Interaction with the environment may trigger changes to one or more aspects of the agent. These changes may result in the agent improving the way that it interacts with the environment and therefore learning has been accomplished. 

Although this breakdown of machine learning is relatively simplistic, it describes how learning occurs at the basic level. The machine or agent has been programmed to be capable of perceiving and modeling its environment and it is able to learn when changes affect aspects of the machine's programs or subprograms and improve its performance. This really is not too different from how human beings learn. Intelligent human beings are expected to change their actions and improve their performance based on events that have occurred and changes that have been made. A machine is essentially engaged in the same logical pathway. 

Inherent in the machine learning discussion is whether machines should be able to learn at all. Some suggest that the best way to use artificial intelligence is in a supervised fashion, where agents are programmed to complete tasks and do not experience the change to their components or learning. Allowing machines to engage in learning covers the reality that some tasks cannot be adequately programmed and require a machine to learn (think about an AI program playing chess, for example). Machine learning also allows human beings in the background to access information about relationships for the purposes of data mining. 

Related to machine learning is the concept of deep learning. Deep learning is a category of algorithms of machine learning that allows increasingly greater processing of raw input data to occur. Deep learning is referred to as deep because it involves layers of data representation that allows increasingly complex operations to be performed. The deep or layered aspect of deep learning is important as it represents a form of how human neural networks process information, by creating models that may be quite abstract. Deep learning will be discussed in greater detail later.  

# 4.Stacked Denoising Autoencoders

In this chapter we are going to explore autoencoders, with a specific focus on stacked denoising autoencoders. We will mainly focus on the theory behind these networks and learn the important concepts and techniques. We will not dive in too deep when it comes to code, because this topic is somewhat more advanced and not entirely befitting an intermediary guide to machine learning. However, it is important that you study the theory and the principles of autoencoders so that you can later add another tool to your machine learning kit.

Before we start exploring and discussing the stacked denoising autoencoders, we need to talk about autoencoders in general.

## Autoencoders

They are another important piece of the deep learning puzzle. In many ways autoencoders are similar to the restricted Boltzmann machine. You can call them related because autoencoders train in the same fashion as RBMs. It is worth mentioning, however, that they are trained easier in some cases and they are often preferred when the Boltzmann machine isn’t performing well. But what is an autoencoder, exactly?

It is a neural network with a 3-layer structure where the outputs are connected to the inputs. The purpose of an autoencoder is to learn the encoding (or representation) for a dimensionality reduction. This is achieved by ignoring any signal noise. However, this is only one side of the network. The other side is about reconstruction, where we take the reduced representation and build up the encoding to be nearly the same as the input we started with. In other words, the autoencoder compresses the data from the input layer, and then takes that compressed data to uncompress it so that it matches the original data. This is done so that dimensionality reduction is performed, and to ignore data noise.

To give you an example, we can use a simple autoencoder to work on image recognition. We take the first encoding layer to encode basic image data such as the corners. Then the second encoding layer will process the output of the first layer and encode other features, such as the iris of an eye. Lastly, we have the third layer that can encode the rest of the eye until we have the entire image code to match whatever the image represents. In the final phase, the layers will then decode all of these representations back into the original data.

Autoencoders fulfill the same purpose as PCA. But why bother to employ this technique if we already have a similar one? Simply put, it depends on the data you’re working with. There’s a downside to PCA. It is not so effective when it comes with high-dimensional data, however autoencoders perform extremely well. Autoencoders are simply more advanced techniques that apply noise reduction and stacking methods. This allows them to work with complex data at large scales, while also maintaining accuracy.

Now that you know more about autoencoders, let’s study the structure or architecture to gain a better understanding of how they are implemented.

Structure and Learning

The architecture of an autoencoder is fairly basic. Like with most basic structures, the input data goes to the hidden layer, and from there to the output layer. One key difference compared to other neural networks is that the hidden layer contains the smallest number of nodes compared to the input and output layers.

Another feature worth mentioning is that the output is set as the input. Why? Because after encoding the input in the hidden layer, we rely on the accuracy to reconstruct it. Here’s a simple example of the encoding:

y = s(Wx + b)

In this example, the encoding is done by mapping the “x” input to a new version of itself “y”. Just like in a previous example, “W” represents the weight value that is attached to “x” and “b” is a variable that can be adjusted. These variable adjustments can be extremely useful because they can limit the error in reconstruction.

Now let’s take a brief look at the learning process. When this type of network trains, it relies on a low reconstruction error in order to be as accurate and efficient as possible. The error can be measured using the following formula:

Stacked Denoising Autoencoders

Autoencoders are useful and powerful on their own, however by stacking them we can boost the accuracy greatly. Stacked denoising autoencoders are extremely popular tools used in data science and machine learning, especially when working with natural language processing. These networks can also be applied on image, audio, or text data. This accuracy can be attained by directing the encoded representation from one layer to the next as the input of that layer.

Stacked denoising autoencoders are used in a similar fashion as the restricted Boltzmann machines. Every single layer will be composed from a denoising autoencoder, and a sigmoid element. The autoencoder element is used in a pretraining process of the entire sigmoid net.

Take note that when working with stacked denoising autoencoders, we are using the training set error as the performance measure. This involves a process of layer to layer pretraining because we required the network parameters to be aligned before performing the optimization process. When we start with the fine tuning, we need test and validation data to train the network. This is done over epochs, but only a small number of them because we’ll have greater update phases. The purpose of this entire process is to obtain results that are as accurate as they can be.

To summarize for now, we so far have two major advantages: learning feature representations for high dimensional datasets, and training without involving complex feature engineering. On top of these two benefits, there’s a third characteristic worth keeping in mind. If we properly construct a stacked autoencoder, we can obtain the hierarchic form of its input data. Then if we have consecutive layers of a stacked autoencoder, they can learn high level features progressively. There are no limits or rules that dictate the number or size of layers. It all depends on our scenario and what problem we need to solve. The only real approach to the process is exploring and experimenting with the parameters.

High layers can learn complex structures and compositions, meaning that they can recognize human faces and patterns, handwritten characters, and other various objects. Stacked denoising autoencoders are great at learning extremely complex data as they can be infinitely stacked. Repeatedly stacking autoencoders can only improve the performance and capabilities of a deep network, with the only serious downside being the time and power it takes to compute everything.

On this note, we are going to end this chapter, because the application of stacked denoising autoencoders is beyond the scope of this book. Solving natural language processing problems, for instance, is a more complex process that should be left for when you reach a more advanced level of knowledge of machine learning applications and techniques. For now it should be enough to understand the somewhat light theory behind it so that you can form a rough idea for future implementations. With that being said, let’s move on to the next chapter and discuss semi-supervised learning.

# 5.Robotics  

Robotics is an interdisciplinary field that combines elements of engineering, science, physics, computer science, and electronics, just to name a few. Robotics concerns the design, implementation, programming, and maintenance of robots. A robot can be any physical system that is designed to perform an action or series of actions with varying degrees of autonomy. Robotics has a long history and has probably been in the human psyche ever since the first Greek stories of automatons were being told – though today’s robots are a little different from the ones you learned about in Modern technology allows robots to be smarter, more lifelike, friendlier, and overall more useful than ever before. Many believe that humanity is headed for a new industrial revolution that will be spearheaded by the mass adoption of these systems in virtually every economic sector. Besides the obvious sort of industrial robots that you find in car manufacturing plants and refineries, there are also robotic systems being developed for retail, hospitality, transportation, telecommunication, medicine, and food services.  

Robotics and artificial intelligence often get lumped together, but they are both distinct things. While some aspects of robotics lend themselves to use artificial intelligence techniques, the field as a whole is not preoccupied with simulating intelligence. Robotics can also be divided into several subfields that specialize in certain applications of robotic principles. On the industrial side of things, robots are used to handle tasks that are easy to delegate to a machine. Some of these tasks require high precision or repetitive motions that would be too difficult for a human to sustain for long periods of time. Others are designed for high throughputs like food packaging and labeling. These systems vary in how many behaviors they are capable of performing, their physical properties, and how they are programmed. Industrial robots come in different varieties, but one of the most common configurations is the “arm” type. These have similar designs but perform different tasks. They also have different degrees of freedom that allow them to move differently. Kinematics is very important for these types of robots because the mathematical equations determine how the joints on the arms move.  

Interest in humanoid robots severely lacks with industrial robots regarding market penetration and usefulness. While research in androids or human-like robotic systems remains high, the role of the humanoid robot remains a techno-curiosity more than a commercially viable business – though one day it is conceivable that they will be bought and sold as housekeepers like the robots in The Jetsons. There already exist housekeeping aid robots like the Roomba that has been available since 2002. The Roomba is manufactured by a robotics company fittingly named iRobot. Rodney Brooks, a professor in robotics at MIT, co-founded the company in 1990 with fellow classmates. Since then, Brooks has gone on to start another company called Rethink Robotics in 2009, most known for its creation of the Sawyer and Baxter collaborative robots. Baxter is fundamentally an industrial robot with industrial capabilities but with a bit of imagination. Unlike most industrial robots that usually resemble a mechanical arm, Baxter has two main limbs and an animated LCD face. It was designed to perform mundane tasks on an assembly line.   

Baxter is a humanitarian take on the industrial robot. Instead of performing tasks rapidly and mechanically, Baxter uses sensors to become “aware” of its surroundings. The LCD screen will display a face according to the robot’s state. It can also respond to changes in its environment like ceasing operation if it drops a tool or piece and is unable to recover it. One of the most intriguing facets of the robot is that workers can programme it in the facility. Where other industrial robots require an engineer to be configured through control systems, Baxter is programmable by “hand”. An unskilled worker can move the robot’s hands to perform a certain task, and the computer will try its best to reproduce the movements. This makes Baxter accessible to everyone on the production line, not just educated technicians. Baxter has been lauded as being safer than traditional industrial systems that do not pay attention to other factors outside of their immediate programming. Despite this, the company went out of business in October 2018 due to low sales. Many old guard manufacturing companies saw these systems as experimental and the technology probably not there yet. The robots Sawyer and Baxter are still used in research today. Some universities use them to teach students in robotics courses. More recently, researchers hooked up electrodes between Baxter and a human operator to directly transmit brain signals. Sometime in the future, the interaction between human and robot may resemble something that is as intuitive as simply thinking.  

Most industrial robots do not require to sense things or be particularly smart. They perform a set task and are usually left alone. In contrast, humanoid robot research focuses on the ability of the robot to perceive the world around them and to interact with it. To be able to move a robot requires some propulsion system, like a series of actuators or electric motors. Another option is to use hydraulics or pneumatic systems. All robots need an energy source, either a battery or a direct connection to the current through a wall socket. To be able to see, a robot can be equipped with cameras, LIDAR, and various sensors. Computer vision is coupled with the cameras, and the sensors directly send environmental data like speed, position, balance, and so forth to the robot’s control system. If machine learning is just a combination of statistics and programming, robots are a combination of a great many other things. In both cases, neither approach a general intelligence like the Star Wars droid 3-CPO. If that is the case, what is the current state of the art in robotics? Robotics research is split into many areas of focus, with some people working on sensors, robot dexterity, human-robot interaction, autonomous motion, and so on.  

Humanoid robots are projected to disrupt areas of retail, hospitality, and food service. The chances are that you have already seen the automated menu systems for McDonald’s and other fast food restaurants online. These systems are definitely being worked on, but may not see the implementation for various reasons. Some startups are even working on burger making systems that can perform virtually all of the duties of the average burger flipper at a fraction of the cost. The role of the humanoid robot in customer service is more obvious in places like Japan where robotics has entered the mainstream. Of all the industrialized nations today, Japan has the highest robot density by a large margin. Most of these robots are used in the automotive industry, but a number of them take on customer service roles. They can be found in select department stores greeting customers and in airports acting as luggage carriers. With an ever-contracting population and less unskilled workers willing to do these jobs, it makes sense that Japan has a high adoption rate. For many Japanese citizens, service robots serve to increase the quality of life and are a normal part of their daily lives.   

However, there is still a long way to go for the average consumer in other countries to warm up to these robotic and automated systems. Some would even say that the need simply isn’t there. In 2017, Japanese deaths outnumbered births by 1,000 to one. The population dropped by a massive 264,000 people in one year alone. Other industrialized nations with rising unemployment rates and a stable population perhaps don’t need as many robots. There are also other concerns besides just population and unemployment for why service robots are yet to be seen abroad. Overcoming the uncanny valley effect is no easy feat, especially with older generations. In Japan, people are used to them, so the effect holds less weight – though the same cannot be said for older generations in other countries. Young people today are more comfortable using self-checkout lines and automated systems, but the older generation overwhelmingly subscribes to the importance of face-to-face interaction with their community. A big argument for service robot adoption in Japan is their large aging population. End of life care is synonymous with assisted living, loss of personal autonomy, and embarrassing mishaps. These are areas that service robots can directly address. For one, an older patient is less likely to feel embarrassed if a robot is cleaning after their bathroom accidents. If there is a strong human-robotic interaction, the patient may feel that the robot is a part of themselves like we think our phones are. The result is a net gain in personal autonomy, all things considered.  

With a shortage of geriatrics and personal care professionals plus a global aging population not just in Japan, service robots are projected to rise. Less and less people are signing up for these important ends of life careers. The pay for these jobs is low when compared to other medical professions that require a similar amount of training. If nobody else wants to take care of the elderly, who will? Not every family is willing or able to care for aging parents. Additionally, the risk of malpractice and abuse in assisted living institutions is high. Taking care of the elderly is not an easy job by any means. Combine this with a meager wage, and you have the basis for unfair treatment. Every aging person deserves to be treated with dignity and respect. Whether service robots can render this kind of treatment is up for debate. And it is a debate that will doubtlessly unfold within the current century.  

Would older generations be keen on using a service robot for their daily needs? To some, a robot may seem intimidating or impersonal. After all, robots are not intelligent the way that we are. They may be able to handle basic conversational skills and respond to our commands, but that is a far cry from genuine intelligence. There is also the question of whether these systems should have a human-like appearance or to remain obviously robot looking. Humanoid robots are more likely to create an uncanny valley effect, but it is not exclusive to human-like design. Any robot that acts sufficiently “alive” can elicit the effect. Research into the area of the ameliorating, the uncanny valley falls under human-robot interaction. We know from this research that certain robotic behaviors elicit certain human emotions like fear and uncertainty. For example, when a robotic agent gets too close or invades somebody’s personal space, there is a fear response. If a robot is just lounging around with no purpose, the human perceives it as daunting and even useless. Interacting with these systems can result in unanticipated behavior in the human. Humans are likely to ascribe personality traits to a robot even when these aren’t explicitly programmed. This factor of unpredictableness has lead researchers and designers to add emotive cues to their robots.   

Where service robots suffer from the uncanny valley effect, utility robots do not. Virtually every major military across the globe is investing in robots to aid in the battlefield and in operations. A US-based company, Boston Dynamics, is working on robotic systems known for their mobility. The company made headlines with its design of a quadruped robot named BigDog for the Defense Advanced Research Projects Agency (DARPA). The robot has obvious military applications as a pack mule carrying ammunition and supplies for soldiers on patrol. The project was eventually scrapped because the system was deemed too loud to be used in live combat operations. These sorts of systems are mostly considered prototypes though. Other robots used by the US military include the Foster-Miller TALON family of remotely operated vehicles. They resemble little tanks or planet rovers with fully tracked movement. They are capable of using small arms fire to heavy machine guns completely remotely. Though TALON saw some deployment in Iraq and Afghanistan, its current use remains limited. Other fully weaponized systems are readily used like the General Atomics MQ-1 Predator drone and the MQ-9 Reaper. These belong to a class of aircraft called UAVs or uncrewed aerial vehicles. Predator and Reaper drones can either be controlled by an operator on the ground, or they can fly autonomously with the direction of onboard computers. These systems have faced increased scrutiny with high profile killings involving civilians and questionable rules of engagement. In 2011, under the Obama Administration, a 16-year-old American citizen of Yemeni descent was killed in a drone strike while eating at a restaurant in Yemen. It is unclear why the boy was targeted, but his father was a suspected al-Qaeda leader and was later killed in a similar strike.  

The legitimacy of so-called “killer-robots” comes into question now and then when a new system is announced. At the heart of the debate is whether a nation should possess the kind of power to kill remotely without trial and in the case of 16-year-old in a country that is not at war. Commentators are quick to point out that a machine with killing power is capable of being hacked. They appeal to the “Skynet” scenario where autonomous weapons gain sentience and begin to exterminate humans. Such scenarios are mostly far-fetched science fiction and are not helpful in the debate. While we know that some of these systems are vulnerable to getting hacked, we have yet to see a hacked autonomous system cause loss of life and limb. If there ever is a case where one does, it may cause enough trouble that governments are forced to ban them. Still, others question whether robots going to war is even a good idea. If state-of-the-art machine learning algorithms can barely drive autonomous cares with a certain degree of safety, how can we expect a robot to accurate wage war? War has several more dimensions of complexity than driving down the street does. Deploying actual robo-soldiers seems like an unlikely use of military spending with current technology – though you can rest assured that major governments are researching them.  

A “killer robot” is a blanket term that is also unhelpful. Should a Predator drone be considered a robot any more than a tank with an autonomous turret is? Sentry guns have been in development for several years now and are regularly deployed into the battlefield. The most common of these are called close-in weapon systems (CIWS) and are used to protect battleships from missile and aircraft attacks. A CIWS is basically a large caliber cannon with a high rate of fire that is capable of shooting down missiles at 4,000 rounds per minute or higher. Unlike your grandfather’s anti-aircraft systems that may have required manual sighting, CIWS use radar guiding on a rotating mechanical platform to lock on targets autonomously. Not only that, but once “live”, the weapon system can engage without manual input after locking on. Any missile or aircraft that is detected by the radar system is automatically fired upon. In the case of the Phalanx CIWS used by the US Navy, a single 20mm Vulcan gatling cannon is used with computer-like accuracy. The problem of targeting is reduced to a simple algorithm. It doesn’t require machine learning or any other fancy artificial intelligence techniques. If the radar picks up an object that is approaching the ship, it needs first to make sure that its course is directed towards the ship. If the approach of the object is directly heading towards the ship, then the system must decide to fire. If the object is in between the minimum and maximum velocity range, then the cannon fires. But if the object is too slow or too fast, the system does nothing. Both the minimum and maximum velocity range can be programmed by the operator.  

CWIS, like the Phalanx, are considered autonomous weapons, yet they use very simple tech that has been around since the Gulf War. However, by today’s standards, this is still a “dumb” cannon. The imperfect nature of the weapon has been demonstrated in a few disastrous training exercises. In one instance, the system successfully shot down a dummy drone target, but fuel and debris from the explosion damaged the ship and crew members. In another instance, the dummy drone was shot down, but the system reengaged it as it was in free fall, inadvertently sending rounds in the direction of an opposite ship and injuring crew members. This behavior should be expected from its simple rules of operation. A more sophisticated weapon system could probably have avoided these incidents. But as a last resort missile defense system, the Phalanx does a relatively good job against isolated missile strikes. Other autonomous, radar-guided systems are common throughout the world. Again, these don’t need complicated machine learning schemes to identify targets and engage them. Israel’s iron-dome system of missile defense is hailed by some commentators as the most advanced missile defense system in the world. These systems demonstrate some degree of intelligence, but really all they are doing is calculating velocities.  

All things considered, the future of robotics is bright. Demand for robot systems will likely rise with uneven proportion to robotics professionals, creating well-paying jobs for those who are interested. There will be a glut of these jobs and a shortage of robotics designers and engineers. At the same time, lower-skilled jobs like robot technician and repairmen may emerge. Robotics will infiltrate other areas of tech like the cloud computing space and the internet of things. Robots connected to the cloud will lead to the creation of a cloud robotics marketplace were bidders can remotely program robots to perform certain tasks. Just like Alexa skills, these specific robot programs can be bought and sold in an open marketplace. Not only this, but robotics is taking on increasingly more important roles in business structure. A new executive position called chief robotics officer (CRO) will emerge for bleeding-edge organizations that make heavy use of robotic systems.  

There are split views about just how far the field or robotics can go when it comes to automating human tasks. Whether or not the introduction of these technologies leads to technical unemployment and whether they should be regulated is up for debate.  

# 6.Reinforcement Learning 

Reinforcement learning involves where the learning data is used to give feedback that will determine how the model adjusts to the prevailing conditions in order to achieve the target. The system on its own is able to evaluate the model performance based on feedback response provided and then make necessary adjustments. For instance, the concept is perfectly applied in self-driving cars (Artificial Intelligence) and also in chess master algorithms. 

Reinforcement learning as indicated above occurs in an interactive environment. In other words, the learner is in no way taught what to expect but finds out on their own according to the consequences of their actions, a concept known as “goal-oriented learning”. In this chapter, we shall cover the basics of RL and be ready to learn a lot. The major RL components that we will cover in this section are listed below: 

·          Fundamentals of Reinforcement Learning 

·          RL algorithm 

·          RL environment 

·          Various RL platforms 

·          Applications of Reinforcement Learning 

Fundamentals of RL 

Assume we want to train a dog how to catch an object thrown into the air. The dog may not necessarily understand all the concepts and theories involved here. The best way to accomplish this is to throw the object in the air and every time the dog catches it, be ready to reward it. If the dog fails, then there is no reward. The dog will eventually analyze what actions transpired until it was rewarded. The reward will motivate the dog to repeat the same actions for more and more rewards. 

Likewise, in the RL environment, you may be able to teach the model what to do but based on positive rewards, the model will tend to repeat certain actions. The agent in this matter or a model is more responsive to positive rewards and forget actions that led to negative rewards. 

Sometimes, we have scenarios of delayed rewards or may be only given out when the task is done. There might be rewards or no rewards at each step just to confirm if there are mistakes. 

Assume you are to teach a robot on how to navigate through without hitting a mountain. 

One rule would be to take away 10 points when the robot hits a mountain and gets stuck. Through this the robot will understand that whenever it hits a mountain, there is a negative reward and therefore will not hit the mountain again. 

The other rule would be to give the robot 20 points each time it navigates in the right direction. Of course, the robot must try to maximize the rewards by remaining in the right path. 

The model here or agent (robot) can apply two basic concepts of RL to navigate smoothly and get more rewards. The RL model can decide to explore different possibilities so as to get more rewards. And in this case, there is a higher possibility that the agent will poorly perform since it might utilize the wrong cations. The other way is to exploit only the previous actions that resulted in positive rewards. When the model follows the path of exploiting only the known previous actions, there is a greater possibility of it missing out on the best actions though it will receive rewards. And unfortunately, it impossible to perform both exploration and exploitation at the same time. 

Agent 

An agent basically is a software program that is capable of making intelligent decisions and is a learner in RL. They make decisions and act according to the environment of interaction plus rewards that follow. 

Agent Environment Interface 

The agent being an intelligent software is able to perform a function, At at time, t, and then move from state At to the next state labeled At+1. Again, according to the action, the agent is given rewards, R. 

Model 

This represents the agent’s learning environment. The learning here can be either through model-based or model-free learning. For model-based learning, the agent is free to exploit all the previously learned information before making a decision. Model-free learning on the other hand involves where the agent entirely relies on trial and error method so as to perform the required action. For example, when you want to move to college from home, you either use the foreknowledge of the routes to college or just try different routes and finally choose the fastest method. 

Policy Function 

A policy basically is what controls how the agent behaves in the environment. The behavioral nature of the agent depends on which type of policy it is operating under. From our previous example about getting to college from home, the various routes represent the different possible policies. Some routes may be very short while others are long cuts. The routes are called policies since they are the guidelines towards achieving your ultimate goal. The symbol ᴫ is always used to denote a policy. 

Most policies are always represented in a lookup table or as a complex search process. 

Value function 

There is always a value function for each and every state of the agent. This function gives how profitable it is for the agent to be located in a particular state. The function is dependent on policy and denoted by v(s). Value function represents the total expected rewards received by the agent right from the initial state. The various types of value function include: 

Optimal value function: Gives the highest value for all states when compared to the other value functions. And so it is the optimal policy that has the optimal value function. 

Stationary policy: This kind of policy involves where the action-distribution returns are entirely dependent on the last two states visited by the agent. 

Deterministic stationary policy: This is a policy that is able to deterministically select an action of the agent based on its current state 

Algorithms for control learning 

There are various algorithms applied to reinforce learning as discussed below: 

Criterion for Optimality 

A learning agent is expected to make mistakes during its first moments of getting into the environment. So the agent is supposed to receive discounted rewards if it is to achieve optimal goals. The policy set here should be that which expects a minimum return from the agent itself. There are two policies that are totally involved in obtaining optimality, that is, optimal policy, deterministic stationary policy and stationary policy. 

Brute Force 

This RL algorithm includes the following processes: 

1\. Any possible policy there are sample returns accrued to it 

2\. The policy with the highest expected returns is selected. 

Issues with this algorithm include: The number of policies can extremely large of infinite therefore difficult to manipulate. Another possible issue would be a difficulty in dealing with a policy of varied returns. Imagine a policy with such a large variation on its returns. Getting the average value of returns per policy may be tedious at times. 

Value Function Approaches 

This kind of algorithm tries to get the maximum returns by maintaining a set of estimated returns for some particular policies, either current policy or optimal policy. A policy that achieves maximum returns from the initial state may be deemed best for application.  

Direct Policy Search 

Another possible way of determining the best policy involves having to search directly from some set of policy space. The two methods used here are: gradient-based and gradient-free methods. The gradient-based search involves where you start mapping from finite dimensional parameters to specifics where policies space is located.  

Applications of Reinforcement Learning 

Among the vast areas of application for RL, some are still under investigation and yet some are already implemented. These areas include: 

·          Large-scale empirical evaluation 

·          Predictive state representation 

·          Lifelong learning 

·          Dopamine-based learning in the brain 

·          Part of the model for human skill learning 

·          Etc.

# 7.Linear Algebra 

A field of mathematics that scientists all over the world confirm to be a prerequisite to an in-depth understanding of machine learning is linear algebra. Though with various notations and tools, difficult findings and theories, linear algebra is a broad discipline, and the bolts and nuts taken from the field are practical for practitioners of machine learning. That is why it is possible to focus on the relevant or the right parts with a solid foundation of the concept of linear algebra. And from a machine learning perspective, it is vital to know the exact meaning of linear algebra. Also, it is critical to know whether linear algebra is the mathematics of data, or if it has any remarkable impact on the field of statistics, and how linear algebra is the cause of several practical mathematical tools including computer graphics and Fourier series. 

As the mathematics of data, linear algebra is a branch of mathematics and the language of data as vectors and matrices. A linear combination is the total of linear algebra. It is the utilization of arithmetic on vectors which are columns of numbers and matrices which arrays of numbers. As a study of vector mappings and spaces, linear algebra is about planes and lines that are needed for linear transforms.  

To start on this journey, you need to know the basic inferential and descriptive statistics. However, knowing more mathematics is required once you have covered the basic concepts in machine learning. There is a need for more mathematics in a situation where they make any underlying assumption and their limitations to understand how these algorithms work. 

## The Importance of Linear Algebra 

If you are on a journey of learning machine learning and data science, it is vital to know the importance of the reason linear algebra is essential with these four examples: 

Example 1: 

Imagine the perception you have when you attempt to take in the picture of a flower. Well, it is easy since you can make out leaves and flower. However, it can be such a challenging task when, for the computer to engage in the same job, you are asked to mark that logic. Since the brain of human has passed through evolution for millions of years, you can identify the flower. To have the power of telling if the color of an image is black or red, we have no clue of the things that go on in the background. To perform the task is the only our brains have been trained to do. 

However, it is a difficult task to make a computer engage in a similar mission, and it is a dynamic feature of study in computer science and machine learning in general. We may need to reflect on a specific question ahead of making identification of image attributes; so, what is the process of storing this image by a machine? 

To prepare the single 0 and 1 is how they design computers nowadays. Therefore, how can they store such an image inside a network with various attributes like the color? The accomplishment of this storage is through the construct containing the intensities of pixel known as Matrix. As a result, it is in the capacity of how they process this matrix to make out colors and some other things. At the back end will all the operation anyone wants to carry out on this stage will happen using matrices and linear algebra.  

Example 2: 

Have you heard the term “XGBOOST?” Any domain of data science domain household knows that data science competitions winners employ quite often an algorithm. To give predictions, it takes the Matrix form to store the numeric data. Not only does it offer more precise results, but XGBOOST is also capable of faster data process. Furthermore, apart from XGBOOST, other numerous algorithms make use of Matrices for data processing and storage. 

Example 3: 

As the latest catchword around now, deep learning uses matrices for storing inputs, including giving topnotch answers to these questions using text or speech or image. Also stockpiled in the matrices are weights that a neural network trained. 

Example 4: 

Dealing with text is one more dynamic field of machine learning research, and term-document matrix, words’ bag, and so on are some of the techniques they frequently use. In the same manner, to perform tasks such as language translation, language generation, semantic analysis, and so many others, all these methods store counts of words within documents and to perform tasks, accumulate this occurrence count in a matrix form. 

Thus, let’s hope that, to some extents, you have had some understanding of machine learning and its connection with linear algebra. To employ matrices for data processing and storage, we know the text, image, or any general data. It is now time to experience the linear algebra from the top. 

## Linear Algebra Problems Representation 

It is with an uncomplicated problem that we may want to begin. Let’s consider that the cost of 1 bat and 2 balls or 100 units is 2 bats and 1 ball. Finding the value of a bat and a ball is what we are required to do now. Let’s assume Rs ‘x’ is the value of a ball while Rs ‘y’ is that of a bat. Depending on the circumstance, anything can be the values of Rs ‘x,’ and ‘y,’ i.e., variables is ‘y’ and ‘x.’ to interpret this form in mathematics, we will go like this; 

(1)………………… 2x + y = 100 

Likewise, the subsequent condition may have a similarity like this; 

(2)………………………. X + 2y = 100 

Right now, to satisfy both the equations, ‘y’ and ‘x’ value is what we need and to find the prices of ball and bat. The solution to a set of linear equations is finding ‘x,’ and ‘y’ values are the basic problem of linear algebra. The big picture is data has a representation in the linear equations form in linear algebra. And in turn, the vectors and matrices forms are the representation of these linear equations. Depending on the condition, there may be variation in the equations and those of variables, yet their form is in vectors and matrices representations.  

## Visualize the Problem 

Usually, visualizing the data problems can be quite helpful, and doing that will help a case such as this. The linear equations are the representation of flat objects. To have a clear understanding of the line, it may be a good idea, to begin with, the simplest one. A collection of the entire points that gratify the given equation is a line corresponding to an equation. For example; 

Our equation (1) gets satisfied with (30, 40), (50, 0), and (0,100/3, 100/3) points. As a result, it is on our equation’s corresponding line (1) that these lines should lay. Similarly, our equation (2) enjoys some of these points (100/3, 100/3), (100, 0), and (0, 50). 

At present, the dot that sits on the two lines is quite paramount to seek satisfaction on both conditions. By instinct, the connection point is what we need to find on the two lines. We can use the operations of elementary algebraic such as subtraction, addition, and substitution to solve the problem. 

(1)…………………………. 2x + y = 100 

(2)……………………………..X + 2y = 100 

(1) Equation is:  

y = (100 – x)/2 

In equation (2), y value will be:  

(3)…………………………… x + 2\* (100 – x)/2 = 100 

You can solve equation (3) for x as well as y afterward since a single variable x equation is in equation (3). 

Right now, explore as we take a step further even though the equation looks simple. 

## Complicating the Problem 

With three variables, let’s assume an array of three conditions is given to you and put to identify the value of the entire variables, each as given below. We can make out what ensue by solving the problem. 

(4)…………………… x+y+z=1 

(5)………………………… 2x+y=1 

(6)………………………… 5x+3y+2z=4 

We get the result below in equation (4); 

(7)………………………… z=1-x-y 

Then, in equation (6), while we replace merit of z with, we have; 

5x+3y+2(1-x-y) =4 

(8)…………………… 3x+y=2 

At this time, in the above problem of bar and ball, and as the two variables instance, let’s solve equations (8) and (5) to find ‘x’ and ‘y’ values. When we know ‘x’ and ‘y,’ to find ‘z’ value, we can use (7). 

In this case, it will increase our efforts of problem-solving with the addition of more variable. In 10 equations, let us visualize that we get 10 variables. It can be time-consuming and tedious when we attempt to solve 10 equations at once. Now, let’s take a plunge into the ocean of data science. How do we now proffer a solution when data points we have are in millions? 

In the original data set, data points are in millions. Then, imagine if it is mandatory for us to repeat it several times and to tender a solution, can take so many years. Besides, the war has never ended with just this one. As a result, what do we do? Quit and run away? Certainly, NO! 

For us to give a solution to a massive group of linear equations, the matrix is what we need. However, let’s turn to matrices and visualize our problem in physical importance before we go further. Directly related to how to use matrices is the next step. 

## Planes 

The three variables in a linear equation, whose coordinates satisfy the equation, represent the set of all points. By such an equation, can you decipher its physical representation? Attempt to image 2 variables, while adding the third one, in the same instance in any comparison. As you should know, it is a three-dimensional analog of line and that it represents. Indeed, the representation of a plane is three variables of a linear equation. Three variables represent a plane in a linear equation. More precisely, extending up to infinity, a plane is a flat geometric object. 

It indicates that we desire to unearth the connection of those planes on the instance of a line by finding solutions to 3 variables linear equation. If you look deeply, in which ways can a group of three planes intersect? Let’s see if things are possible in these four cases; 

1.  The intersection is not present 
2.  The intersection of the three planes at a point 
3.  In a line, the intersection of planes 
4.  Intersection happens with a plane 

Most of the super mathematicians and regular individuals like us can only visualize things in 3-Dimensions, and it is complicated unachievable for humans to visualize things in 4 (or 10000) dimension. Therefore, how is it possible for mathematicians to effectively tackle data of higher proportion? In their heads are tricks and one such ploy mathematicians utilize to take care of data of larger size is matrices. 

Right away, it’s time to move on to the main focus, which is the matrix. 

## Matrix 

Matrix is the process of writing the same items collectively for our necessity to manipulate and handle them. In data science, while training several algorithms, the matrix is what they use to accumulate information such as how an artificial neural network stores weights. Technically, as far as data science is concerned, a 2-D collection of numbers is a matrix.  

123 

456 

789 

Usually, ‘I’ Denotes Rows And ‘J’ Denotes Column. The I’th Row Indexes The Elements And The Jth Column. Through Some Alphabet Like Elements Of A By A (Ij), We Mean The Matrix. 

In the matrix above; 

A12 = 2 

Reach the second column after getting along the first row to get the result. 

Matrix’s related words 

Order of matrix – row\*column, i.e., 3\*4 is the matrix’s order if a matrix has 3 rows and 4 columns. 

Square matrix – when the number of columns is the same as that of rows. 

Diagonal matrix – diagonal matrix has elements of non-diagonal that is the same as 0. 

Upper triangular matrix – the elements under diagonal is the same as 0 in the square matrix. 

Lower triangular matrix – the elements over the diagonal is the same as 0 in the square matrix. 

Scalar matrix – the diagonal elements is the same as some constant k in the square matrix. 

Identity matrix – the complete non-diagonal elements are the same as 0, and all diagonal elements are the same as 1 in the square matrix. 

Column matrix – sometimes a representation of a vector, there is only one column in the matrix. 

Row matrix – there is the only row in a matrix. 

Trace – a square matrix total diagonal elements. 

# 8.How Companies Use Big Data to Increase Sales

Companies use Big Data in countless ways to adapt their business model, especially in advertising. This allowed not only to produce better reports but also to improve sales through better advertising.

Here are some examples of how companies today use Big Data and how you can use it to boost your sales.

Predict the products that customers may want to buy.

How many times have you consulted your Amazon recommendations and have you thought and found surprisingly exactly what you are looking for on your site? Many companies use the big date for this purpose. For example, Amazon uses Big Data to determine exactly what kind of products you want to buy in the future.

According to Entrepreneur, the retail giant - which has reached $ 1 trillion in net worth by the end of 2018 - gives clients an overview of the factors that determine the recommended products. In this context, Amazon cites various data to find out what their customers want. These factors include:

• When customers buy

• How customers rate their purchases

• Which customers with the same buying habits are buying

The last factor is the most important when it comes to Big Data. Amazon can correctly determine the type of products you want to buy based on customers with similar buying habits.

Similarly, you can use this type of data to make forecasts for your customers. It does not matter what your business model is. All you need is data! When you see an increase in sales, you start to notice trends. For example, Amazon realized that TV buyers usually bought a TV, which the retailer started selling in the hope that customers would buy it together ([https://www.entrepreneur.com/article/](https://www.entrepreneur.com/article/) 325923)

Make better business decisions

You can use Big Data to get a head start on operational risk and make better, more efficient decisions. Before the advent of better technology and before people were connected via the Internet, fraud problems were rare. But now that many of us are connected in one way or another, a business can sometimes be compromised in just a few clicks.

Operational risk is particularly high in financial institutions. Fraudsters are constantly trying to develop systems to benefit people and businesses. However, with the evolution of big data, the financial institutes realized that they could use this information to prevent fraudsters from entering.

Banks, for example, are now using Big Data to monitor their transactions in a "face-to-face" business line to eliminate fraud at all levels. They analyze information about who sends/receives money, how often they are involved in the behavior, how much money they send and where they live.

This type of technology can be useful to any business, not just banks. As the data is collected, trends appear and anything that deviates from the "status quo" triggers a digital note about that transaction. This makes it easier for companies to identify frauds when they occur and minimize their operational risks.

Use important data to influence customer behavior.

Marketing operations are becoming more complex due to the complex nature of the market. Also, consumers are becoming more and more complex, and their behavior changes over time. It is also very difficult to predict consumer behavior through traditional use only; the data. Big data is essential to determine how to get customers to make important decisions when they access your page. Businesses use this data to learn about their customers' behaviors and direct them to a sale or conversion.

More precisely, the data analyzes each action taken by a client when it is displayed on his page. He can see the typed keys of the client and see how he moves the mouse. Can predict the actions that will be undertaken next.

To satisfy the customers, you have to follow them, you have to worry about them, and you need data to do everything. But this process is usually complex, difficult and time-consuming, and you need data. Not just any type of data, accurate and accurate data. Managing this complex task for hundreds or thousands of your customers is undoubtedly tedious. This process is complex, no doubt because a wide variety of data is involved and you need to analyze the data as completely as possible.

Big Data has the advantage of helping you create a robust profile for your users and create unique marketing campaigns. All the statistics collected from all your users will help you create highly convertible ads. Thus, you can easily configure funnels for a specific market by linking and linking them in a very obvious way.

Building a robust profile of your visitors is an important aspect of good customer relationship management. Customers are dynamic. To satisfy customers, you must accompany them; you must know who they are, what they like and what they might do, buy or do with whom they associate. You need to know what they are doing when they visit your site. Customers expect better and more personalized marketing. Without a doubt, it is something very complex, and it can be tedious and take a lot of time. You will need more than just a funnel builder for this complex task in a very obvious and complete way. You need something more robust that follows the pages visited on your site and at what time they visited it to create highly convertible ads. You do not want to start running too many ads and waiting for some marketing messages to be converted to leads. A better approach to optimize your campaigns and manage your landing pages, create targeted marketing campaigns, and track your traffic sources and events on your site will require more than just email campaign builder, and more than creating pages. Sales. This process involves analyzing a large amount of data that can be easily resolved through large data.

As an entrepreneur, you can use this data to provide your customers with what they want when they want. For instance, if you are running a marketing website and a customer is accessing your site to read an article, the big date can predict when the reader will access the "X" to close the window. The big date has also been used in digital marketing, where customer data (visitors) are entered to increase the mailing list.

# 9.What Is Supervised Machine Learning 

This guidebook has spent a bit of time going through some of the building blocks and other basics of machine learning and why it is such a great thing to learn how to work with. Now that we know a bit about that, it is time to work with some of the meat and potatoes that come with supervised machine learning, and how we are able to use this to get the results that we want out of some of these supervised learning algorithms.  

We are going to start out our look at learning algorithms with the ideas behind supervised learning. This kind of learning is going to happen when you pick out one of the learning algorithms that have the ability to learn what the right response is to any input of data that the user gives to the program or the computer. The neat thing here is that supervised learning is able to do this in a few different ways. It can choose to look at some targeted responses and examples that are given to it and then learns based on those examples, or you can choose to include some labels in strings or other values to ensure that the program can, over some time, learn the best way to behave.  

Supervised machine learning can be a simple process to look at, but let’s take a look at an example that you can really bring this home. Think back to an elementary classroom with a bunch of students and the teacher. The teacher decides that it is time to learn a new topic and to help their students, the teacher will show a bunch of examples about the situation.  

From this, the students are going to be able to learn how to memorize the examples that they are given because they know that these are going to give them the general rules about this specific topic. Then, at any time when the students see these kinds of examples or even something that is pretty similar, then they know how to respond. And if there is an example that isn’t the same or similar to what they learned about, then they know how to respond to those as well with this method.  

There are quite a few learning algorithms that you are able to use when it comes to supervised machine learning. We are going to focus on the four most common types that you are most likely to use when you want to start with supervised machine learning including:

1.  Random forests 
2.  Decision trees 
3.  KNN 
4.  Regression algorithms 

The Decision Trees 

We now know a bit about how supervised machine learning is going to work. It is time to look at some specific examples of how these learning algorithms are going to work. And the first one we will look at is known as a decision tree learning algorithm.  

With this one, you will find a lot of efficiencies when it comes to data, especially if you are taking a look at a few different options and you want to figure out which method is going to be the right decision for your business or on your project. When there are a few options presented with the decision tree, you get the benefit of seeing the possibilities and the outcomes that each one is going to produce for you. This is often one of the most efficient and accurate ways to make sure that the decisions fit your needs.  

There are different times when you would want to work with a decision tree. You may find working with it for a continuous random variable or for some of the other categorical variables that are available. However, you will usually use this kind of learning algorithm in order to do classification problems.  

To help you make a good decision tree, you need to be able to split up whole domain sets so that you get two sets at least, often three or more, of similar data. These will then be sorted out, using their independent variables, because it is going to help you to distinguish out the different sets that you have in front of you.  

This brings up the question of how you will be able to make all of this work. Let’s say that we have a group of people, 60 of them. Each person in that group will have three independent variables that will include their gender, height, and class. When you take a look at this ground, you know from the beginning that 30 of these students like to play soccer when they have some free time. You can work with the decision tree in order to figure out which people in that group like to play soccer and which don’t.  

To help you with this one, you can take the learning algorithm for a decision tree and look at that group of people before dividing them into some groups. You would need to use the variables of height, class, and gender to help with this. The hope with this is that when the whole thing is done, you can end up with a homogenous set of people.  

Of course, there are going to be a few others of the learning algorithms that you are able to use in order to do this, and they may work well with the decision tree to help you split up some of the data that you are working with. This is going to give you a minimum of two kinds of subsets that will produce outcomes that are pretty homogenous. Remember that it is possible to have more, but since we just want to know whether the group is going to be soccer players or not, then we just want to work with two groups.  

Decision trees are going to be a good option for programmers to choose because they make it really easy to split up all of your data, and then you can make some good decisions based from what shows up in that data. It is a good way to help you make some great decisions for your business because you will be able to get all of your information out in front of you to make decisions, rather than just having to guess.  

Random Forests 

The next type of learning algorithm that you are able to work with is the random forest. There are a lot of times when the decision tree is going to work out well for you, but there are times when you may want to make this a bit different, and the random forest is going to be the right option for you.  

One time, when you would want to work with a random forest, is when you would like to work with some task that can take your data and explore it, like dealing with any of the values in the set of data that is missing or if you would like to be able to handle any of the outliers to that data set.  

This is one of the times when you are going to want to choose the random forest rather than working with the decision trees, and knowing which time to use each of these different learning algorithms. Some examples of when the programmer would want to work with a random forest include: 

·          When you are working on your own training sets, you will find that all of the objects that are inside a set will be generated randomly, and it can be replaced if your random tree thinks that this is necessary and better for your needs.  

·          If there are M input variable amounts, then m<M is going to be specified from the beginning, and it will be held as a constant. The reason that this is so important is that it means that each tree that you have is randomly picked from their own variable using M.  

·          The goal of each of your random trees will be to find the split that is the best for the variable m.  

·          As the tree grows, all of these trees are going to keep getting as big as they possibly can. Remember that these random trees are not going to prune themselves.  

·          The forest that is created from a random tree can be great because it is much better at predicting certain outcomes. It is able to do this for you because it will take all prediction from each of the trees that you create, and then will be able to select the average for regression or the consensus that you get during the classification.  

These random forests are going to be the tool that you want to use many times with the various parts of data science, and this makes them very advantageous compared to the other options. First, these algorithms are able to handle any kind of problem that you are focusing on, both the regression and classification problems. Most of the other learning algorithms that you will encounter in this guidebook are only able to handle one type of problem rather than all of them.  

Another benefit of these random forests is that they are going to help you handle large amounts of data. If your business has a lot of different points that you want to go through and organize, then the random forest is one of the algorithms that you need to at least consider.  

There is a limitation that comes with using random forests though, which is why you will not be able to use it with all of the problems that you want to take on. For example, this can work with regression problems like we talked about before, but they are not going to be able to make any kind of prediction that goes past the range that you add to your training data. You will be able to get some predictions, of course, but these predictions will end up becoming limited. It will stop at the ranges that you provide, lowering the amount of accuracy that is found there.  

KNN Algorithm 

Next on the list of learning algorithms that we are going to take a look at is the K-nearest neighbors, or KNN, algorithm. This is one that is used a lot in supervised machine learning, so it is worth our time to take a look at it here. When you work with the KNN algorithm, you are going to use it to help take a lot of data and search through it. The goal is to have k-most similar examples for any data instance that you would like to work with. When you get this all organized in the proper manner, this KNN algorithm will be able to take a look through that set of data, and then it will summarize the results before using these to make the right predictions that you need. 

A lot of businesses will use this kind of model in order to help them become more competitive with the kind of learning that they are able to do in the industry. This is going to work because there will be a few elements in this model that will compete against each other. The elements that end up winning in here are going to be the way that you are the most successful and you get the prediction that will work the best for you.  

Compared to the other two learning algorithms that are out there, this one is going to be a bit different. In fact, some programmers are going to see this as one of the lazier learning processes because it is not able to really create any models unless you go through and ask it to do a new prediction. This is a good thing for some projects if you would like to keep the information in the models relevant or have more say in what you are adding to the models, but in other situations, it is not going to be all that helpful.  

There are a lot of benefits of working with the KNN learning algorithm. For example, when you choose to use this kind of algorithm, you can learn how to cut out the noise that sometimes shows up inside the set of data. The reason that this works is that it is going to work solely with the method of competition to help sort through all of the data in the hopes of finding the stuff that is the most desirable. This algorithm is useful because it can take in a lot of data, even larger amounts, at the same time which can be useful in a lot of different situations.  

However, you are going to run into a few conditions to consider when it comes to this algorithm. The biggest issue is that there are high amounts of costs computationally, especially when you compare it to what some of the other learning algorithms will do. This is because KNN is going to look through the points, all of them before it sends you a prediction. This takes a lot of time and money overall, and may not be the one that you want to use.  

Regression Algorithms 

Next on the list is the regression algorithm. You will be able to use this because it is a type where you will investigate the relationship that is there between the dependent variables and the predictor variables that you like to use. You will find that this is the method a programmer will want to work with any time they see there is a casual relationship between the forecasting that you do, the time-series modeling, and all of the variables.  

You will want to work with these regression algorithms any time that you want to take all of the different points in your set of data and you want it to fit onto a line or a curve as closely as possible. This helps you to really see if there are some factors that are common between these data points so that you can learn about the data and maybe make some predictions as well.  

Many programmers and companies are going to use this kind of regression algorithm in order to help them make great predictions that then help the business to grow, along with their profits. You will be able to use it in order to figure out a good estimation of the growth in sales that the company is looking for, while still being able to base it on how the conditions of the economy in the market are doing now and how they will do in the future.  

The neat thing about these kinds of learning algorithms is that you are able to place in any kind of information that seems to be pertinent for your needs. You are able to add in some information about the economy, both how it has acted in the present and in the past so that this learning algorithm is able to figure out what may happen to your business in the future. The information that you add to this needs to be up to date and easy to read through, or this algorithm could run into some issues.  

Let’s take a look at an example of how this can work. If you go with the regression algorithm and find that your company is growing near or at the same rate that other industries have been doing in this kind of economy, then it is possible to take that new information and use it to make some predictions about how your company will do in the future based on whether the economy goes up or down or even stays the same.  

# 10.How To Build A Predictive Model 

In this chapter we are going to melt through the keyhole to the other side... We’ll cross the boundary from the sane and sensible world of the everyday into the twisted multi-dimensional realm of the data scientist; i.e. technical specialists with mathematics degrees and PhDs. On our journey we are going to: 

Describe the process that a data scientist should follow when applying machine learning to develop predictive models that are going to be used to drive business benefits as part of an automated decision-making system. 

·          Explain this process in a way that a normal person can understand. This is to help you keep tabs on what data scientists are doing. This in turn will ensure that you get what you have asked for, rather than what the data scientist thinks your organization needs. 

In my experience, when data scientists have been left to “just get on with it” and deliver results as a coup de grace at the end of the project, what tends to be delivered are sub-optimal solutions. In the worst case, they may fail to deliver anything useful at all.  

The vast majority of the data scientists I’ve worked with are very conscious of the need to involve their clients in the machine learning process and have worked hard to get business input to their projects. However, it’s sad to say that I have also seen more than one instance of deliberate attempts by data scientists to confuse normal people with tech speak or have avoided speaking to them all together. This is so that they can get on with the important mathsy stuff without having to deal with those awful dumb wits who actually have to run the organization on a day-to-day basis.  

A simple rule is that if a data scientist can’t explain to you what they have done and why, then they have failed in their task. They also need to give the business a clear understanding of what the benefits of their work are. As a business user, I have no interest in the fact that a predictive model is 95% accurate and this is 10% more discriminatory than the process it’s going to replace. What I want to know is how much money it’s going to make me, how many lives it’s going to save, how many less staff I’ll need to employ, or whatever. It’s a poor data scientist that can’t express the benefits of their solution in terms of the benefit it will provide to their client’s bottom line.  

However, it works both ways and it’s not fair to lay everything on the data scientists. It’s not an unreasonable ask that business users make an effort to gain a basic understanding of how a data scientist goes about the machine learning process. As projects progress there should be two-way exchanges of information, and regular meetings where preliminary findings and results, problems and issues are presented and discussed in a non-technical business focused way. This then then guides how the project is taken forward.  

With this in mind, I’m going to avoid going into the mathematics of various algorithms used for machine learning, such as those used to train neural networks or decide how the splits in decision trees are assigned. For those of you who are interested in the technical details, the most common algorithms used for machine learning are all pretty well documented (see appendix B for some recommended books and internet sites). Likewise, the implementation of these algorithms are available in commercial statistics packages that you can buy, or are freely available via open source software (e.g. R and Python code libraries). Therefore, you don’t need to know how to code up specific machine learning algorithms; you just need to know how to call the relevant function or procedure in your chosen software package. 

The machine learning process 

The first thing the data scientist needs to do is to quantify the business problem; i.e. to represent what the business is trying to achieve as a simple number or score. The sales director of a retail store may start a conversation with a data scientist with a statement such as:  

“We want a predictive model to identify our best customers.”  

So, the first question to ask is: 

“What do you mean by best?”  

To which the sales director responds: 

“Those customers that will make the biggest financial contribution to our business.” 

OK, that seems reasonable, but does “financial contribution” relate to gross sales or net profit? Are we talking about contribution per store visit, per click, or per unit time (week/month/year)? Are we looking at individual or household contribution when we talk about “customers”? and the list goes on. A data scientist needs to tease out a precise definition of what the business wants, and then express this in a way that can be represented by the scores generated by the model that they build.  

In this example, it may be that after some discussion with the marketing director it is agreed that the model will be designed to predict total gross spend for individuals per quarter year. Quarterly gross spend is selected because this definition aligns with the organizations reporting period, and total revenue (sum of spending) is the key performance indicator for the sales director.  

Individual rather than household spend is chosen because it is agreed that although household spend would theoretically be better, the organization’s customer databases are structured at an individual not household level. It would not be possible to deploy a model based on household spend within the bounds of the organization’s current IT infrastructure. Could the IT be upgraded to provide a household view? No, certainly not as part of this project because the business has not allocated any budget for IT changes this year. 

Given this information, the data scientist should determine that this is a regression type problem to predict the amount each individual customer will spend over a three month forecast horizon.  

In parallel to determining how to express the business objective quantitatively, a data scientist needs to undertake exploratory analysis to understand the organization’s data and IT assets, how they work and how they interact with each other and the wider business. This includes: 

What databases does the organization have?  

What is the purpose of each database, and what business processes make use of them? 

What do the databases contain? i.e. what data items and the format of those data items. For example, if it’s numeric or textual data. 

How is each database updated and maintained? Most organizations have a mix of “real time” customer databases that are updated as soon as something changes, and batch databases which are updated less frequently; i.e. overnight or at month end. 

What decision making systems are already in place? Will the model be implemented within an existing system, or will new functionality be required? 

·          What data does the organization currently use for decision making purposes? Even if this data feeds an antiquated manual process, it is likely that this data will be extremely valuable for machine learning purposes because the organization has already identified it as useful. 

In a perfect world, organizations have comprehensive documentation (metadata) that provides an inventory of its data assets in terms of the types of data it holds, how that data is formatted and where it comes from. However, in practice this sort of information is often patchy, incorrect or out of date. A lot of useful information is held in the heads of business users, who use it on a regular basis as part of their day jobs. There may be a data item called “Customer demographics 3” which contains letters A, B,….G. What on earth does that mean? It’s not documented anywhere, but Claire in operations knows that it matches the income grades they use. “A” means an annual income of under $20,000, “B” $20-35,000, and so on. 

Many organizations also maintain data that they no longer understand. Yet, they are afraid to purge it, on the off chance it’s something vital that a business critical process relies upon. Potential new data sources, both internal and external, should also be examined during the exploratory analysis phase, as these may enhance the predictive ability of any models which are developed.  

Overall, a good deal of effort is required to explore the universe from which data can be gathered and to decide what can potentially be used, and what cannot.  

Once a data scientist has a good understanding of what data an organization has and how it is structured, then they can move to Stage 3, and think about creating the development sample that is going to be used in the machine learning process.  

A very naïve approach to building predictive models for business is simply to throw every piece of information that an organization has into the machine learning process. In practice, much data is out-of-date, unstable or otherwise inappropriate. It should therefore be excluded from the development sample in case it degrades the performance of the machine learning process. 

Some typical reasons to exclude data from the machine learning process are:  

·          Out-of-date data. If the data is no longer relevant to today’s world, then don’t consider it. Data about how people used their cell phones in the time before smart phones existed is not going to be very useful in telling you about smart phone usage today. 

·          Not representative of the target population. The development sample should only contain cases that mirror the population to which the model will be applied. If a revenue model is being developed exclusively for online customers, then you should exclude in-store transactions if spending patterns are different for these two channels. Likewise, if you are developing a speech recognition system from sound samples, all samples should be speech related. If you have examples of barking dogs or traffic noise, then these need to be removed. 

·          Stability of data. Will the data used in the machine learning process be available when the model is applied? If a data item is not available at the point of implementation, then it should be excluded. 

·          Legal and ethical reasons. Do you want to use sensitive personal data such as race, gender and sexual orientation? This type of data can be very predictive, but it may be illegal to use it. If it is legal, then the use of such data may create reputational risk if it becomes known that you treat certain groups differently than others. If a discount strategy based on model scores results in you only offering discounts to straight men – that’s probably going to be controversial. 

·          Deterministic cases. If you have certain customers which you know with certainty how you are going to treat them, then you don’t need a predictive model for this. Including them in the development sample will only weaken the power of the model, as measured on the remainder of the population[\[32\]](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX). 

·          Inexplicability. A fundamental principle of machine learning is that you should be very cautious about building models using data which you don’t fully understand. This is particularly true for models that are subject to industry regulation or are strategically important to an organization’s success. If a data scientist presents you with a model using data that they can’t explain, then that’s a risk that you should be concerned about.  

If an organization has huge databases, then this may be problematic in terms of the computer resources required to analyze them as part of the machine learning process. It is not unusual for only a sample; say 1:10 or 1:100 cases to be selected for inclusion in the development sample. “Big Data Purists” may argue that you should analyze all available data because failing to do so may result in subtle patterns being missed, and hence sub-optimal models being created. In one sense they are right in that if you take a sample rather than using the full population the resulting model will not be as accurate. However, it’s very much a case of diminishing returns. For almost all practical business problems, the benefits of taking more than a few tens of thousands of cases is marginal. If you sample in an appropriate way[\[33\]](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX), then you’ll get 99% of the benefit from a model developed using 100,000 cases of one developed using 10 million. To put it another way, just because you have huge amounts of data does not necessarily mean that you need to invest in specialist hardware/software to be able to apply machine learning – you just need to be smart in how you do it and focus on the data that really matters. 

The fourth stage of the process is data preparation. This is required because the raw data may be badly formatted, contain errors or not provide the best possible representation of the data; i.e. a different representation will make it easier for the machine learning process to find the important patterns in the data. There are four main tasks that occur during data preparation: 

·          Creation of new data. Age is more predictive than Date of Birth for most types of problem. Therefore, age may need to be calculated if only Date of Birth is available. Likewise, if you have data about credit card transactions, it’s best to create summary variables representing average spend per transaction, number of transactions last month, time since last transaction, and so on. 

·          Data cleaning. Data may be missing or incorrect. A key purpose of data preparation is to identify where this type of data exists, and to either remove it (an exclusion) or reformat it; i.e. recode all incorrect data with a standard value. If dates of birth used to calculate age are in the future or impossibly far in the past, you may want to define a default value of say ‘-1’ for age, to represent these cases. 

·          Consolidation. It’s good practice to represent similar data in a similar way. If you have a data item called property type, where values of “D”, “Det” and “Detached” all mean the same thing; i.e. “Detached house”, then these should be consolidated into a single value which is used to represent all cases of Detached. 

·          Conversion to numeric. Machine learning algorithms like numeric data. “Yes”/”No”/”Maybe” would be converted in to 0/1/2 flags instead. For complex text or speech such as a twitter feed, then one approach is to include flags to indicate if certain key words feature or not, or to generate counts of the number of times certain words appears. 

Once a suitable data sample has been prepared then it’s time for data pre-processing and preliminary variable selection (Stage 5 of Figure 9). With data pre-processing, one is putting the data into a format that is going to be most amenable to the chosen machine learning algorithm.  

Pre-processing usually involves two processes: standardization and transformation. Standardization processes scale data so that everything has similar values. If you have two data items such as gross annual income and height in metres then one approach to standardization is to subtract the respective average and then divide by the range of values (or some other measure[\[34\]](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX)). In this way, both will be centered on zero, and have broadly similar ranges.  

# 11.Data Preprocessing With Machine Learning 

The first thing that we are going to take a look at here to help us get started with some of the things that we can do with machine learning is data preprocessing. You need to make sure that any data you are working with is in the right format before they are able to work with machine learning at all. Converting data to the right format so that you can do some work with machine learning is going to be known as data preprocessing.  

Now, it is going to depend on the type of data you would like to work with, but there are going to be a few steps that need to happen in order to help you see the preprocessing work well. These steps are important to work with because they will ensure the data comes in the right form to be used. The steps that you should focus on for this part will include: 

·          Getting the data set 

·          Importing your libraries 

·          Importing the dataset 

·          Handling any of the missing values 

·          Handling the categorical data 

·          Dividing the data into different training sets and test sets 

·          Scaling the data.  

Let’s take a closer look at each of these and how they can work together to prepare your data the proper way.  

Getting the data set 

Now, we need to take a bit of time to look over this set of data. When we do that, we start to notice that there is a lot of information about the age, gender, and the BMI of the patients at hand. This set of data is also going to come with an extra column that will show us whether or not the patients we are looking over are diabetic or not. You should also notice that the age and the BMI columns are going to be numerical, while the other two columns are going to be categorical in nature instead.  

Another distinction that we need to make here is going to be between the dependent and the independent variable. When we are looking these over, the variable whose value is predicted to come in as dependent and the variables that are used to make these predictions will become our independent variables. When we look at this kind of example, the diabetic column is going to be seen as the dependent variable because it will rely, at least a bit on the other columns there. Then we will notice that the other columns are going to be out independent options.  

Importing the libraries that you need 

Now that you have some of the data that you need to get started on this, you need to work on importing the library. Python automatically comes with some prebuilt libraries that are able to perform a variety of tasks. For the purpose of this book, we are going to use the Scikit Learn Library. To keep it simple, we are going to install three libraries that are the most essential for helping us do machine learning. These include numpy, matplotlib.pyplot, and pandas.  

First off is the numpy library. This is a good one to download because it can help you get some of those mathematical functions that are more complex done. Since machine learning does spend time in the mathematical field, it is worth your time to make sure that this particular library is in place.  

The next library that you will want to take a look at is going to be the matplotlib.pyplot library. This is another good one that can be used often because it helps with any of the charts that you will want to work with. Often, when you are looking through some of the data that is needed to work with machine learning, it is helpful to have this library present. It at least lets you have a good idea of the data points and where they fall on the charts.  

And we need to take some time to download the Pandas library. This one is important as well, and you will find that it is really easy to use. Many times a programmer is going to be able to use it in order to import and view any of the sets of data that they want to use with machine learning.  

If you want to import these libraries, you will either need to come up with a new notebook for Python in Jupyter, or you are able to use Spyder in order to open up a brand new file. The codes that we are going to focus on in this part of the guidebook are going to be useable with Spyder. To help you import these libraries, you need to work with the codes below 

import numpy as np 

import matplotlib.pyplot as plt 

import pandas as pd 

Importing the data that you need 

Once you have been able to download the three libraries that we have just talked about, it is now time to look at the steps that are needed in order to import the set of data that you would like to use in your chosen application. This is also going to give us a better look at why the pandas library is so important to use in this part of the process.  

The data set that we are going to use will show up in the Comma Separated Values, or CSV format. The pandas library will have inside of it the read\_csv function that is going to take us to the path to the SCV formatted set of data as the parameter and then will load up the set of data into the pandas data frame, which is basically going to be an object that stores the set of data in the form of rows and columns. To help us get this to happen, we need to use the code below:

Patient data = pd.read\_csv(“D:/Datasets/patients.csv”) 

The script above is going to help you to load up the data set for patients.csv in the dataset fold that you have it set. If you are using the Jupyter notebook, this is even easier to do. You would just use the following script to help you see what the data looks like: 

patient\_data.head() 

But, if you are working with the Spyder program, you would go over to your Variable explorer and then double click on patient\_data variable from the list of variables that show up. Once you click on the right variable, you will be able to see all the details of this dataset.  

When we reach this point in the process, you should then be able to see that the data frame that comes with pandas is going to look very similar to the matrix with zero-based index. Once you are able to load all of this up, the next step is to divide the set of data into a matrix of features and vector of dependent variables. The feature set is going to be able to hold all of the variables that you have that are considered independent.  

For example, the feature matrix for patients.csv data set is going to include the information that you place for age, BMI, and gender of the patient. In addition, the size that you see with your feature matrix is going to be equal to the number of independent variables by the number of records. For this example, our matrix is going to end up being three by twelve. This is because we have three independent variables and twelve patients with records we are going to look at.  

To help us get started with this one, we need to first go through and create the feature. You are able to provide it with any name that you would like, but the traditional method of doing this is going to be with the capital X. To help us have a better chance at reading the code, we will give it the name of features, and then use the script below to make it work the way that we want.  

features = patient\_data.iloc \[:,0:3\].values 

With the script that we used above, the iloc function of your data frame is used to help select all the rows as well as the first three columns from the patient\_data of the data frame. This iloc function is going to take on two parameters. The first is the range of rows to select, and then the second part is going to be the range of columns you want the program to select.  

If you would like to create your own label vector from here, you would use the following script to get it done: 

labels = patient\_data.iloc\[:3\].values 

Handling any missing values that show up 

If you stop now and look at the object that is labeled patient\_data, you will notice that there is a record that is missing at index 4 for the column of the BMI on that patient. To help us be able to handle it when values are missing, the easiest approach out be to find a way to remove the record that is missing a value. However, this record could also have some crucial information in it that we need to focus on, so you will sometimes want to keep it there.  

Another option that you can use to help deal with some of these missing values is to add in some kind of value or character that will be able to replace the value that is missing. Often we find that the best choice to replace that value with is either the mean or the median of all the other values that are found in that column. To help you handle the values that are missing when they come up, you just need to use the imputer class that is found in the library of sklearn.preprocceing. the script that you will need to make sure this happens is below 

from sklearn.preprocessing import Imputer 

imputer = Imputer(missing\_values=”Nan”, strategy=”mean”, axis =0) 

imputer = imputer.fit(features\[:,1:2\]) 

features\[:,1:2\] = imputer.transform(features\[:,1:2\]) 

With the script that we wrote above, the first line is in charge of importing the Imputer class from the right library. We then went on to create the object of the Imputer class. This is going to take on three parameters including axis, strategy, and missing\_value. In terms of the missing\_value parameter, we are specifying that this is the value that we want to be replaced. In our data set, the missing value is being shown by “nan”. The strategy parameter is going to specify the type of strategy that we want to use in order to fill in this missing value. You can also choose from most-frequent, median, and mean. And then the axis parameter is going to denote which axis we want to impute here 

Handling any of our categorical data 

Right now we know that the algorithms that we may use with machine learning are going to be based on concepts that are mathematical in many cases, and to work with these mathematics, we need to be able to work with numbers. Because of this kind of issue, it is going to become easier and more convenient for us to work in values that are categorical and then work on moving them to be numerical. When we look at the example that we are doing here, we see that there are two values that are seen as categorical and those are the gender and diabetic options. How are we able to turn Male and Female, and Yes and No into numerical values to make things easier? 

The good news is that with the sklearn.preprocessing library, there is the LabelEncorder class, the one that is going to take your categorical column and then give you the right numerical output to make sense out of it. The script that you can use for this one includes: 

from sklearn.preprocessing import LabelEncoder 

labelencorder\_features = LabelEncoder)\_ 

features\[:,2\] =labelencoder\_features.fit\_transform(features\[:,2\]) 

Just like what we did with the Imputer class, the LabelEncorder class is going to have a fit\_transform method, which is just a combination of the transform and the fit methods. The class is going to be able to take the categorical column that you have as the input and then will return the right numeric values to help you out.  

In addition, you can always take the labels vector and then convert it to a set of numeric values as follows: 

labels = labelencoder\_features.fit\_transform(labels) 

Your training sets vs. your testing sets 

The next thing that we need to take a look at is the training sets and the test sets. These are going to be two very important things when it comes to the work that you are doing in machine learning, Being able to separate out the values that you have in a smart manner for this to work is going to make the biggest difference overall.  

This splitting up of the test and the training set is going to be done to make sure that any algorithm that you use for machine learning doesn’t end up overfitting and trying too hard, messing up the data that you get. When we talk about the idea of overfitting, we are looking at the tendency that machine learning is going to do well with the results it gives on the training data, but then it ends up giving poor results when you get to the test data.  

A good model that you can rely on when you work in machine learning is one that is able to give you some good results with both of these, with the training data and the test data. With this, we are able to say that the model we picked as correctly learned all of the underlying assumptions from our set of data, and then that we are able to accurately use it to make the decisions that we need out of any new set of data that we decide to use.  

To get a better idea of how this is going to work, Let’s look at the script that we use below. This script is going to help us divide up the data into the 75 percent train size, and the rest is going to be the test size.  

from sklearn.model\_selection import train\_test\_split 

train\_features, test\_features, train\_labels, test\_labels = train\_test\_split (features, labels, test\_size = 0.25, random\_state = 0) 

When you execute this script above, you are going to see the train\_features variable is going to contain the matrix of 9 features (because this is the 75 percent of 12) while the train\_labels is going to contain the labels that correspond to this. However, with the test-features, you are going to have the remaining three features and the test\_label will have the corresponding labels.  

Scaling the data we have 

Now we are to the final thing that we need to look at when we get to this part of the process. We need to look at the steps that are needed in order to scale any of the data we have when we place it into our machine learning algorithm. It is important to know all about scaling because there are going to be some sets of data that will show up a big difference between the values that come with it.  

For example, if we decided to add in a new column for the number of red blood cells of patients in this, then it is likely that the numbers are going to be hundreds of thousands (unless the patient is really sick), while it is not likely the age column would even get to 100. Many of the models that you can use with machine learning are going to use what is known as the Euclidean distance to help us find the distance that occurs in the points of data you are looking at.  

The good news is that the sklearn.preprocessing library is going to contain the class known as StandardScaler that you can use in order to implement the standardization features. Like with other preprocessing classes, it will also contain the fit-transform that we talked about before and it will take a data set that you provide it as the input, and then output a scaled data set. The following script will make this happen for you.  

from sklearn.preprocessing import StandardScaler 

feature\_scaler = StandardScaler() 

train\_features = feature\_scaler.fit\_transform(train\_features) 

test\_features = feature\_scaler.transform(test\_features) 

one thing to note is that there isn’t really a need for you to scale labels on any of your classification problems. For regression problems, we will take a look at how to scale labels for a regression section.  

And that is all there is to it. You need to go through some of these steps along the way to make sure that you are preprocessing the information, and that it is ready to go with the work. Your algorithms are going to be more accurate and will work out much better if you are able to add in these preprocessing steps to the mix. They will ensure that you are able to get the best results because the data is prepared in the manner that it should be.  

# 12.Machine Learning and Robotics  

First, we need to define a robot. They are machines, often programmable by a computer, that are able to carry out a series of complex actions without intervention. A robot can have its controls systems embedded or be controlled by an external device. In popular literature and film, many robots are designed to look like people, but in fact, they are usually designed to perform a task and that requirement determines how they appear. 

Robots have been with us for almost as long as computers. George Devol invented the first digitally operated and programmable one in 1954, called Unimate. In 1961, General Motors bought it to use for lifting hot metal die castings. And like computers, robots have changed our society. Their strength, agility, and ability to continue to perfectly execute the same repetitive tasks have proved an enormous benefit. And while they did cause some serious disruption to the manufacturing industries, putting many people out of work, their ascension in our societies has provided far more employment opportunities than they have taken. 

Robots in current use can be broken down into several categories: 

## Industrial Robots/Service Robots 

These robots are probably familiar. You have likely seen them on the television or streaming video of automated factories. They usually consist of an “arm” with one or more joints, which ends with a gripper or manipulating device. They first took hold in automobile factories. They are fixed in one location and are unable to move about. Industrial robots will be found in manufacturing and industrial locations. Service robots are basically the same in design as industrial robots but are found outside of manufacturing concerns. 

## Educational Robots 

These are robots used as teacher aids or for educational purposes on their own. As early as the 1980s, robots were introduced in classrooms with the turtles, which were used in classrooms where students could train them using the Lego programming language. There are also robot kits available for purchase like the Lego Mindstorm. 

## Modular Robots 

Modular robots are consisted of several independent units that work together. They can be identical or have one or more variation in design. Modular robots are able to attach together to form shapes that allow them to perform tasks. The programming of modular robotic systems is of course, more complex than a single robot, but ongoing research in many universities and corporate settings is proving that this design approach is superior to single large robots for many types of applications. When combined with Swarm Intelligence (see below), modular robots are proving quite adept at creative problem-solving. 

## Collaborative Robots 

Collaborative robots are designed to work with human beings. They are mostly industrial robots that include safety features to ensure they do not harm anyone as they go about their assigned tasks. An excellent example of this kind of collaborative robot is Baxter. Introduced in 2012, Baxter is an industrial robot designed to be programmed to accomplish simple tasks but is able to sense when it comes into contact with a human being and stops moving. 

Of course, all the examples above do not require any artificial intelligence. When robots are coupled with machine learning, researchers use the term “Robotic Learning”. This field has a contemporary impact in at least four important areas: 

Vision 

Machine Learning has allowed robots to visually sense their environment and to make sense of what they are seeing. New items can be understood and classified without the need to program into the robot ahead of time what it is looking at. 

Grasping 

Coupled with vision, Machine Learning allows robots to manipulate items in their environment that they have never seen before. In the past, in an industrial factory, each time a robot was expected to interact with a different-shaped object, it would have to be programmed to know how to manipulate this new object before it could be put to work. With Machine Learning, the robot comes equipped with the ability to navigate new item shapes and sizes automatically. 

Motion Control 

With the aid of Machine Learning, robots are able to move about their environments and avoid obstacles in order to continue their assigned tasks. 

Data 

Robots are now able to understand patterns in data, both physical and logistical, and act accordingly on those patterns. 

## Example of Industrial Robots and Machine Learning  

One example of the benefit of applying Machine Learning to robots is of an industrial robot which receives boxes of frozen food along a conveyor. Because it is frozen, these boxes often have frost, sometimes quite a lot of frost. This actually changes the shape of the box randomly. Thus, a traditionally-trained robot with very little tolerance for these shape changes would fail to grasp the boxes correctly. With Machine Learning algorithms, the robot is now able to adapt to different shapes, random as they are and in real time, and successfully grasp the boxes. 

Another industrial example includes a factory with over 90,000 different parts. It would not be possible to teach a robot how to manipulate these many items. With Machine Learning, the robot is able to be fed images of new parts it will be dealing with and it can determine its own method to manipulate them. 

In 2019, there will be an estimated million robots in service on the planet. That’s up a million from 2015. As more and more robots are combined with Machine Learning algorithms, this number is sure to explode. 

# 13.How AI Is Revolutionizing Industry 

Artificial intelligence is arguably the single factor that is most changing industry today and is likely to continue to do so in the future. Many thinkML of AI in terms of the commercially available products that they may use in their daily life. Siri and Alexa, in addition to smart home AI and other IoT devices that use AI, have become ubiquitous. They are everywhere. But artificial intelligence is changing industry in ways that are invisible to many men and women. These are things happening behind the scenes. 

## Agriculture 

Agriculture is an industry that often falls under the radar in developed nations because it generally represents such a small percentage of GDP. Even in countries where agricultural products are major exports, agriculture is often not being perceived as being as significant as computer technology, aviation, heavy industry, or other industries that are more conspicuous. But agriculture is important, and AI has been changing this industry in dramatic ways. 

Three keys ways in which AI is changing agriculture include AI use in predictive analytics, crop and machinery monitoring, and agricultural robots. Agriculture robots powered by AI can actually farm the land in ways similar (if not superior) to human workers of the past. AI can also be involved in analyzing farm operation data, much as it is able to do in other businesses. This merely requires that AI is provided with the data or linked to the machines that generate the data. Finally, AI can use drones and other agents (including computer programs) to monitor both crops and machinery in ways that would not have been possible before. 

## Education 

AI applications in education are very numerous. Although education is often thought of as an area that perhaps requires a human finesse or emotional intelligence, many educators have jumped on the AI bandwagon as they recognize how AI can aid them in their educator tasks. Ways that AI is changing education include: distance learning, chatbots, school recruitment and outreach, computers using AI in the classroom or dorm room, shifting role of educators in schools based on AI assuming roles, feedback for both educators and students, artificial intelligence tutors for students, AI agents for grading, tailoring of educational software to student needs. 

The truth is, because artificial intelligence can use whatever data you give it, the possibilities of AI in education are almost endless. For example, AI programs may be able to review student data and make recommendations on areas in which students need improvement based on a more nuanced understanding of the data than the teachers have.AI can even recommend changes in instruction based on student performance in certain areas. The sky is really the limit for AI in education. 

## Entertainment 

Machine learning and experimental APIs have found a place in the entertainment industry. As with other areas of business, a big area for entertainment to make use of AI is in predictive analytics. Predictive analytics in the context of entertainment can mean many things, but this would include predicting consumer behavior in order to suggest certain types of products, like films, digital programming, or TV shows. AI can also use to market products directly to customers using the web or app-based utilities. AI of this type tracks user data to make tailored recommendations. 

AI can also be involved in preparing products for release using deep learning. For example, AI can be involved in video editing, including syncing audio and video, AI can be involved in various aspects of CGI, and AI can be involved in image analysis for entertainment purposes. As we have seen, machine learning can play a powerful role in language processing and translation, and this can be very relevant in the entertainment industry. 

## Journalism 

Natural language processing capabilities of machines mean that artificial intelligence applications in journalism are potentially endless. Beyond functions like translation, transcription, and speech segmentation (part of transcription), AI can also be involved in generating original content, including full-length articles. Some YouTubers have experimented with having their dialogues written by AI, and although this is often undertaken as a joke, many times the AI generated content is indistinguishable from that written by a human being. 

Much of the AI advancement in journalism involves automation of routine tasks. In fact, automation is one of the key points that business can keep in mind when imaging how to integrate AI into their business. One way that AI can help to improve journalistic function by automation is by collecting data from multiple sources in order to create content. AI can do this in seconds, whereas it might take hours for a human to do the same thing. AI can also be involved in marketing journalistic content after it is created. 

## Transportation 

It goes without saying that the greatest way that AI is revolutionizing transportation is with the invention of the self-driving car. Although self-driving automobiles have been in development since the 1970s, it has only been recently that advancements in image analysis, machine learning, and semantic segmentation have allowed self-driving to be a safe endeavor that human beings can expect to see in the near future. Indeed, navigation systems powered by AI are already in place both in automobiles and in aviation. 

The tasks that AI has in self-driving involves deep learning. AI in self-driving cars needs to be engaged in multiple complex algorithms at the same time, including recognizing signs in the environment, recognizing markers on the road, awareness of other vehicles and pedestrians, using location and weather data to guide actions, responding to input from a human driver, and physically moving the automobile. The fact that self-driving cars are being developed by companies like Tesla and others that can actually do this represents one of the great achievements of modern-day machine learning. 

# Conclusion

Thanks for making it through to the end, let’s hope it was informative and able to provide you with all of the tools you need to achieve your goals whatever they may be. 

The next step is to get started with using machine learning to achieve your goals. There are so many cool things that you are able to do when you bring machine learning into the mix that it is definitely worth your time to give it a try. While conventional programming can help you to get a good start and can make a lot of great programs along the way, there is nothing that compares to what you can do when you learn how to work on machine learning. 

This guidebook took some time to explore the different parts that come with machine learning. We discussed what this process was all about along with the building blocks that help you to get started and the ways that statistics make it easier to work with machine learning. Then we moved on to some of the different learning techniques that are found in machine learning, including supervised machine learning, unsupervised machine learning, and reinforcement learning. Understanding how to work with each of these and getting the right algorithm for your needs is so crucial to the success of your program.