
$r_{i}(t) = s(t - \Delta t_{i})e^{j\omega_{c}(t - i\frac{2\pi\Delta x\cos\phi}{\omega_{c}\lambda})} \approx s(t)e^{j\omega_{c}t}e^{- 2\pi j\frac{i\Delta x\cos\phi}{\lambda}},\quad i = 0,1,\ldots,l - 1,$

![Equation](images/B978044329238500010X/si420.png)

where we have assumed a relatively low time signal variation. After converting the received signals in the baseband (multiplying by $e^{-j\omega_{c}t}$), the vector of the received signals (one per array element) at time $t$ can be written in the following linear regression-type formulation:

$$
\mathbf{u}(t): = \begin{bmatrix} {u_{0}(t)} \\ {u_{1}(t)} \\ \vdots \\ {u_{l - 1}(t)} \\ \end{bmatrix} = \mathbf{x}s(t) + \mathbf{\eta}(t),
$$

![Equation](images/B978044329238500010X/si422.png)(4.105)

where

$$
\mathbf{x}: = \begin{bmatrix} 1 \\ e^{- 2\pi j\frac{\Delta x\cos\phi}{\lambda}} \\ \vdots \\ e^{- 2\pi j\frac{(l - 1)\Delta x\cos\phi}{\lambda}} \\ \end{bmatrix},
$$

![Equation](images/B978044329238500010X/si423.png)

and the vector $\mathbf{\eta}(t)$ contains the additive noise plus any other interference due to signals coming from directions other than $\phi$, so that
