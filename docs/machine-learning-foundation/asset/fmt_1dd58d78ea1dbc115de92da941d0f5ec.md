
### Step Five: Inference (Use the Model)

As you inspect the different clusters found when `k=19`, you find a surprisingly large cluster of books. Here's an example from fictionalized cluster #7.

![](Images/image00102.jpeg)

As you inspect the preceding table, you can see that most of these text snippets are indicating that the characters are in some kind of long-distance relationship. You see a few other self-consistent clusters and feel you now have enough useful data to begin writing an article on unexpected modern romance microgenres.

#### Terminology

*   **Bag of words**: A technique used to extract features from the text. It counts how many times a word appears in a document (corpus), and then transforms that information into a dataset.
*   **Data vectorization**: A process that converts non-numeric data into a numerical format so that it can be used by a machine learning model.
*   **Silhouette coefficient**: A score from -1 to 1 describing the clusters found during modeling. A score near zero indicates overlapping clusters, and scores less than zero indicate data points assigned to incorrect clusters. A score approaching 1 indicates successful identification of discrete non-overlapping clusters.
*   **Stop words**: A list of words removed by natural language processing tools when building your dataset. There is no single universal list of stop words used by all-natural language processing tools.

#### Additional reading

Machine Learning Mastery is a great resource for finding examples of machine learning projects.

The *How to Develop a Deep Learning Bag-of-Words Model for Sentiment Analysis (Text Classification)* blog post provides an example using a bag of words–based approach pair with a deep learning model.

## Example Three: Spill Detection from Video

In the previous two examples, we used classical methods like linear models and k-means to solve machine learning tasks. In this example, we’ll use a more modern model type.

> **Note**: This example uses a neural network. The algorithm for how a neural network works is beyond the scope of this lesson. However, there is still value in seeing how machine learning applies in this case.

### Step One: Defining the Problem

Imagine you run a company that offers specialized on-site janitorial services. A client, an industrial chemical plant, requires a fast response for spills and other health hazards. You realize if you could automatically detect spills using the plant's surveillance system, you could mobilize your janitorial team faster.

Machine learning could be a valuable tool to solve this problem.

![](Images/image00103.jpeg)

### Step Two: Model Training (and selection)

This task is a supervised classification task, as shown in the following image. As shown in the image above, your goal will be to predict if each image belongs to one of the following classes:

*   Contains spill
*   Does not contain spill

![](Images/image00104.jpeg)

#### Step Two: Building a Dataset

*   **Collecting**
    *   Using historical data, as well as safely staged spills, you quickly build a collection of images that contain both spills and non-spills in multiple lighting conditions and environments.
*   **Exploring and cleaning**
    *   You go through all the photos to ensure the spill is clearly in the shot. There are Python tools and other techniques available to improve image quality, which you can use later if you determine a need to iterate.
*   **Data vectorization (converting to numbers)**
    *   Many models require numerical data, so all your image data needs to be transformed into a numerical format. Python tools can help you do this automatically.
    *   In the following image, you can see how each pixel in the image on the left can be represented in the image on the right by a number between 0 and 1, with 0 being completely black and 1 being completely white.

![](Images/image00105.jpeg)

*   **Split the data**
    *   You split your image data into a training dataset and a test dataset.

### Step Three: Model Training

Traditionally, solving this problem would require hand-engineering features on top of the underlying pixels (for example, locations of prominent edges and corners in the image), and then training a model on these features.

Today, deep neural networks are the most common tool used for solving this kind of problem. Many deep neural network models are structured to learn the features on top of the underlying pixels so you don’t have to learn them. You’ll have a chance to take a deeper look at this in the next lesson, so we’ll keep things high-level for now.

#### CNN (convolutional neural network)

Neural networks are beyond the scope of this lesson, but you can think of them as a collection of very simple models connected together. These simple models are called neurons, and the connections between these models are trainable model parameters called weights.

Convolutional neural networks are a special type of neural network particularly good at processing images.

### Step Four: Model Evaluation

As you saw in the last example, there are many different statistical metrics you can use to evaluate your model. As you gain more experience in machine learning, you will learn how to research which metrics can help you evaluate your model most effectively. Here's a list of common metrics:

| Accuracy | False positive rate | Precision |
| :--- | :--- | :--- |
| Confusion matrix | False negative rate | Recall |
| F1 Score | Log Loss | ROC curve |
|  | Negative predictive value | Specificity |

In cases such as this, accuracy might not be the best evaluation mechanism.

Why not? You realize the model will see the 'Does not contain spill' class almost all the time, so any model that just predicts “no-spill” most of the time will seem pretty accurate.

What you really care about is an evaluation tool that rarely misses a real spill.

After doing some internet sleuthing, you realize this is a common problem and that Precision and Recall will be effective. You can think of precision as answering the question, "Of all predictions of a spill, how many were right?" and recall as answering the question, "Of all actual spills, how many did we detect?"

Manual evaluation plays an important role. You are unsure if your staged spills are sufficiently realistic compared to actual spills. To get a better sense how well your model performs with actual spills, you find additional examples from historical records. This allows you to confirm that your model is performing satisfactorily.

### Step Five: Model Inference

The model can be deployed on a system that enables you to run machine learning workloads such as `AWS Panorama`.

Thankfully, most of the time, the results will be from the class 'Does not contain spill'.

![](Images/image00106.jpeg)

But, when the class 'Contains spill' is detected, a simple paging system could alert the team to respond.

![](Images/image00107.jpeg)

#### Terminology

**Convolutional neural networks (CNN)** are a special type of neural network particularly good at processing images.

**Neural networks**: a collection of very simple models connected together.

*   These simple models are called neurons
*   The connections between these models are trainable model parameters called weights.

#### Additional reading

As you continue your machine learning journey, you will start to recognize problems that are excellent candidates for machine learning.

The AWS Machine Learning Blog is a great resource for finding more examples of machine learning projects.

*   In the *Protecting people from hazardous areas through virtual boundaries with Computer Vision* blog post, you can see a more detailed example of the deep learning process described in this lesson.

# Lesson Review

Congratulations on making it through the lesson. Let's review what you learning
