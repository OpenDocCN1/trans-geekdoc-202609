
## 6.8.3 Adversarial Attack Generation Techniques

*   **Fast Gradient Sign Method (FGSM)**: A quick and easy gradient-based method used to create adversarial tasks to reduce the maximum amount of perturbation that may be applied to any individual pixel of the image to lead to misclassification. `FGSM` attack is a white-box attack with the goal of misclassification.
    *   Advantage: Relatively fast computation time.
    *   Disadvantage: Each feature is added with perturbations.

*   **Jacobian-based Saliency Map Attack (JSMA)**: A feature selection that helps to reduce the number of features that need to update while producing erroneous predictions. Flat perturbations are systematically applied to features in descending order of saliency value. The goal of this greedy method is to raise the predicted erroneous outputs over numerous iterations that modify one pixel at a time.
    *   Advantage: Perturbs few features.
    *   Disadvantage: Computationally complex compared to `FGSM`.

*   **Deepfool Attack**: An adversarial sample generation method without a target. It reduces the Euclidean distance between perturbed instances and the original data. It calculates the decision boundaries among classes and repeatedly introduces perturbations.
    *   Advantages: Produces adversarial instances well, with higher misclassification rates and lower perturbations.
    *   Disadvantages: Requires more processing than `FGSM` and `JSMA`. Additionally, adversarial instances are probably not the best.

*   **Carlini & Wagner Attack (C&W)**: Relies on the Limited-memory Broyden-Fletcher-Goldfarb-Shanno (`L-BFGS`) threats in the optimization process. It excludes box limitations and uses other objective functions. As a result, the technique is better at producing adversarial examples. Baseline defeats like defensive distillation and adversarial training are defeated by it.
    *   Advantages: Generates adversarial elements effectively and can overcome selected adversarial defenses.
    *   Disadvantages: Computationally complex compared to `FGSM`, `JSMA`, and `Deepfool`.

*   **Generative Adversarial Networks (GANs)**: Utilize two neural models to produce adversarial threats. The result is that one behaves as a generator and the other as a discriminator. The generator aims to provide samples that the discriminator will misclassify in a zero-sum competition between the two networks. The discriminator makes an effort to discriminate between genuine samples and those produced by the generator.
    *   Advantages: Produce instances that are different from a training set.
    *   Disadvantages: Computationally complex and unstable.

*   **Zeroth-Order Optimization Attack (ZOO)**: A method perfect for black-box attacks since it enables the calculation of the gradient of the classifiers without having access to the model. By querying the expected model with updated individual features, the method calculates gradient and hessian and applies Adam’s or Newton’s method to optimize perturbations.
    *   Advantages: Performance is the same as the `C&W` attack. Does not require training in the alternative models or details about the classification model.
    *   Disadvantages: Needs many queries to obtain the expected output.

## 6.8.4 Adversarial Attack Defensive Methods

Detecting adversarial attacks is challenging due to the black-box nature of deep learning models, where the actual cause cannot be identified correctly. Some of the solutions can be listed as follows.

*   **Adversarial Training**: The system is trained to learn the possible adversarial attacks, simulating the design of an immune system. This will improve the robustness of the model to produce a set of threats against a system beforehand. However, this method may not avoid all types of threats, as it is impossible to produce all conceivable attacks in advance due to their size.

*   **Continually Alter the Learning Algorithms**: By keeping the algorithms confidential and rarely modifying the model, a moving target can be produced. One option is to extract and save the data at the time of acquisition and then assess it with the input of the algorithm.

*   **Limited-memory Broyden-Fletcher-Goldfarb-Shanno (L-BFGS)**: A non-linear gradient-based numerical optimization methodology. It reduces the number of perturbations that are added to images. This requires less computer memory and is used for parameter estimation in machine learning.
    *   Advantages: Performs better in producing adversarial elements.
    *   Disadvantages: Computationally complex, consumes more time and is difficult to use in practice, as the optimization is based on box constraints.

## 6.8.5 Best Practices to Avoid Adversarial Attacks

*   Select the dataset from a trustworthy resource, which is evaluated by a recognized organization. Generally, the datasets that are extensively used in deep learning applications have a higher integrity. The datasets from unknown sources may contain hidden malicious patterns that can poison the model training.

*   Take precautions to anonymize sensitive data such as credit card details. Attackers may use membership inference techniques to explore the training data, even if the data is kept private.

*   Hire a trustworthy developer to develop a deep learning model that has not been harmful or is not susceptible to adversarial attacks.

*   Check the truthfulness of the provider before downloading a deep learning algorithm from open-source sites such as `GitHub` or `PyTorch Hub` and incorporating it with the application. If the publisher of the source code is a reputed organization, then the model may not have been intentionally poisoned or adversarially compromised, however, it may have unintentional adversarial vulnerabilities.

*   Awareness of user access when the model is open-source and publicly available. Potential attackers can conduct adversarial attacks on any other application that utilizes the same model out of the box since they have access to the same model.

*   Set defenses to account for malicious behavior. Even if the model uses an industrial API, the same `API` can be used to create an adversarial model by the attackers. Methods such as passing the input images via different scaling and encoding types can be applied to neutralize the adversarial perturbations.
