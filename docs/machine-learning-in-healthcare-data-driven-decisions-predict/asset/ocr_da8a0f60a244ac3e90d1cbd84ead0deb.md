![](bbox=[0.11, 0.09, 0.82, 0.67])

Figure 1: Proposed framework.

# 3.2 Multi-objective Optimization via Pareto Front Approximation

The Pareto front P is defined as

```
P = \{J(\theta) \in R^m : \nexists \theta' \text{ with } J(\theta') \succ J(\theta)\} (3)
```

where $J(\theta') \succ J(\theta)$ means $J(\theta')$ dominates $J(\theta)$.