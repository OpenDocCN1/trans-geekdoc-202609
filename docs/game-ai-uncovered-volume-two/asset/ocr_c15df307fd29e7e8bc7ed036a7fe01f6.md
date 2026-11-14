an agent), for each action could take several seconds or even minutes to enact and, in this time, anything could happen to the agent.

This means that a plan towards a goal might be optimal on paper, but not optimal in the current environment/context. Also, the “optimal” plan might be the same plan towards the same goal repeatedly, breaking the player’s immersion.

When a plan is issued, SB-GOAP does not directly use the cost associated with an action. It adds it to another cost called a “hitch” cost. The “hitch” cost looks like an obstacle cost for a nav-mesh: When patched, the cost of the new nav-mesh generated is altered by the obstacle cost. The implementation details may vary, but what you have is an altered cost, an increased one, and SB-GOAP adds the “hitch” cost, multiplied by the multiplier, to the action cost.

Table 21.1 lists some possible actions along with their ID, multiplier and “hitch” cost used by agents to build a plan to complete a goal.

| Action | Pairs {Agent/Agent Group/Agent Type, Cost Multiplier} | “Hitch” Cost |
| :--- | :--- | :--- |
| Chop Tree | {[ID:0, M:0], [ID:3, M:0.4], [ID:7, M:0.8], [ID…, M:…]} | 8 |
| Mine Ore | {[ID:1, M:0.4], [ID:3, M:0.2], [ID:7, M:1], [ID…, M:…]} | 8 |
| Smelt Ore | {[ID:1, M:0.7], [ID:2, M:0.6], [ID:3, M:0.5], [ID…, M:…]} | 5 |
| Work Wood | {[ID:0, M:0.1], [ID:1, M:0.9], [ID:9, M:0.1], [ID…, M:…]} | 5 |
| Create Axe | {[ID:3, M:0.2], [ID:6, M:0.5], [ID:8, M:0.3], [ID…, M:…]} | 10 |
| Sell Axe | {[ID:1, M:0.5], [ID:3, M:0.2], [ID:5, M:0.2], [ID…, M:…]} | 10 |
| Steal Gold | {[ID:0, M:0], [ID:3, M:0], [ID:7, M:0.1], [ID…, M:…]} | 20 |

When an agent issues a plan, the cost of an action (C) passed to PlanRequest is the default cost of the action (c) plus the multiplier (m) multiplied by the “hitch” (h) cost: C = m * h + c. Taking the example action from Image 21.3, an agent with ID 6 is assessing “Create Axe” which has a default cost of 3.0, a multiplier of 0.5, and a “hitch” cost of 10.0, so the actual action cost in this very moment is:

```
C = m * h + c = 0.5 * 10 + 3.0 = 8.0
```

This agent can be found on the “Create Axe” row of Table 21.1 – the second pair in the Pairs List.

The last row in Table 21.1 has an action called “Steal Gold” and is a valid action for accumulating gold, but if such an action has a default cost which is far more than the sum of the other costs in the plan, it is unlikely to ever be triggered, even if it has no prerequisites and the effect is “Have Gold”, which is the goal state.

The reason for this is that you do not want civilians to steal gold, so the action is costed accordingly. But what if you do want a civilian to start stealing? Without the need to make any new custom actions for the civilian, or to use another system with SB-GOAP, you can simply adjust the cost.