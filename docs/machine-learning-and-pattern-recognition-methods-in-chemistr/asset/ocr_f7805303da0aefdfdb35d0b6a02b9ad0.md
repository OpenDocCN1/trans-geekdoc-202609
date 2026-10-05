of the extent of rotational ambiguity have been investigated (Golshan, Abdollahi & Maeder, 2012; Khodadadi Karimvand & Abdollahi, 2018).

A simulated data set was analyzed. The kinetic model used for data was the irreversible parallel reactions in the form of $A \xrightarrow{k1} B; F \xrightarrow{k2} D$, assuming that only species $A$ and $F$ are present in the reaction mixture. The kinetic equations, Eqs. (7.23)-(7.26), can be used to describe the concentration profiles of the reactants $(A, F)$ and the products $(B, D)$ of the considered two first-order reactions.

```
$[A_i] = [A_0] \exp(-k_1 t_i)$
$[B_j] = [A_0] (1 - \exp(-k_1 t_i))$
$[F_i] = [F_0] \exp(-k_2 t_i)$
$[D_i] = [F_0] (1 - \exp(-k_2 t_i))$
```

Also to recognize in the realm of three-component systems, we assume that F has no absorption in the spectral region investigated. Concentration profiles for the reactants and the product simulated based on chemical models (Eqs. 7.23–7.26), with the rate constants equal to $k_1=0.05s^{-1}$ and $k_2=0.15s^{-1}$, with $[A_0]=[F_0]=1M$. Measurement times were between 1 and 47 or 4 and 47 s. The simulated absorbance spectra of data set X were then calculated by post-multiplication of concentration with pure spectra. To more rigorously test the methods, random errors by normal distributions with mean zero and standard deviation up to 0.3% of averaged absorbance were added to the simulated data. The concentration and spectra profiles and the resulting “measured” spectra for data set X are plotted in Fig. 7.12. It contains 24 spectra corresponding to the calculated profiles. The measurement time for this data has been chosen between 1 and 47 with an increment of 2. If starting at time zero the rotational ambiguity is very small.

The grid search method performs the calculation of all feasible solutions fitting the data and fulfilling the constraints of non-negativity and the hard model, also delivering the rate constants for the modeled reaction. Fig. 7.10A shows the areas of feasible solutions which were obtained independently by grid search minimization of the residuals procedure in U-space under non-negativity (in brown in the printed version)) and after additional hard constraints of the same data X in (dark gray in the printed version) for $D$ and blue (light gray in the printed version) and green (gray in the printed version) for $A$ and $B$.

The introduction of the hard constraint results in perfectly defined concentration profiles for $A$ and $B$ and reduced AFS for the concentration