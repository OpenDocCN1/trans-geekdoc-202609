# 8.3.2 Fine-tuning a pretrained model

Another widely used technique for model reuse, complementary to feature extraction, is _fine-tuning_ (see figure 8.15). Fine-tuning consists of unfreezing a few of the top layers of a frozen model base used for feature extraction, and jointly training both the newly added part of the model (in this case, the fully connected classifier) and these top layers. This is called _fine-tuning_ because it slightly adjusts the more abstract representations of the model being reused in order to make them more relevant for the problem at hand.

I stated earlier that it's necessary to freeze the convolution base of VGG16 in order to be able to train a randomly initialized classifier on top. For the same reason, it's only possible to fine-tune the top layers of the convolutional base once the classifier on top has already been trained. If the classifier isn't already trained, the error signal propagating through the network during training will be too large, and the representations previously learned by the layers being fine-tuned will be destroyed. Thus the steps for fine-tuning a network are as follows:

+   1 Add our custom network on top of an already-trained base network.
+   2 Freeze the base network.
+   3 Train the part we added.
+   4 Unfreeze some layers in the base network. (Note that you should not unfreeze “batch normalization” layers, which are not relevant here since there are no such layers in VGG16. Batch normalization and its impact on fine-tuning is explained in the next chapter.)
+   5 Jointly train both these layers and the part we added.

You already completed the first three steps when doing feature extraction. Let’s proceed with step 4: we’ll unfreeze our `conv_base` and then freeze individual layers inside it.

![](bbox=[0.62, 0.08, 0.88, 0.81])

Figure 8.15 Fine-tuning the last convolutional block of the VGG16 network