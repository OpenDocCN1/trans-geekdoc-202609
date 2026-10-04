Table 1. Descriptive statistics of the dataset

| Attribute | Count | Mean | std | Min | 25% | 50% | 75% | Max |
|---|---|---|---|---|---|---|---|-|
| FRUITS_VEGGIES | 15972 | 2.922 | 1.442 | 0 | 2 | 3 | 4 | 5 |
| DAILY_STRESS | 15971 | 2.791 | 1.367 | 0 | 2 | 3 | 4 | 5 |
| PLACES_VISITED | 15972 | 5.232 | 3.311 | 0 | 2 | 5 | 8 | 10 |
| CORE_CIRCUIT | 15972 | 5.508 | 2.840 | 0 | 3 | 5 | 8 | 10 |
| SUPPORTING_OTHERS | 15972 | 5.616 | 3.242 | 0 | 3 | 5 | 10 | 10 |
| SOCIAL_NETWORK | 15972 | 6.474 | 3.086 | 0 | 4 | 6 | 10 | 10 |
| ACHIEVEMENT | 15972 | 4.0007 | 2.755 | 0 | 2 | 3 | 6 | 10 |
| DONATION | 15972 | 2.715 | 1.851 | 1 | 1 | 3 | 5 | 5 |
| BMI_RANGE | 15972 | 1.410 | 0.491 | 1 | 1 | 1 | 2 | 2 |
| TO_COMPLETED | 15972 | 5.745 | 2.624 | 0 | 4 | 6 | 8 | 10 |
| LOST_VACATION | 15972 | 2.889 | 3.692 | 0 | 0 | 0 | 5 | 10 |
| DAILY_SHOUTING | 15972 | 2.931 | 2.676 | 0 | 1 | 2 | 4 | 10 |
| SUFFICIENT_INCOME | 15972 | 1.728 | 0.944 | 1 | 1 | 2 | 2 | 2 |
| PERSONAL_AWARDS | 15972 | 5.711 | 3.089 | 0 | 3 | 5 | 9 | 10 |
| TIME_FOR_PASSION | 15972 | 3.326 | 2.729 | 0 | 1 | 3 | 5 | 10 |
| WEEKLY_MEDICATION | 15972 | 6.233 | 3.016 | 0 | 4 | 7 | 7 | 10 |
| AGE | 15972 | 1.602 | 0.944 | 0 | 1 | 2 | 2 | 3 |
| GENDER | 15972 | 0.382 | 0.486 | 0 | 0 | 0 | 1 | 1 |
| WORK_LIFE_BALANCE_SCORE | 15972 | 666.751 | 45.019 | 480 | 636 | 667.7 | 698.5 | 820.2 |
| MONTH | 15972 | 6.659 | 3.395 | 1 | 4 | 7 | 10 | 12 |

The descriptive statistical summary of the collected data is provided in Table 1.

# METHODOLOGY

# Proposed Architecture

We initiate the process by handling the data, addressing missing values, and ensuring its integrity. Employing the advanced random forest backtracking method, we performed feature selection to to precisely gauge the significance of each variable. Following which, we used 14 different regression models to calculate R-squared values and Mean Squared Error (MSE), methodically evaluating the predictive power. Our investigation resulted in a complicated approach known as stacking ensembling, in which we combined several base models and meta-regressors. This meticulous fusion allowed us to pinpoint optimal model configurations that exhibited