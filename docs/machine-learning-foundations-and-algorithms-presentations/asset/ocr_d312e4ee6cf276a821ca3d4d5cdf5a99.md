# Weight initialization

Q: What happens if we initialize all weights constantly for such a network?

![](bbox=[0.073, 0.375, 0.396, 0.755])

We need random initialization!

+   - First idea: Small random numbers (e.g. gaussian with zero mean and 1e-2 standard deviation)
- Works ok for small networks... how about deep networks?

+   - All the gradients are the same!
- Network can never learn “distinct features”