Small sample size: The disadvantage is that you are testing it against a small sample size, and not all errors may be caught. It won't be easy to target a suitable set of users and assess the full impact of the new model.

# A/B Testing

Here are some characteristics of A/B testing:

+   Controlled variables: You split the users into two groups in a random fashion and then test them with the old and new versions of the model to compare their performance. The first group is called the control group and is served the old model, and the other group is called the treatment group and is served the new model.

+   Statistical relevance: The benefit of this approach is that it allows you to make data-driven decisions. It allows you to test different features and configurations.

+   Planning: It takes a lot of planning to avoid biases. It will need to run for a substantial amount of time or need a substantial amount of traffic to reach statistical significance.

+   Targeting: It is also difficult to target the right set of users and therefore understand the full impact of the model.

> NOTE AB testing is similar to canary deployment. However, it requires a more significant number of users and will take longer, typically days or weeks, to reach a conclusion.

# Shadow Deployment

With shadow deployment, you have the old and new versions running side by side.

+   Data synchronization: While the old version serves the users, the new version is used purely for testing and analysis. Both versions take in the same input data.