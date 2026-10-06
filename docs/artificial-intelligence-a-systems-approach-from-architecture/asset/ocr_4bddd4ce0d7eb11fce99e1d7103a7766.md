In general, there is a set of desired properties that we want robust AI systems to demonstrate:

+   Resiliency:
  - Is the ML model stable to small perturbations
  - Can the AI system continue to operate even in the presence of attacks (i.e., graceful degradation)?
  - Can transfer learning succeed using pretrained models if faced with adversarial threats?
Explainability:
  - Can the AI system be explained in enough detail to understand the decision-making process?
  - Are there rules interpreting the model structure?
Reliability:
  - Does the AI system do what it is expected to do?
  - Are any potential failure modes (including analysis of counterfactuals)?
Verifiability:
  - Can the end-to-end AI system guarantee protection against data leakage, stealing of intellectual property, privacy, and other breaches?
  - Are there guards to identify drifts in data, algorithm, and/or overall performance?

Mitigation techniques for addressing the resiliency property have been proposed and extensively evaluated in the literature—a small subset is discussed here. These representative techniques have limitations—see the discussion by Carlini and others studies [17, 42–44]. Our objective is to expose the reader to a few of these techniques, not to give an exhaustive list, since this defense-attack (analogous to a mouse-cat game) evolves rapidly

+   - Adversarial training: The training set includes representative adversarial samples.
- Data sanitization: Cleaning of data from adversarial poisoning attacks.
- Defensive distillation: True class labels are converted into soft labels are approximate probabilistic outputs representing the correct classification, providing more flexibility to the classifier.
- Feature squeezing: Typical training samples have a wide space where adversaries can add perturbations. This technique reduces that space—for example, by special