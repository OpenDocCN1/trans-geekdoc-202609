
# Machine Learning Chapter 1: Machine Learning, iOS & You

This is where transfer learning can help. In fact, no matter what sort of problem you're trying to solve with machine learning, transfer learning is the best way to get about 99% of the time. With transfer learning, you can reap the benefits of the hard work that other people have already done. It's the smart thing to do!

When a deep-learning model is trained, it learns to identify features in the training images that are useful for classifying these images. Core ML comes with a number of ready-to-use models that detect thousands of features and understand 1,000 different classes of objects. Training one of these large models from scratch requires a very large dataset, a huge amount of computation and can cost big.

Most of these freely available models are trained on a wide variety of photographs of humans, animals and everyday objects. The majority of time is spent on learning how to detect the best features from these photos. The features such as model has already learned — edges, corners, patches of color and the relationships between these shapes — are also useful for classifying your own data into the classes you care about, especially if your training examples are similar in nature to the type of data that model has already been trained.

So it would be a bit of a waste if you had to train your model from scratch to learn the exact same features. Instead, to create a model for your own dataset, you can take an existing pre-trained model and customize it for your data. This is called transfer learning, because you transfer the knowledge from the existing model into your own model.

In practice, you'll use the existing pre-trained model to extract features from your own data, and then you only train the final classification layer of the model so that it learns to make predictions from the extracted features — but this time for your own class labels.

![](img/5720be5c3cca252e12448e68d25607b5_35_0.png)

Transfer learning has the huge advantage that it is much faster than training the whole model from scratch, but your dataset can now be much smaller. Instead of millions of images, you now only need a few thousand or even a few hundred.

Machine Learning

Chapter 1: Machine Learning, iOS & You

Apple provides two tools that transfer learning: Create ML and Turi Create. But this is such a useful technique that you can find transfer learning tools for the most popular machine-learning tasks, like image classification or sentiment analysis. Sometimes it's as easy as drag-and-dropping your data; at most, you write just a few lines of code to read in and structure your data.

## Can mobile devices really do machine learning?

A trained model might be hundreds of MB in size, and inference typically performs billions of computations, which is why inference often happens on a server with fast processors and lots of memory. For example, Siri needs an internet connection to process your voice commands — your speech is sent to an Apple server that analyzes its meaning, then sends back a relevant response.

This book is about doing state-of-the-art machine learning on mobile, so we'd like to do as much on the device as possible and avoid having to use a server. The good news: Inference on iOS devices works well thanks to core technologies like Metal and Accelerate.

The benefits of on-device inference:

- Faster response times: It's more responsive than sending HTTP requests, doing real-time inference is possible, making for a better user experience.
- It's also good for user privacy: The user's data isn't sent off to a backend server for processing, and it stays on the device.
- It's cheaper since the developer doesn't need to pay for servers and electricity: The user pays for using battery power. Of course, you don't want to abuse this privilege, which it's important to make sure your models run as efficiently as possible. We'll explain, in this book, how to optimize machine-learning models for mobile.

What about on-device training? The bad news: Mobile devices still have important limitations. Training a machine-learning model takes a lot of processing power and, even for small models, simply is out of reach of most mobile devices at this point. That said, updating a previously trained model with new data from the user, such as a predictive keyboard that learns as you type (also known as "online training"), is certainly possible today provided that the model is small enough.

![](img/5720be5c3cca252e12448e68d25607b5_36_0.png)

Note: While Core ML 3 allows for a limited kind of training on the device, it is not intended for training models from scratch, only to fine-tune a model on the user's data. The current edition of this book focuses on making predictions using a model that was trained offline, and it explains how to train those models on your Mac or a cloud service.

## Why not in the cloud?

Companies such as Amazon, Google and Microsoft provide cloud-based services for doing machine learning, and there are a lot of smaller players as well. Some of these just provide raw computing power (you rent servers from them). Others provide complete APIs wherein you don't not to concern yourself with the details of machine learning all — you just send your data to their API and it returns the results a few seconds later.

There are a lot of benefits to using these cloud services: 1) You don't need to know anything about machine learning — so you don't need to read the rest of this book; 2) Using it is as easy as sending an HTTP request; and 3) Other people will take care of running and maintaining the servers.

However, there are also downs: 1) You're a canned service that is often not tailored to your own data; 2) If your app needs to do machine learning in real-time (such as on a video), then sending HTTP requests is going to be too slow; 3) Convenience has a price: you have to pay for using these services, and once you've chosen one, it's hard to migrate your app away from them.

In this book, we don't focus on using cloud services. They can be a great solution for many apps — especially when you don't need real-time predictions — but mobile developers we feel that doing machine learning on the device, also known as edge computing, is just more exciting.

## Frameworks, tools and APIs

It may seem like using machine learning is going to be a pain in the backside. Well, not necessarily... Every technology you work with, machine learning has levels of abstraction — the amount of difficulty and effort depends on which level you need to work at.

### Apple's task-specific frameworks

The highest level of abstraction is the task level. This is the easiest to grasp — it maps directly to what you want to do. Apple and the other major players provide task-focused toolkits for tasks like image or text classification.

As Apple's web page says: You don't have to be a machine learning expert!

Apple provides several Swift frameworks for doing specific-learning tasks:

- Vision: Detect faces and landmarks, rectangles and bars in images; track objects across video; classify cats/dogs and many other types of objects; and much more. Vision also makes it easier to use Core ML models, taking care of formatting the input correctly.
- Natural Language: Analyze to identify the language, part of speech, as well as specific people, places or organizations.
- SoundAnalysis: Analyze and classify audio waveforms.
- Speech: Convert speech to text, and optionally retrieve answers using Apple's servers or an on-device speech recognizer. Apple sets limits on audio duration and daily number of requests.
- SiriKit: Handle requests from Siri or Maps for your services by implementing an Intents extension in one of a growing number of Intent Domains: messaging, lists and notes, workouts, payments, photos and more.
- GameplayKit: Evaluate decision trees that contain questions, possible answers and consequent actions.

If you need to use one of the tasks from the above list, you're in luck. Just call the appropriate APIs and let the framework do all the hard work.
