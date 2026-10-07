# Step 1:

Lets set,
numbers_of_selections = The times the ad_i was selected up to round n.
numbers_of_rewards = The rewards of the ad_i up to round n.

We consider a d size vector. d indicates the number of bandits (in this case of the Ads, i.e. of d = 10). We first create number_of_selections as a list of 0's of size d with all elements equal to 0:

```
numbers_of_selections = [0]*d
```

Similarly we create numbers_of_rewards = [0]*d

So that we can access and update the "Number of Selection" and "Number of Rewards" of the d-th Ad, by accessing the corresponding elements of these two vectors/lists

```
d = 10
numbers_of_selections = [0]*d
numbers_of_rewards = [0]*d
```

# NOTE:

Creating an Empty List of Length 10:

```
l = [None] * 10
l = [None, None, None, None, None, None, None, None, None, None]
```

Assigning a value to an existing element of the above list:

```
l[1] = 5
l = [None, 5, None, None, None, None, None, None, None, None]
```

Similarly we created 10 size list of's as:
name_list[]*10

# Step 2: Notice we have two indices, n-th and i-th Ad. n increments the 10,000 trials and i increments 10 Ads. Hence we need two for loops.

+   We do the following:
ni. The average reward of ad_i up to round n
ii. (n) and
iii. Upper bound of the confidence interval i. Upper-Confidence-Bound for each Ad at round n:

```
for n in range (0, N):
    for i in range (d):
        avg_reward = numbers_of_rewards[i]/numbers_of_selections[i]
        log(n+1) = because of index
        delta = math.sqrt(math.log(n+1))/(2*numbers_of_selections[i])
        upper_conf_bound = avg_reward + delta
```

```
# UCB Implementation
import math
 d is No. of Ads or Number of Bandits
d = 10
N = 10000 # Total number of trials

numbers_of_selections = [0]*d
numbers_of_rewards = [0]*d
or n in range (0, N):
    for i in range (d):
        avg_reward = numbers_of_rewards[i]/numbers_of_selections[i]
        log(n+1) = because of index
        delta = math.sqrt(math.log(n+1))/(2*numbers_of_selections[i])
        upper_conf_bound = avg_reward + delta
```