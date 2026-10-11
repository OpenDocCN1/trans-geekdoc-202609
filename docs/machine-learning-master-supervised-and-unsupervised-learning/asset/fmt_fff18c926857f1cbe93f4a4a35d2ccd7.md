
# Machine Learning Process

## Step 2: Preparing the Data

After the training data is gathered, we move on to the next step of machine learning: data preparation, where the data is loaded into a suitable place, and then prepared for use in machine learning training. Here, the data is first put all together, and then the order is randomized as the order of data should not affect what is learned.

In this step, we wrangle the data collected in Step 1 and prepare it for training. We can clean the data by removing duplicates, correct errors, deal with missing values, data type conversions, and so on. We can also do the visualization of the data, as this will help us to see if there are any relevant relationships between the different attributes, how we can take their advantage, and as well as, a show if there are any data imbalances present.

Another major component of data preparation is breaking down the data sets into 2 parts. The larger part (~80%) would be used for training the model while the smaller part (~20%) is used for the evaluation of the trained model’s performance. This is important because using the same data sets for both training and evaluation would not give a fair assessment of the model’s performance in real-world scenarios.

## Step 3: Choosing a Model

The selection of the model type is our next course of action once we are done with the data-centric steps. There are various existing models developed by data scientists that can be used for different purposes. Different classes of models are good at modeling the underlying patterns of different types of datasets. These models are designed with different goals in mind. For instance, some models are more suited to dealing with texts while another model may be better equipped to handle images.

## Step 4: Training

At the heart of the machine learning process is the training of the model. The bulk of the work is done at this stage. Training requires patience and experimentation. It is also useful to know the field where the model would be implemented.

Training can prove to be highly rewarding if the model starts to succeed in its role. The training process involves initializing some random values for say `X` and `Y` of our model, predict the output with those values, then compare it with the model's prediction and then adjust the values so that they match the predictions that were made previously.

This process then repeats, and each cycle of updating is called one training step.

It is comparable to when a child learns to ride a bicycle. Initially, they may have multiple falls but, after a while, they develop a better grasp of the process and can react better to different situations while riding the bicycle.

## Step 5: Evaluation

With the model trained, it needs to be tested to see if it would operate well in real-world situations. That is why the part of the data set created for evaluation is used to check the model’s proficiency. This puts the model in a scenario where it encounters situations that were not a part of its training.

Evaluation becomes highly important when it comes to commercial applications. Evaluation allows data scientists to check whether the goals they set out to achieve were met or not. If the results are not satisfactory then the prior steps need to be revisited so that the root cause behind the model’s underperformance can be identified and, subsequently, rectified. If the evaluation is not done properly then the model may not excel at fulfilling its desired commercial purpose. This could mean that the company that designed and sold the model may lose their goodwill with the client. It could also mean damage to the company’s reputation as future clients may become hesitant when it comes to trusting the company’s acumen regarding machine learning models. Therefore, evaluation of the model is essential for avoiding the aforementioned ill-effects.

## Step 6: Hyperparameter Tuning

Once the evaluation is over, any further improvement in our training can be possible by tuning the parameters. There were a few parameters that were implicitly assumed when the training was done. Another parameter included is the learning rate that defines how far the line is shifted during each step, based on the information from the previous training step. These values play a role in the accuracy of the training model and how long the training will take.

Naturally, the question arises that why we need hyperparameter tuning in the first place when our model is achieving its targets? This can be answered by looking at the competitive nature of machine learning-based service providers. Clients can choose from multiple options when they seek a machine learning model to solve their respective problems. However, they are more likely to be enticed by the one which produces the most accurate results. That is why for ensuring the commercial success of a machine learning model, hyperparameter tuning is a necessary step.

## Step 7: Prediction

The final step of the machine learning process is prediction. This is the stage where we consider the model to be ready for practical applications.

This is the point where the value of machine learning is realized. Here we can finally use our model to predict the outcome of what we want.

## Applications of Machine Learning

Machine learning helps to improve business decisions, boost productivity, detect diseases, forecast the weather, and much more. A machine learns automatically from the inputs. Some of the best machine learning applications are mentioned as follows.

### Social Media Features

Social media platforms like Facebook, Instagram, LinkedIn, and so on, use machine learning algorithms for users. Social media create some attractive and excellent features using machine learning. For example, Facebook notices and records the activities, chats, likes, comments, and the time spent by users on specific kinds of posts, videos, and so on. Machine learning learns from the user’s activities & experiences and makes friends and page suggestions for the user’s profile.

Let us take another example, when a user uploads a picture of him with a friend and Facebook instantly recognizes that friend. Facebook checks the poses and projections in the picture, notice the unique features, and then match them with the people in the user’s friend list and tag that friend automatically.

### Product Recommendations

Product recommendation is used in almost every e-commerce website today. This is a very advanced application of machine learning techniques. Using machine learning, e-commerce websites track the user’s behavior based on previous purchases, searching patterns, cart history, and so on. Based on this tracking, the e-commerce websites recommend the product to users that somehow matches the user’s taste.

### Image & Speech Recognition

Image recognition is one of the most common applications of machine learning. Image processing is used to identify objects, persons, places, digital images, and so on in an image. This technique is used for further analysis, such as pattern recognition, character recognition, face detection, or face recognition. Facebook provides us with a feature of auto friend tagging suggestions. Whenever a user uploads a photo with his Facebook friends, then the user automatically gets a tagging suggestion with the name of his friends.

Speech recognition is the translation of spoken words into text. It is also known as automatic speech recognition (ASR) or speech-to-text. Google and Alexa are using speech recognition technology to follow voice instructions.
