is in a low-bias region, member classification appliances produce a deviation that is very low, the existence of such a low deviation region is a universal phenomenon.

Therefore, the choice of the parameters ($\sigma$, $C$) of the low-deviation region to complete the classifier algorithm category can also improve the classification effect, and it is called the parameter classifier algorithm.

To obtain better and more accurate classification algorithms, starting from the integration of the regression learning machine, Krogh and Vedelsby [7], deduced the integrated learning generalisation error formula. This generalisation error formula also has a very important guiding significance for the classifier category. For the learning machine $q$, the generalisation error of their ensemble $E$ satisfies the following relations:

```
$$ E = \overline{E} - \overline{A} \,. $$
```

$\overline{E}$ is a weighted average of the generalisation error of the $q$ learning machine, which reflects the inherent error of the learning machine. $\overline{A}$ is a weighted average of the generalisation error of the $q$ learning machine relative to the generalisation error of the ensemble, which indicates the difference between the learning machines (ambiguity).

Based on the two-dimensional random bagging ensemble learning algorithm described in [20], the transformation learning algorithm $\mathcal{L}$ is implemented while changing the input space objects $X$. In the field of learning algorithms $\mathcal{L}$, the choice of appropriate parameters ($\sigma$, $C$) is the most important factor. However, through support vector machine model parameter research and discussion, it is found that in the low-bias region, the choice of parameters for the deviation is relatively low. Therefore, the model parameter pairs ($\sigma$, $C$) in the low-bias region are chosen randomly when the learning algorithm $\mathcal{L}$ is trained to obtain the morphism $f_i$. The classifier combining the feature classifier algorithm and parameter classifier algorithm is called the two-dimensional classifier.

# ### 15.4.3 Example analysis and results

To verify the category theory and learning expression, mapping mechanism theory can be applied to the classifier algorithm. We perform verification and comparison through some numerical experiments and an improved algorithm is proposed, proving the validity of the theory and the expression of the improved algorithm feasibility. The feasibility of theoretical research is a topic for future study.

Before we perform the experiments, we first take the example data set (Figure 15.13), and then classify the results using the original classifier category algorithm. The result is shown in Figure 15.14. The data set is simple, but the classification effect can be seen intuitively.

Define $X$ as Class 1, as Class 2, experimental results are obtained, and the error rates are for Class 1 errors=0.13, Class 2 errors=0.2, Total errors = 0.17 integrated.