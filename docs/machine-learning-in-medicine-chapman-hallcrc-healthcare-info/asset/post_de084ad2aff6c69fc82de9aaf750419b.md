
to detect the presence of LVH (i.e. Sokolow-Lyon and Cornell criteria among others); furthermore, these criteria are very specific (>90%), with poor sensitivity (<20%) and an accuracy of ≈ 50% [6].

Recently some studies have been published aimed to improve the classification of patients with LVH. The majority of these studies includes anthropometric variables also and not electrocardiographic variables only. Lin and Liu [14] classified young adults as having or not having LVH through an SVM algorithm. In this study, 28 electrocardiographic features and other clinical features (age, height, weight, BMI, waist circumference, systolic and diastolic blood pressure and body surface area) were evaluated. The SVM model was compared with the traditional ECG voltage criteria (Cornell and Sokolow-Lyon). Although the SVM model had a more balanced relation between sensitivity and specificity (86.7% and 73.3% each), the Cornell voltage criterion had a higher accuracy (93% vs. 74.2%) [14].

Sparapani and colleagues (2019) describe how the Bayesian Additive Regression Trees can classify the presence of LVH. This effort was nested in MESA (Multi-Ethnic Study of Atherosclerosis), where 3,214 men and 3,600 women were included. This algorithm is defined by a statistical model with a prior and a likelihood and is a tree-based Bayesian non-parametric method. In this study, 552 amplitude and duration electrocardiographic measurements were included. The MRI were the gold standard method to classify LVH. The proposed model had a ROC AUC of 82.9%, a specificity of 94.6%, and a sensitivity of 29%. Compared with the model of Gen-Min Lin, this model had more specificity (similar to the standard criteria), and in relation to the Cornell voltage product and voltage criteria, the Bayesian Additive Regression Tree showed better performance [15].

## 12.2.2 Non-Alcoholic Fatty Liver Disease

Nowadays, multiple scores are used to predict NAFLD. Poynard et al. [16] published the SteatoTest, a tool to predict NAFLD [16] in an attempt to reduce the need for liver biopsy. The author used logistic regression to model the probability of the presence of NAFLD; variables such as age, gender, body mass index (BMI), glucose, alanine transaminase, alpha 2 microglobulin, A-1 apolipoprotein, haptoglobin, total bilirubin, total cholesterol and triglycerides were evaluated. This model had an accuracy between 0.8 and 0.9 (varying with the sensitivity and specificity cut-offs). An updated model was published holding the accuracy with a simpler model [17].

Further study tried to improve the classification of NAFLD using previously described variables and some others (i.e. diastolic blood pressure and uric acid) [18], but with a dimensionality reduction with a lasso regression combined with a multivariable logistic regression. In this case, the model was structured with eight variables (including gender, age, total cholesterol, BMI, waistline, diastolic blood pressure, serum uric acid, and course of disease on high-density lipoprotein-cholesterol) and had an accuracy in the training and validation set of 0.848 and 0.809 respectively.

ML algorithms also have been used in the edge of the knowledge of metabolic disease, which includes lipidomics and glycomics. These "omics", includes a larger list of variables and could explain more about the phenomenon behind the disease. Perkakis (2019) evaluated 49 healthy subjects and 31 patients with biopsy-proven NAFLD. The author previously measured some hormone variables also: adiponectin, leptin, activin A and follistatin. The "omics" variables were measured by mass spectrometry and liquid chromatography-mass spectrometry. The ML algorithms included in the analysis were SVM, k nearest neighbor, and random forest. In this case, the SVM model with a non-linear kernel had the highest accuracy (with lipidomics variables and with other variables) [19]. However, the uniqueness of the DT algorithm is that it often imitates the human-level thinking, which makes it easier to understand the data and makes some reasonable interpretations. Unlike black-box algorithms such as neural network and SVM, the logic behind the DT algorithm is comprehensible and easy to explicate [20].

## 11.3 METHODOLOGY

DT is one of the most popular ML algorithms used for both classification and regression problems [20]. A DT exploits a tree-like model where each node represents a feature (attribute), each link (branch) exhibits a decision (rule) and each leaf embodies an outcome (categorical or continuous value). The algorithm of the proposed DT-based model aiming to diagnose LVH and NAFLD is mentioned in Algorithm 11.1.

### Algorithm 11.1: Decision Tree Algorithm

**Input:** Set of possible instances X and label Y  
**Output:** A Decision Tree $f : X \to Y$  
**function** DECISION_TREE(X, Y)  
1. Assign all training instances to the root of the tree. Set current node to root node.  
2. a. Partition all data instances at the node by the value of the attribute.  
b. Compute the **information gain ratio** from the partitioning.

$$ \mathrm{Gain\ ratio}(S, A) = \frac{\mathrm{Gain}(S, A)}{\mathrm{Split\ information}(S, A)} $$

$\mathrm{Gain}(S, A)$ = expected reduction in entropy due to sorting on $A$, $S = \{X\}$ is a collection of training examples.

$$ \mathrm{Gain}(S, A) \equiv \mathrm{Entropy}(S) - \sum_{v \in \mathrm{Values}(A)} \frac{|S_{v}|}{|S|} \mathrm{Entropy}(S_{v}) $$

where $\mathrm{Values}(A)$ is the set of all possible values for attribute $A$, and $S_{v}$ is the subset of $S$ for which attribute $A$ has value $v$ (i.e., $S_{v} = \{s \in S | A(s) = v\}$).

$$ \mathrm{Split\ information}(S, A) \equiv -\sum_{i=1}^{c} \frac{|S_{i}|}{|S|} \log_{2} \frac{|S_{i}|}{|S|} $$

where $S_{i}$ is a subset of $S$ for which $A$ has value $v_{i}$, and $c$ is the number of classes.

3. Identify a feature that generates the highest information gain ratio.  
Exploit this feature to be the splitting criterion at the current node.  
**if** the best information gain ratio is 0 **then**  
label the current node as a leaf and return.  
**end if**

4. Partition all instances according to the attribute value of the best feature.  
5. Denote each partition as a child node of the current node.  
6. a. If the child node is “pure” (has instances from only one class), label it as a leaf and return.  
b. If not set the child node as the current node and repeat Step 2.  
**end for**  
**end function**

A DT represents a list of disjunctive rules that lead to a class or value; they classify instances by sorting them down the tree from the root to some leaf nodes. Once a DT is learned, it can be used to evaluate new instances to determine their class. The instance is traversed through the tree from the root until it arrives at a leaf. The class assigned to the instance is the class for the leaf. The DT is constructed through a recursive partitioning strategy based on a given training sample, it expands a leaf node unless the given stopping criterion is satisfied, the goal is to split the data into disjoint sets by maximizing the “distance” between groups at each split. In the proposed algorithm, the information gain ratio is used for splitting criteria as shown in Algorithm 11.1. One of the bottlenecks of the DT algorithm is that it suffers from overfitting, i.e. each leaf will represent a very specific set of attribute combinations available in the training data, but unable to classify attribute value combinations that are not seen in the training data. In order to prevent overfitting, it is recommended to prune the DT, i.e. the lower ends (the leaves) of the tree are “snipped” until the tree is much smaller. The proposed pruning algorithm is illustrated in Algorithm 11.2.

### Algorithm 11.2: Pruning Algorithm

**Input:** A Decision Tree $f: \text{X}\text{\rightarrow}\text{Y}$  
**Output:** A Decision Tree $f_{1} \subseteq f$  
**function** PRUNING($f$)  
1. Classify all branches in the tree.  
2. Count the total number of leaves in the tree.  
3. while the number of leaves in the tree exceeds the desired number do  
   a. Find the branch with the least Information Gain.  
   b. Remove all child nodes of the branch.  
   c. Relabel the branch as a leaf.  
   d. Update the leaf count.  
**end while**  
**end function**
