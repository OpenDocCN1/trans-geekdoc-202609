Let S_out be the output transcription (“I love robots”). Let S* be the correct transcription (“I love machine learning”). In order to understand whether #1 or #2 above is the problem, you can perform the **Optimization Verification test**: First, compute Score_A(S*) and Score_A(S_out). Then check whether Score_A(S*) > Score_A(S_out). There are two possibilities:

# Case 1: Score_A(S*) > Score_A(S_out)

In this case, your learning algorithm has correctly given S* a higher score than S_out. Nevertheless, our approximate search algorithm chose S_out rather than S*. This tells you that your approximate search algorithm is failing to choose the value of S that maximizes Score_A(S). In this case, the Optimization Verification test tells you that you have a search algorithm problem and should focus on that. For example, you could try increasing the beam width of beam search.

# Case 2: Score_A(S*) ≤ Score_A(S_out)

In this case, you know that the way you’re computing Score_A(.) is at fault: It is failing to give a strictly higher score to the correct output S* than the incorrect S_out. The Optimization Verification test tells you that you have an objective (scoring) function problem. Thus, you should focus on improving how you learn or approximate Score_A(S) for different sentences S.

Our discussion has focused on a single example. To apply the Optimization Verification test in practice, you should examine the errors in your dev set. For each error, you would test whether Score_A(S*) > Score_A(S_out). Each dev example for which this inequality holds will get marked as an error caused by the optimization algorithm. Each example for which this does not hold (Score_A(S*) ≤ Score_A(S_out)) gets counted as a mistake due to the way you’re computing Score_A(.).

For example, suppose you find that 95% of the errors were due to the scoring function Score_A(.), and only 5% due to the optimization algorithm. Now you know that no matter how much you improve your optimization procedure, you would realistically eliminate only ~5% of our errors. Thus, you should instead focus on improving how you estimate Score_A(.).