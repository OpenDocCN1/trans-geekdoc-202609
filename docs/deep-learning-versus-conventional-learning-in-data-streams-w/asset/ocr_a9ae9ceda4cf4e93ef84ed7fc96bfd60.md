![](bbox=[0.08, 0.08, 0.45, 0.26])

FIGURE 4. Comparison of established model and real system for Example 2 using training data.

the last 148 pairs are taken as test data to use in evaluating the fuzzy models.

![](bbox=[0.55, 0.14, 0.9, 0.31])

FIGURE 6. Comparison of the established model and the real model for the Box-Jenkins example using training data.

![](bbox=[0.08, 0.31, 0.45, 0.51])

FIGURE 5. Comparison of established model and real system for Example 2 using testing data.

TABLE 5. Comparison among various identification methods for Example 2.

| Model | Number of rules | Training APE | Testing APE |
|---|---|---|---|
| Sugeno and Kang(1) [48] | 3 | 1.5% | 2.1% |
| Sugeno and Kang(2) [49] | 4 | 0.59% | 3.4% |
| ANFIS [47] | 8 | 0.043% | 1.066% |
| Proposed method | 6 | 0.0031% | 0.3892% |

provides the best APE value (0.0031%) for the training data and the testing data (0.3892%). The proposed identification approach is thus more effective in approximating the non-linear model, with significantly high accuracy, than the other approaches.

# C. EXAMPLE 3: BOX-JENKINS GAS FURNACE SYSTEM

Consider a multiple-input single-output gas furnace system [10], [13], [23], [26], [43], [51]–[59] with 296 input and output measurements. In this model, u represents the flow of gas into the gas stove, and y represents the carbon dioxide concentration flowing out of the stove. In order to compare the identification results with those in the literature, u(k), u(k – 1), u(k – 2), y(k – 1), y(k – 2), and y(k – 3) are chosen as the input data in this example. By executing the modified cluster validity criteria, the rule number (r = 2) is found. Similar to previous studies [10], [13], [23], [26], [43], the first 148 data pairs are taken as training data and

![](bbox=[0.55, 0.38, 0.9, 0.56])

FIGURE 7. Comparison of the established model and the real model for the Box-Jenkins example using testing data.

The antecedent part and the consequent parameters of the T-S model obtained using the proposed method are listed in Table 6. The performance result and the approximation error of the established fuzzy model approximating the real system for the training data and testing data are depicted in Fig. 6 and Fig. 7, respectively. It can be seen that the established T-S fuzzy model output is in good agreement with the actual model output. Table 7 shows a detailed comparison of the results obtained with the proposed identification method as well as other methods. From Table 7, it can be readily seen that the established T-S fuzzy model has a high accuracy, with a training MSE value of 0.0080 and a testing MSE value of 0.0846, which are better than those reported in previous studies [10], [13], [23], [26], [43], [51]–[59]. Furthermore, the established T-S fuzzy model with two fuzzy rules has a training MSE value of 0.0080 and a testing MSE value of 0.0846. Although some studies also established T-S fuzzy models with two fuzzy rules, their training and testing MSE values were larger. In contrast, with the same fuzzy rules, better MSE values for training and testing are achieved by our model.