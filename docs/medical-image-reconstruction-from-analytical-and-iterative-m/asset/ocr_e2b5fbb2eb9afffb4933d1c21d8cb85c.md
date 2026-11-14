```
Y^{(n)}=G\left[F^{(k)}P+H^{(k)}Y^{(n-1)}\right].
```

The nonlinear filter G can be a Huber filter, a guided filter, a bilateral filter, a BM3D filter, and so on. The approach discussed in this section is sometimes referred to as an iterative POCS approach. Here, POCS is an abbreviation for projections onto projections onto convex sets. In layman’s language, this approach alternatively uses different methods back-and-forth, and each method has its own goal. The effectiveness of this POCS method is illustrated in Figure 8.9, where an FBP reconstruction is compared with a POCS reconstruction for a low-dose CT patient study.

![](bbox=[0.11, 0.3, 0.82, 0.49])

**Fig. 8.9:** (Left) An FBP reconstruction of low-dose CT image. (Right) A POCS reconstruction of the same image.

# ## 8.8 A viewpoint from calculus of variations

The discussion in the previous sections gives an impression that the new FBP algorithms can only be derived from the iterative Landweber algorithm. In fact, these new FBP algorithms can be derived without using the iterative Landweber algorithm. In this section, we give an example of deriving a new FBP algorithm by using calculus of variations.

Let the image to be reconstructed be f(x, y) and its Radon transform be [Rf](s, θ), defined as

```
[Rf](s, θ) = ∫_{-∞}^{∞} ∫_{-∞}^{∞} f(x,y)δ(x cos θ + y sin θ - s)dxdy,
```

where δ is the Dirac delta function, θ is the detector rotation angle, and s is the line-integral location on the detector. The Radon transform [Rf](s, θ) is the line integral of the object f(x, y). Image reconstruction is to solve for the object f(x, y) from its Radon