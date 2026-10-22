(actual $20k, predicted $10k). Therefore, we might have to train the model to be better at predicting 95th percentile bills, even if it reduces the overall metrics.

# Challenges of Class Imbalance

ML, especially deep learning, works well in situations when the data distribution is more balanced, and usually not so well when the classes are heavily imbalanced, as illustrated in Figure 4-8. Class imbalance can make learning difficult for the following three reasons.

![](bbox=[0.14, 0.26, 0.84, 0.51])

Figure 4-8. ML works well in situations where the classes are balanced. Source: Adapted from an image by Andrew Ng26

The first reason is that class imbalance often means there’s insufficient signal for your model to learn to detect the minority classes. In the case where there is a small number of instances in the minority class, the problem becomes a few-shot learning problem where your model only gets to see the minority class a few times before having to make a decision on it. In the case where there is no instance of the rare classes in your training set, your model might assume these rare classes don’t exist.

The second reason is that class imbalance makes it easier for your model to get stuck in a nonoptimal solution by exploiting a simple heuristic instead of learning anything useful about the underlying pattern of the data. Consider the preceding lung cancer detection example. If your model learns to always output the majority class, its accuracy is already 99.99%.27 This heuristic can be very hard for gradient descent

26 Andrew Ng, “Bridging AI’s Proof-of-Concept to Production Gap” (HAI Seminar, September 22, 2020), video, 1:02:07, https://oreil.ly/FSFWS.

27 And this is why accuracy is a bad metric for tasks with class imbalance, as we’ll explore more in the section “Handling Class Imbalance” on page 105.