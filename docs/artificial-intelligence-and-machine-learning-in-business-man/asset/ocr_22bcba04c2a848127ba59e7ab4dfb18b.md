# Artificial Intelligence and Machine Learning in Business Management

![](bbox=[0.273, 0.093, 0.725, 0.246])

FIGURE 15.7 Character segmentation.

+   iii. Else, assign the smallest label value from the neighbouring pixel labels to the current pixel.
iv. Save the equivalence relationship between neighbouring labels.
On the second pass:

+   1. Iterate each pixel in the image one row at a time from top to bottom.
2. If the element is foreground:
i. Relabel the pixel with the smallest equivalent label.

As in CCA, we consider the white pixels as foreground and black pixels as background, we invert the binary image of the segmented plate and then apply CCA to it. Once all connected regions are found, localization is used to mark the connected parts in the image i.e., characters. The result is shown in Figure 15.7.

# 15.4.9 CHARACTER RECOGNITION

After character segmentation, the next thing to do is to recognize the characters correctly. Before that, each character segmented from the previous stage is resized to 20px by 20px. This was done as a preprocessing step for character recognition.

There are a number of ways to perform character recognition, such as template matching, feature extraction based on edge distances, Machine Learning, etc. Our approach is based on Machine Learning the system accuracy can be improved by improving the training process. Using Machine Learning, an extracted character image is mapped to its actual character.

Machine Learning is the subset of AI that deals with the process of teaching systems to accept data, self-learn from it, improve by experience and use this learning to produce more useful results. It can be simply defined as a branch of AI that deals with data, processes, discovers patterns and uses it for prediction. Machine Learning is categorized as supervised, unsupervised and reinforcement learning. In supervised learning, the machine maps input to output based on its learning over provided input-output pairs. Here, supervised learning is used, as we have an idea of how different characters look like, and different inputoutput pairs of the character image and its label can be provided as training data.