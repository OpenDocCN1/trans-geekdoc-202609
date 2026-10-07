# Machine Learning

# Chapter 6: Taking Control of Training with Keras

This is the output of the softmax layer, which makes sure that the most confident prediction is large, less confident predictions are smaller, and all the numbers add up to 1. 0. That probability distribution looks a lot messier than the ground-truth:

![](bbox=[0.203, 0.183, 0.794, 0.432])

# The predicted probabilities

The highest number in this vector is for pretzel (38.55%) but that the model isn't entirely certain and thinks it might be a banana after all (21.59%). Especially early on the training process, the model will not be very certain about its predictions.

Now that you have two vectors of 20 elements each, it means you can compare them. The formula for this is known as the cross-entropy loss. This chapter has already had much in it, so let's say that this compares each element between the two vectors in same fashion, and adds the results. This gives the loss for this particular image, which is just a single number.

If the prediction was also (mostly) banana, then the softmax output looks like the ground-truth and the loss is very small; if the prediction was 100% banana, then the loss is 0 because it's exactly right.

If the prediction for this image is not banana, the loss is a larger number. The worse the prediction is, the less the predicted probabilities match the ground-truth probabilities, and the higher the loss will be.

For this particular example, the loss is 1. 5329. That number by itself doesn't tell you very much, it's just a number. What's important is that this number goes down over while the model is being trained. Say that, after a few more epochs of training, the prediction for this image now has 0. 9 for banana and the remaining 0. 1 is

![](bbox=[0.162, 0.923, 0.338, 0.958])

231