```
fig, ax = plt.subplots(figsize=(4,3))
ax.plot(weights, costs, 'b')

# current best guess at the minimum
weight_min = 3

# we can follow the path downhill from our starting point
# and find out the weight value where our initial, blue graph is
# (approximately) the lowest
for i in range(10):
    # for a weight, we can figure out the cost
    cost_at_min = weight_min**2
    ax.plot(weight_min, cost_at_min, 'ro')

# also, we can figure out the slope (steepness)
# (via a magic incantation called a "derivative")
slope_at_min = 2*weight_min

# new best guess made by walking downhill
step_size = .25
weight_min = weight_min - step_size * slope_at_min

ax.set_xlabel('weight value')
ax.set_ylabel('cost')
print("Approximate location of blue graph minimum:", weight_min)
```

Approximate location of blue graph minimum: 0.0029296875

![](bbox=[0.28, 0.66, 0.68, 0.82])