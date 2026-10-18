
$$\\begin{array}{r} {df(t,Y\_{t}) = \\frac{\\partial f}{\\partial t} \\cdot dt + \\frac{\\partial f}{\\partial Y\_{t}} \\cdot (\\mu\_{t} \\cdot dt + \\sigma\_{t} \\cdot dz\_{t}) + \\frac{1}{2} \\cdot \\frac{\\partial^{2}f}{\\partial Y\_{t}{}^{2}} \\cdot {(\\mu\_{t} \\cdot dt + \\sigma\_{t} \\cdot dz\_{t})}^{2} + \\ldots} \\\\ \\end{array}$$

Next, we use the rules: `(*dt*)² = 0`, `dt ⋅ dz[t] = 0`, `(*dz[t*])² = dt` to get `Ito's Lemma`:

$$\\begin{array}{r} {df(t,Y\_{t}) = (\\frac{\\partial f}{\\partial t} + \\mu\_{t} \\cdot \\frac{\\partial f}{\\partial Y\_{t}} + \\frac{\\sigma\_{t}^{2}}{2} \\cdot \\frac{\\partial^{2}f}{\\partial Y\_{t}{}^{2}}) \\cdot dt + \\sigma\_{t} \\cdot \\frac{\\partial f}{\\partial Y\_{t}} \\cdot dz\_{t}} \\\\ \\end{array}$$

(C.1)

`Ito's Lemma` describes the stochastic process of a function `f` of an `Ito Process` `Y` in terms of the partial derivatives of `f`, and in terms of the drift `μ` and dispersion `σ` processes that define `Y`.

If we generalize `Y` to be an `n`-dimensional stochastic process (as a column vector) with `μ[t]` as an `n`-dimensional (stochastic) column vector, `σ[t]` as an `n × m` (stochastic) matrix, and `z[t]` as an `m`-dimensional vector of `m` independent standard Brownian motions (as follows):

$$\\begin{array}{r} {d\\mathbf{\\mathbf{Y}}\_{t} = \\mathbf{\\mathbf{\\mu}}\_{t} \\cdot dt + \\mathbf{\\mathbf{\\sigma}}\_{t} \\cdot d\\mathbf{\\mathbf{z}}\_{t}} \\\\ \\end{array}$$

then we get the multi-variate version of `Ito's Lemma`, as follows:

$$\\begin{array}{r} {df(t,\\mathbf{\\mathbf{Y}}\_{t}) = (\\frac{\\partial f}{\\partial t} + {(\\nabla\_{\\mathbf{\\mathbf{Y}}}f)}^{T} \\cdot \\mathbf{\\mathbf{\\mu}}\_{t} + \\frac{1}{2}Tr\\lbrack\\mathbf{\\mathbf{\\sigma}}\_{t}^{T} \\cdot (\\Delta\_{\\mathbf{\\mathbf{Y}}}f) \\cdot \\mathbf{\\mathbf{\\sigma}}\_{t}\\rbrack) \\cdot dt + {(\\nabla\_{\\mathbf{\\mathbf{Y}}}f)}^{T} \\cdot \\mathbf{\\mathbf{\\sigma}}\_{t} \\cdot d\\mathbf{\\mathbf{z}}\_{t}} \\\\ \\end{array}$$

(C.2)

where the symbol `∇` represents the gradient of a function, the symbol `Δ` represents the Hessian of a function, and the symbol `Tr` represents the Trace of a matrix.

Next, we cover two common `Ito` processes, and use `Ito's Lemma` to solve the Stochastic Differential Equation represented by these `Ito` Processes:

## C.7 A LOGNORMAL PROCESS

Consider a stochastic process `x` described in the form of the following `Ito` process:

$$\\begin{array}{r} {dx\_{t} = \\mu(t) \\cdot x\_{t} \\cdot dt + \\sigma(t) \\cdot x\_{t} \\cdot dz\_{t}} \\\\ \\end{array}$$

Note that here `z` is standard (one-dimensional) Brownian motion, and `μ, σ` are deterministic functions of time `t`. This is solved easily by defining an appropriate function of `x[t]` and applying `Ito's Lemma`, as follows:

$$\\begin{array}{r} {y\_{t} = \\log(x\_{t})} \\\\ \\end{array}$$

Applying `Ito's Lemma` on `y[t]` with respect to `x[t]`, we get:

$$\\begin{aligned} {dy\_{t}} & {= (\\mu(t) \\cdot x\_{t} \\cdot \\frac{1}{x\_{t}} - \\frac{\\sigma^{2}(t) \\cdot x\_{t}^{2}}{2} \\cdot \\frac{1}{x\_{t}^{2}}) \\cdot dt + \\sigma(t) \\cdot x\_{t} \\cdot \\frac{1}{x\_{t}} \\cdot dz\_{t}} \\\\ & {= (\\mu(t) - \\frac{\\sigma^{2}(t)}{2}) \\cdot dt + \\sigma(t) \\cdot dz\_{t}} \\\\ \\end{aligned}$$

So,

$$\\begin{array}{r} {y\_{T} = y\_{S} + {\\int\_{S}^{T}{(\\mu(t) - \\frac{\\sigma^{2}(t)}{2})}} \\cdot dt + {\\int\_{S}^{T}\\sigma}(t) \\cdot dz\_{t}} \\\\ \\end{array}$$

$$\\begin{array}{r} {x\_{T} = x\_{S} \\cdot e^{{\\int\_{S}^{T}{(\\mu(t) - \\frac{\\sigma^{2}(t)}{2})}} \\cdot dt + {\\int\_{S}^{T}\\sigma}(t) \\cdot dz\_{t}}} \\\\ \\end{array}$$

`x[T]|x[S]` follows a lognormal distribution, i.e.,

$$\\begin{array}{r} {\\left. y\_{T} = \\log(x\_{T}) \\right.\\sim\\mathcal{N}(\\log(x\_{S}) + {\\int\_{S}^{T}{(\\mu(t) - \\frac{\\sigma^{2}(t)}{2})}} \\cdot dt,{\\int\_{S}^{T}\\sigma^{2}}(t) \\cdot dt)} \\\\ \\end{array}$$

$$\\begin{array}{r} {E\\lbrack x\_{T}|x\_{S}\\rbrack = x\_{S} \\cdot e^{{\\int\_{S}^{T}\\mu}(t) \\cdot dt}} \\\\ \\end{array}$$

$$\\begin{array}{r} {E\\lbrack x\_{T}^{2}|x\_{S}\\rbrack = x\_{S}^{2} \\cdot e^{{\\int\_{S}^{T}{(2\\mu(t) + \\sigma^{2}(t))}} \\cdot dt}} \\\\ \\end{array}$$

$$\\begin{array}{r} {Variance\\lbrack x\_{T}|x\_{S}\\rbrack = E\\lbrack x\_{T}^{2}|x\_{S}\\rbrack - {(E\\lbrack x\_{T}|x\_{S}\\rbrack)}^{2} = x\_{S}^{2} \\cdot e^{{\\int\_{S}^{T}2}\\mu(t) \\cdot dt} \\cdot (e^{{\\int\_{S}^{T}\\sigma^{2}}(t) \\cdot dt} - 1)} \\\\ \\end{array}$$

The special case of `μ(t) = μ` (constant) and `σ(t) = σ` (constant) is a very common `Ito` process used all over Finance/Economics (for its simplicity, tractability as well as practicality), and is known as Geometric Brownian Motion, to reflect the fact that the stochastic increment of the process (`σ ⋅ x[t] ⋅ dz[t]`) is multiplicative to the level of the process `x[t]`. If we consider this special case, we get:

$$\\begin{array}{r} {\\left. y\_{T} = \\log(x\_{T}) \\right.\\sim\\mathcal{N}(\\log(x\_{S}) + (\\mu - \\frac{\\sigma^{2}}{2})(T - S),\\sigma^{2}(T - S))} \\\\ \\end{array}$$

$$\\begin{array}{r} {E\\lbrack x\_{T}|x\_{S}\\rbrack = x\_{S} \\cdot e^{\\mu(T - S)}} \\\\ \\end{array}$$

$$\\begin{array}{r} {Variance\\lbrack x\_{T}|x\_{S}\\rbrack = x\_{S}^{2} \\cdot e^{2\\mu(T - S)} \\cdot (e^{\\sigma^{2}(T - S)} - 1)} \\\\ \\end{array}$$

## C.8 A MEAN-REVERTING PROCESS

Now we consider a stochastic process `x` described in the form of the following `Ito` process:

$$\\begin{array}{r} {dx\_{t} = \\mu(t) \\cdot x\_{t} \\cdot dt + \\sigma(t) \\cdot dz\_{t}} \\\\ \\end{array}$$

As in the process of the previous section, `z` is standard (one-dimensional) Brownian motion, and `μ, σ` are deterministic functions of time `t`. This is solved easily by defining an appropriate function of `x[t]` and applying `Ito's Lemma`, as follows:

$$\\begin{array}{r} {y\_{t} = x\_{t} \\cdot e^{- {\\int\_{0}^{t}\\mu}(u) \\cdot du}} \\\\ \\end{array}$$

Applying `Ito's Lemma` on `y[t]` with respect to `x[t]`, we get:

$$\\begin{aligned} {dy\_{t}} & {= ( - x\_{t} \\cdot \\mu(t) \\cdot e^{- {\\int\_{0}^{t}\\mu}(u) \\cdot du} + \\mu(t) \\cdot x\_{t} \\cdot e^{- {\\int\_{0}^{t}\\mu}(u) \\cdot du}) \\cdot dt + \\sigma(t) \\cdot e^{- {\\int\_{0}^{t}\\mu}(u) \\cdot du} \\cdot dz\_{t}} \\\\ & {= \\sigma(t) \\cdot e^{- {\\int\_{0}^{t}\\mu}(u) \\cdot du} \\cdot dz\_{t}} \\\\ \\end{aligned}$$

So the process `y` is a martingale. Using `Ito Isometry`, we get:

$$\\begin{array}{r} {\\left. y\_{T} \\right.\\sim\\mathcal{N}(y\_{S},{\\int\_{S}^{T}\\sigma^{2}}(t) \\cdot e^{- {\\int\_{0}^{t}2}\\mu(u) \\cdot du} \\cdot dt)} \\\\ \\end{array}$$

Therefore,

$$\\begin{array}{r} {\\left. x\_{T} \\right.\\sim\\mathcal{N}(x\_{S} \\cdot e^{{\\int\_{S}^{T}\\mu}(t) \\cdot dt},e^{{\\int\_{0}^{T}2}\\mu(t) \\cdot dt} \\cdot {\\int\_{S}^{T}\\sigma^{2}}(t) \\cdot e^{- {\\int\_{0}^{t}2}\\mu(u) \\cdot du} \\cdot dt)} \\\\ \\end{array}$$

We call this process “mean-reverting” because with negative `μ(t)`, the process is “pulled” to a baseline level of 0, at a speed whose expectation is proportional to `−μ(t)` and proportional to the distance from the baseline (so we say the process reverts to a baseline of 0 and the strength of mean-reversion is greater if the distance from the baseline is greater). If `μ(t)` is positive, then we say that the process is “mean-diverting” to signify that it gets pulled away from the baseline level of 0.

The special case of `μ(t) = μ` (constant) and `σ(t) = σ` (constant) is a fairly common `Ito` process (again for its simplicity, tractability as well as practicality), and is known as the Ornstein-Uhlenbeck Process with the mean (baseline) level set to 0. If we consider this special case, we get:

$$\\begin{array}{r} {\\left. x\_{T} \\right.\\sim\\mathcal{N}(x\_{S} \\cdot e^{\\mu(T - S)},\\frac{\\sigma^{2}}{2\\mu} \\cdot (e^{2\\mu(T - S)} - 1))} \\\\ \\end{array}$$
