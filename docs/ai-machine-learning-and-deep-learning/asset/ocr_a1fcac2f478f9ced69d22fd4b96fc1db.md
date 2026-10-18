training that are explicitly robust enough to model misspecification can make deployment in the real world considerably more practicable.

# TABLE 6.1  **Overview of Adversarial ML/ DL/ DRL Attacks with Finance Applications**

| **ADVERSARIAL ATTACK** |  |  |  |
|---|---|---|---|
| **TYPE** |  | *EVASION ATTACK*<br>*(ATTACKS IN THE INFERENCING PHASE)* | *POISONING ATTACK*<br>*(ATTACKS IN THE TRAINING PHASE)* |
| ML | Regression | **Confidence reduction attacks:**<br>In which adversarial attacks are launched to compromise the accuracy of the deployed (online) ML-based system.<br>A spoofing attack requires a high attack budget. The attacker creates local extrema in the order book on a market prediction model, which uses a relatively simple structure compared with deep learning, such as linear regression models, since those models are fast for training and inferencing. | **Source confidence reduction attacks:**<br>In which adversarial attacks are launched to compromise the accuracy of the model in the training phase.<br>Source poisoning attack costs a low attack budget; however, the attacker needs to hack into the ML pipeline on a market prediction model that uses a relatively simple structure compared with deep learning. |