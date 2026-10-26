This is 0.5 or 50% as we might intuitively expect. Now, we might consider the joint probability of rolling an even number with both dice simultaneously. The joint probability for independent random variables is calculated as follows:

$$P(A \cap B) = P(A) \times P(B)\tag{5.4}$$

This is calculated as the probability of rolling an even number for dice1 multiplied by the probability of rolling an even number for dice2. The probability of the first event constrains the probability of the second event.

$$P(\text{dice1} \in \{2,4,6\} \cap \text{dice2} \in \{2,4,6\}) = P(\text{dice1} \in \{2,4,6\}) \times P(\text{dice2} \in \{2,4,6\})\tag{5.5}$$

We know that the probability of rolling an even number of each die is 0.5, therefore the probability of rolling an even number is $\frac{3}{6}$ or 0.5. Plugging that in, we get: 0.5 $\times$ 0.5 (0.25) or 25%. Another way to look at this is to consider that rolling one die gives 6 combinations. Rolling two dice together gives 6 combinations for dice2 for each of the 6 combinations of dice1 or (6 $\times$ 6) 36 combinations. A total of 3 of the 6 combinations of dice1 will be even, and 3 of the 6 combinations of those will be even. That gives (3 $\times$ 3) 9 out of the 36 combinations as an even number of each die or ($\frac{9}{36}$ = 0.25) 25%.

If you are ever in doubt of your probability calculations when working with independent variables with discrete events, think in terms of combinations and things will make sense again. We can construct a table of the joint probabilities based on our knowledge of the domain. The complete table is listed below with dice1 across the top (x-axis) and dice2 along the side (y-axis). The joint probabilities of each event for a given cell are calculated using the joint probability formula, e.g. 0.166 $\times$ 0.166 or 0.027 or about 2.777%.

|   | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| 1 | 0.027 | 0.027 | 0.027 | 0.027 | 0.027 | 0.027 |
| 2 | 0.027 | 0.027 | 0.027 | 0.027 | 0.027 | 0.027 |
| 3 | 0.027 | 0.027 | 0.027 | 0.027 | 0.027 | 0.027 |
| 4 | 0.027 | 0.027 | 0.027 | 0.027 | 0.027 | 0.027 |
| 5 | 0.027 | 0.027 | 0.027 | 0.027 | 0.027 | 0.027 |
| 6 | 0.027 | 0.027 | 0.027 | 0.027 | 0.027 | 0.027 |

Listing 5.1: Example of the joint probability table for rolling two die.

This table captures the joint probability distribution of the events of the two random variables, dice1 and dice2. It is pretty boring, but we can use it to sharpen our understanding of joint and marginal probability of independent variables. For example, the joint probability of rolling a 2 with dice1 and a 2 with dice2 can be read from the table directly as 2.777%. We can explore more elaborate cases, such as rolling a 2 with dice1 and rolling an odd number with dice2. This can be read off as summing the values in the second column for rolling a 2 with dice1 and the first, third, and fifth rows for rolling an odd number with dice2.

$$P(\text{dice1} = 2 \cap \text{dice2} \in \{1,3,5\}) = 0.027 + 0.027 + 0.027\tag{5.6}$$

This comes out to be about 0.083, or about 8.333%. We can also use this table to calculate the marginal probability of dice1 rolling a 2 in the presence of dice2. This is calculated as the sum of an entire column of probabilities for dice1 or a row of probabilities for dice2. For example, we can calculate the marginal probability of rolling a 6 with dice2 as the sum of probabilities