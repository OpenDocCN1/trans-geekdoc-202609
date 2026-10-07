# # Formulating the Logistic Regression algorithm

Before we discuss the Logistic Regression algorithm, we need to discuss the Linear Regression algorithm.

Linear Regression algorithm is an algorithm for solving Regression problems. In Regression problems, we need to predict a continuous variable, and in the classification problem, we need to predict a categorical variable.

# # Understanding the Linear Regression algorithm

Consider that we set up an experiment to determine the length of the hypotenuse of right-angled triangles. This experiment can be conducted by drawing right-angled triangles on a piece of paper and measuring the length of the sides using a scale. Let us say that the data obtained from our experiment is shown in Figure 4.2. We will give this data to the machine to learn how to determine the length of the Hypotenuse.

| Features | Target |
| A | B | C |
| 4 | 2 | 4.45 |
| 6 | 6 | 8.5 |
| 3 | 9 | 9.5 |
| 7 | 5 | 8.6 |
| 2 | 12 | 12.2 |
| 3 | 9 | 9.4 |
| 4 | 7 | 8 |

Figure 4.2: Results from the Experiment to be used as input data by the machine.

To analyze the data in Figure 4.2, the Data Scientist creates a visualization, as shown in Figure 4.3:

![](bbox=[0.323, 0.706, 0.676, 0.925])

Figure 4.3: Visualization of Data in Figure 4.2