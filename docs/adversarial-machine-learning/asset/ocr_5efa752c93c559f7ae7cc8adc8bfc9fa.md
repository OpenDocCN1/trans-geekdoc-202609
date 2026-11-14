performance. No assumption is made about how the experts form their advice or about their performance; in fact, their advice may be adversarial and may incur arbitrary loss.

By developing algorithms with provable small regret, the composite predictor performs comparably to the best expert without knowing which one will be best a priori. By designing strategies that minimize regret, online learning provides an elegant mechanism to combine several predictors, each designed to address the security problem in a different way, into a single predictor that adapts relative to the performance of its constituents—all while facing arbitrarily adversarial data. As a result, the attacker must design attacks that are uniformly successful on the set of predictors rather than just on a single predictor because the composite learner can perform almost as well as the best without knowing ahead of time which expert to follow.

We now delve more deeply into the online learning setting, but for a full description and several regret minimizing algorithms see Cesa-Bianchi & Lugosi (2006).

As discussed earlier, the learner forms a prediction from the M expert predictions and adapts its predictor $h^{(k)}$ based on their performance during $K$ repetitions. At each step $k$ of the game, the defender receives a prediction $\hat{y}^{(k,m)}$ from the $m^{th}$ expert\(^2\) and makes a composite prediction $\hat{y}^{(k)}$ via $h^{(k)}$. After the defender's prediction is made, the true label $y^{(k)}$ is revealed, and the defender evaluates the instantaneous regret for each expert; i.e., the difference in the loss for the composite prediction and the loss for the $m^{th}$ expert's prediction. More formally, the $k^{th}$ round of the expert-based prediction game follows\(^3\):

+   1 Defender Update function \( h^{(k)} : \mathcal{Y}^M \rightarrow \mathcal{Y} \)
+   2 Attacker Choose distribution \( P_Z^{(k)} \)
+   3 Evaluation:
+   * Sample an instance \( (x^{(k)}, y^{(k)}) \sim P_Z^{(k)} \)
+   * Compute expert advice \( \{ \hat{y}^{(k,m)} \}_{m=1}^M \); e.g., \( \hat{y}^{(k,m)} = f^{(m)}(x^{(k)}) \)
+   * Predict \( \hat{y}^{(k)} = h^{(k)}(\hat{y}^{(k,1)}, \hat{y}^{(k,2)}, \dots, \hat{y}^{(k,M)}) \)
+   * Compute instantaneous regret: \( r^{(k,m)} = \ell \left( \hat{y}^{(k)}, y^{(k)} \right) - \ell \left( \hat{y}^{(k,m)}, y^{(k)} \right) \) for each expert \( m = 1 \dots M \)

This game has a slightly different structure from the games we presented in Sections 3.4.1 and 3.5.1—here the defender chooses one strategy at the beginning of the game and then in each iteration updates the function \( h^{(k)} \) according to that strategy. Based only on the past performance of each expert (i.e., the regrets observed over the previous \( k - 1 \) iterations of the game), the defender chooses an online strategy for updating \( h^{(k)} \) at the \( k^{th} \) step of the game to minimize regret (Cesa-Bianchi & Lugosi

\(^2\) An expert's advice may be based on the data, but the defender makes no assumption about how experts form their advice.

\(^3\) We again assume that costs are symmetric for the defender and adversary and are represented by the loss function. Further, as in Section 2.2.4 we simplify the game to use the surrogate loss function used in place of a 0-1 loss. Finally, this game is also easily generalized to the case where several instances/labels are generated in each round.