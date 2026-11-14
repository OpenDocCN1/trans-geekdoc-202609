# Generating Scenarios from Standard Deviations in the Blending Problem

> NOTE
> Just as in the previous section, we will need to employ OpenSolver. Just set the problem up normally as you would with regular Solver and use the OpenSolver Solve button on the ribbon when you're ready.

Imagine instead of receiving just the specs, you also received standard deviations along with your specifications in a tab titled **Specs Variability**, as shown in Figure 9.37. The goal is to find a blending plan that’s less than $1.25 million that best meets the quality expectations in light of supplier variability.

| | A | B | C | D | E | F |
|---|---|---|---|---|---|---|
| 1 | | | | standard deviations | | |
| 2 | Varietal | Region | Brix / Acid Ratio | Acid (%) | Astringency (1-10 Scale) | Color (1-10 Scale) |
| 3 | Hamlin | Brazil | 2 | 0.12% | 0.7 | 1 |
| 4 | Moscambi | India | 1.1 | 0.09% | 0.05 | 1.3 |
| 5 | Valencia | Florida | 0.2 | 0.19% | 0.7 | 1.4 |
| 6 | Hamlin | California | 1 | 0.18% | 0.9 | 0.9 |
| 7 | Gardner | Arizona | 1.3 | 0.13% | 0.6 | 0.3 |
| 8 | Sunstar | Texas | 1.4 | 0.09% | 0.4 | 1 |
| 9 | Jincheng | China | 0.3 | 0.19% | 0.2 | 0.3 |
| 10 | Berna | Spain | 0.8 | 0.12% | 0.4 | 0.9 |
| 11 | Verna | Mexico | 1 | 0.17% | 0.5 | 0.2 |
| 12 | Biondo Comn Egypt | | 0.9 | 0.17% | 0.7 | 0.1 |
| 13 | Belladonna | Italy | 0.6 | 0.07% | 0.9 | 0.1 |

Figure 9.37: Specifications with standard deviation added

You can create a copy of the original Minimax Relaxed Quality tab called **Robust Optimization Model**, where the new standard deviations (cells C2:F13 in Specs Variability) will go in N6:Q16 adjacent to the old specifications.
Once they’re in there, what do you do with them?
You’re going to use the mean and standard deviation for the specs to create yet another *Monte Carlo simulation*.

To answer the question, “If these are the distributions for my stats, what would an actual order look like?” you can create several random scenarios to see the possibilities. To draw a scenario, you read the normal CDF—characterized by the mean and standard deviation—backward. The formula in Excel for reading the normal CDF backward (or “inverted” if you like) is NORM.INV.

So begin by generating your scenarios below all of your work. In A33, you can add a title that says “Scenario.” In B33, you can add a 1, for the first scenario.