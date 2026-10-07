# Chapter 8: Advanced Convolutional Neural Networks

Having feature extraction as a separate step only makes sense if you plan to reuse the same images in every epoch. But with random data augmentation — where images are rotated, flipped and distorted in many ways — no two images are the same. And all the feature vectors will be different for every epoch.

That's why this MobileNet-based model is trained end-to-end and not in two separate stages. In every epoch, Keras needs to compute all the feature vectors again because all the training images are now slightly different from last time. It's a bit slower, but that's a small price to pay for having a much larger training set with very little effort.

After training for 10 epochs, the validation accuracy stops up. Here is the code for plotting the accuracy again (as in the last chapter):

```
def combine_histories():
    history = {
        "loss": [],
        "val_loss": [],
        "acc": [],
        "val_acc": []
    }

    for h in histories:
        for k in history.keys():
            history[k] += h.history[k]
    return history

history = plot_accuracy(history)
fig = plt.figure(figsize=(10, 6))
plt.plot(history["acc\])
plt.plot(history["val_acc\])
plt.xlabel("Epoch")
plt.ylabel("Accuracy")
plt.legend(["Train", "Validation\])
plt.show()

plot_accuracy(history)
```