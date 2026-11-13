![](bbox=[0.1, 0.07, 0.88, 0.32])

the original model). The validation accuracy ends up consistently in the 80–85% range—a big improvement over our first try.
Let’s check the test accuracy.

```
Listing 8.18 Evaluating the model on the test set
```
test_model = keras.models.load_model(
    "convnet_from_scratch_with_augmentation.keras")
test_loss, test_acc = test_model.evaluate(test_dataset)
print(f"Test accuracy: {test_acc:.3f}")
```
```

We get a test accuracy of 83.5%. It’s starting to look good! If you’re using Colab, make sure you download the saved file (convnet_from_scratch_with_augmentation.keras),
as we will use it for some experiments in the next chapter.

By further tuning the model’s configuration (such as the number of filters per
convolution layer, or the number of layers in the model), we might be able to get an
even better accuracy, likely up to 90%. But it would prove difficult to go any higher
just by training our own convnet from scratch, because we have so little data to work
with. As a next step to improve our accuracy on this problem, we’ll have to use a pre-
trained model, which is the focus of the next two sections.

# 8.3 Leveraging a pretrained model

A common and highly effective approach to deep learning on small image datasets is
to use a pretrained model. A pretrained model is a model that was previously trained on
a large dataset, typically on a large-scale image-classification task. If this original data-
set is large enough and general enough, the spatial hierarchy of features learned by
the pretrained model can effectively act as a generic model of the visual world, and
hence, its features can prove useful for many different computer vision problems,
even though these new problems may involve completely different classes than those
of the original task. For instance, you might train a model on ImageNet (where classes