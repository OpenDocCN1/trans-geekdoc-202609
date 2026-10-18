found were *DstBytes*, *DstLoad*, and *DstRate*, described in the Table 15.3, where the description and score are shown.

# TABLE 15.3  Best Features Selected with the Random Forest Algorithm from Dataset A

| FEATURES | SCORES | DESCRIPTION |
|---|---|---|
| Destination bytes (DstBytes) | 0.272996 | Destination/source bytes count |
| Destination load (DstLoad) | 0.182034 | Destination bits per second |
| Destination rate (DstRate) | 0.181972 | Destination packets per second |

Still in the scenario **RF**, the best features from the dataset **B** were found, with a score over 0.15: *Ploss*, *Dport*, *SrcPkts*, and *TotPkts*. The features are described in Table 15.4.

# TABLE 15.4  Best Features Selected with the Random Forest Algorithm from Dataset B

| FEATURES | SCORES | DESCRIPTION |
|---|---|---|
| Total percent loss (Ploss) | 0.309460 | Percent packets retransmitted/dropped |
| Destination port (Dport) | 0.183496 | Destination port number |
| Source packets (SrcPkts) | 0.181972 | Source/destination packet count |
| Total packets (TotPkts) | 0.180653 | Total transaction packet count |

For the scenario **P**, the Pearson correlation coefficient was calculated so that the features achieving the higher scores – over 0.55 – of correlations with the target – which identify the flow as 0 (normal) or 1 (under attack) – could be identified. Using the dataset **A**, the best features were: *DstLoss*, *Ploss*, *Mean*, and *SrcLoss*. The description and scores of these features are illustrated in the Table 15.5.

# TABLE 15.5  Best Features Selected with the Pearson Correlation Coefficient from Dataset A

| FEATURES | SCORES | DESCRIPTION |
|---|---|---|
| Destination loss (DstLoss) | 0.949714 | Destination packets retransmitted/dropped |