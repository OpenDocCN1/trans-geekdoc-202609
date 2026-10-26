![](bbox=[0.021, 0.039, 0.069, 0.155])

# Dynamic Declaration: Advantages

+   - Dynamic declaration has one major advantages
+     - Flexibility: it can express *arbitrarily dynamically structured* networks by declaring as many as dataflow graphs as the number of training data

```
/* (b) dynamic declaration */
for t = 1 → T:
    read the tth data batch {xᵢᵗ}ᵢ₌₁ᴷ.
    for k = 1 → K:
        declare a data flow graph Dᵢᵗ for xᵢᵗ.
        single-instance computation: Dᵢᵗ(xᵢᵗ).
```