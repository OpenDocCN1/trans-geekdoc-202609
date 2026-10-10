
# 6

# Learning to Take Action

## Reinforcement Learning

In chapter 1, we discussed *recommendation systems* for predicting customer behavior as an application of machine learning. Given a large data set of customer transactions, we can find *association rules* of the form, “People who buy *X* are also likely to buy *Y*.” Such a rule implies that among the customers who buy *X*, a large percentage have also bought *Y*. So, if we find a customer who has bought *X* but has not bought *Y*, we can target them as a potential *Y* customer. *X* and *Y* can be products, authors, cities to be visited, videos to be watched, and so on; we see many examples of this type of recommendation every day, especially while surfing online.

Though this targeting approach is used frequently, and efficient algorithms have been proposed to learn such rules from very large data sets, interesting algorithms that make use of *generative models* are being proposed these days.

Remember that while constructing a generative model, we think about how we believe the data is generated. In customer behavior therefore, we consider the causes that affect this behavior. We know that people do not buy things at random. Their purchases depend on a number of factors, such as their household composition—that is, how many people they live with, their gender, ages—and their income, their taste (which in turn is a result of other factors such as the place of origin), and so on. Though some companies have loyalty cards and collect some of this information, in practice, most of these factors are not known, are hidden, and need to be inferred from the observed data.

Note, however, that even if we have some idea about what such factors, an overreliance on them can be misguided because they are often wrong or incomplete; there may also be factors that we cannot immediately think of or factors that are not as important as we think, which is why it is always best to learn (discover) them from data.

Extracting such hidden causes will build a much better model than trying to learn associations among products. For example, a hidden factor may be “baby at home,” which will lead to the purchase of different items such as diapers, milk, baby formula, wipes, and so on. So instead of learning association rules between pairs or triples of these items, if we can estimate the hidden baby factor based on past purchases, this will trigger an estimation of whatever it is that has not been bought yet.

In practice, there are many such factors; each customer is affected (or defined) by a number of these, and each factor triggers a subset of the products. The factor values are not 0 or 1 but continuously valued, and this distributed representation provides a richness when it comes to representing customer instances.

This approach aims to find structure by decomposing data into two parts. The first one, the mapping between customers and factors, defines a customer in terms of the factors (with different weights). The second one, the mapping between factors and products, defines a factor in terms of the products (with different weights). In mathematics, we model data using matrices, which is why this approach is called *matrix decomposition*, or sometimes *tensor* decomposition, tensors being matrices with more than two dimensions.

Such a generative approach with hidden factors makes sense in many other applications. Let us take the case of movie recommendations (see figure 16). We have customers who have rented a number of movies and we have a score for each movie they watched, and from those we want to make a recommendation.

The first characteristic of this problem is that we have many customers and many movies, but the data is *sparse*. Every customer has watched only a small percentage of the movies, and most movies have been watched by only a small percentage of the customers. Based on these facts, the learning algorithm needs to be able to generalize and predict successfully, even when new movies or new customers are added to the data.

![](images/13811_016_fig_000.jpg)

In this case too, we can think of hidden factors, such as the age and gender of the customer, which makes certain genres, such as action, comedy, and so on, a more likely choice. Using decomposition, we can define each customer in terms of such factors (in different proportions), and each such factor triggers certain movies (with different probabilities). This is better—easier, cheaper—than trying to come up with rules between pairs of movies. Note again that such factors are not predefined but are automatically discovered during learning; they may not always be easy to interpret or assign a meaning to.

Another possible application area is *document categorization* (Blei 2012). Let us say we have a lot of documents, and each is written using a certain bag of words. Again the data is sparse; each document uses only a small number of words. Here, we can interpret hidden factors as topics. When a reporter writes a report, they want to write about certain topics, so each document is a combination of certain topics, and each topic is written using a subset of all possible words. This is called *latent semantic indexing*. It is clear that this makes more sense than trying to come up with rules such as “People who use the word *X* also use the word *Y*.”

Thinking of how the data is generated through hidden factors and how we believe they combine to generate the observable data is important, and it can make the estimation process much easier. What we discuss here is an additive model where we take a sum of the effects of the hidden factors. Models are not always linear—for example, a factor may inhibit another factor—and learning nonlinear generative models from data is one of the important current research directions in machine learning.

Thinking of how the data is generated through hidden factors and how they combine to generate the observable data is important, and it can make the estimation process much easier.

In the next chapter, we will discuss a different type of scenario where the learning system is an agent that is situated in an environment. The agent, e.g., a robot, has sensors to detect its state in the environment and can take actions, as a result of which it gets a reward or not. As we will see shortly, the aim in this case corresponds to learning what actions should the agent take in which state to maximize the total reward.

Let us say we want to build a machine that learns to play chess. Assume we have a camera to see the positions of the pieces on the board, ours and our opponent’s, and the aim is to decide on our moves so that we win the game.

In this case, learning is difficult because of two reasons. First, it is very costly to have a teacher who will take us through many games, indicating the best move for each board state. Second, in many cases, there is no such thing as the best move; how good a move is depends on the moves that follow. A single move does not count; a sequence of moves is good if after playing them we win the game. The only real feedback is at the end of the game, it’s the result of the game, whether we win or lose.

There is no such thing as the best move. A single move does not count; a sequence of moves is good if after playing them we win the game.

Another example is a robot that is placed in a maze to find a goal location. The robot can move in one of the four compass directions and should make a sequence of movements to reach the goal. There may be obstacles, static or dynamic, that the robot should navigate around. As long as the robot moves around, there is no feedback and the robot tries many moves until it reaches the goal; only then does it get a reward (for correct completion of the task). In this case there is no opponent, but we can have a preference for shorter trajectories—the robot may be running on a battery—which implies that in this case we are playing against time.
