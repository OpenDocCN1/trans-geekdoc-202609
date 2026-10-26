![](bbox=[0.02, 0.04, 0.07, 0.16])

# DyNet is Optimized for Dynamic Declaration

+   - Key Ingredients
+     - Separate parameter declaration and graph construction
+     - Declare trainable parameters and construct models first
+     - Construct computation graphs
+     - Conclusion: Define parameter once, but define graphs dynamically depending on inputs → therefore making the graph construction lighter-weight

```
model = dy.Model()

pW = model.add_parameters((20,4))
pb = model.add_parameters(20)

dy.renew_cg()
x = dy.inputVector([1,2,3,4])
W = dy.parameter(pW) # convert params to expression
b = dy.parameter(pb) # and add to the graph

y = W * x + b
```