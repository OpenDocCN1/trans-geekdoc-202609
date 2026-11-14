easy or hard the previous problems were, they all had one thing in common—they treat the input data as gospel.

![](bbox=[0.135, 0.165, 0.85, 0.525])

Figure 9.34: Solved de-acidification model

This doesn't always conform to the reality many businesses find themselves in. Parts are not all to spec, shipments don't always arrive on time, demand doesn't match the forecast, and so on. In other words, there's variability and risk in the data.

How do you take that risk and model it within an optimization model?

# Normally Distributed Data

In the orange juice problem, you're trying to blend juices to take out variability, so is it reasonable to expect that the product you're getting from our suppliers won't have variable specs?

Chances are that shipment of Biondo Commune orange juice you're getting from Egypt won't have an exact 13 Brix/Acid ratio. That may be the expected number, but there's probably some give around it. And oftentimes, that wiggle room can be characterized using a cumulative probability distribution. We used probability distributions earlier in this book when performing the F- and t-tests in Chapter 6, “Regression: The Granddaddy of Supervised Artificial Intelligence.”