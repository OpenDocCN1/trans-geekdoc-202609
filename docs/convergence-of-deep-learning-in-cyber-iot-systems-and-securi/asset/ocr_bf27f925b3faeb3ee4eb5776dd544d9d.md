# CONVERGENCE OF DL IN CYBER-IoT SYSTEMS AND SECURITY

0 0 0 0 0 0 0 1 0 0 0 0
0 0 0 0 0 0 0 1 0 0 0
0 1 0 0 0 0 0 0 1 0 0
0 0 1 0 0 0 1000 1 0 0 0
0 0 0 1 0 0 0 0 0 0 1
0 0 0 0 1 0 0 0 1 0 0
0 0 0 0 0 1 0 0 1 0 0
0 0 0 0 0 0 0 1 1 0 1
0 0 0 0 0 0 0 1 0 0 1

Step 3: Initialize the Q-Values with zeroes [0,0,0,0,0,0,0,0,0,0,0]
Step 4: Iterate temporary variable “j” for “n” times:
Randomize the current state
Playable actions:

+   - If reward (Currentstate, j)) > 0
- Playableaction.append (j)
- Nextstate = Randomize (playableactions)
- Step 5: Calculate the temporal difference:

```
TD = R[current_state, next_state] + gamma*Q[next_state, np.arg-max(Q[next_state, next_state])] - Q[current_state, next_state]
```

Q[current_state, next_state] = Q[current_state, next_state] + \alpha*TD

Q-Values:
[[ 0 1661 0 0 0 0 0 0 0 0 0]
[1246 0 2213 0 0 1246 0 0 0 0 0]
[0 1661 0 0 0 0 0 2970 0 0 0]
[0 0 0 0 0 0 0 2225 0 0 0]
[0 0 0 0 0 0 0 0 703 0 0]
[0 1661 0 0 0 0 0 0 931 0 0]
[0 0 0 2213 0 0 3968 2225 0 0 0]
[0 0 0 1661 0 0 2968 0 0 1670 0]
[0 0 0 0 0 528 0 0 936 0 0]
[0 0 0 0 1246 0 0 703 1246 0]
[0 0 0 0 0 0 0 936 0 1661]
[0 0 0 0 0 0 0 2225 0 1246 0]]

* Nike