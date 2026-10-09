$$\overline{\mathrm{ATE}} = \frac{1}{K} \sum_{k=1}^{K} (y_{k1} - y_{k0}). \qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad (5.10)$$

This estimator will tend to have lower variance than the ATE in Equation 5.2 for a completely randomized design that just allocated each field to a single treatment status.

A related strategy is *matched pairs*, common in medical trials, where two similar patients are paired and each given a different treatment. The difficulty in this later setting is that, unlike the agricultural example where a single field is split in two, the matched pair contains two distinct people who will inevitably differ on many observable and unobservable characteristics. ATE estimators based on human pairs are thus sensitive to the matching procedure and don’t always offer reliable variance reduction.

Other useful strategies include factorial designs, where combinations of treatments are organized in a manner that forces independence from confounding factors and allows one to understand interaction effects, and sequential designs that use information from early trials to inform later trials in a dynamic experiment. Many of these more complex setups are best understood through a *potential outcomes*10 framework wherein each subject is modeled as having its own treatment effect:

$$y_{i}(1) - y_{i}(0). \qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad (5.11)$$

Here, $y_{i}(1)$ is the response for individual $i$ if they are treated, and $y_{i}(0)$ is their response in an alternative untreated world. Of course, in most settings, you only ever get to see $y_{i}(di)$ for $di = 1$ or $0$, and thus Equation 5.11 is partially unobservable. But the concept of potential outcomes turns out to be a useful formalism for the analysis of real-world experimental settings. For example, this allows for a concise definition of the average treatment effect:

$$\mathrm{ATE} = \mathbb{E}[y(1) - y(0)]. \qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad (5.12)$$

This removes the need for the extra conditions listed after our earlier ATE definition in Equation 5.1.

Potential outcomes is not the only way to think about causation, but it is a framework that works nicely for practical applications. We will make use of it in the coming sections and in future chapters.