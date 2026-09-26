![](image_rsrcTX.jpg)

  

# Machine Learning: An Overview of Artificial Intelligence

By Charles River Editors  

![](image_rsrcTY.jpg)

A graph of a support vector machine that has learned to distinguish black and white circles

# About Charles River Editors

![](image_rsrcTZ.jpg)

Charles River Editors is a boutique digital publishing company, specializing in bringing history back to life with educational and engaging books on a wide range of topics. Keep up to date with our new and free offerings with [this 5 second sign up on our weekly mailing list](http://charlesre.wufoo.com/forms/charles-river-editors/), and visit [Our Kindle Author Page](http://www.amazon.com/Charles-River-Editors/e/B006K1DIAW/?_encoding=UTF8&camp=1789&creative=390957&linkCode=ur2&qid=1351020208&sr=1-2-ent&tag=httpwwwcharle-20) to see other recently published Kindle titles.

We make these books for you and always want to know our readers’ opinions, so we encourage you to leave reviews and look forward to publishing new and exciting titles each week.

# Introduction

![Kernel Machine.svg](image_rsrcU0.jpg)

A graph of kernel machines being used to analyze separable functions

Machine Learning

Machine learning, in its broadest sense, is a series of methods to recognize and exploit patterns in data. The name comes from the goal of trying to automate (via machines) the process that humans have used to observe the world around them and draw conclusions (i.e. learn) from those observations. Although all practical work in the machine learning field is done through computer programming, the concepts are independent of programming knowledge and instead rely on a mathematical basis. This overview will look only at the conceptual and mathematical side of the field, with little mention of the programming or practical applications.

There are a multitude of algorithms that are grouped within the general category of machine learning. Depending on the type of information available, as well as the goal of a problem, many techniques will not work well or simply be impossible to apply. The key to learning different algorithms is to know in which situation each functions best. In many situations there is some sample data from a system and the goal is to interpret this data to define the system or to predict the behavior of new situations. These techniques will be examined later in the overview. Initially, problems will not provide sample data, but instead define a problem according to some constraints; the goal will be to find an optimal solution given the constraints.

Machine Learning: An Overview of Artificial Intelligence looks at the attempts to develop machine learning, from successes to failures. Along with pictures depicting important people, places, and events, you will learn about machine learning like never before.

[Machine Learning: An Overview of Artificial Intelligence](#part0001.xhtml)

[About Charles River Editors](#part0002.xhtml)

[Introduction](#part0003.xhtml)

[Search Algorithms and Goal Trees](#part0005.xhtml)

[Game Playing](#part0005.xhtml#aRF)

[Constraint Satisfaction](#part0005.xhtml#aRG)

[Nearest Neighbors](#part0005.xhtml#aRH)

[Decision Trees and Random Forests](#part0005.xhtml#aRJ)

[Neural Networks](#part0005.xhtml#aRK)

[Genetic Algorithms](#part0005.xhtml#aRM)

[Support Vector Machines](#part0005.xhtml#aRN)

[Boosting](#part0005.xhtml#aRP)

[Conclusion](#part0005.xhtml#aRR)

[Online Resources](#part0005.xhtml#aRS)

[Bibliography](#part0005.xhtml#aRT)

[Free Books by Charles River Editors](#part0006.xhtml)

[Discounted Books by Charles River Editors](#part0007.xhtml)

## Search Algorithms and Goal Trees

The first method to be covered in this overview will be goal trees and methods for searching through them; this type of problem is also referred to as uninformed search. These algorithms are typically taught through examples of route-planning or game-playing problems. For example, a character is in the city of Arad and need to drive to Bucharest; each vertex in the graph is called a node, and it is labeled with a letter (in this case we will use the first letter of each city’s name). Each node is connected to a limited number of other nodes with edges, and there is a specific distance assigned to each edge; in the example this would be the driving distance from one city to the next. These nodes and edges define the constraints on the problem; the goal is to go from A to B in the shortest distance or time. A simple map is shown as a graph below in Figure 1.

![](image_rsrcU1.jpg)

Figure 1: Example of a graph-based map

Upon initialization, the algorithm does not know how the nodes are connected or the distance from one node to another. It learns this information only as it encounters each node. So, starting at point A the algorithm knows that it can go to nodes Z, S, or T as well as the distance to each. While this example is quite simple, imagine the challenges that Google Maps faces when choosing the optimal route from Los Angeles to New York where there are millions of possible nodes. In this situation, it is computationally unfeasible to calculate every possible route and then compare all of them. The algorithm must choose which nodes to traverse and in what order. There are a variety of techniques to solve this problem, and the math behind them is very straight forward.

The simplest method is called breadth-first search. In this case, the path with the least node so far is expanded to one more node; this is repeated until the end destination is reached. So, from A, the algorithm first evaluates the path A → Z, A → S, and A → T (in any order). From there it will expand one of these nodes to the next level and continue this until B is reached. Note that this approach does not make use of the distances between nodes; it simply expands nodes according to the count of nodes. A variation of breadth-first search called uniform-cost search does make use of these distances. In uniform-cost search, the path with the shortest distance so far is expanded (regardless of how many nodes are required to get there). The problem with this method is that all paths that have been traversed must be saved while the algorithm is running. The number of possible paths grows exponentially; with millions of nodes, the amount of information saved is immense. In addition, there is not much machine learning going on here; it is basically a brute-force approach that tries every possible route until something works.

Breadth-first search is named after the visual representation of this technique according to a goal tree. If every path explored so far is defined as a state, then these states can be visually described according to a tree structure as shown in Figure 2, where the black lines are explored regions and the green are unexplored. Utilizing breadth-first or uniform-cost search, the tree grows in breadth very quickly, and the path representing each branch of the tree is saved separately. As the tree grows, the number of states saved in memory grows as well. The beam search method can be applied with breadth-first search in order to eliminate this problem. With beam search, only a limited number of paths at each level are saved. The name is derived from the idea that limiting the width of the tree follows a path similar to walking along a beam. The beam width is chosen (for example, 10), then after each level of the tree is explored, only the 10 shortest paths so far are saved for further exploration. The beam width must be chosen according to the total number of possible paths; if it is too small then the correct path will be discarded, and the algorithm will not reach the goal, if it is too large then there is little advantage over the standard breadth-first search.

![](image_rsrcU2.jpg)

Figure 2: Goal tree for uninformed search

Another simple uninformed search technique is called depth-first search. In this approach, the deepest unexplored node is expanded. This is performed until the path reaches the end goal, or until it terminates (reaches a dead end). If the path terminates, it is backtracked until reaching another unexplored node, and the search continues from there. The name is taken again from the goal tree; in this situation the tree grows vertically (in depth) very quickly. This method is subject to a large amount of luck; if the algorithm happens to expand the correct nodes soon then it can reach the optimal solution very quickly. However, if the wrong nodes are expanded (nodes which will never reach the goal or take a very long path to reach it), this method can take a very long time to converge to an optimal solution. One possible approach to improve the depth-first search is called depth-limited search. Returning to the goal tree, each horizontal level is assigned a depth where Arad is depth 0, Sibiu is depth 1, Faragas is depth 2, etc. An estimated depth limit (how far the goal node is expected to lie) is chosen and each branch of the tree is explored only to this depth, instead of explored until termination. A further modification is called iterative-deepening search, where an initial depth limit is chosen and then the tree is explored depth-first to this depth. If the goal is not reached at the initial depth limit, the limit is raised, and the tree is expanded further, which is continued until the goal is reached. Iterative-deepening can prioritize branches according to the length of the path so far; so that the shortest unexpanded path is deepened first. This provides significant computational savings over breadth-first or depth-first searches, and typically converges much faster.

Since the uninformed search algorithm does not know a graph until it explores it, all of the methods discussed so far have only made use of the paths already traveled in prioritizing which nodes to expand. If a little more information about the nodes is known, techniques called informed search can be utilized. These methods do not know the edge lengths between nodes but use some form of estimated distance to the goal node in order to prioritize search paths. Returning to the graph from Figure 1, the GPS coordinates of each city can be used to calculate a straight-line distance, and this can be used to estimate their driving distance from each other. In some situations, this may be a poor estimate (if there is a large lake between two cities that would need to be driven around), but in most cases it is a good estimate.

One informed search technique is called greedy search, which simply expands the node with the smallest estimated distance to the goal. If the estimated distance is close to the true distance, this works well, but if there are large variations between the two it can take a long time to converge. A more intelligent method is called A\* (A-star) search. Using A\*, each unexplored node is assigned a score: ![](image_rsrcU3.jpg)where ![](image_rsrcU4.jpg)is the distance travelled so far from the start node to the node being scored, and ![](image_rsrcU5.jpg)is the estimated distance from the node being scored to the goal node.

With this score, the nodes are expanded in order of lowest score. In this way, A\* utilizes both the distance traveled so far as well as the estimated distance in order to prioritize which nodes to explore next. Although very simple, A\* typically converges quickly and provides a solution very close to the optimum. This technique of scoring all possible choices is integral to machine learning methods, and similar concepts can be found in many algorithms. Since computers inherently rely on quantitative results, they typically need a numerical value in order to determine that a solution is preferred.

A well-studied problem which involves a graph-based search is the “traveling salesman” problem; in this case the goal is not to find the path between two nodes but between multiple nodes where the nodes can be visited in any order. All of the search algorithms discussed so far can be used to find the paths one by one, and it is usually fairly straight forward to determine a route that reaches all of the required nodes. Once a solution is found, the goal is to determine if it is the optimal solution or if there exists a better route. A simple approach for this application is the hill-climbing algorithm. Given a solution, the hill-climber alters one aspect of it (for example, changing the order that two nodes are visited) then evaluates this new solution. If the new solution is better than the old, the old one is discarded; if the new solution is worse, it is discarded. This is repeated many times until no better solution can be obtained. The name hill-climbing is derived from the idea that the algorithm will only go “uphill” to improve the solution one step at a time. This guarantees that it will never arrive at a solution worse than the initial stat, but leaves it vulnerable to obtaining a local optimum.

The concept of optimization is common in almost all machine learning techniques. The general flow involves an iterative process where the algorithm tries to locate the optimal solution based upon an objective function. The objective function is used to score the algorithm in order to provide a quantitative evaluation of the result. Depending on the application, the best result could be the maximum of the objective function or its minimum. Numerous techniques exist for optimization, and some will be discussed later in this overview; this is simply an introduction of the concept. Some objective functions contain only one optimum with a gradient along the whole function; these are named convex functions and are usually the easiest to optimize. A hill climbing algorithm will typically succeed in finding the global optimum of a convex function. In more complex problems (especially high dimensional objective functions), the function can contain multiple local minimums and local maximums, as well as flat regions with no gradient. A global optimum is the location of the highest or lowest value of the objective function; a local optimum is the location where the function is lowest or highest compared to nearby values, but not over the entire function domain. These complex functions can be very difficult to optimize, and different techniques can yield very different results for different functions. If a simple optimization algorithm such as the hill climber is used, its result depends heavily on the initial starting point.

![](image_rsrcU6.jpg)

Figure 3: Local and global optimum of a simple function

## Game Playing

A search algorithm works in an environment with defined rules, such as the constraint that movements can only be performed from one node to the next along an edge. For the class of algorithms considered in game-playing, there are also defined rules (rules of the game) but there is also an adversarial opponent attempting to stop the algorithm from reaching the optimum. The actions of this adversary depend upon how much knowledge it obtains about the goals and strategy. There are in general four categories of games, defined according to the amount of information known to all players, as well as whether the games contain a random component.

![](image_rsrcU7.jpg)

Figure 4: Four game categories

Initially the focus will be on the first scenario, where both players know exactly the current state of the game as well as all possible future states. Although seemingly simple, the number of possible game states makes solving these problems very difficult; a computer only recently (2016) was able to beat an expert player of the game Go. To express the number of possible game states, the same type of goal tree will be used for searching. Each level of the tree represents a set of possible system states; in this case, configurations of the game. An example of this tree is shown below for tic tac toe; each level represents the move of one player. Even with a simple game such as tic tac toe, the tree grows in width very quickly in order to consider all possible outcomes. 

![](image_rsrcU8.jpg)![](image_rsrcU9.jpg)

Figure 5: Goal tree for tic tac toe

The established method for solving these types of problems is known as minimax. This name comes from the fact that the algorithm’s goal will be to maximize the objective function while it is the “active” player (the player able to make a move), while minimizing the same objective function for turns where the other player is active. The objective function needs to be some quantitative evaluation of the current game state, usually where the best score is the highest. For tic tac toe, an example of this would be the number of possible winning configurations available to the active player minus the number of winning configurations available to the inactive player. With an empty board, this function will evaluate to 0 (both players have 8 possible ways they could win). If the algorithm is the “X” player, they have 9 possible moves; using this objective function the scores for each possible move are listed in red. With only 1 “X” on the board the algorithm still has 8 ways to win; but by choosing the middle square the algorithm can block the most possibilities for its opponent.

A simple implementation of minimax would choose the move with the highest objective value after 1 move (as shown in red). However, it is assumed that the opponent will also play to win the game; in this case, when it is the opponent’s turn, they will choose the move that maximizes the objective function for themselves (equal to minimizing it for the algorithm). Therefore, a smarter implementation of minimax would not only calculate all possible configurations after 1 of its own moves, but also calculate all possible configurations after 2 moves (1 by each player). This brings us to the second level of the tree, where each board will have 1 “X” and 1 “O”. Given all 9 possible configurations on level 1, each will have 8 possible configurations on level 2 (called “branches” or “children”). Given the move made by the algorithm on level 1, its opponent will choose the lowest score on level 2 (hence min then max). Therefore, an algorithmic player which looks 2 layers deep should choose the maximum of the level 2 minimums. In other words, each configuration on level 1 will receive a score that is the minimum of all of its children states. The algorithm should choose the maximum of these scores.

This process can be repeated level by level until the algorithm evaluates every possible board state. From the possible outcomes of each, the algorithm can make the best choice for its first move. In a simple game like tic tac toe, it is possible for a normal computer to evaluate all possible moves in a reasonable amount of time. However, for more advanced games (chess or Go), this is impossible. A personal computer could only look a few levels deep before time ran out for it to make a move; similar to the search algorithm, the size of the tree grows nearly exponentially as new layers are added. Of course, it is possible to simply let the algorithm search to a given depth and then choose whatever state is best at that depth. In this situation, if two algorithms play each other, whichever one looks deepest is guaranteed to win a majority of the time.

In order to eliminate some branch evaluations, constraints can be placed on the possible values each level can take. This is termed “pruning” the tree, as the branches that do not need to be evaluated are considered to be trimmed. It is possible to eliminate branches based upon upper (α alpha) and lower (β beta) limits for the values that each could take. This technique is named alpha-beta (or α-β) pruning. The elimination is done based upon at least 3 levels of a minimax tree. The process is described in the steps below using a simple 3 level tree:

1)   ![](image_rsrcUA.jpg)A tree has a 0-level maximization decision block (indicated by an upward pointing arrow). The first branch is fully explored to level 2. Since level 1 is a minimization step (downward arrow), that node is assigned a value that is the minimum of its children. Since the level 0 block will choose the maximum of all level 1 values, it must be greater than or equal 3.

2)  When exploring the next level 1 branch, the node has a lower limit of 3. If the node evaluates to 3 or less it will never be chosen by the top node, so its value will not affect the decision. Since it is a minimization step, if any level 2 node is less than 3, the remainder of the level 2 nodes no longer need to be evaluated. In this case, the first level 2 node is 2, so the remaining nodes can be pruned (shown with an “x”) and not explored. 

![](image_rsrcUB.jpg)

3)  This is continued for all level 1 branches until all have been explored or pruned. In some cases, no branches can be pruned if the values do not exceed the α or β constraints. In this case it will look similar to the sequence below.

![](image_rsrcUC.jpg)![](image_rsrcUD.jpg)![](image_rsrcUE.jpg)

Figure 6: Alpha-beta pruning step by step

Using alpha-beta pruning results in the exact same final result from the minimax tree, but with potentially much fewer function evaluations. The effectiveness of the pruning depends upon the order that nodes are evaluated, as can be seen in the example above. If the level 2 nodes of the last branch were evaluated in opposite order, 2 of them could be pruned. Typically there is little that can be done about the order in which nodes are visited, unless some other knowledge about their order is available.

So far, the minimax tree has assumed that both players know all possible moves. Sometimes there is some portion of the decision that involves probability, such as a dice roll. It is also possible that some information about the game state, while deterministic, is unknown to each player (battleship). In these cases, some nodes of the tree can be expressed as a weighted mean of its children nodes. This is shown in the tree below, where the weights on each branch are specified next to the branch. It is important to remember that for any node, the sum of probabilities of all its children must equal 1. This ensures that the values of different nodes are comparable. In the example, there are 2 branches weighted at 0.5 each (0.5 + 0.5 = 1). Another valid combination would be 0.85 and 0.15, or if there are 3 branches 0.2, 0.2, and 0.6; whichever best describes the data. This type of node is called an expectimax node (and therefore a tree containing them is an expectimax tree), based upon the concept of expected value, which is the statistical term for a weighted mean. The other minimum and maximum nodes function the same as before. It is worth noting that evaluating several levels of expectimax nodes results in very low probabilities of reaching each bottom node. If the tree has many expectimax levels the advantage of α-β pruning is diminished due to 2 reasons: many nodes will have values very close to each other, and the randomness of the outcomes does not guarantee the true result will match the expected result.

![](image_rsrcUF.jpg)

Figure 7: Expectimax tree example

## Constraint Satisfaction

Although the search and game playing algorithms contain constraints, the field of constraint satisfaction is typically involved with more formal descriptions of constraints. In these fields, the system state is defined by a vector of variables \[X1, X2, X3, … Xn\] (often called features or attributes) where each variable has a value from a specific domain Di. The problem places constraints on each variable; the constraints can come in three forms: unary, binary, or n-ary. This problem will be introduced through the example of coloring a map of Australia as shown below. Australia has 7 territories (Xi variables), and the map will only contain 3 colors (\[Red, Green, Blue\] is the domain for all variables).

![](image_rsrcUG.jpg)![](image_rsrcUH.jpg)

Figure 8: Territories of Australia and constraint graph

A unary constraint is any constraint that applies to one variable; similarly, a binary constraint applies to two variables. A unary constraint would be of the form C(Xi) → Xi = Da, such as Western Australia must be red. A binary constraint would be of the form C(Xi, Xj) → Xi ≠ Xj, such as the color of Western Australia cannot equal the color of Northern Territory. An n-ary constraint is one that involves 3 or more variables; an example is that the color of 2 adjacent territories cannot be equal. An n-ary constraint can always be expressed as a group of binary and unary constraints. The constraints on each of the territories can be summarized through the graph shown next to the map, where each node is a territory and each edge is a binary constraint.

Similar to depth-first search, an approach can simply start by assigning a value to one variable; then continue by updating constraints on all connected nodes and continuing to assign values one nodes at a time. Eventually, this approach will reach either a valid solution or a place where no solution exists that satisfies the constraints. At this time, the process can backtrack and make a different decision at the next unexpanded node. This is called backtracking search and is relatively inefficient and unintelligent. Again, all possible options can be expressed with a goal tree.

![](image_rsrcUJ.jpg)

Figure 9: Goal tree for backtracking search

Using some heuristics can improve the performance of backtracking search; a heuristic is guidance based upon the experience of experts. First is the Minimum Remaining Values heuristic: on each iteration, assign first the variable with the smallest domain. Initially all territories are white so only unary constraints are a factor in this decision. After the first color is assigned, as seen in the goal tree, then the domains of Northern Territory (NT) and Southern Australia (SA) are reduced to 2 options. Second is the Degree Heuristic: on each iteration, assign first the variable with the most constraints on other unassigned variables. In this example, that is SA since it has the greatest number of edges in the graph. Third is the Least Constraining Value: choose the variable value that eliminates the fewest possible values for the remaining variables. Looking at the last level of the goal tree shown above: if Q is assigned red, then SA can still be blue; however, if Q is assigned blue then SA has no valid options and the tree terminates and must be backtracked (so red should be chosen).

In addition to tracking the constraints on each iteration of the algorithm, the valid domains of all variables should be tracked as well. This process is called forward checking, from the idea that the algorithm is looking ahead to possible outcomes for all variables. This also involves ensuring that the constraints on existing domains do not eliminate possible options. An example of a poor assignment is shown below with forward checking. After three variable assignments, SA has no possible values left within its domain. However, including constraints would have identified this issue after 2 variable assignments. On the third row of domains, SA and NT both have only blue left; since these territories border each other this map configuration should be rejected, and Q should be assigned a different color.

![](image_rsrcUK.jpg)

Figure 10: Forward checking should have rejected the second decision to make Q green

The functions covered so far introduce the core concepts of constraint satisfaction and searching. Of course, many different techniques exist which have not been discussed here. There are numerous variations of the algorithms discussed, as well as completely different tactics which have been applied to these problems.  The key lessons learned in solving these constrained problems will carry over into the true machine learning portion of this overview. First, the algorithm needs an evaluation function in order to determine the best solution; if this function is not chosen correctly no method will work. Second, there are a multitude of different approaches that could yield a solution for any given problem; a good engineer will be able to choose the application that functions efficiently and fits the problem. Third, computational complexity should always be considered when programming a solution. Due to noise, random variation, or an unfeasible number of outcomes; it is typically impossible to determine the perfect solution, so the goal should be to determine a good solution.

## Nearest Neighbors

The field of machine learning is often divided into three subcategories: supervised learning, unsupervised learning, and reinforcement learning. The remainder of this overview will cover supervised learning, which encompasses a majority of machine learning algorithms. Supervised learning can be summarized as algorithms which evaluate known (“labeled”) data in order to make predictions on unknown (“unlabeled”) data. Data typically has a series of attributes (“input”) expressed as a vector for each data point, along with a vector of output variables for each data point. If the output variables are classes (i.e. data point Xi is Green from the domain \[Red, Green, Blue\]), the task is called classification. If the output variables are continuous (i.e. data point Xi is 0.65 from the domain \[0, 1\]), the task is called regression. In either case, the learning algorithm is supplied with a dataset of input vectors and their respective output vectors. After training the algorithm, it should be able to predict the output given an input vector.

The first, and simplest, technique used in supervised learning is called k-Nearest Neighbors. The idea is that, for any new input vector, the algorithm will find the k-nearest input vectors from the known dataset where k is some small integer. Then it will look at only those k vectors to determine the output for the new vector. Although it is a simple concept, identifying the “nearest” examples needs to be done in a careful manner. Euclidean distance is the traditional metric for vectors defined by continuous numerical coordinates, and it is the straight line distance between the two points. Manhattan distance, also called the city block distance, is the distance used if lines can only be drawn parallel to coordinate axes (at right angles). For categorical input data the Hamming distance is applicable, which is simply the sum of attributes that are unequal between the two vectors. A distance metric is typically defined as one where the closest points have a distance of 0, and the higher the distance magnitude the further away the points. If the data points are sparse vectors (each vector contains many zeros), the cosine similarity is often used to compute distance. This metric measures the cosine of the angle between two vectors and is often used in text analysis. Note that for a similarity metric, a value of 0 means the points are far apart and the highest value equates to the closest points (cos(0) = 1). To substitute cosine similarity into a distance calculation, it is acceptable to use 1 – S(x, y) or cos\-1(S(x, y)).

Table 1: Common distance metrics

![](image_rsrcUM.jpg)

Also of note, when discussing distance functions, is the practice of feature normalization. For each input vector, its variables all represent a different quantity with a different range of possible values. For example, if a vector describes the weather it could include features such as humidity in the domain \[0, 1\], temperature in the domain \[-40, 120\], and wind speed in the domain \[0, 50\]. Most distance metrics will naturally emphasize the features with the greatest range. In order to correct this, the range of each feature can be adjusted to lie within the domain \[0, 1\] while maintaining the scaled mean and variance of the original data. The formula for this is simple: for each feature subtract the minimum value then divide by the largest value, as shown below

![](image_rsrcUN.jpg)

If the true range of the variables is known, this range can be used instead of the min and max of the data. While there are other normalization techniques which adjust the data according to its mean or variance (as opposed to range), this is the simplest and most common method. The improvement in result can be seen through the below example with Euclidean distance:

Table 2: Normalization Example

 
| Sample || Humidity (%) || Temp (°F) || Wind Speed (mph) ||  || Sample || Humidity Norm. || Temp Norm. || Wind Speed Norm. |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 || 0.08 || 90 || 35 || 1 || 0.00 || 1.00 || 1.00 |
| 2 || 0.85 || 65 || 20 || 2 || 0.94 || 0.00 || 0.00 |
| 3 || 0.90 || 85 || 25 || 3 || 1.00 || 0.80 || 0.33 |

| Distance || Sample 1 || Sample 2 || Sample 3 ||  || Distance || Sample 1 || Sample 2 || Sample 3 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Sample 1 || 0.00 || 29.16 || 11.21 ||  || Sample 1 || 0.00 || 1.70 || 1.22 |
| Sample 2 || 29.16 || 0.00 || 20.62 ||  || Sample 2 || 1.70 || 0.00 || 0.87 |
| Sample 3 || 11.21 || 20.62 || 0.00 ||  || Sample 3 || 1.22 || 0.87 || 0.00 |

It is clear how, without normalization, sample 3 is about twice as far from sample 2 as it is from sample 1. This is due primarily to the close temperatures of samples 1 and 3; however, this nearly ignores the fact that the humidity and wind speed of samples 2 and 3 are very close. If the goal of the classifier is to predict rainy days, this will not work. After normalization, samples 2 and 3 are the closest to each other, which seems reasonable given the close humidity and wind speeds.

After defining the distance metric and normalization, k-Nearest Neighbors (kNN) can be used for classification or regression tasks. In classification, the mode of the output classes of the k-nearest data points is used as the classification decision for each unknown data point. Looking at the example data below, if k = 1 then the algorithm will only look at the closest data point. This will be data sample # 3, which is class A; therefore, with k = 1 the new data point is assigned to class A. In binary classification, it is customary to only use odd number for k to avoid the case where the new point is equidistant from 2 points with different classes. If k is increased to 3, utilizing Euclidean or Manhattan distance, the closest sample points are # 3, 5, and 7 which are classes A, B, and B respectively. Therefore, with k=3, the new point is assigned to class B. The task for regression is performed in the same way, except the output classes will have k numeric values instead of discrete classes. A typical solution to this is to take a weighted mean of these numeric values, where each value is weighted by its distance from the new point (the closer values having a higher weight).

Table 3: Example data for NN classification

 
|  || Input Vector || Output |
| --- | --- | --- |
| Sample || x1 || x2 || y |
| 1 || 1 || 2 || B |
| 2 || 2 || 2 || B |
| 3 || 1 || 0 || A |
| 4 || 2 || 1 || A |
| 5 || 2 || 0 || B |
| 6 || 3 || 0 || A |
| 7 || 1 || 1 || B |
| 8 || 0 || 2 || A |
| 9 || 0 || 1 || B |
| 10 || 3 || 2 || B |
|  |
| New || 1 || 0 || ? |
|  ||  ||  ||  |

In supervised learning, it is often impossible to look at the results and determine how well the algorithm is working. By definition, engineers use the trained algorithm to determine unknown data, so they do not have any known true values to compare against. This leaves them with no objective function for which to evaluate the performance of the classifier. In the kNN application, engineers needs to choose the k value; in order to do this they need to know if k = 1 performs better or worse than k = 5. To solve this problem, they should create an artificial unknown dataset from the known sample data. In other words, some of the labeled data is taken and the labels are removed. Then, they can take these unlabeled vectors, use the algorithm to determine the output, and compare this to the true labels. These will be referred to as the training data (that which is still labeled) and the test data (the artificial unknown data).

Using this new dataset, it is necessary to develop an objective function to evaluate algorithm performance. The objective function of the entire model is typically a combination of its performance on each individual data point in the training set. In classification situations, a common evaluation function (often called a loss or cost function) is just a comparison between the predicted value (from the algorithm) and the known true class. Then, all of these comparisons are added and divided by the number of points in the test set. For a test set of n data points with Y as the known labels and Ŷ as the predicted labels, this loss function is expressed as:

![](image_rsrcUP.jpg)

For regression problems there are different methods for computing loss, just as there are different distance functions for continuous variables. The simplest regression losses are the mean squared error (MSE) and mean absolute error (MAE), which are analogous to the Euclidean and Manhattan distances. The equations for each are shown below:

![](image_rsrcUR.jpg)

Depending on the size of the known dataset and the application, about 5-30% of the sample points should be removed to join the test data. To select which data points get removed to be  part of the test data, a random selection is typically performed in order to avoid any human bias. Even with a random selection, it is possible that bias is introduced in the train-test split. To eliminate this, cross-validation can be implemented to generate multiple pairs of training and test sets. For example, cross validation can be used to divide the dataset randomly into 10 groups. Then the algorithm will be trained 10 times, each time treating 9 of these groups as the training data and the 10th as the test data. After training on all these different datasets any bias should be removed; in addition, the engineer has a better gauge for performance range of the model, since each training and test set pair will yield a different accuracy score.

## Decision Trees and Random Forests

When discussing kNN, the labeled data was split into training and test sets; however, it was never really discussed what it means to train a classifier or regressor. From here on, the algorithm (classification or regression) will be referred to as a model, since it is trying to build a prediction of the real world based on data. In general, a model will have some parameters that can adjust how it makes predictions. Training the model is the process of adjusting these parameters to fit the training data. A kNN model is very simple, the only parameter that needed to be chosen was k. With this definition, training a kNN model would involve trying several different k values and seeing which resulted in the best (lowest) result from the loss function.

A decision tree model follows the same structure as the goal trees that have been used repeatedly in this overview. The difference here is that the tree structure and decision nodes are determined by the training data. Whereas a kNN model compared the distance between all features of a vector, the decision tree will look at the features individually in order to create its prediction. Each node will only look at one feature of the training data, and it will make a decision based upon the value of that feature. These models will be described for a classification application, but they can also be used for regression problems. They can also be used for input vectors with continuous or discrete values; for continuous variables, each node will be a threshold. A weather-based example is shown below, where the data has three features with the following domains: Outlook \[Sunny, Overcast, Rain\], Humidity \[High, Normal\], and Wind \[Strong, Weak\]. Note that the tree reaches different depths along different branches, and that along the same level of the tree different branches can split according to different features.

![](image_rsrcUS.jpg)

Figure 11: Simple decision tree example

With a decision tree model, the parameters to be chosen are the order of features to be evaluated at each level, as well as the threshold values for continuous variables. It is beneficial to have a tree which splits the data cleanly into classes in as few branches as possible. To develop the tree the engineer needs a measure of class division, so that each node can split the data in the most efficient way. The standard measure of this division is entropy, a term borrowed from physics where it means the disorder of a system. The goal is to divide the data in a way that minimizes disorder, and therefore groups the data into cleanly defined classes. The entropy equation is shown below, where p(xi) represents the percentage of samples assigned to each class i.

![](image_rsrcUT.jpg)

With entropy measurable for each possible split of the data, the engineer can simply evaluate the possible options at each node. At the top node: measure the entropy if data is split along feature X1, measure again if it is split along X2, etc, and choose the split that minimizes entropy. At level 1 of the tree: now all the data is divided into 2 (or more) groups, and for each group the split should be decided separately by again evaluating all options and choosing the lowest entropy.

If the dataset is large and complex enough, this process of dividing the data can go on almost indefinitely. In practice the tree is usually limited to a certain depth (often around 10 or 20 levels), since the tree grows exponentially in size. If a tree is deep enough it can fit the training data perfectly; in other words, it will predict the class of the training data correctly on 100% of the samples. While this may sound beneficial, it is useful to remember that the goal is to predict the behavior of unseen data. There is always some noise or bias present in real world datasets; this means that the unseen data the algorithm will encounter will not behave exactly like the training data. If the model is near 100% accuracy on the training data, most likely it is identifying patterns in noise and bias in the training data as opposed to the true behavior of the underlying data. When the model fits the training data too well it is called overfitting; conversely when the model is too simple for the training or test data it is termed underfitting. Looking at the plots below, the best result is the model from the middle plot; even though the training accuracy of the third plot will be the highest, it will have lower accuracy on the test data.

![](image_rsrcUU.jpg)

Figure 12: Underfitting vs. Overfitting

Comparing the accuracy of the model on the training data and the test data can tell us when a model is overfitting, but now the engineer needs to solve this problem. Methods designed to prevent overfitting are called regularization techniques. One technique is to use cross validation as described previously, which serves to train the model on different pairs of training and testing datasets which will help account for bias in any one set. Another technique is to use an ensemble method. An ensemble model, broadly, is a model that combines several other models. A common ensemble model utilizing decision trees is called a random forest. The name of the method, unsurprisingly, comes from the idea that many trees combine to create a forest.

A random forest uses multiple shallow trees, each of which would underfit the training data if used alone. The attributes to be used for each tree are selected at random before training begins, and each tree is trained independently to a fixed depth (i.e. 5 levels). The training data itself can also be randomly sampled. In a standard decision tree, the model will select the attributes that provide the greatest information gain given all of the training data. If some of these attributes are removed, that tree can no longer rely on them to make decisions, it must therefore rely on other attributes. Similarly, if some of the training data is randomly removed then the bias present in those samples is removed from the tree. The random sampling of features and samples is done with replacement; this means that the sampling for every tree is done using all original features and data, independent of what features or data samples were selected for other trees.

After training a random forest, the model is comprised of several shallow trees, each of which can make a computationally quick prediction. These separate predictions are combined into the ensemble model to generate one output for each sample in the test set. In classification problems, the majority decision of the trees is typically used; as with a kNN model, it is therefore beneficial to use an odd number of trees for binary classification. In regression problems, the individual outputs are typically averaged to come to the ensemble prediction. It is also possible to unequally weigh the output of each model according to some criteria (i.e. its accuracy on the training or test data).

## Neural Networks

The latest rage in machine learning is a supervised model called an artificial neural network (ANN or simply NN). The concept has been around for many decades, but recent advances in processing power have allowed ANNs to provide amazing results for many machine learning tasks. Neural networks cannot mimic the function of the human brain, but the name originates from the idea that many “neurons” making simple decisions can be combined to make a complex decision in the same general way that a brain is believed to function.

First, it is worthwhile to examine the functionality of a single neuron in the network; one neuron can be used alone as a simple machine learning model for linear or logistic regression. Logistic regression is another method for binary classification, where a regression output is transformed to be either 0 or 1. Given an input vector x = \[x1, x2, … xn\] the model will make a prediction ŷ. Each neuron encompasses two functions: a linear combination of all input variables, and then an activation function on this combination. The equation and schematic of a single neuron will look like this, where g is the activation function:

![](image_rsrcUV.jpg)![](image_rsrcUW.jpg)

Figure 13: Schematic of one neuron

The diagram makes clear that there are two separate steps: first all of the input variables xi are multiplied by some weight wi, these are added together with some constant bias term b; it is common to refer to this sum as the activation a. This activation is passed as input to some activation function g(a), which yields ŷ. The weights w and bias b are the model parameters which will be trained. Different activation functions exist but two common ones are the sigmoid and ReLU functions. These two functions are similar in that they have a nonlinearity at a = 0; this is key to provide a decision boundary to the neuron. In other words, if the activation a is below 0 then ŷ will equal 0 (or very close to it); if the activation function a is above 0, then ŷ will also be greater than 0. Their equations and graphs are shown below. For the remainder of this overview the default activation function will be the sigmoid function unless otherwise noted.

![](image_rsrcUX.jpg)

Figure 14: Two common activation functions

The primary technique to train a neuron is called backpropagation: it updates the weights wi and b in order to fit the training data. The equations to calculate backpropagation are derived from partial derivatives of the loss function, and therefore are particular to the loss function utilized by the model. Many problems in machine learning can be reduced to binary classification, which is simply classification where there are only two output classes. The process of training a one neuron network will be demonstrated in this format, although the process for more complex problems is similar. As an example, the entropy loss function will be used as defined below:

![](image_rsrcUY.jpg)

Given that yi will be either 0 or 1 for each example in the training or test set, the loss will evaluate to either -![](image_rsrcUZ.jpg)(if yi = 1) or ![](image_rsrcV0.jpg)(if yi = 0). To understand why this works well as a loss function, the behavior of the logarithmic function is important to understand. The log function, regardless of what base is used, equals 0 when its input is 1 and equals ![](image_rsrcV1.jpg)when its input is 0. Looking again at the plot of the sigmoid activation function, ![](image_rsrcV2.jpg)will be some value between 0 and 1. The goal of training the classifier is for ![](image_rsrcV2.jpg)to be very close to 1 when yi = 1 and very close to 0 when yi = 0. Therefore, if yi = 1 and ![](image_rsrcV2.jpg)is a value close to 1, then the loss on that example will be very small; however, if yi = 1 and ![](image_rsrcV2.jpg)is very close to 0, the loss will be very large as the loss approaches ![](image_rsrcV3.jpg)as ![](image_rsrcV2.jpg)approaches 0. The same relationship is true for examples where yi = 0. It is clear this loss function heavily penalizes instances where the model incorrectly predicts the output.

An ideal classifier will predict every example in the test set correctly, which would result in a loss function evaluating to zero. Therefore, the goal of training a neural network is to minimize the loss function by adjusting the model parameters wi and b. From calculus, the minimum of a function is always located where its derivative equals 0. Since the loss function depends on multiple variables (parameters), the partial derivative with respect to each variable must be computed. Using the partial derivatives of the loss function, each individual parameter will be updated by a small step after evaluating each example from the training set. The size of this step is determined by a value chosen before training begins, called the learning rate α. This introduces the concept of a model hyperparameter. The model parameters are adjusted automatically by backpropagation during training. The term hyperparameter is a feature of the model that is not automatically adjusted but must be chosen by the engineer when designing the model. Methods for choosing hyperparameters will be discussed later when large neural networks are considered.

After the model output for each training example is evaluated against the training set y values, each parameter will be updated according to the following formula:

![](image_rsrcV4.jpg)

In other words, each parameter is adjusted according to how much of the loss function can be attributed to that parameter. If a particular xi has a very large magnitude, then it will have a large impact on the value of y. If that input value xi is very important to the determination of y, then it is appropriate for it to have a large impact. However, if variations in that particular xi should only have a small impact on y, then the weight on that input should be reduced. By repeating this process over and over for every example in the training set, the model slowly adjusts weights until they minimize the loss function. For each input feature, if the majority of training examples show that a high xi should result in a 1 classification, then the weight wi corresponding to that input will increase. Similarly, if the majority of training examples agree on a 0 classification with a high xi, the weight wi will decrease until it is a large negative value. If the training set is inconsistent about the value of y given xi, then the weight wi will decrease towards 0 so that attribute xi has a very small impact on the predicted output ŷ. Working with only one neuron, the model is not very flexible so in most cases the minimum of the loss function will still have relatively poor accuracy.

Calculating derivatives is very common in many machine learning applications. Mathematically, the derivative is defined as the rate of change of a function at a specific value. Knowing the rate and direction of change is very valuable when trying to understand the behavior of that underlying (unknown) function. For example, if the optimization objective is to find the global maximum or global minimum, it would make sense to obtain the gradient at several locations. The gradients identify which direction is “uphill” or “downhill”. If they all point towards one point being the global optimum, then it is worthwhile investigating that location for the optimum. If they all point in different directions, most likely the underlying function has multiple local optima. The technique of computing a gradient and moving “downhill” or “uphill” from that point is called gradient descent or gradient ascent.

The example shown so far has dealt with only one neuron acting independently; however, the purpose of a neural network is to combine many neurons together so that their combined output can approximate a very complex function. In fact, most modern neural networks consist of hundreds or thousands of neurons. In a standard network, each neuron functions exactly as described above; it takes in many inputs, calculates a weighted sum of those inputs, and then passes that sum through a nonlinear function to generate one output. Although it may seem like a simple idea, combining many of these neurons together enables a network to fit nearly any complex function.

![](image_rsrcV5.jpg)

Figure 15: Example of a neural network with 3 layers (2 hidden layers and 1 output layer)

As can be seen in the image of a larger network, each attribute of the input is passed to each neuron in the first layer. Similarly, the output from each neuron in the first layer is passed to each neuron in the second layer. This means that each input can be processed in a different way by different neurons (using different weights), and similarly the output from each neuron can be processed multiple ways. The input values are sometimes called the input layer, but these are simply the values from the normalized data. The figure shown above is a neural network with 3 layers (not counting the input data as a layer); the last layer is called the output layer and all other layers are termed hidden layers since their output is usually not seen. This structure is called a dense or fully-connected network, since each neuron is connected to all neurons in the layers directly adjacent to its layer.

The process of training a large network is identical to the example shown for one neuron. Each example in the training set is passed through the network which calculates ŷ given the input values and current weights; this is also called forward propagation. Then, the loss for each example is calculated and backpropagated to update all weights. Of course, the mathematics to determine the partial derivatives for backpropagation become increasingly complicated as the network grows. Luckily, many software programs exist which are designed specifically for use with neural networks. They provide frameworks wherein it is very easy to define the structure of a network; in addition, they calculate the partial derivatives for backpropagation automatically.

Extrapolating from the one neuron example, it is clear that a larger network will contain many parameters which need to be adjusted during training. Even with software tools, the task of training a large network is very computationally expensive and can often take hours or days on a normal processor. In the earlier description of backpropagation and neuron function, calculations were performed individually by one neuron. In large networks with many neurons, having each neuron evaluated individually is a huge inefficiency. The process can be streamlined so that these calculations are performed in parallel, known as vectorization. Any software package designed for working with neural networks will include this functionality by default. Computer hardware also plays a factor in the time required to train a network; any serious application of neural networks will utilize GPUs (graphics processing units) for training as opposed to CPUs (central processing units). CPUs perform calculations one at a time, whereas GPUs can perform many (simple) calculations simultaneously; since this is exactly what needs to be done when training a neural network, a GPU can train the same network in a fraction of the time that it would take a CPU.

Many high-profile machine learning problems have recently been tackled with neural networks, often called deep learning. Deep learning is simply a term to represent neural networks with many layers, although the term “deep” is now being adopted by other methods which work in similar ways. There is no threshold to define what a deep network is, but some implementations have contained over 1000 layers with tens of thousands of neurons. In almost all situations, a network of this size is not necessary. There are various other network architectures which can improve accuracy without adding numerous layers. More advanced networks make use of convolutional layers, recurrent layers, residual networks, and many other techniques which will not be discussed in this overview.

Although the training of a neural network can be handled fairly easily with the correct software tools, there are still many network structure options which need to be decided on by the engineer. For example: is it better to have 4 layers of 5 neurons each or 5 layers of 4 neurons each? The engineer also needs to decide what learning rate to use, which activation function to use, which optimization algorithm to use, etc. There are no clear rules for making these decisions, and they typically involve some trial and error. A good technique is to find published research which tackles a related application. If a researcher was able to achieve high performance on a similar problem with a specific network, most likely it can be duplicated for similar performance. Many papers published on neural networks are the end result of numerous months of trial and error, utilizing different network architectures. In deep learning applications, it is often possible to find the fully trained network available online. Due to the large computational requirements of training deep networks, implementing a pre-trained network can save many hours of computational time. Of course, the weights trained on a particular dataset may or may not provide adequate performance on new samples.

An engineer experimenting with different networks needs a method to determine which design yields the best performance. Expanding the rationale used for splitting the labeled data into training and test sets, labeled data is often split 3 ways to obtain another test set (typically named the validation set). The engineer then uses the training data for training different model designs, then each of these designs is evaluated on the validation set, and the model with the best performance on the validation set is chosen. After deciding on the model, it is evaluated on the test set in order to obtain an estimate of its prediction accuracy on unseen examples.

The validation or test set is also used to determine how many iterations of training are needed for the model. An iteration is simply the process of passing all training samples to the algorithm once. As is the case with most supervised learning algorithms, neural networks tend to overfit the training data. The neural network will adjust its weights on every iteration to better fit the training data. Again, the goal is to identify the patterns in the training data which are true for the underlying population without identifying the patterns (noise) which are present in only the training data. To determine how long this will take, it is best to observe the training and validation errors after every iterations of training. In the figure below, the error is plotted against the number of training iterations; the goal is to minimize the error on the test set. As training begins, the error for both training and validation sets decreases. If training continues, the error on the training set will continue to drop but the validation error will begin to rise. This is caused by the model overfitting the training data. By monitoring the validation error, the engineer can ensure that training ends when the validation error reaches a minimum; this will most likely correspond to where the test set error reaches a minimum as well.

![](image_rsrcV6.jpg)

Figure 16: Training and Validation errors

## Genetic Algorithms

Also called evolutionary algorithms, genetic algorithms are another optimization technique that can be applied to a wide variety of problems. The general concept is to start with a population of many possible solutions to a problem. Each individual solution in this population is scored according to some objective function. Then, the high scoring individuals are combined in some method to create a new population. The idea originates from the theory of evolution, in which the individuals most fit for their environment reproduce at higher rates than those less fit. Biological evolution takes many generations to converge to an optimal solution; similarly, genetic algorithms are typically slow to converge. Depending upon the implementation, however, they are sometimes able to escape from local optima and reach global optima.

Genetic algorithms are often implemented with crossover; crossover is a set method of combining samples from the population to produce new examples. Given two samples (expressed as 1 dimensional vectors), a simple method is to take the first half of one and the second half of the other. This can be seen in the simple example diagram shown below. The two “parent” samples (A1 & A2) from the initial population are combined to create two “child” samples (A5 & A6) for the second generation. The red line at the middle of the vector is called the crossover point, since the samples are split there and swapped. Crossover could also involve swapping the two middle genes, or swapping then rearranging the last 2 genes, or any combination imaginable.

![](image_rsrcV7.jpg)

Figure 17: Example of one generation of a genetic algorithm

After the first crossover is performed as shown, the new population of 4 samples (A3, A4, A5, and A6) is again evaluated with the objective function. Again, the two highest scoring samples are combined and replaced to form a new generation. This process can be repeated indefinitely until a local optimum is reached. Depending on how large the initial population is, this can take many iterations. Similar to the hill-climbing method, genetic algorithms are prone to identifying local optima as opposed to global optima. The most popular technique for avoiding this is to allow “genetic mutations” in the population. Borrowing another term from biology, this is the concept of allowing samples to change outside of the features that they “inherit” from the previous population.

Returning to the above example, the two samples A5 and A6 inherited all of their genes directly from samples A1 and A2. If mutations were allowed, some of these genes could change according to another rule; typically, this rule is just random chance. For example, mutations could be allowed on the first and last genes with a 50% random chance. In this case, each sample in the new population (A5 and A6) would have a 50% chance of a 0 or a 1 for the first and last features. Since the new population will be re-evaluated according to the objective function, undesired mutations (as well as undesired inherited traits) will naturally be eliminated from the population as more crossovers take place. By allowing random changes in the population’s genes, mutations help prevent the algorithm from getting stuck in a local optimum.

## Support Vector Machines

In classification problems, the objective is to determine the class of an unknown sample based upon its input features. This goal can be conceptualized as finding the boundary between the different classes in the input space, where the input space contains the number of dimensions of the input features. This boundary is typically called the decision boundary, since samples on one side of the boundary will be classified differently from those on the other side.

Support vector machines (SVMs) are based upon the idea that, in order to build a classifier, it is not necessary to evaluate every point in the training set. It is only necessary to identify all decision boundaries; and in order to identify a boundary, only the points on either side of it must be evaluated. If two groups of data are able to be separated by a single line, most likely there are multiple lines which can separate them. The SVM method assumes that the best dividing line is that which is furthest away from all points along the boundary. The distance from the closest data point to the boundary is termed the margin. With SVMs, the goal will be to find a straight line which maximizes this margin. Looking at the simple 2-dimensional figure below there are many lines which can correctly divide all of the sample points, of which two are shown. The optimal dividing line is the black horizontal line, since its margin is greater than the green line’s margin. Traditional SVMs, as presented here, can only be used to classify data that is able to be separated by a straight line. If a nonlinear decision boundary is required, the data must be projected onto another space where it is linearly separable.

![](image_rsrcV8.jpg)

Figure 18: Two possible decision boundaries to separate the negative class from the positive class

Given a two-dimensional input, as shown in the figure above, each data point x will have two features (x1, x2). The classifier’s goal is to take in these features and output a class ŷ, which will be either -1 or 1 since this is binary classification. In logistic regression the decision boundary is set at 0; if ŷ evaluates to any negative value it is classified as the negative class (-1), and if it is positive then the +1 class. However, in order to create some margin between the classes, two decision boundaries will be defined. First, if ŷ is greater than or equal to 1 then the point will be classified as positive. Similarly, if ŷ is less than or equal to -1 then the point will be classified as negative. This forces the classifier to be more cautious with its decision; ŷ must clearly belong to one class or another. Given the multi-dimensional input x, the equation used by an SVM is:

![](image_rsrcV9.jpg)

Where ω is a vector of parameters of the same length as x. For a two-dimensional problem this is equal to:  
![](image_rsrcVA.jpg) 

To determine the decision boundaries, this equation for ŷ is set equal to the limits defined above. Since the goal is to have all positive training examples greater than or equal to 1, the only points that are necessary to define the boundary are those that lie on it. These points will be equal to 1, and every other positive point will be greater than 1. The inverse is true for the negative class. In the above diagram, the points closest to the black boundary have a thicker circle around them. Substituting the features of these three boundary points into the ŷ equation (equal to +1 and -1 respectively) will create a system of equations where only the ω parameters are unknown. Solving this system of equations yields the equation for the classifier. By solving the problem in this manner, it forces the classifier to obtain an equation which maximizes the distance between the two classes.

After the classifier equation has been obtained, it can be used on the validation and training data sets to determine its accuracy. Although in the training data the equation was defined so that all points evaluated to above +1 or below -1, in new data this will not necessarily be true. In this case, the decision boundary is set at the 0 value, as shown by the black solid line in the diagram. The dashed boundaries at +1 and -1 are only needed to ensure the line chosen maximizes the margin between classes.

## Boosting

An ensemble model is any model which combines the output of several other models. This generic description of an ensemble can be interpreted in several ways. The random forest classifier, as discussed, can easily be viewed as an ensemble of decision trees. Similarly, an individual decision tree can be viewed as an ensemble of many small binary classifiers. In the standard decision tree each node divides the dataset according to the value of only one feature; each of these nodes can be seen as a very simple classification model. The boosting method can be applied to any ensemble type model and will be introduced here through its application on a relatively simple decision tree classifier. Boosting has been shown to provide significant performance improvement over a non-boosted ensemble, and it is often utilized in winning solutions to online competitions.

The most popular boosting algorithm is called Adaboost, which is short for adaptive boosting. The concept originated from the idea that each individual model will perform well on some data points, and that the samples it performs poorly on will be better evaluated by another model. Therefore, many simple “weak” classifiers can be combined in order to form a “strong” classifier. The key to boosting is that each weak model is given a weight wt with which its results will be weighted. Utilizing this weight, the equation for the ensemble model output will be:

![](image_rsrcVB.jpg)

Where ht(x) is the output of each individual classifier, and there is a total of T classifiers. In general, more weight will be placed on classifiers which perform better on the training data.

This concept is clear and is in fact just a generalized version of the equation used by the random forest classifier; with random forest the weights on each decision tree were equal, with boosting these weights are unequal. The Adaboost algorithm is used in order to determine the value of these weights wt. These weights are parameters of the ensemble model, and therefore are learned during training. Another weight is introduced, αi, which will be utilized only during training. The weights wt are determined during training but really only utilized on the validation and test sets, as well as after the model is finalized. The αi weights will be used to weigh individual training samples, completely separate from the wt weights. The αi weight is used to place greater emphasis (higher weight) on training examples for which the previous classifiers performed poorly. Weighing these samples forces the next classifier to focus on predicting them correctly. The overall process flow for Adaboost will follow the figure below.

![](image_rsrcVC.jpg)

Figure 19: Adaboost overall process flow

Assume that the classifier is being trained on data for which the output class may be either 0 or 1, and for which each data point has 2 dimensions (x1, x2). Utilizing all samples in the training data the initial data weights αi are set equal, since it has not yet been determined on which samples the classifiers behave poorly. For simplicity, the initial weights are all equal to (1/N), where N is the number of samples in the training set. The training data is then used to train the first classifier h1(x), where the classifier evaluates (x1, x2) for each data point. The predicted output from this classifier ŷ is compared to the true labeled value of each training sample, and the weighted error of ht(x) is calculated as:

![](image_rsrcVD.jpg)

Note that this error value ranges between 0 and 1. For the first classifier, all αi weights are equal so it treats all samples equally; however, after these weights are adjusted they force the classifier to fit samples with higher weights. Utilizing this equation places a greater penalty on data points with higher αi weights; since the classifier will be trained so that it minimizes the error, it will give priority to fitting the points with larger weights. Utilizing this error Et, the weight wt for the newly trained classifier ht(x) will be calculated as:

![](image_rsrcVE.jpg)

The natural logarithm evaluates to zero at 1; in the binary classification problem this is equal to Et = 0.5; this is the error that would be predicted from a classifier which generates random guesses. As the error approaches zero, wt will increase. Similarly, as the error approaches 1, wt will go further negative. If the classifier has 0 error and predicts all samples perfectly, wt will evaluate to infinity; in this situation boosting is not necessary and the weak classifier can be used alone. Allowing for negative wt weights, although counterintuitive, functions very well for binary classification. If an individual classifier performs poorly on a dataset (error of greater than 0.5), then its inverse will perform better. In this case, using a negative weight will invert the classifier predictions and improve overall accuracy.

After updating the classifier weights wt, the data weights αi must also be updated as shown in the flow chart. The goal is to place a higher weight on the samples which were previously misclassified, and a lower weight on those samples which were correctly classified. This is performed according to the below equation:

![](image_rsrcVF.jpg)

Utilizing these equations, the process is repeated multiple times until multiple weak classifiers have been trained on the data, and each one has a weight associated with it. Typically, classifiers will be added until the model reaches a goal accuracy or until the test set accuracy plateaus. After training is complete, the αi weights can be discarded as only the wt model weights will be needed to use the ensemble model. If enough weak classifiers are added to the model, a boosted classifier can eventually fit the training data perfectly. Of course, this brings with it the possibility of overfitting. For this reason, the test and validation set accuracies should be monitored during training in the same fashion they were monitored when training a deep neural network.

## Conclusion

This overview has introduced many different types of algorithms for machine learning and data analysis, the majority of which were covered at a very shallow depth. In addition, the examples provided made some simplistic assumptions that are often not true in real world data. The foundation presented here is meant to provide a guide for those interested in learning more about data science and machine learning, as well as those attempting to solve a problem in the field. Any of the techniques introduced can be applied as described; however, there are typically numerous variations and additions to each of the algorithms which can tailor it for a specific application and yield superior results.

It is recommended to research an individual topic in greater depth before implementing it on a real-world problem. There are numerous other machine learning techniques which have not been addressed here and may be better suited to a particular problem. Many of these techniques, however, share mathematics and underlying logic with the surface level content of this overview. A solid understanding of the theoretical background behind a specific algorithm is necessary in order to effectively apply it. Most machine learning techniques can be readily applied with publicly available software tools, but it is up to the engineer to choose the correct algorithm and approach.

Recent advancements in machine learning have caused some expectations of the field to be sensationalized. From the introduction provided here, it should be clear that a machine learning algorithm is not a form of intelligence and is certainly not sentient. The field simply applies algorithms in order to recognize patterns in data and navigate these patterns. Machine learning has been successfully applied in almost every field of study and can reap significant performance and efficiency benefits.

## Online Resources

[Other books about science by Charles River Editors](http://www.amazon.com/mn/search/ref=as_li_ss_tl?_encoding=UTF8&camp=1789&creative=390957&field-keywords=charles%20river%20editors%20science&linkCode=ur2&tag=crebooksinternal-20&url=search-alias%3Daps&linkId=52EAEUNKKBTEJMQX)

[Other books about machine learning on Amazon](http://www.amazon.com/mn/search/ref=as_li_ss_tl?_encoding=UTF8&camp=1789&creative=390957&field-keywords=charles%20river%20editors%20ancient%20history&linkCode=ur2&tag=crebooksinternal-20&url=search-alias%3Daps&linkId=52EAEUNKKBTEJMQX)

## Bibliography

Starner, Thad. Georgia Tech OMSCS 6601 course materials. [https://www.cc.gatech.edu/~thad/6601-gradAI-fall2015/Schedule.html](https://www.cc.gatech.edu/~thad/6601-gradAI-fall2015/Schedule.html)

Computational Creativity Research Group. Search in Problem Solving. [http://ccg.doc.gold.ac.uk/ccg\_old/teaching/artificial\_intelligence/lecture3.html](http://ccg.doc.gold.ac.uk/ccg_old/teaching/artificial_intelligence/lecture3.html)

Jensi, R. and G. Wiselin Jiji. “A Survey on optimization approaches to text document clustering.” CoRR abs/1401.2229 (2014)

Scikit Learn. Underfitting vs. Overfitting. [http://scikit-learn.org/stable/auto\_examples/model\_selection/plot\_underfitting\_overfitting.html](http://scikit-learn.org/stable/auto_examples/model_selection/plot_underfitting_overfitting.html)

Neural Networks and Machine Learning. Cornell University Blog for CS 2850. [http://blogs.cornell.edu/info2040/2015/09/08/neural-networks-and-machine-learning/](http://blogs.cornell.edu/info2040/2015/09/08/neural-networks-and-machine-learning/)

Sharma, Sagar. Activation Functions: Neural Networks. Towards Data Science. (2017) [https://towardsdatascience.com/activation-functions-neural-networks-1cbd9f8d91d6](https://towardsdatascience.com/activation-functions-neural-networks-1cbd9f8d91d6)

Ng, Andrew. Machine Learning. [https://www.coursera.org/learn/machine-learning](https://www.coursera.org/learn/machine-learning)

Nielsen, Michael. Neural Networks and Deep Learning. (2017) [http://neuralnetworksanddeeplearning.com/chap1.html](http://neuralnetworksanddeeplearning.com/chap1.html)

EliteDataScience. Overfitting in Machine Learning: What it is and how to Prevent it. (2017) [https://elitedatascience.com/overfitting-in-machine-learning](https://elitedatascience.com/overfitting-in-machine-learning)

Mallawaarachchi, Vijini. Introduction to Genetic Algorithms. (2017) [https://towardsdatascience.com/introduction-to-genetic-algorithms-including-example-code-e396e98d8bf3](https://towardsdatascience.com/introduction-to-genetic-algorithms-including-example-code-e396e98d8bf3)

# Free Books by Charles River Editors

We have brand new titles available for free most days of the week. To see which of our titles are currently free, [click on this link](https://www.amazon.com/s/&rh=n:154606011,p_36:0-0&field-keywords=Charles%20River%20Editors/ref=as_li_ss_tl?_encoding=UTF8&linkId=MLBAO6PXTATGNGTA&linkCode=sl2&tag=httpwwwcharle-20&linkId=121341aa0eab529875dfdd5df7929881).

# Discounted Books by Charles River Editors

We have titles at a discount price of just 99 cents everyday. To see which of our titles are currently 99 cents, [click on this link](https://www.amazon.com/s/?tag=httpwwwcharle-20&rh=n:154606011,p_36:99-99&field-keywords=%22Charles%20River%20Editors%22).