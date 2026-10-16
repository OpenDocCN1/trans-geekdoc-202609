```
In [37]:

```python
print("row_vec:", row_vec,
      "col_vec:", col_vec,
      "dot:", np.dot(row_vec, col_vec), sep='\n')
```
```

```
row vec
[0 1 2 3 4]
col_vec:
[[ 0]
 [10]
 [20]
 [30]
 [40]]
dot:
[[300]]
```

So, far, we’re mostly good. But what happens if we swap the order? You might expect to get the same answer: after all, in basic arithmetic 3 × 5 = 5 × 3. Let’s check it out:

```
In [38]:

```python
out = np.dot(col_vec, row_vec)
print(out)
```
```

```
[[  0   0   0   0   0]
 [  0  10  20  30  40]
 [  0  20  40  60  80]
 [  0  30  60  90 120]
 [  0  40  80 120 160]]
```

Cue Dorothy: “Toto, I’ve a feeling we’re not in Kansas anymore.” What happened here? We’ll focus on one output element—the 20 in the second-from-the-top row—to get a handle on the craziness we unleashed. Where does it come from? Well, we never really defined how the output is produced—except to say that it does a sum product on two 1D arrays. Let’s remedy that.

Pick an element in the output, out[1, 2]. That’s row 1 and column 2, if we start our counting from zero. out[1, 2] has the value 20. Where does this 20 come from? It comes from taking a dot product on row 1 of col_vec with column 2 of row_vec. That’s actually the definition of what np.dot does. The source values are col_vec[1, :] which is [10] and row_vec[:, 2] which is [2]. Putting those together gives 10 × 2 → 20 with no additional summing needed because we only have one value in each. You can go through a similar process for the other entries.

Mathematically, this is written as outᵢⱼ = dot(leftᵢ, rightⱼ) where dot is our friendly sum product over 1D things. So, the output row i comes from the left input’s row i and the output’s column j comes from the right input column j. Taking from each row and each column gives a 5 × 5 result.

If we apply the same logic to the to the row-column case, we see