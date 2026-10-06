56 Machine Learning: Concepts, Tools and Data Visualization

MCTS also encourages players to search for actions in the other direction by giving them a certain amount of penalties a player visits only one side. This is to prevent a search from becoming too one-sided.

+   - Rollout Policy: Rollout policy has much lower performance than a policy network but it does have the advantage of being able to calculate much faster. Therefore, when running simulations in the Evaluation stage of MCTS, a roll-out policy is used.
- Value Network: Value networks are also used in the evaluation phase. In the evaluation stage, both rollout policy and a value network calculate the scores independently, and the final scores of this state are calculated by adding the two at a specific ratio. According to a number of papers, it is better to add the scores by using a combination of the two (ELO Rating 2900) rather than using only either (ELO 2450 and 2200 in a single machine) policy or a value network.

After completing the selection, expansion, and evaluation process for each step, the score(s) evaluated for the selected state is displayed. This score is used to update the score of the path visited during the backup process and the number of visits. After the time for the update has elapsed, the most visited state position in the MCTS tree is finally selected.

The process of updating the MCTS tree described above is, unfortunately, one that proceeds via a distributed operation.
In its last development, AlphaGo performed MCTS by distributing calculations across multiple CPUs and GPUs instead of performing calculations on a single computer, this becoming a form of artificial intelligence with such a "god-like" degree of searching ability that it has proven outside the understanding of even professional Go players.

# 4.2 IBM Watson

Watson was named after IBM's founder and first CEO, industrialist Thomas J. Watson.

Watson is a question-answering computer system capable of answering questions posed in natural language, developed for IBM's DeepQA project by a research team led by principal investigator, David Ferrucci. The computer system was initially developed to answer questions on the quiz show Jeopardy! and was featured on its February 14, 2011 episode. The first machine to win in a battle with humans was not AlphaGo. IBM's Deep Blue beat the 1996 World Chess Champion Garry Kimparov. AI Watson, the upgraded version of Deep