
By design, the adaptive strategy converges as soon as the likelihood can not be improved in the given search direction. Therefore, a *χ*² stopping criterion can be employed, assuming convergence if the probabilistic symmetric *χ*² distance between two subsequent iterations is below some threshold *ϵ* > 0:

```
\left. {\chi^{2}\left( {{\hat{\overset{\rightarrow}{f}}}^{(k)},{\hat{\overset{\rightarrow}{f}}}^{(k - 1)}} \right) = 2 \cdot {\sum\limits_{i = 1}^{1}\left( {{\hat{\overset{\rightarrow}{\overset{\rightarrow}{f}}}}\_{i}^{(k)} - {\hat{\overset{\rightarrow}{f}}}\_{i}^{(k - 1)}} \right)^{2}}/{\hat{\overset{\rightarrow}{\overset{\rightarrow}{f}}}}\_{i}^{(k)} + {\hat{\overset{\rightarrow}{f}}}\_{i}^{(k - 1)}} \right)
```

Usually, `DSEA^+` will take a large first step with *α* > 1 and then quickly reduce the step sizes due to its fast convergence property. It will stop after only a few iterations, as soon as the *χ*² stopping criterion is reached. This will typically result in an accurate estimate of the true target spectrum $\overset{\rightarrow}{f}$.

### 10.4.4 Classifier Choice

One advantage of `DSEA` is that any classifier which returns confidence scores can be employed, e.g., neural networks, random forests, logistic regression, Naive Bayes,

![Fig. 10.6: The mode of a time-dependent deconvolution result is studied as a univariate time series. The figure clearly shows the concept shift that is artificially introduced by arranging two groups of observations.](graphic/b_9783110785968-010_fig_006.png)

Fig. 10.6: The mode of a time-dependent deconvolution result is studied as a univariate time series. The figure clearly shows the concept shift that is artificially introduced by arranging two groups of observations.

nearest neighbors, and many others. This property is particularly beneficial if some classifier is already conventional for a given use case. Random forests, for instance, are the standard learning method in several Cherenkov telescope collaborations, and they can continue to be also used in `DSEA`. Moreover, the ability to plug in many different classification methods allows practitioners to easily try and test multiple alternatives for which off-the-shelf implementations are available.

Considering the marginalization from Equation 10.40, it is preferable to employ classifiers of which the confidence scores $c\_{h}(i \mid \overset{\rightarrow}{x}$ resemble conditional probabilities ${\mathbb{P}}(y \equiv i \mid X = \overset{\rightarrow}{x}).$ In particular, we prefer *calibrated* [[134]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_134) classifiers. The confidence values of such classifiers (approximately) match the long-run empirical probability $\hat{\mathbb{P}}(y \equiv i \mid X = \overset{\rightarrow}{x}),$ i.e.

```
\left. \hat{\mathbb{P}}\left( {Y \equiv i \mid c\_{h}(i \mid \overset{\rightarrow}{x}) = c} \right)\rightarrow c\text{~for~}N\rightarrow\infty \right.
```

Any classifier that is not sufficiently well calibrated can be turned into a calibrated classifier by means of *probability calibration* [[396]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_396). This additional training step uses a labeled calibration data set that is disjunct from the training set with which the actual classifier is trained. Our experience shows that probability calibration does not improve the classifier in terms of accuracy but achieves remarkable improvements in terms of the deconvolution performance.

### 10.4.5 Leveraging Eventwise Contributions

Since `DSEA` aggregates predictions instead of observations, we are free to alter the aggregation ^from `D`[Y]to $\overset{\rightarrow}{f}$ (see [Figure 10.5](#9783110785951_034588.xhtml#b_9783110785968-010_fig_005)) to account for other variables like zenith angle or time. For instance, we could study how the spectrum of a gamma-ray source changes over time, by aggregating the event-wise contributions in `D`[*ŷ*] in a sliding time window.

We recognize that such a sliding window aggregation is not equal to the outcome of multiple separate, one-per-window deconvolutions, due to the reweighting in `DSEA`. Still, a sliding-window aggregation allows a practitioner to obtain insights about the deconvolution result in terms of additional variables in an efficient way because all event-wise contributions are readily computed. Likelihood-based methods do not have this property because their estimates are already based on aggregations; they can be run on separate windows but can not guarantee that an aggregation of their window-wise estimates is equal to an estimate of the full data set.

The feasibility of time-dependent deconvolution with `DSEA^+` is verified in the toy study from [Figure 10.6](#9783110785951_034588.xhtml#b_9783110785968-010_fig_006). In this study, a concept shift is generated artificially by arranging two subsets of the simulated MAGIC data, one with low energy values and one with high energy values. In the beginning, only low particle energies are observed. Suddenly, the concept changes, and only high energy values follow. This concept shift is akin to a transient event, such as a gamma-ray burst. `DSEA^+` deconvolves both groups together, returning the contribution of each observation in the entire data set. In fact, it does not know about the two artificial groups. The returned contributions are then aggregated in each sliding window position, which moves over the time-ordered contributions. For simplicity, each reconstructed spectrum is represented only by its mode, i.e., its peak position. [Figure 10.6](#9783110785951_034588.xhtml#b_9783110785968-010_fig_006) clearly shows that `DSEA^+` successfully reconstructs the concept shift that was artificially generated.

Another benefit of retaining event-wise contributions is the inspection and verification of the results. If a deconvolution result does not look physically plausible, we can use these contributions to trace the error back to groups of individual events, both in `D`[obs] and `D`[train]. Are there specific mismatches between the simulation and the real data which hinder a successful deconvolution? Are there events that likely picture background but contribute much? Is the classifier incapable of predicting a certain group of events? We can use the eventwise contributions to trace down and debug these issues.

### 10.4.6 Excursion: Document Analysis in Political Science

Electoral programs allow political scientists to characterize political parties, track their positional changes over time, and identify their strategies, among other research goals [[267]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_267). The high cost of hand-labeling documents such as electoral programs motivates automated methods for text analysis. However, it is rarely the individual labels that political and social scientists are interested in. Rather, many works choose the frequency of labels in a collection to be a more appropriate representation [[202]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_202). For instance, the spectrum of political issues in an electoral program facilitates the characterization and study of political parties. Estimating this spectrum, just like estimating energy spectra in particle and astroparticle physics, is, in fact, a deconvolution problem.
