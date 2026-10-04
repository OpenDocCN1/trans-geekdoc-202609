# Machine Learning Algorithms 189

The function creates the Q-Learning agent, agent, which is ready to be trained in the chosen environment.
A MATLAB simulation demonstrating the use of the rlAgent function is described below. The simulation involves the creation of an agent which will be trained to find the optimal path in an environment to achieve the highest reward. An environment interface is first created using the rlPredefinedEnv available in MATLAB's Reinforcement Learning Toolbox. In this example, MATLAB's Basic Grid World is selected as the environment [52]. This environment is a 5x5 grid in which the agent can move to 4 directions: North (action 1), South (action 2), East (action 3) and West (action 4). Initially, the agent is placed at cell [2,1] and must make its way to the terminal state which is at cell [5,5] where a reward of +10 is obtained. The agent is blocked by the black cells as shown in Figure 3.26 and there is a special jump from the cell [2,4] to [4,4] which has a reward of +5. Every other action results in a reward of -1.

| | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---||}{
| 1 | | | | | |
| 2 | | ● | | | |
| 3 | | | | | |
| 4 | | | | +5 | |
| 5 | | | | | +10 |

Figure 3.26. MATLAB's Basic Grid World.

The codes given in Listing 3.38 generate the environment interface with which the agent will interact to learn:

# Listing 3.38. Q-Learning – Generate environment interface

```
rng(0) % For repeatability
env = rlPredefinedEnv("BasicGridWorld");
```

A reset function is created by the line of code given in Listing 3.39 to reset the position of the agent to cell [2,1] at the beginning of each training episode and simulation. Cell [2,1] has state number 2:

# Listing 3.39. Q-Learning – Define reset function

```
env.ResetFcn = @() 2; % Reset position to state 2
```