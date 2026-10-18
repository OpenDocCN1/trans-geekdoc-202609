As the previous sections indicated, attacks against ML systems have three primary goals: reducing the learning ability of the model, producing faults in model behavior, and acquiring sensitive information from the system. Attacks can be grouped by which phase (training or deployment) they target, and those groups can then be used to select defensive techniques such as those just presented. While no defense is absolute, an appropriately selected defensive schema can reduce attacker confidence and slow down their attempts at subverting the ML system’s behavior, providing time for human operators to intervene.

As further research is conducted on potential attacks on machine learning systems, new defensive techniques and refinements of existing techniques will continue to be made. The most promising research seeks to find algorithmic approaches for detecting and correcting adversarial behavior in real time, enabling a deployed ML model to actively mitigate attacker damage. These techniques, like the mix up inference approach, rely on routine self-checks of model output but are intended to require less input from human operators to correct errors and attacker damage.

# REFERENCES

+   1. [“The Three Types of Machine Learning Algorithms,”](https://pioneerlabs.io/insights/the-three-types-of-machine-learning-algorithms) *Pioneer Labs | Technology Strategists & Delivery Experts.* (accessed Feb. 11, 2021).

+   2. [K. Eykholt](http://arxiv.org/abs/1707.08945) *et al.*, “Robust Physical-World Attacks on Deep Learning Models,” *ArXiv170708945 Cs*, Apr. 2018, Accessed: Feb. 11, 2021. [Online]. Available: http://arxiv.org/abs/1707.08945.

+   3. [“What is a Honeypot?”](https://usa.kaspersky.com/resource-center/threats/what-is-a-honeypot) *usa.kaspersky.com*, Jan. 13, 2021. (accessed Feb. 11, 2021).

+   4. [F. Younis](#) and A. Miri, “Using Honeypots in a Decentralized Framework to Defend Against Adversarial Machine-Learning Attacks,” in *Applied*