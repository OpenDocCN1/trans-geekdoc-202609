If you were ever exposed to dot products and got completely lost when your teacher started discussing geometry and cosines and vector lengths, I'm so, so sorry! Your teacher wasn't wrong, but the idea is no more complicated than checking out of the grocery store. There are two things that make the linear combination (expressed in a dot product): (1) we multiply the values pairwise, and (2) we add up all those subresults. These correspond to (1) a single multiplication to create subtotals for each line on a receipt and (2) adding those subtotals together to get your final bill.

You'll also see the dot product written mathematically (using q for quantity and c for cost) as ∑ᵢ qᵢcᵢ. If you haven't seen this notation before, here's a breakdown:

+   1. The ∑, a capital Greek sigma, means add up,
+   2. The qᵢcᵢ means multiply two things, and
+   3. The i ties the pieces together in lockstep like a sequence index.

More briefly, it says, “add up all of the element-wise multiplied q and c.” Even more briefly, we might call this the sum product of the quantities and costs. At our level, we can use sum product as a synonym for dot product.

So, combining NumPy on the left-hand side and mathematics on the right-hand side, we have:

np.dot(quantity,cost) = ∑ᵢ qᵢcᵢ

Sometimes, that will be written as briefly as qc. If I want to emphasize the dot product, or remind you of it, I'll use a bullet (●) as its symbol: q ● c. If you are uncertain about the element-wise or lockstep part, you can use Python's zip function to help you out. It is designed precisely to march, in lockstep, through multiple sequences.

In [13]:

```
for q_i, c_i in zip(quantity, costs):
    print("{:2d} {:5.2f} --> {:5.2f}".format(q_i, c_i, q_i * c_i))

print("Total:",
      sum(q*c for q,c in zip(quantity,costs)))  # cool-kid method
```

2 12.50 --> 25.00
12 0.50 --> 6.00
3 1.75 --> 5.25
Total: 36.25

Remember, we normally let NumPy—via np.dot—do that work for us!

# 2.5.1 Weighted Average

You might be familiar with a simple average—and now you're wondering, “What is a weighted average?” To help you out, the simple average—also called the mean—is an