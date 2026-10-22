“the accuracy of differential privacy models drops much more for the underrepresented classes and subgroups.”25

# Compactness versus fairness trade-off

In Chapter 7, we talked at length about various techniques for model compression such as pruning and quantization. We learned that it’s possible to reduce a model’s size significantly with minimal cost of accuracy, e.g., reducing a model’s parameter count by 90% with minimal accuracy cost.

The minimal accuracy cost is indeed minimal if it’s spread uniformly across all classes, but what if the cost is concentrated in only a few classes? In their 2019 paper, “What Do Compressed Deep Neural Networks Forget?” Hooker et al. found that “models with radically different numbers of weights have comparable top-line performance metrics but diverge considerably in behavior on a narrow subset of the dataset.”26 For example, they found that compression techniques amplify algorithmic harm when the protected feature (e.g., sex, race, disability) is in the long tail of the distribution. This means that compression disproportionately impacts underrepresented features.27

Another important finding from their work is that while all compression techniques they evaluated have a nonuniform impact, not all techniques have the same level of disparate impact. Pruning incurs a far higher disparate impact than is observed for the quantization techniques that they evaluated.28

Similar trade-offs continue to be discovered. It’s important to be aware of these trade-offs so that we can make informed design decisions for our ML systems. If you are working with a system that is compressed or differentially private, allocating more resources to auditing model behavior is recommended to avoid unintended harm.

# Act early

Consider a new building being constructed downtown. A contractor has been called upon to build something that will stand for the next 75 years. To save costs, the contractor uses poor-quality cement. The owner doesn’t invest in supervision since they want to avoid overhead to be able to move fast. The contractor continues building on top of that poor foundation and finishes the building on time.

25 Eugene Bagdasaryan and Vitaly Shmatikov, “Differential Privacy Has Disparate Impact on Model Accuracy,” arXiv, May 28, 2019, https://oreil.ly/nrJGK.

26 Sarah Hooker, Aaron Courville, Gregory Clark, Yann Dauphin, and Andrea Frome, “What Do Compressed Deep Neural Networks Forget?” arXiv, November 13, 2019, https://oreil.ly/bg fFX.

27 Sara Hooker, Nyalleng Moorosi, Gregory Clark, Samy Bengio, and Emily Denton, “Characterising Bias in Compressed Models,” arXiv, October 6, 2020, https://oreil.ly/ZTT72.

28 Hooker et al., “Characterising Bias in Compressed Models.”