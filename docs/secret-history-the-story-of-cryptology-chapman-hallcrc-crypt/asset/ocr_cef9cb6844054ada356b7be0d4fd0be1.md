![](bbox=[0.26, 0.1, 0.7, 0.49])

Figure 11.1 Claude Shannon (1916–2001). (Attribution 2.0 Generic (CC BY 2.0) by Tekniska museet, https://www.flickr.com/photos/tekniskamuseet/6832884236/sizes/o/.)

For example, suppose the message is a weather report and the various possibilities, along with their probabilities are as follows:

| Message | Probability |
|---|---|
| $M_1$ = Sunny | 0.05 |
| $M_2$ = Cloudy | 0.15 |
| $M_3$ = Partly Cloudy | 0.70 |
| $M_4$ = Rain | 0.10 |

A report of “Sunny” is more surprising than a report of “Partly Cloudy” and can therefore be said to convey more information.

Let the function that measures the amount of information conveyed by a message be denoted by $I(M)$, where $M$ is the message. In general, if the probability of $M_i$ is greater than the probability of $M_j$, we should have $I(M_i) < I(M_j)$. Also, if we receive two weather reports (for different days), the total amount of information received, however we measure it, should be the sum of the information provided by each report; that is, $I(M_i M_j) = I(M_i) + I(M_j)$.

The input of the function $I$ is shown to be the message, but $I$ should really just be a function of the probability of the message; that is, if two messages are equally probable, they should be evaluated as containing the same amount of information. We also want the function $I$ to change continuously as a function of this probability. Informally, a very small change in the probability of a message should not cause a “jump” (discontinuity) in the graph of $I$.