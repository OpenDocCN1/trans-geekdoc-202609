$var(b_1) = \sigma_e^2 \sum f_i^2 = \sigma_e^2 \sum \frac{(X_i - ar{X})^2}{(SS_X)^2}$

$= \frac{\sigma_e^2}{SS_X} \text{ because } SS_X = \sum(X_i - ar{X})^2$

so the standard error of $b_1$ is

$\frac{\sigma_e}{\sqrt{SS_X}}$

and the estimated standard error of $b_1$ is

$SE(b_1) = \frac{s_e}{\sqrt{SS_X}}$

To find the standard error of $b_0$, we start by showing that $b_0$ can be expressed as a linear combination of the Ys. Starting with Equation 17.12,

$b_0 = ar{Y} - b_1ar{X} = \frac{1}{N}\sum Y_i - ar{X}\sum f_i Y_i = \sum\left(\frac{1}{N} - ar{f}_iight)Y_i$

so,

$b_0 = \sum g_i Y_i \text{ where } g_i = \frac{1}{N}\frac{ar{X}(X_i - ar{X})}{SS_X}$

Assuming independence and homoscedasticity, as for $b_0$,

$var(b_0) = \sigma_e^2 \sum g_i^2$

Substituting and simplifying, we have

$var(b_0) = \sigma_e^2 \left[\frac{1}{N} + \frac{ar{X}^2}{SS_X}ight]$

so the estimated standard error of $b_0$ is

$SE(b_0) = s_e\sqrt{\frac{1}{N} + \frac{ar{X}^2}{SS_X}}$