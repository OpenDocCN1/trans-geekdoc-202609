| *ADVERSARIAL ATTACK* |  |  |
|---|---|---|
| *TYPE* | *EVASION ATTACK* (*ATTACKS IN THE INFERENCING PHASE*) | *POISONING ATTACK* (*ATTACKS IN THE TRAINING PHASE*) |
| Reward function | Indirectly impact the DRL model by Evasion attacks on environment and Man in the middle evasion attacks on states. | Man in the middle poisoning attacks on Reward function: Directly impact the DRL model:
1. By flipping reward signs, the attacker can directly change the reward from the environment, and the agent will learn with the wrong reward.
2. When an agent reacts to the environment, it gets a wrong state instead of getting the correct next state from the environment. The attacker manipulates states and lets an agent perform the improper action and get the bad reward.
The attacker hacks into the DRL system and directly changes the reward function of the asset allocation model. |

# 6.8 CONCLUSION AND FUTURE WORK

Adversarial machine learning (ML) has been studied for more than a decade. Adversarial deep learning (DL) have also been researched for a decade. This paper presents a high-level overview of the trust and security