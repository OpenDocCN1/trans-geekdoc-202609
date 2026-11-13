![](bbox=[0.226, 0.081, 0.69, 0.345])

Figure 5.15 Validation loss for a model with appropriate capacity

# 5.4 Improving generalization

Once your model has shown itself to have some generalization power and to be able to overfit, it's time to switch your focus to maximizing generalization.

# 5.4.1 Dataset curation

You've already learned that generalization in deep learning originates from the latent structure of your data. If your data makes it possible to smoothly interpolate between samples, you will be able to train a deep learning model that generalizes. If your problem is overly noisy or fundamentally discrete, like, say, list sorting, deep learning will not help you. Deep learning is curve fitting, not magic.

As such, it is essential that you make sure that you're working with an appropriate dataset. Spending more effort and money on data collection almost always yields a much greater return on investment than spending the same on developing a better model.

+   - Make sure you have enough data. Remember that you need a dense sampling of the input-cross-output space. More data will yield a better model. Sometimes, problems that seem impossible at first become solvable with a larger dataset.
+   - Minimize labeling errors—visualize your inputs to check for anomalies, and proofread your labels.
+   - Clean your data and deal with missing values (we'll cover this in the next chapter).
+   - If you have many features and you aren't sure which ones are actually useful, do feature selection.

A particularly important way to improve the generalization potential of your data is feature engineering. For most machine learning problems, feature engineering is a key ingredient for success. Let's take a look.