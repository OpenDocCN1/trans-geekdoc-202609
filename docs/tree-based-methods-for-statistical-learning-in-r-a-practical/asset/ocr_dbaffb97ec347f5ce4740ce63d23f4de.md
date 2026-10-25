$$ \boldsymbol{f} = \{ f(\boldsymbol{x}_i) \}_{i=1}^N . $$

Steepest descent in “function space” can be used to find the optimal \(\widehat{\boldsymbol{f}}\) as the sum of \(B\) \(N\)-dimensional component vectors:

$$ \boldsymbol{f}_B = \sum_{b=0}^B \boldsymbol{f}_b, \quad \boldsymbol{f}_b \in \mathbb{R}^N, $$

where, similar to before, \(\boldsymbol{f}_0\) is an initial guess, and each component \(\boldsymbol{f}_b\) depends on the current estimate \(\boldsymbol{f}_{b-1}\), and so forth. Steepest descent finds the next update using

$$ \boldsymbol{f}_b = \boldsymbol{f}_{b-1} - \gamma \boldsymbol{g}_b, $$

where

$$ \boldsymbol{g}_b = \left\{ \left[ \frac{\partial L(f)}{\partial f} \right]_{f=f_{b-1}(\boldsymbol{x}_i)} \right\}_{i=1}^N \quad (8.3) $$

is a length \(N\) column vector whose \(j\)-th component (\(g_{jb}\)) is the gradient of \(L(\boldsymbol{f})\) evaluated at \(f = f_{b-1}(\boldsymbol{x}_j)\).

One drawback is that the gradient components \(\boldsymbol{g}_b\) in (8.3) are only defined at the observed training observations \(\boldsymbol{x}_i\) (\(i=1,2,\dots,N\)), whereas we want the final prediction function \(f_M(\boldsymbol{x})\) to be defined at new data points; otherwise, how would we make new predictions? Further, the procedure does not take into account the fact that observations with similar feature values are likely to have similar predictions [Ridgeway, 1999]. To this end, Friedman [2001] proposed using a class of functions that make use of the director information to approximate the gradient at each step. In gradient tree boosting (the focus of this chapter), for example, a regression tree is used to approximate the gradient at each step. In particular, at each step, we fit a \(J\)-terminal node regression tree\(^\text{b}\), which has the form

$$ f(\boldsymbol{x}_i; \boldsymbol{\theta}, \boldsymbol{R}) = \sum_{j=1}^J \theta_j I(\boldsymbol{x}_i \in R_j), $$

where \(\boldsymbol{\theta} = \{ \theta_j \}_{j=1}^J\) represents the terminal node estimates (i.e., the mean response in each terminal node), \(\boldsymbol{R} = \{ R_j \}_{j=1}^J\) represents the disjoint regions