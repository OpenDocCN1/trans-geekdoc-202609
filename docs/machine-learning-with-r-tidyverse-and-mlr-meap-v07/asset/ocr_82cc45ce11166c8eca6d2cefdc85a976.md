+   - If you need to identify clusters of cases, use a clustering algorithm

# ### 1.2.3 A brief word on deep learning

If you’ve done more than a little reading about machine learning, you have probably come across the term *deep learning*, and you may have even heard the term in the media.

Deep learning is a subfield of machine learning (all deep learning is machine learning, but not all machine learning is deep learning) that has become extremely popular in the last 5 to 10 years for two main reasons:

+   1. It can produce models with outstanding performance
+   2. We now have the computational power to apply it more broadly

Deep learning uses *neural networks* to learn patterns in data, a term referring to the way in which the structure of these models superficially resembles neurons in the brain, with connections allowing them to pass information between them. The relationship between AI, machine learning, and deep learning is summarized in figure 1.7.

![](bbox=[0.133, 0.433, 0.354, 0.617])

**Figure 1.7** The relationship between artificial intelligence (AI), machine learning, and deep learning. Deep learning comprises a collection of techniques that form a subset of machine learning techniques, which themselves are a subfield of AI.

While it’s true that deep learning methods will typically out-perform "shallow" learning methods (a term sometimes used to distinguish machine learning methods that are not deep learning) for the same dataset, they are not always the best choice for a given problem. Deep learning methods often are not the most appropriate method for a given problem for three reasons:

+   1. **They are *computationally expensive*.** By expensive, we don’t mean monetary cost of course, we mean they require a lot of computing power, which means they can take a long time (hours or even days!) to train. Arguably this is a less important reason not to use deep learning, because if a task is important enough to you, you can invest the time and computational resources required to solve it. But if you can train a model in a few minutes that performs well, then why waste additional time and resources?
+   2. **They tend to require more data.** Deep learning models typically require hundreds to thousands of cases in order to perform extremely well. This largely depends on the