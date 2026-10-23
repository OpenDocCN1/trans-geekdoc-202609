13 13 negative 0.007734856 36.11
14 14 negative 0.013633048 35.03
33 84 negative 0.012909645 40.00
35 86 negative 0.013874760 39.65
37 88 negative 0.011207163 38.94
39 90 negative 0.018840671 38.87
60 111 negative 0.013920748 39.23
61 112 negative 0.010758628 37.03
69 120 negative 0.010122101 38.58
71 122 negative 0.023491891 36.30
73 124 negative 0.012213669 40.57
75 126 negative 0.009964716 42.00
76 127 negative 0.022611430 39.05
80 131 negative 0.017640808 39.94
81 132 negative 0.024336411 38.25
83 134 negative 0.015876619 39.29
84 135 negative 0.009475816 41.44
86 137 negative 0.013483160 42.00
94 145 negative 0.027757804 39.45

By chance, three of these discrepant reactions (108, 128, and 126) were already checked; the others are compared in Figure 3.9. Essentially, two had reactive profiles of the three false-positive reactions (undetermined Cq but classified as positive by SVM); conversely, the 20 false-negative reactions (a Cq with an average of 39.19 ± 1.97 classified as negative by SVM) show profiles consistent with low template inputs. It can be advocated that the combination fit-point/maxRatio is quite powerful because it allows the identification of discrepancies in the reactions profiles to help validate the reactions more accurately. This is the current use of maxRatio in the Abbott Molecular m2000 RealTime System. The SVM overlay applied herein is expected to further reduce the discrepancies and instantiate groups — such as suppressed fluoresce, low template, or wholly misinterpreted — that will help the operator understand what problem caused the discrepancy. Nevertheless, a shortcoming of the model was its extreme dichotomy: ‘positive’ and ‘negative’ cluster could not describe the data set with sufficient detail.