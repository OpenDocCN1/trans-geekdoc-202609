a way that the two shares stack to form a “gray” 2 x 2 block, while a black pixel is shared in a way that results in a black 2 x 2 block.

More formally:

```
Share(m):
initialize empty images s₁, s₂, with dimensions twice that of m
for each position (i, j) in m:
  randomly choose b₁ ← { { } }
  if m[i,j] is a white pixel: set b₂ := b₁
  if m[i,j] is a black pixel: set b₂ to the “opposite” of b₁ (i.e., { { } } \ {b₁})
  add 2 x 2 block b₁ to image s₁ at position (2i, 2j)
  add 2 x 2 block b₂ to image s₂ at position (2i, 2j)
return (s₁, s₂)
```

It is not hard to see that share s₁ leaks no information about the secret image m, because it consists of uniformly chosen 2 x 2 blocks. In the exercises you are asked to prove that s₂ also individually leaks nothing about the secret image.

Note that whenever the source pixel is white, the two shares have identical 2x2 blocks (so that when stacked, they make a “gray” block). Whenever a source pixel is black, the two shares have opposite blocks, so stack to make a black block.

# Example

![](bbox=[0.292, 0.46, 0.812, 0.695])

# Exercises

+   3.1. Generalize Construction 3.5 to be an n-out-of-n secret-sharing scheme, and prove that your scheme is correct and secure.
+   
+   3.2. Prove Theorem 3.7.
+   
+   3.3. Fill in the details of the following alternative proof of Theorem 3.6: Starting with L_tss-L, apply the first step of the proof as before, to duplicate the main body into 3 branches of a new if-statement. Then apply Exercise 2.3 to the second branch of the if-statement. Argue that m_L can be replaced with m_R and complete the proof.