# 10.2 Cluster analysis

validation loss.

One heuristic approach to handle this is to fit models of different orders, $M = 1$ to $M = M_{\max}$. We then plot the error (either the training error, the validation error, or both) as a function of $M$. Based on this plot, the user can make a subjective decision about when the decrease in the objective appears to level off, so that it is unjustified to increase the model complexity further. That is, we select $M$ such that the gain in going from $M$ to $M+1$ clusters is insignificant. If the dataset indeed has a few distinct clusters, this graph will typically look like an elbow, and this method for selecting $M$ in thus sometimes called the _elbow method_. We illustrate it for the $k$-means method in Figure 10.9.