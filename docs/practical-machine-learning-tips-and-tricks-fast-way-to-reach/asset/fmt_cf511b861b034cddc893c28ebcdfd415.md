
# 14.4.3.2 The Dual Problem

We revamp Equation 7.22 as the following:

```
T(y−Xw) + λ w 2 (14.21)−Xw)J(w) = (y
```

and its answer is given by Equation 7.23.

Equation 14.21 isn’t yet in terms of internal items. Notwithstanding, utilizing the framework reversal lemma (Equation 4.107 TODO) we revamp the edge gauge as follows:

```
w = XT(XXT + λIN)−1y (14.22)
```

which takes `O(N3 + N2D)` time to figure. This can be invaluable assuming `D` is enormous. Besides, we see that we can to some extent kernelize this, by supplanting `XXT` with the Gram matrix `K`. But what about the leading `XT` term? Let us define the following dual variables:

```
α = (K + λIN)−1y (14.23)
```

Then we can change the basic factors as follows:

```
N
w = XTα = ∑αxi (14.24)
i=1
```

This lets us know that the arrangement vector is only a direct amount of the `N` preparing vectors. At the point when we plug this in at test time to figure the prescient mean, we get:

```
N           N
y = f(x) = ∑αxT x = ∑ακ(xi,x) (14.25)
i=1         i=1
```

So we have successfully kernelized edge relapse by changing from base to double factors. This method can be applied to numerous other direct models, for example, calculated regression.

## 14.4.3.3 Computational Cost

The expense of processing the double factors `α` is `O(N3)`, though the expense of registering the base factors `w` is `O(D3)`. Thus the piece technique can be valuable in high dimensional settings, regardless of whether we just utilize a straight portion (c.f., the SVD stunt in Equation 7.24). In any case, forecast utilizing the double factors takes `O(ND)` time, while expectation utilizing the base factors just takes `O(D)` time. We can speedup expectation by making `α` meager, as we examine in Section 14.5. If `L` is quadratic misfortune, this is comparable to edge relapse, and in case `L` is the log-misfortune characterized in Equation 6.3, this is identical to calculated regression. However, in case we supplant the misfortune work with some other misfortune work, to be clarified beneath, we can guarantee that the arrangement is inadequate, so forecasts just rely upon a subset of the preparation information, known as help vectors.

This mix of the portion stunt in addition to a changed misfortune work is known as a help vector machine or SVM. Note that SVMs are exceptionally unnatural from a probabilistic mark of view.

*   First, they encode sparsity in the misfortune work rather than the prior.
*   Second, they encode bits by utilizing an algorithmic stunt, rather than being an unequivocal piece of the model.
*   Finally, SVMs don’t bring about probabilistic results, which causes different troubles, particularly in the multi-class characterization setting (see Section 14.5.2.4 TODO for details).

It is feasible to acquire inadequate, probabilistic, multi-class bit based classifiers, which fill in also or better than SVMs, utilizing strategies like the `L1VM` or `RVM`, examined in Section 14.3.2. Notwithstanding, we incorporate a conversation of SVMs, regardless of their non-probabilistic nature, for two principle reasons.

*   First, they are exceptionally famous and broadly utilized, so all understudies of AI should know about them.
*   Second, they enjoy some computational upper hands over probabilistic techniques in the organized result case; see Section 19.7 TODO.

# 14.4.4 Kernel PCA

# 14.5 Support Vector Machines (SVMs)

## 14.5.1 SVMs for Classification

### 14.5.1.1 Primal Structure

**Representation**

```
H : y = f(x) = sign(wx +b) (14.27)
```

In Section 14.3.2, we saw one way to derive a sparse kernel machine, namely by using a GLM with kernel basis functions, plus a sparsity-promoting prior such as `ℓ1` or `ARD`. An elective methodology is to change the true capacity from negative log probability to some other misfortune work, as we examined in Section 6.4.5. Specifically, consider the `ℓ2` regularized empirical hazard function:

```
J(w,NL(yi,y ) + λ w 2 (14.26)λ) =∑i = 1 ˆi
```

**Evaluation**

```
min 1 w 2 (14.28)
w,b 2
∥ ∥
s.t. yi(wxi +b) 1,i = 1,2, . . . ,N (14.29)
⩾
```

where `ˆi = wTxi + w0`.

### 14.5.1.2 Dual Form

**Representation**

```
( N )
H : y = f(x) = sign ∑αyi(x·xi) +b (14.30)
i=1
```

**Evaluation**

```
min 1 N N 2 ∑ ∑
α α jyiyj(xi·xj)−∑α (14.31)
α i=1 j=1 i=1 N
s.t. ∑αyi = 0 (14.32)
i=1
α 0,i = 1,2, . . . ,N (14.33)
⩾
```

### 14.5.1.3 Primal Structure with Slack Variables

**Representation**

```
H : y = f(x) = sign(wx +b) (14.34)
```

**Evaluation**

```
N ≜
min C 1 w 2 (14.35)
w,b ∑ξ + 2i=1
∥ ∥
s.t. yi(wxi +b) 1− ξ (14.36)
ξ 0, I = 1,2, . . . ,N (14.37)
⩾ ⩾
```

Define slack variables:

```
ξ 1−yi(w·xi +b),ξ 0 (14.47)
≜ ⩾ ⩾
```

### 14.5.1.4 Dual Structure with Slack Variables

**Representation**

```
H : y = f(x) = sign ∑αyi(x·xi) +b (14.38)
```

**Evaluation**

```
min 1 N N 2 ∑ ∑
α α jyiyj(xi·xj)−∑α (14.39)
α i=1 j=1 i=1 N
s.t. ∑αyi = 0 (14.40)
i=1
0 α C,i = 1,2, . . . ,N (14.41)
⩽ ⩽
```

**QP, SMO**

Then `w,b,ξ` fulfill the imperatives 14.35 and 14.36. Furthermore genuine capacity 14.37 can be composed as:

```
N
min∑ξ + λ w 2
w,b i=1
∥ ∥
```

If `λ = 1 / 2C`, then:

```
min 1
(N 1 )
w 2 (14.48)
w,b C C∑ξ
+2i=1
∥ ∥
```

It is identical to condition 14.35.

### 14.5.1.5 Hinge Loss

Linear help vector machines can likewise be deciphered as pivot misfortune minimization:

```
min∑L(yi, f(xi)) + λ w 2 (14.45)
w,b i=1
∥ ∥
```

where `L(y, f(x))` is a pivot misfortune function:

```
{
L(y, f(x)) = 1−y f(x), 1−y f(x) > 0 (14.46)
0, 1−y f(x) 0
⩽
```

**Proof.** We can compose condition 14.45 as conditions 14.35 14.37. ∼

### 14.5.1.6 Optimization

```
min 1 N N 2 ∑ ∑
α α jyiyj(xi·xj)−∑α (14.39)
α i=1 j=1 i=1 N
s.t. ∑αyi = 0 (14.40)
i=1
0 α C,i = 1,2, . . . ,N (14.41)
⩽ ⩽
```

**KKT Conditions**

```
α = 0 ⇒ yi(w· xi +b) 1 (14.42)
⩾
α = C ⇒ yi(w·xi +b) 1 (14.43)
⩽
0 < α < C ⇒ yi(w· xi +b) = 1 (14.44)
```

## 14.5.2 SVMs for Regression

### 14.5.2.1 Representation

```
H : y = f(x) = wTx +b (14.49)
```

### 14.5.2.2 Evaluation

```
J(w) = C N 1 w 2 (14.50)
∑L(yi, f(xi)) + 2i=1
∥ ∥
```

where `L(y, f(x))` is an epsilon harsh misfortune work:

```
L(y, f(x)) = {0 , |y− f(x)| < ε (14.51)
|y− f(x)|− ε , otherwise
```

and `C = 1/λ` is a regularization constant. This goal is raised and unconstrained, however not differentiable, in view of the outright worth capacity in the misfortune term. As in Section 13.4 TODO, where we talked about the rope issue, there are a few potential calculations we could utilize. One well known methodology is to figure the issue as an obliged improvement issue. Specifically, we acquaint slack factors with address how much each point lies outside the tube:

```
yi ≤ f(xi) + ε + ξ+
yi ≥ f(xi) − ε − ξi−
```

Given this, we can modify the evenhanded as follows:

```
J(w) = C N ++ ξ ) + 1 w 2 (14.52)
∑(ξ 2i=1
∥ ∥
```

This is a standard quadratic issue in `2N + D + 1` variables.

## 14.5.3 Choosing C

![](image_rsrc1S0.jpg) ![](image_rsrc1S1.jpg)
(a) (b)

**Fig. 14.2:** (a) A cross approval gauge of the 0-1 blunder for a SVM classifier with RBF part with various precisions `γ = 1/(2σ2)` and distinctive regularizer `γ = 1/C`, applied to an engineered informational index drawn from a combination of 2 Gaussians. (b) A cut through this surface for `γ = 5`. The red specked line is the Bayes ideal mistake, figured utilizing Bayes rule applied to the model used to produce the information. In light of Figure 12.6 of (Hastie et al. 2009).

SVMs for both arrangement and relapse necessitate that you indicate the bit work and the parameter `C`. Typically `C` is picked by cross-approval. Note, nonetheless, that `C` connects unequivocally with the kernel boundaries. For instance, assume we are utilizing a RBF portion with pre cision `γ`.
