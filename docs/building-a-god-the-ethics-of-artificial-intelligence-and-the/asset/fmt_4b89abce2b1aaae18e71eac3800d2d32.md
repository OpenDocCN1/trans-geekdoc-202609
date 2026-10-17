
It is interesting to see the historical advancements in the process of evolution itself. It has gradually moved from Darwinian natural selection (where species were selected to survive or perish based on their adaptive abilities to changing environments), to a more rapid rate of artificial selection (where humans intervened in the process to hurry things up by selecting the types of qualities they wanted in plants and animals), to the current mechanized process of Lamarckian evolution I call “technoselection” (where the machines themselves will choose what qualities they wish to transfer to the next generations). As mentioned earlier, my colleagues (Bullock and Mckernon) and I have written about this process elsewhere[^(67)](#Notes.xhtml#ch01.ftn.0078) and are concerned about how our species intends to plan for this eventuality. For, if Moravec’s prediction for humanity is correct, and I. J. Good’s prediction of an “intelligence explosion” is true, and John von Neumann’s prediction of a “technological singularity” is true, then at some point in the not-too-distant future the process of technoselection will potentially make us humans quaint and unnecessary.

> Moravec was probably better known for his opinion that robots would overtake humans in the near future. He estimated that computer intelligence would equal that of humans by 2040 and that machines would far surpass human intellect in the years thereafter. Moravec also argued that biological humans would eventually be rendered extinct. Although he believed there would be ways for human minds to survive in this future, he posited that human bodies would no longer be competitive from an evolutionary perspective.[^(68)](#Notes.xhtml#ch01.ftn.0079)

As mentioned earlier, one of the recurring themes throughout this book and deeply considered within the AI risk fields is the notion of “time lines.” When, exactly, will artificial general intelligence equal and surpass that of humans? Later in the book, you will see a chart[^(69)](#Notes.xhtml#ch01.ftn.0080) representing the various predictions given by forecasters, superforecasters, and professionals within the field. It is interesting to note Moravec’s prediction from the 1980s is now less than twenty years away. To quote Sam Harris:

> No one seems to notice that referencing the time horizon is a total *non sequitur*. If intelligence is just a matter of information processing, and we continue to improve our machines, we will produce some form of super-intelligence. And we have no idea how long it will take us to create the conditions to do that safely… 50 years is not that much time to meet one of the greatest challenges our species will ever face. We seem to be failing to have an appropriate emotional response to what we have every reason to believe is coming.[^(70)](#Notes.xhtml#ch01.ftn.0081)

In other words, you’d think if we knew the potential for disaster was this close, we’d be doing something about it. Well, our collective AI safety communities are certainly trying; but we are few in number—and we need your help. The question is this: Will our collective efforts—yours, mine, and the world’ s—work? It is for this very reason that this book has been written.

#### ***Support Vector Machines (SVMs)***

By the 1990s, neural networks and machine learning were developing more and more sophisticated algorithms. Advances in machine learning, particularly in supervised learning and statistical methods, marked the 1990s. Support vector machines (SVMs) and decision trees gained popularity. SVMs are a class of supervised machine-learning algorithms that can be used for classification or regression tasks. SVMs are particularly well suited for tasks where the goal is to separate data points into different classes or groups. They were introduced by Vladimir Vapnik and his colleagues and involve several key components such as linear separation (i.e., separating data into different classes into “hyperplanes” to better identify the margins between two classes). The margins compose the distance between the hyperplane and the nearest data point from either class. The SVM then aims to maximize this margin for classification. Support vectors are the data points that are closest to the hyperplane and play a crucial role in defining the optimal hyperplane. These are the instances that, if removed or changed, could alter the position of the hyperplane. SVMs have been widely used in various applications, including image classification, text categorization, and bioinformatics. Their ability to handle both linear and nonlinear relationships, along with an emphasis on maximizing margins, makes them a powerful tool in the machine-learning toolkit.

Here’s how an SVM would work for a binary classification task using a hypothetical scenario. The process involves training the SVM on historical data and then making predictions on new, unseen data. Here’s a step-by-step explanation:

##### HYPOTHETICAL SCENARIO

**Task:** Binary classification to predict whether a given e-mail is spam (positive class) or not spam (negative class).

*Steps*

1.  **Data Collection**

    Collect a dataset of labeled e-mails where each e-mail is labeled as spam or not spam based on certain features (e.g., word frequency, presence of certain keywords).

2.  **Data Preprocessing**

    Preprocess the data, extracting relevant features from the e-mails and encoding categorical variables. Split the dataset into training and testing sets.

3.  **Training the SVM**

    Use the training set to train the SVM. During training, the SVM learns the optimal hyperplane that separates the spam and non-spam e-mails, maximizing the margin between the two classes.

4.  **Feature Extraction for Real-Time Data**

    For real-time data, apply the same feature extraction process (e.g., term frequency–inverse document frequency \[TF-IDF\], which retrieves information by quantifying the importance or relevance of a string of words or phrases within a document) used during training to convert the incoming e-mail features into a format suitable for the SVM.

5.  **Prediction in Real Time**

    Use the trained SVM model to predict whether the new e-mail is spam or not. The prediction variable now contains the SVM’s prediction for the new e-mail (1 for spam, 0 for not spam).

Through marginal comparisons and categorizations, the SVM has become an extremely powerful and productive tool for machine learning (ML).

#### ***Decision Trees***

Decision trees are a popular machine-learning algorithm used for both classification and regression tasks in artificial intelligence. Decision trees represent a flowchart-like structure in which each internal node represents a decision based on a particular feature; each branch represents the outcome of the decision, and each leaf node represents the final prediction or classification. These structures make it easy to visualize and understand how decisions are made within the model.

[Figure 1.5](#Chapter01.xhtml#fig1_5) is an example of a decision tree (from Wikicommons) pondering the question of whether or not to upload an image from the internet.

You can see how the process works not only within ML systems, but also in our own decision-making situations.

![fig\_42\_1.jpg](Images/chpt_fig_005.jpg)

Figure 1.5. Decision tree. *Wikimedia Commons.*
