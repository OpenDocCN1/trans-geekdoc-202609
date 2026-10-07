![](bbox=[0.268, 0.085, 0.732, 0.183])

FIGURE 8.3 The aeroogene bevel gears in four states: (a) Healthy state; (b) tooth surface wear; (c) broken tooth; (d) small end collapse.

TABLE 8.1 The Aeroogene Bevel Dataset
| Data Type | Healthy State | Tooth Surface Wear | Broken Tooth | Small End Collapse |
| :--- | :--- | :--- | :--- | :--- |
| Rotational Speed | | | 500/1000/1500/2000/3900 rpm | | |
| Samples for training | 600*5 | 600*5 | 600*5 | 600*5 |
| Samples for testing | 300*5 | 300*5 | 300*5 | 300*5 |
| Label | 0 | 1 | 2 | 3 |

label. Details are shown in Table 8.1. Therefore, it can be seen as a multi-condition classification problem.

# Noise Addition to Simulate Multiple Data Domains

The vibration signal is often contaminated by noise in changing environment, and the data in one domain would be shifted considerably. Therefore, to simulate in multiple

![](bbox=[0.178, 0.517, 0.822, 0.893])

FIGURE 8.4 Illustration of the raw vibration signal in time domain.