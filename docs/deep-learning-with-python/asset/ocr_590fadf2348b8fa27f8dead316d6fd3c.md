+   When manual audits are impossible, consider alternative evaluation avenues such as user surveys (for example, in the case of the spam and offensive-content flagging system).

# ## 6.3.4 Maintain your model

Lastly, no model lasts forever. You've already learned about *concept drift*: over time, the characteristics of your production data will change, gradually degrading the performance and relevance of your model. The lifespan of your music recommender system will be counted in weeks. For the credit card fraud detection systems, it will be days. A couple of years in the best case for the image search engine.

As soon as your model has launched, you should be getting ready to train the next generation that will replace it. As such,

+   Watch out for changes in the production data. Are new features becoming available? Should you expand or otherwise edit the label set?

+   Keep collecting and annotating data, and keep improving your annotation pipeline over time. In particular, you should pay special attention to collecting samples that seem to be difficult for your current model to classify—such samples are the most likely to help improve performance.

This concludes the universal workflow of machine learning—that’s a lot of things to keep in mind. It takes time and experience to become an expert, but don’t worry, you’re already a lot wiser than you were a few chapters ago. You are now familiar with the big picture—the entire spectrum of what machine learning projects entail. While most of this book will focus on model development, you’re now aware that it’s only one part of the entire workflow. Always keep in mind the big picture!

# ### Summary

+   - When you take on a new machine learning project, first define the problem at hand:
+     - Understand the broader context of what you’re setting out to do—what’s the end goal and what are the constraints?
+     - Collect and annotate a dataset; make sure you understand your data in depth.
+     - Choose how you’ll measure success for your problem—what metrics will you monitor on your validation data?

+   - Once you understand the problem and you have an appropriate dataset, develop a model:
+     - Prepare your data.
+     - Pick your evaluation protocol: holdout validation? K-fold validation? Which portion of the data should you use for validation?
+     - Achieve statistical power: beat a simple baseline.
+     - Scale up: develop a model that can overfit.