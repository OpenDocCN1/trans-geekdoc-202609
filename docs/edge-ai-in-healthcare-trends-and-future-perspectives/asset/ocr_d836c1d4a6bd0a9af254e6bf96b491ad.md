TABLE 12.2
Solution format

| Images | Features |
| :--- | :--- |
| | F¹ | F² | F³ | F⁴ | ... | F²² |
| l₁ | 0 | 0 | 1 | 0 | ... | 1 |
| l₁ | 1 | 0 | 0 | 1 | ... | 0 |
| : | | | | | | |
| : | | | | | | |
| lₗ | 0 | 1 | 0 | 1 | ... | 0 |

this scheme, every single solution is called a “Lion”. The initial solution format is shown in Table 12.2.

Among the N number of solutions, some of the solutions are randomly generated, as nomad lions. The remaining population is randomly divided into P prides. Every solution in this algorithm is a specific gender, which remained constant during the optimisation process. Over the searching process, every lion marks its best-visited position. According to these marked positions, every pride’s territory is formed. So, for each pride, marked positions (“best-visited positions”) by its members form that pride’s territory.

Step 2: Fitness calculation. After solution initialisation, the fitness of each lion is calculated. The classification accuracy is regarded as the fitness function. The fitness function is given in Eqn. 12.3.

```
Fitness = Max (Accuracy) (12.3)
```

```
Accuracy = (Tᴾ + Tᴺ) / (Tᴾ + Tᴺ + Fᴾ _ Fᴺ) × 100 (12.4)
```

Step 3: Hunting process. For the hunting process, the hunters are divided randomly into three sub-branches. The group with highest fitness is considered to be the middle and the other groups are considered as the right and left wings. Throughout hunting, if a hunter improves its own fitness, **PREY** (P) will escape from hunter and new position of **PREY** (P’) is obtained as follows:

```
P' = P + rand(0,1) × %I × (P - H) (12.5)
```

Where;
P→ current position of prey,
H→ position of hunter who attack to prey and PI is the percentage of improvement in the fitness of hunter.