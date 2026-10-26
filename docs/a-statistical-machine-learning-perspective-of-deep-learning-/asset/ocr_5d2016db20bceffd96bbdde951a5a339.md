![](bbox=[0.021, 0.039, 0.069, 0.156])

# Dynamic Declaration

+   - Static Declaration vs. Dynamic Declaration
+     - Move the graph declaration and construction (and optimization) from outside of the loop to inside the loop
+     - Perform single instance training because it is hard to batch

```
/* (a) static declaration */
// all samples must share one graph
declare a static data flow graph 𝒟.
for t = 1 → T:
    read the tth data batch {xᵢᵗ}ᵢ₌₁ᴷ.
    batched computation: 𝒟({xᵢᵗ}ᵢ₌₁ᴷ).
```

```
/* (b) dynamic declaration */
for t = 1 → T:
    read the tth data batch {xᵢᵗ}ᵢ₌₁ᴷ.
    for k = 1 → K:
        declare a data flow graph 𝒟ᵗᵢ for xᵢᵗ.
        single instance computation: 𝒟ᵢᵗ(xᵢᵗ)
```