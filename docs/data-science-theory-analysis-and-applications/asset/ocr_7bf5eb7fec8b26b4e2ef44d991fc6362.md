F-score = 2 × Precision × Recall / (Precision + Recall)   (14.9)

Specificity shows the evaluation of how great a strategy is in recognizing a negative emotion accurately.

Specificity = TN / (TN + FP)   (14.10)

At last, Precision shows the proportion of classification, which can be calculated by Equation (14.11).

Precision = TP / (TP + FP)   (14.11)

where TP and TN are the quantity of true positive and true negative prediction of the class, and FP and FN are the quantity of false positive and false negative expectations.

# 14.5 RESULTS AND DISCUSSIONS

Table 14.1 describes the FDCCN model that shows the individual recognition accuracy of all classes. The correlation among happy jump, untrustworthy jump, and angry jump are closer to one another. The performance of this network is good in

TABLE 14.1
Individual Accuracy (%) for 15 Class Emotions of an FDCNN Model

|   | AJ | AS | AW | FJ | FS | FW | HJ | HS | HW | SJ | SS | SW | UJ | US | UW |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AJ | 95 | 0 | 0 | 1 | 0 | 0 | 2 | 0 | 0 | 0 | 0 | 0 | 2 | 0 | 0 |
| AS | 0 | 96 | 0 | 0 | 1 | 0 | 0 | 2 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |
| AW | 0 | 0 | 96 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 2 |
| FJ | 2 | 0 | 0 | 94 | 0 | 0 | 1 | 0 | 0 | 2 | 0 | 0 | 1 | 0 | 0 |
| FS | 0 | 1 | 0 | 0 | 95 | 0 | 0 | 1 | 0 | 0 | 2 | 0 | 0 | 1 | 0 |
| FW | 0 | 0 | 3 | 0 | 0 | 95 | 0 | 0 | 2 | 0 | 0 | 0 | 0 | 0 | 0 |
| HJ | 0 | 0 | 0 | 1 | 0 | 0 | 96 | 0 | 0 | 2 | 0 | 0 | 1 | 0 | 0 |
| HS | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 97 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
| HW | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 94 | 0 | 0 | 3 | 0 | 0 | 2 |
| SJ | 4 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 94 | 0 | 0 | 0 | 0 | 0 |
| SS | 0 | 3 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 95 | 0 | 0 | 1 | 0 |
| SW | 0 | 0 | 4 | 0 | 0 | 2 | 0 | 0 | 0 | 0 | 0 | 92 | 0 | 0 | 2 |
| UJ | 0 | 0 | 0 | 2 | 0 | 0 | 3 | 0 | 0 | 4 | 0 | 0 | 91 | 0 | 0 |
| US | 0 | 3 | 0 | 0 | 2 | 0 | 0 | 1 | 0 | 0 | 2 | 0 | 0 | 92 | 0 |
| UW | 0 | 0 | 2 | 0 | 0 | 5 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 91 |

Note: AJ = AngryJump, AS = AngrySit, AW = AngryWalk, FJ = FearJump, FS = FearSit, FW = FearWalk, HJ = HappyJump, HS = HappySit, HW = HappyWalk, SJ = SadJump, SS = SadSit, SW = SadWalk, UJ = UntrustworthyJump, US = UntrustworthySit, UW = UntrustworthyWalk.