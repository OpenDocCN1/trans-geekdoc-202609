# DEEP-Q Learning-BASED INTEIGENT IOT EDGE SOLUTIONS 135

two parameters, an input state S and an action, R will return a numerical
reward by acting as in state S (Table 6.3):

R -->

**Table 6.3** Rewards representation based on business process matrix.

| L1 | L2 | L3 | L4 | L5 | L6 | L7 | L8 | L9 | L10 | L11 | L12 |
|---|---|---|---|---|---|---|---|---|---|---|---||
| L1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| L2 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
| L3 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |
| L4 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |
| L5 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
| L6 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
| L7 | 0 | 0 | 1 | 0 | 0 | 0 | 1000 | 1 | 0 | 0 | 0 |
| L8 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| L9 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 |
| L10 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 |
| L11 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 |
| L12 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |

We have given the highest reward to L7.

6.4.1.2.5.6 Implementation of the Q Learning Algorithm—Module and Interaction Map

Step 1: Initializing the Q Learning parameters - γ = 0.75 and α = 0.9

Step 2: Define location_to_state = {'L1': 0, 'L2': 1, 'L3': 2, 'L4': 3, 'L5': 4, 'L6': 5, 'L7': 6, 'L8': 7, 'L9': 8, 'L10': 9, 'L11': 10, 'L12': 11}

Define actions = {0,1,2,3,4,5,6,7,8,9,10,11}

Define rewards = [

```
0 1 0 0 0 0 0 0 0 0 0
1 0 1 0 0 1 0 0 0 0 0
0 1 0 0 0 1 0 0 0 0 0
```