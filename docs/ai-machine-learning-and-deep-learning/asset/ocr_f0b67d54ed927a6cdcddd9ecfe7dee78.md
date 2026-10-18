privacy, whereas, in indirect CDL, any participants can intentionally compromise privacy and make decentralized settings more undesirable [12].

# TABLE 4.1 Deep Learning Threats/Attacks

| TYPE OF ATTACKS | ATTACK TARGET | DETAILS |
|---|---|---|
| Model extraction attack | Deep learning model | Steal model parameters, functionality, or decision boundaries |
| Model inversion attack | Training dataset | Infer confidential information from prediction results |
| Poisoning attack | Training dataset | Forge training dataset |
| Adversarial attack | Deep learning model | Perturb benign samples |

# 4.3 AUROR: AN AUTOMATED DEFENSE

# 4.3.1 Problem Setting

In this section, we refer to the server as the entity that collects the data and executes DL algorithms over it. The server can share its computation cost with its customers. The customers that upload their data to the server are referred to as users. We specifically examine the indirect CDL setting, as shown in Figure 4.2. Unlike traditional DL structures, users submit the raw data to the server directly, and the indirect CDL setting masks the data and the submission to the server. This preserves the users’ privacy and saves computation cost.

A privacy-preserving deep learning (PPDL) system was proposed by Shokri et al. [13]. It has been used for many simulations [10, 13]. PPDL uses different privacy techniques to mask the features before submitting them to the server.

# 4.3.2 Threat Model