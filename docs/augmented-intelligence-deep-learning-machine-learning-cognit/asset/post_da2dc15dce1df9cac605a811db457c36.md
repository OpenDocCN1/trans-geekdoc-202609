
## a. JRip (Ripper) Overview

RIPPER was proposed by Cohen [63]. It is used to conduct a global optimization process on the initial ruleset. The motivation for this algorithm was to place or revise each rule individually to amplify the accuracy of the ruleset [64].

This technique follows a three-step process: Grow, Prune, and Optimize. Algorithm 2 shows the outline of RIPPER.

## Algorithm 2: High-level Pseudo-code for JRip algorithm.

```
Algorithm: JRip algorithm
Input: - A sequence of m instances S = {(x₁, y₁)...(xₘ, yₘ)} where xᵢ ∈ Xₖ with labels yᵢ ∈ Y={0,1} from Polish bankruptcy dataset,
- F: Number of folds (optional),
- O: Number of optimization (optional)
- N: Number of minimal weights (optional)
- E: Check error rate (default: check) (optional)
- P: pruning check (default: prune) (optional)
Output: final rule set RS
Initialize: a rule set RS = {}
1- For each class:
2- [Building Stage]: Generate an initial rule set RI
3- Repeat:
4- Grow phase: grow one rule by adding conditions that satisfy the highest information gain: p(log(p/t)-log(P/T)) until the rule is 100% accurate
5- Prune phase: prune each rule according to the pruning metric: p/(p+n)
6- Until error rate >= 0.5 or there are no more positive instances or the description length (DL) of the ruleset is 64 bits greater than the smallest DL
7- [Optimization Stage]:
8- From RI, generate two variants A and B (A from an empty rule and B from the full rule) using the grow phase
9- Prune A and B on a metric: (TP+TN)/(P+N)
10- Compute the original rule according to the description length DL of A and B
11- Select the variant with the minimal DL for RI
12- If there are residual positives:
13- ([Building Stage])
14- Else:
15- ([Deletion Stage])
16- [Deletion Stage]:
17- Delete the rules from the ruleset that would increase the DL of the whole ruleset
18- Add resultant ruleset to RS
19- End For
```

As shown in algorithm 2, JRip is a Java-based implementation of the RIPPER algorithm. This method initializes an empty ruleset RS and starts looping through each class, from the less dominant to the most frequent. The rule generation process has three stages. The building stage splits into two phases: the grow phase is where every value of each attribute gets computed. The condition that has the highest information gain is selected. One rule is grown by greedily appending conditions until it is 100% accurate. The Prune phase prunes each of the generated rules incrementally, according to a specific pruning metric. These two phases repeat until they meet one of the stopping criteria (the mistake rate is more than 0.5, or no more positive instances occur or the rule set's description length (DL) exceeds the computation's minimum DL. This stage generates an initial rule set RI, which will be utilized in the second stage. The optimization stage generates two variants from randomized data using the grow and prune phases. One variant must be created from an empty rule and the other by greedily appending antecedents to the initial condition. The algorithm selects the variant with the minimal DL as an example in RI. If after all of RI being examined, there are still positive samples, then new rules are grown using the building stage. Otherwise, the ripper moves onto the final stage, which deletes the conditions that could enhance the DL of the complete ruleset. Then, it adds the found ruleset to RS, which will be the final output of the algorithm.

## a. AdaBoost Overview

For binary classification, the most commonly used boosting algorithm is AdaBoost. This algorithm was proposed by Freund and Schapire [65]. The following pseudo-code describes the working of this technique.

## Algorithm 3: High-level Pseudo-code for AdaBoost Algorithm.

```
Algorithm: AdaBoost algorithm
Input: -A sequence of m instances S = {(x₁, y₁)...(xₘ, yₘ)} where xᵢ ∈ Xₖ with labels yᵢ ∈ Y={0,1}
from Polish bankruptcy dataset,
-Weak learner
-T (number of iterations)
Output: The final classifier with hypothesis Hx=sign(∑t=1 T αt htx)
Initialize: D₁(i)=1/m for all i =1,.....,m
1-For t = 1 to T
2- Call Weak learner using distribution Dₜ
3- Get Weak classifier and obtain hypothesis ht: X→{-1,+1}
4- Calculate the error rate ε_t = ∑i=1 m D_ti [h_t(x_i)≠y_i] of h_t
5- If ε_t > 0.5 then T=t-1 and abort loop
6- set α_t = ½ ln[(1-ε_t)/ε_t]
7- Update D_{t+1}(i)= D_t(i) exp[-α_t y_i h_t(i)] / Z_t (Z is a normalization factor)
```

As shown in algorithm 3, AdaBoost takes as input a training set of m examples from the Polish bankruptcy dataset to perform binary classification. It initializes with a weight function Dₜ(x), which distributes the same weight to all training samples. In each iteration t, the weak learner is used to create a classifier with a hypothesis hₜ, which computes the error rate eₜ of the training samples. The algorithm uses the error rate to adjust the probability distribution Dₜ(x). This adjustment puts more weight on the misclassified training examples and less weight on the ones that were classified correctly in the previous iteration. This process sequentially constructs several weak classifiers for T iterations. The algorithm finally outputs a classifier with a hypothesis H, obtained using a weighted vote of the previous individual classifiers. The weight of each of these classifiers is obtained using the accuracy of the distribution Dₜ that they used.

The following pseudo-code represents a summary of the adapted model for our problem statement.

Algorithm 4 presents the structure of the adapted algorithm for our problem statement, which we referred to as SBSAda-Rip. The algorithm uses 70% of the data and iterates through T rounds. The method initializes with a distribution D₁ and an empty ruleset RS. In each round t, AdaBoost calls upon a JRip classifier using the distribution Dₜ. The JRip classifier goes through a series of stages. It starts at the building stage. It builds (while satisfying the highest information gain: p(log(p/t)−log(P/T)) and prunes (according to the pruning metric: p/(p+n)) one rule at a time. When it reaches at one of the termination criteria, it creates an initial ruleset RI. The optimization stage uses RI to split the rules and optimize them by re-growing and re-pruning them (using (TP+TN)/(P+N)). The best ones are selected and re-added to RI. The final stage, which is the deletion and selection stage, uses the new RI to produce the final rule set RS. This stage deletes the conditions that hinder the ruleset and adds the resultant ruleset to RS. From the computation performed in the JRip classifier, AdaBoost obtains a hypothesis hₜ. The error rate of the hypothesis is then calculated, and if it is superior to 0.5, then the distribution Dₜ₊₁ is updated. This whole process is replicated until there are no more misclassified instances in the data. In the end, we obtain the most suitable classifiers with hypotheses H(x) and their rulesets.

## 5.4.3. Testing Sub-Phase

This phase measures the performance of the trained model with the test data. We obtain the proposed model from the chosen best hypothesis and ruleset, which we consider the optimal option.

## 5.5. Validation

To evaluate our algorithms’ performance for generating prediction rules, this section addresses two primary research questions.

## Algorithm 4: High-level Pseudo Code of the enhanced Boosting model.

```
Algorithm: SBSAda-rip algorithm
Input: -A sequence of m instances S = {(x₁, y₁)...(xₘ, yₘ)} where xᵢ ∈ Xₖ (Xₖ the subset obtained from SBS) with labels yᵢ ∈ Y={0,1} from Polish bankruptcy dataset
-JRip algorithm
-T (number of iterations)
Output: The final classifier with hypothesis H(x) and its final rule set RS
Initialize: D_t(i)=1/m for all i=1,...,m, a rule set RS = {}
1-For t = 1 to T
2- Call JRip using distribution D_t:
3- For each class:
4- [Building Stage]: Generate an initial rule set RI
5- Repeat:
6- Grow phase: grow one rule by adding conditions that satisfy the highest information gain: p(log(p/t)-log(P/T)) until the rule is 100% accurate
7- Prune phase: prune each rule according to the pruning metric: p/(p+n)
8- Until error rate >= 0.5 | no more positive instances | description length (DL) of the ruleset is 64 bits greater than the smallest DL
9- [Optimization Stage]:
10- from RI, generate two variants, A and B (A from an empty rule and B from the full rule) using the grow phase
11- prune A and B on metric: (TP+TN)/(P+N)
12- compute the original rule according to the description length DL of A and B
13- select the variant with the minimal DL for RI
14- If there are residual positives:
15- ([Building Stage])
16- [Deletion Stage]:
17- Delete the rules from the ruleset that would increase the DL of the whole ruleset
18- Add resultant ruleset to RS
19- End For
20- Get JRip classifier and obtain hypothesis h_t
21- Calculate the error rate e_t = Σ_i=1^m D_ti [h_t(x_i)≠y_i] of h_t
22- If e_t > 0.5 then T=t-1 and abort loop
23- set α_t = ½ ln [(1-e_t)/e_t]
24- Update D_{t+1}(i)= D_t(i) exp[-α_t y_i h_t(i)] / Z_t (Z is a normalization factor)
```

## 5.5.1. Research Questions

RQ 01: To what extent the proposed approach can discover an accurate classification model from the given dataset compared to other methods?

RQ02: What is the significant comparison between the existing model and the proposed model ?

## 5.5.2. Description of the Experimental Database

To validate our work, we used the financial information of Polish companies in
