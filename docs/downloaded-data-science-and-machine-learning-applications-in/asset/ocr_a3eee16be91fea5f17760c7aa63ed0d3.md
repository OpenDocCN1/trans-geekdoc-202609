# **Table 11.7.** Gas lift data.

| Parameters | Values |
|---|---|
| Minimum valve spacing | 250 ft |
| Kill fluid gradient | 0.465 ft/psi |
| Operating Injection Pressure | 1300 psi |
| Kick off pressure | 1900 psi |
| Gas lift valve type | R-20 Monel<br>Port size: 32<br>R-value: 0.25 |
| Differential pressure dP across valve | 250 psi |
| Vertical Lift Performance correlation | Petroleum Experts 2 |
| Surface Equipment correlation | Beggs and Brill |
| Well Depth | 12300 ft |
| Water Cut | 14% |
| Maximum Liquid rate | 12472 STB/D |
| Maximum Gas Available | 10 MMScf/day |

# 2.5.1 *Back Propagation Neural Network*

BPNN is a type of ANN model that involves fine-tuning the weights of the neural network based on the error rate obtained in a previous iteration. Proper tuning of the weights allows one to reduce the error rate which makes the model more accurate thereby increasing the generalisation of the model.

# 2.5.2 *Radial Basis Function Neural Network*

RBFNN is a type of neural network which approximates multivariable functions or multivariate by a linear combination of terms so that it can be used in more than one dimension. It is applied to approximate functions or data which is known at a finite number of points so that evaluations of the approximate function can take place often and efficiently.

# 2.5.3 *ANN Procedure*

For this work, historical production data from the Jubilee field which is the production data from the wells was grouped into training and testing data. MATLAB was the software used in building the ANN models. The inputs for the prediction were days, gas rate, cumulative gas produced, cumulative oil production, and flowing bottomhole pressure. The output for the model was the THP. To test the accuracy of the model, some statistical parameters were measured as the MAPE and correlational coefficient (R). A value of R closer to 1 means good accuracy while a value closer to 0 for MAPE indicates the