
The size of the YOLO model you trained with Turi Create is 64.6 MB. That's pretty hefty! This is reaching the upper limit of what is acceptable on mobile devices. It's possible to use object detection models that are much smaller than YOLO to give very good results, such as SSD on top of MobileNet (about 26 MB).

Try training MobileNet+SSD detection API at github.com/tensorflow/models/tree/master/research/object detection. This is a good project to get some experience working directly with TensorFlow. main difficulty will be converting the data into a format that this API understands.

To convert the final TensorFlow model to Core ML, you can use tf-corem and the following repo: github.com/vonholst/SSDMobileNet CoreML.

Compare the mAP of this model with the MAP reported for YOLO this chapter to see if MobileNet+SSD compares favorably or not. Good luck!

- Change the semantic segmentation demo app to only keep pixels that belong to cats and dogs — or whatever your favorites are from the 20 Pascal VOC classes.

## Key points

- To create a model that can detect multiple objects, it's not enough to add extra bounding box predictors. Single-stage detectors like YOLO and SSD put the predictors into a grid so that they only look at specific portions of the input image. They also train different predictors to specialize in various shapes and sizes.

- Non-maximum suppression (NMS) is a post-processing step used to only keep the best bounding box predictions. The YOLO model that is trained by Turi Create will automatically apply NMS.

- Semantic segmentation lets you make a unique class prediction for every pixel in the image. Instead of a single probability distribution, this predicts as many probability distributions as there are pixels.

## Where to go here?

Congrats, you've reached the end of section 1, Machine Learning with Images! Of course, we hope this is really only the beginning of your journey into the wonderful world of computer vision and deep learning.

Some new areas to explore:

- Models that can create new images. Style transfer is a technique of taking a photo and making it look like a famous painting. Generative models can produce totally new works of art, such as an infinite number of unique anime characters, youtube.com/watch?v=PUkWQbGa4Fg.

- Instead of working with still images you can also add a dimension and make predictions on video. One example is tracking moving objects, which is like object detection but over. Another futuristic application — literally! is predicting what will happen in the next frames of the video.

- Human pose detection. You can use a neural network to find keypoints on the human body, as some person's hands and feet are. It's even possible to reconstruct realistic 3D models of the human body from photos, densepopose.org.

And more... The possibilities are endless!

One project that was published recently is Everybody Dance Now, which combines techniques of human pose detection and generative models to copy a regular person, turning anyone into a dancing pro. See the amazing video at youtube.com/watch?v=PCBTZhh41Ris.

Believe it or not, you already understand 90% of the techniques used in that project and many others. Everything builds on what you've learned in the first part of this book.

If you want to know exactly Everybody Dance Now works, check out the paper. You can find it here: arxiv.org/pdf/1808.07371.pdf. A lot of the collective knowledge in machine learning isn't written down in books, articles and blog posts, but in academic papers. If you're serious about machine learning, getting into the habit of reading those papers.

To be honest, it can be hard to get into research papers. The Everybody Dance paper won't make sense to you at first reading. Don't fret! Simply read a few other papers on the same topic. Skip parts that don't make sense to you yet. Gradually, you'll get comfortable with the way these papers are written. And once you speak the language of a certain subfield such as human pose detection or generative models, new papers become easier to read.

A good place to find papers is on arxiv.org. Even better the Arxiv Sanity Preserver at arxiv-sanity.com, which also has a “top hype” section where you can find the latest buzz is about. To stay up-to-date on what's happening in machine learning, the papers are where they's at.

> Note: We heartily recommend watching the fast.ai videos once you've finished this book. This is one of the best online courses about computer vision

## Section II: Machine Learning with Sequences

In this section, you'll learn how to apply machine learning to sequential data. You'll work on a new iOS app which attempts to identify a user's activity using data from their iPhone's motion sensors. In the process, you'll learn how to build a good training dataset, how to create an activity classification model using Turi Create, and how to incorporate your model into an iOS app to support responsive classifications with real-time data.

- Data Collection for Sequence Classification: In this chapter, you'll learn how working with sequences differs from working with discrete data like individual images. You'll learn how to collect iPhone sensor data, as well as what it takes to build a good training dataset.

- Training a Model for Sequence Classification: In this chapter, you'll learn about neural networks designed to work with sequences. You'll learn how to use Turi Create to train an activity classification model from the previous chapter.

- Sequence Classification: In this chapter, you'll learn how to pass real-time sequential data captured from a device's motion sensors into your Core ML model. You'll learn some tricks to help keep your apps responsive and accurate while processing sequences of streaming data.

## Chapter 11: Data Collection for Sequence Classification

By Chris LaPollo

> **Update Note:** Apple loves to keep us waiting. As of writing, the CoreML APIs needed to update this chapter weren't quite ready. As Apple releases new APIs, we'll continue to update this chapter. We'll also notify you and let you know how to access the updated versions.

You worked exclusively with images throughout the first section of this book, and for good reason — knowing how to apply machine learning to images lets you add exciting and useful features to your apps. Techniques like classification and object detection can help you answer questions like “Is this snack healthy?” or “Which of these objects is this?”

But you've focused on images — even when processing videos, you processed each individually.

![](img/5720be5c3cca252e12448e68d25607b5_374_0.png)

## The Case of Disappearing Cookies

## 11: Data Collection for Sequence Classification

Each of the above images tells only part of the story. Rather than considering them individually, you need to reason over them as a sequence. There are many tasks that involve working with sequential data, such as:

- Extracting meaning from videos. Maybe you want to make an app that translates sign language, or search for clips based on the events they depict.

- Working with audio, for example converting speech to text, or songs to sheet music.

- Understanding text, as these sentences you've been reading, are sequences of words, themselves sequences of letters.

- Countless others. From weather data to stock prices to social media feeds, there are endless streams of data.

With many types of data and almost as many techniques for working with it, this chapter can't possibly cover everything. But to keep things practical, this chapter focuses on a specific type of sequence classification — human activity detection. That is, using sensor data from a device worn by a person to identify what that person is doing. You've already experienced activity detection on your devices, by checking your daily step count on your iPhone or closing rings on your Apple Watch. Those just scratch the surface of what's possible.

In this chapter, you'll learn how to collect sensor data from Apple devices and prepare for it by training a machine learning model. You'll use that data in the next chapter, along with Turi's task-focused API for activity detection, to build a neural network that recognizes user activity from device motion data. Finally, you'll use your neural net to recognize player actions in a game. The game you make is like the popular Pop It, but instead of calling out physical bits to bob and twist, it will call out gestures for the player to make with their iPhone. Perform the correct action before time runs out! The gestures detected include a chopping motion, a shaking motion and a driving motion (imagining turning steering wheel).
