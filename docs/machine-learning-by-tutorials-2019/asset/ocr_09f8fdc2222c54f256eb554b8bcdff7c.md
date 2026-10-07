# Chapter 9: Beyond Classification
By Matthijs Hollemans

**Update Note:** This chapter has been updated to iOS 13, Xcode 11 and Swift 5.1

The previous chapters have taught you all about image classification with neural networks. But neural networks can be used for many other computer vision tasks. In this chapter and the next, you'll look at two advanced examples:

+   - **Object detection:** find multiple objects in an image.
- **Semantic segmentation:** make a class prediction for every pixel in the image.

Even though these models are much more sophisticated than what you've worked with so far, they're based on the same ideas. The neural network is a feature extractor and you use the extracted features to perform some task, whether that is classification, detecting objects, face recognition, tracking objects, or pretty any other computer vision task.

That's why you spent so much time on image classification: to get a grasp of the fundamentals. But now it's time to take a few steps further...

# Where is it?

Classification tells you what is in the image, but always considers the image as a whole. It works best when the picture has just one thing of interest in it. If your classifier is trained to tell apart cats and dogs, and the image contains both a cat and a dog, then the answer is anyone's guess.