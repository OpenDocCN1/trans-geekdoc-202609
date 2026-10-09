effective information occurs in the left and right singular value vector matrix $U, V$. Therefore, the Lie group layered learning algorithm, through the $U, V$ structure of Lie group, learns by layer to improve the accuracy of identification.

# # 7.4 Lie group deep structure heuristic learning

The heuristic approach uses a method that facilitates the problem itself to guide the learning process. In the field of artificial intelligence, diagnosis, machine learning, automatic reasoning, and others, the heuristic search algorithm has been widely used. In this paper, based on the third section, and combined with the idea of the heuristic search algorithm, Lie group deep structure heuristic learning is proposed.

# ## 7.4.1 Heuristic learning algorithm

In artificial intelligence, a large number of problems in the solution technology depend on the search. The heuristic approach uses the problem itself to guide the information and the search process. In this learning process, the selection of the heuristic function is crucial, and the efficiency and success of the whole algorithm are determined. Heuristic search is usually used for two different types of problems:

+   (1) Forward inference
(2) Backward inference

Forward inference is generally used for a state space search. In forward inference, inference is performed from the predefined initial state to the target state in the opposite direction. Backward inference is generally used for problem reduction. In backward inference, inference is performed from the given target state to the initial state.

The function used to evaluate the importance of a node is called an evaluation function. The evaluation function $f(x)$ is defined as the estimated value of the minimum path cost of all paths from the initial node $S_0$ subjectively to the target node $S_g$ via the node $x$.

The general form is

```
$f(x) = g(x) + h(x)$
```

where $g(x)$ represents the actual cost from the initial node $S_0$ to the node $x$, and $h(x)$ represents the cost of the optimal path from $x$ to the target node $S_g$. It embodies the heuristic information of the problem, which is determined by the characteristics of the problem, and $h(x)$ is called a heuristic function [38]. Thus, the heuristic approach translates the description of the problem state into a description of the degree of problem solving, which is represented by the value of the evaluation function.