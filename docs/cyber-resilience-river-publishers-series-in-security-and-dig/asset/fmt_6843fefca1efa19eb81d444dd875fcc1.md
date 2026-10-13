
# Methods of subjective probability

Methods of subjective probability can be classified depending on the *form* of *issues* posed to the experts or on the *event characteristics and random variables* and also depending on the *number of experts* involved in obtaining the probabilities. For cyber risk assessment of the tasks in a context of uncertainty, it is required to make probability (possibility) estimate of environmental conditions (unidentified factors). Since the external environment can assume only one value from a given set usually the methods for sets of incompatible events for estimation of subjective probabilities are applied. Among methods designed for probabilities estimate in case of finite sets of incompatible events, more practical value was obtained by the following methods: *direct probability assignment method, ratio technique and eigenvalue method*, in case of infinite sets of incompatible events – *variable interval method and the fixed interval method* [34, 152, 244].

![Figure 2.11 Focus areas of cyber risk management process.](Images/fig00131.jpg)

**Figure 2.11** Focus areas of cyber risk management process.

The detailed elaboration and adaptation of the above-mentioned methods are required for practical implementation and solving issues of cyber resilience and cyber security (Figure 2.12). It is also required to develop and implement the specific algorithms for interviewing experts in these methods. In addition to algorithms, implementing the specified methods it is necessary to create graphical representation procedures on the data obtained from the expert. This will allow the experts to make necessary adjustments in their previous estimates based on the overall picture. The procedures for probabilities aggregation should be established for the processing of probabilities, obtained from the several experts. They can be based on the *weighted sum method*. To improve the expert assessments consistency, an iterative examination procedure based on *the Delphi technique* is usually developed.

![Figure 2.12 Improvement of the existent methodology of cyber risks management.](Images/fig00132.jpg)

**Figure 2.12** Improvement of the existent methodology of cyber risks management.

## Obtaining the subjective probability problem statement

The problem statement is the requirement to develop probability distribution on a finite set of incompatible (exclusive) events [34, 56, 155] by interviewing the experts.

### (1) Direct assessment of event probabilities

In this method, an expert or a group of experts is provided with a list of all events. An expert shall consistently specify the probability of all the events. The method may have the various modifications. In one of the modifications, it is proposed to firstly select the most probable event from the proposed list, and then to evaluate its probability. After that this event is removed from the list and the same procedure is applied to the remaining list. The sum of all obtained probabilities must be equal to one.

### (2) Ratio technique

In this method, the expert is supposed to select the most probable event. The unknown probability is attributed to this event `P[1]`. Then the expert shall evaluate the probabilities ratio of all other events to the `P[1]` probability of the selected event (coefficients `C[2]...C[N]`). Considering the fact that the probabilities sum is equal to `1`, the following equation is composed:

> `P[1](1 + C[2] + C[3] + ··· + C[N]) = 1` (2.4)

Having solved this equation and finding the value of `P[1]`, one can calculate the sought probabilities.

### (3) Eigenvalue method

The eigenvalue method is based on the fact that the unknown probability vector (`P[1],...,P[n]`) is the eigenvector of some specially designed matrix, corresponding to its largest eigenvalue. Firstly, the expert is asked which one of the two events is more probable. Assuming that the most probable event is `S[1]`. Secondly, comes the question of what fold the `S[1]` event is more probable than the `S[2]` event. The ratio obtained from the expert is written in the relevant place in the matrix.

### (4) Equivalent basket method

This method allows obtaining a probability based on the expert comparison of the alternative utility. Assuming that it is required to calculate the probability of some `S[1]` event. Let us choose two any wins, for example, cash prizes, which are significantly different, e.g. the first is `1` thousand $, and the second is `0` $, and offer the expert a choice to participate in one of two lotteries. In the first lottery the expert gets the cash prize (`1` million $) if the `S[1]` event takes place, and gets the second prize (`0` $ rub.) if the event does not occur. To arrange the second lottery let us imagine a hypothetical basket filled with white and black balls, initially in equal proportions, for example `50` balls of each color. If the participant picks the white ball, he/she receives a cash prize in the amount of `1` thousand $, if the black one – `0` $. The expert is suggested to give preference to one of two lotteries. If from the expert's point of view the lotteries are equal, it is concluded that the probability of the event `S[1]` equals to `0.5`. If the expert prefers the first lottery, a part of black balls is removed from the basket and replaced with the same number of white balls. If the expert gives preference to the second lottery, a part of white balls is replaced with black ones. And again, in both cases the expert is invited to participate in one of two lotteries. Having changed the ratio of balls in a hypothetical basket, the equivalence of the two lotteries can be achieved. Then the sought probability of the `S[1]` event equals to the share of white balls in their total number.

## Methods for obtaining estimates of continuous distributions

They are used to find the distribution function (or frequency distribution) of subjective probabilities of a continuous random variable. In practice, two methods are applied: *variable interval method* and *fixed interval method* [52–54, [303](#Reference.xhtml#ref0309)].

### Variable interval method
