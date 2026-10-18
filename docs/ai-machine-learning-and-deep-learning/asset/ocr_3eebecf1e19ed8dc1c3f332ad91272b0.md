algorithms in Bayesian networks [7], four results were calculated:

+   1. Probability of DoS and MitM attacks to the field devices level
+   2. Probability of DoS and MitM attacks to the field devices level given the evidence of attack on any other nodes in the network
+   3. Probability of DoS and MitM attacks to the field devices level given the evidence of attacks and that there were no phishing and malware injection attacks to the management level
+   4. Most probable explanation given the evidence of DoS and MitM attacks to the field devices level

The first three results are presented in Tables 7.4, 7.5, and 7.6. As for the most probable explanation: If there is evidence that there was a DoS attack but not a MitM attack or that there was a MitM attack but not a DoS attack to the field devices level, the most probable explanation includes a social engineering attack to the management level, then a phishing attack to the management level, after that a DoS attack to the KNX IP router, and finally any of the attacks of the evidence.

# TABLE 7.4 Probability of DoS and MitM Attacks to the Field Devices Level

| ATTACK | PROBABILITY |
|---|---|
| DOSF | 0.3257822 |
| MITMF | 0.2627260 |
| DOSF and MITMF | 0.1897563 |

# TABLE 7.5 Probability of DoS and MitM Attacks to the Field Devices Level Given the Evidence of Attack on Any Other Nodes in the Network

| ATTACK | EVIDENCE | PROBABILITY |
|---|---|---|
| DOSF | SECP | 0.4134291 |
| MITMF |  | 0.3334087 |
| DOSF and MITMF |  | 0.2408075 |
| DOSF | PHCP | 0.6054472 |