(infinitesimal) notions of robustness. The most prominent of these measures is the gross-error sensitivity defined as

```
\gamma^* (H, F_{\mathcal{Z}}) \triangleq \sup_z |IF (z; H, F_{\mathcal{Z}})|.
```

Intuitively, a finite gross-error sensitivity gives a notion of robustness to infinitesimal point contamination.

Research has highlighted the importance of robust procedures in security and learning tasks. Wagner (2004) observes that common sensor net aggregation procedures, such as computing a mean, are not robust to adversarial point contamination, and he identifies robust alternatives as a defense against malignant or failed sensors. Christmann & Steinwart (2004) study robustness for a general family of learning methods. Their results suggest that certain commonly used loss functions, along with proper regularization, lead to robust procedures with a bounded influence function. These results suggest such procedures have desirable properties for secure learning, which we return to in Section 9.1.

# 3.6 Repeated Learning Games

In Sections 3.4.1 and 3.5.1, the considered learning games are one-shot games, in which the defender and attacker minimize their cost when each move happens only once. We generalize these games to an iterated game, in which the players make a series of \(K\) repetitions of the iterated *Causative* game with the ultimate aim of minimizing their total accumulated cost. We assume players have access to all information from previous iterations of the game, and grant the attacker unspecified (potentially arbitrary) control of the training data. At each iteration the defender produces a prediction after which it learns the true label and suffers some loss.

Evaluating the defender's absolute cumulative cost of playing—the analog of risk in the stochastic or PAC settings—is impossible due to the strongly adversarial nature of the data. Instead it is conventional to compare the accumulated cost incurred by the learner relative to the minimum cost achievable (in hindsight) by any one of \(M\) experts—i.e., a set of classifiers each designed to provide different security properties. This relative (additive) performance measure is known as regret, since it represents the regret that the learner feels for not heeding the advice of the best expert in hindsight. The analogous multiplicative ratio of the learner's total cost to the minimum total cost of an expert is the related competitive ratio.

Most commonly, online learners form a composite prediction based on the advice of the experts. As such, the experts can be seen as providing advice to the defender (hence their name), who weighs the advice to produce the composite prediction; e.g., the aggregate prediction could be a weighted majority of the experts' predictions (Littlestone & Warmuth 1994). Further, at the end of each iteration, the defender uses the newly revealed true label to reweigh each expert based on the expert's predictive