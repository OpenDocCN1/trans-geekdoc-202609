FIGURE 6.7 Just before the agent observes the states from the environment, an attack agent is in the middle to perturb states and reward. This attack affects policy and makes the victim agent perform suboptimal action.

# 6.4.3 Attacks on Policy Function

A malicious attack agent can attack a policy (see Figure 6.8). Huang et al. showed an attack on policy function with perturbing the states like Figure 6.8. It introduces the fast gradient sign method (FGSM) in DRL [24]. The target for FGSM on DRL is to find an adversarial input that minimizes the probability of the best action. Moreover, the perturbation added to the input data should be as minor as possible.

![](bbox=[0.11, 0.38, 0.83, 0.75])

FIGURE 6.8 To attack policy, the attack agent can perturb the states and make the victim agent execute an action that the attack agent wants.