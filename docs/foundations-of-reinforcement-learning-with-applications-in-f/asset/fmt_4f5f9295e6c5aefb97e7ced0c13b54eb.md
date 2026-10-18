
$$\\begin{array}{r} {\\mu \\cdot \\pi \\cdot W\_{t} \\cdot dt + \\sigma \\cdot \\pi \\cdot W\_{t} \\cdot dz\_{t}} \\\\ \\end{array}$$  

Likewise, the change in the value of the riskless asset investment from time `t` to time `t + dt` is:

$$\\begin{array}{r} {r \\cdot (1 - \\pi) \\cdot W\_{t} \\cdot dt} \\\\ \\end{array}$$  

Therefore, the infinitesimal change in portfolio wealth `dW[t]` from time `t` to time `t + dt` is given by:

$$\\begin{array}{r} {dW\_{t} = (r + \\pi(\\mu - r)) \\cdot W\_{t} \\cdot dt + \\pi \\cdot \\sigma \\cdot W\_{t} \\cdot dz\_{t}} \\\\ \\end{array}$$  

Note that this is an Ito process defining the stochastic evolution of portfolio wealth. Applying Ito's Lemma (see [Appendix C](#appC.xhtml#appC)) on `log W[t]` gives us:

$$\\begin{aligned} {d(\\log W\_{t})} & {= ((r + \\pi(\\mu - r)) \\cdot W\_{t} \\cdot \\frac{1}{W\_{t}} - \\frac{\\pi^{2} \\cdot \\sigma^{2} \\cdot W\_{t}^{2}}{2} \\cdot \\frac{1}{W\_{t}^{2}}) \\cdot dt + \\pi \\cdot \\sigma \\cdot W\_{t} \\cdot \\frac{1}{W\_{t}} \\cdot dz\_{t}} \\\\ & {= (r + \\pi(\\mu - r) - \\frac{\\pi^{2}\\sigma^{2}}{2}) \\cdot dt + \\pi \\cdot \\sigma \\cdot dz\_{t}} \\\\ \\end{aligned}$$  

Therefore,

$$\\begin{array}{r} {\\log W\_{t} = {\\int\_{0}^{t}{(r + \\pi(}}\\mu - r) - \\frac{\\pi^{2}\\sigma^{2}}{2}) \\cdot du + {\\int\_{0}^{t}\\pi} \\cdot \\sigma \\cdot dz\_{u}} \\\\ \\end{array}$$  

Using the martingale property and Ito Isometry for the Ito integral ∫[0]^(*t*)*π* ⋅ *σ* ⋅ *d**z*[*u*] (see [Appendix C](#appC.xhtml#appC)), we get:

$$\\begin{array}{r} {\\left. \\log W\_{1} \\right.\\sim\\mathcal{N}(r + \\pi(\\mu - r) - \\frac{\\pi^{2}\\sigma^{2}}{2},\\pi^{2}\\sigma^{2})} \\\\ \\end{array}$$  

We assume CRRA Utility with `γ ≠ 0`, so:

$$\\begin{array}{l} {U(W\_{1}) = \\left\\{ \\begin{array}{ll} \\frac{W\_{1}^{1 - \\gamma} - 1}{1 - \\gamma} & {\\text{~for~}\\gamma \\neq 1} \\\\ {\\log(W\_{1})} & {\\text{~for~}\\gamma = 1} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  

We know that maximizing `𝔼[U(W[1])]` is equivalent to maximizing the Certainty-Equivalent Value of `W[1]`, hence also equivalent to maximizing the `log` of the Certainty-Equivalent Value of `W[1]`, which in this case (using the formula for `x[CE]` from the section on CRRA) is given by:

$$\\begin{array}{r} {r + \\pi(\\mu - r) - \\frac{\\pi^{2}\\sigma^{2}}{2} + \\frac{\\pi^{2}\\sigma^{2}(1 - \\gamma)}{2}} \\\\ \\end{array}$$  

$$\\begin{array}{r} {= r + \\pi(\\mu - r) - \\frac{\\pi^{2}\\sigma^{2}\\gamma}{2}} \\\\ \\end{array}$$  

This is a quadratic concave function of `π` for `γ > 0`, and so, taking its derivative with respect to `π` and setting it to 0 gives us the optimal investment fraction in the risky asset (`π*`) as follows:

$$\\begin{array}{r} {\\pi^{\*} = \\frac{\\mu - r}{\\gamma\\sigma^{2}}} \\\\ \\end{array}$$  

## 7.9 KEY TAKEAWAYS FROM THIS CHAPTER

*   An individual's financial risk-aversion is represented by the concave nature of the individual's Utility as a function of financial outcomes.

*   Risk-Premium (compensation an individual seeks for taking financial risk) is roughly proportional to the individual's financial risk-aversion and the measure of uncertainty in financial outcomes.

*   Risk-Adjusted-Return in finance should be thought of as the Certainty-Equivalent-Value, whose Utility is the Expected Utility across uncertain (risky) financial outcomes.

# Chapter 8 Dynamic Asset-Allocation and Consumption

DOI: [10.1201/9781003229193-8](https://doi.org/10.1201/9781003229193-8)

This chapter covers the first of five financial applications of Stochastic Control covered in this book. This financial application deals with the topic of investment management for not just a financial company, but more broadly for any corporation or for any individual. The nuances for specific companies and individuals can vary considerably but what is common across these entities is the need to:

*   Periodically decide how one's investment portfolio should be split across various choices of investment assets—the key being how much money to invest in more risky assets (which have potential for high returns on investment) versus less risky assets (that tend to yield modest returns on investment). This problem of optimally allocating capital across investment assets of varying risk-return profiles relates to the topic of Utility Theory we covered in [Chapter 7](#chapter7.xhtml). However, in this chapter, we deal with the further challenge of adjusting one's allocation of capital across assets, as time progresses. We refer to this feature as `Dynamic Asset Allocation` (the word dynamic refers to the adjustment of capital allocation to adapt to changing circumstances)

*   Periodically decide how much capital to leave in one's investment portfolio versus how much money to consume for one's personal needs/pleasures (or for a corporation's operational requirements) by extracting money from one's investment portfolio. Extracting money from one's investment portfolio can mean potentially losing out on investment growth opportunities, but the flip side of this is the Utility of Consumption that a corporation/individual desires. Noting that ultimately our goal is to maximize total utility of consumption over a certain time horizon, this decision of investing versus consuming really amounts to the timing of consumption of one's money over the given time horizon.

Thus, this problem constitutes the dual and dynamic decisioning of asset-allocation and consumption. To gain an intuitive understanding of the challenge of this dual dynamic decisioning problem, let us consider this problem from the perspective of personal finance in a simplified setting.

## 8.1 Optimization of Personal Finance

Personal Finances can be very simple for some people (earn a monthly salary, spend the entire salary) and can be very complicated for some other people (e.g., those who own multiple businesses in multiple countries and have complex assets and liabilities). Here we shall consider a situation that is relatively simple but includes sufficient nuances to provide you with the essential elements of the general problem of dynamic asset-allocation and consumption. Let's say your personal finances consist of the following aspects:

*   `Receiving money`: This could include your periodic salary, which typically remains constant for a period of time, but can change if you get a promotion or if you get a new job. This also includes money you liquidate from your investment portfolio, e.g., if you sell some stock, and decide not to re-invest in other investment assets. This also includes interest you earn from your savings account or from some bonds you might own. There are many other ways one can `receive money`, some fixed regular payments and some uncertain in terms of payment quantity and timing, and we won't enumerate all the different ways of `receiving money`. We just want to highlight here that `receiving money` at various points in time is one of the key financial aspects in one's life.
