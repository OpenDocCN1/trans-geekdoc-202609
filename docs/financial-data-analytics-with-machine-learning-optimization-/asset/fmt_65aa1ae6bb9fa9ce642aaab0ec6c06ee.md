
### Case 4: if `φ(t; -λ, ε_B)` admits two distinct roots `s₂* < s₁*`, then by defining `t₁* := (T - s₁*)⁺` and `t₂* := (T - s₂*)⁺`, the optimal buying time is given by `τ_B* := inf{t ∈ [0, t₁*] ∪ [t₂*, T] : S_t = q_m_t} ∧ T`.

In [Appendix 7.A.3](#c07.xhtml#c07-sec-0026), we present a table containing the root(s) `s*` (`s₁*` and `s₂*`) of `φ` under various combinations of values of `ε` and `λ`. For any intermediate values at which `φ` is evaluated, the corresponding roots can then be interpolated.

### 7.5.1 Trading Strategies Using the Goodness Index

Suppose that in a given calendar year, we would like to trade one or multiple stocks without any of their derivatives, so as to maximize our profit. This problem is time-inconsistent in nature, as our objective may change day-by-day. In the following, we shall introduce a class of trading strategies with different odds that utilize consecutive optimal selling and buying times, as introduced in [Propositions 7.1](#c07.xhtml#c07-fea-0004) and [7.2](#c07.xhtml#c07-fea-0006).

Generally, while stock returns are expected to be non-stationary, their changes are usually mild within a shorter time frame. For the sake of illustration, here we set `T` to 4 so that each trading horizon contains `T + 1 = 5` trading days, or one week. This motivates us to assume that `μ` and `σ` are constant throughout the trading horizon, and we denote their estimates of the `k`-th trading horizon spanning from day `t_{k,0}` to day `t_{k,T} := t_{k,0} + T` by `μ_{t_{k,0}}` and `σ_{t_{k,0}}`, respectively. We defer the discussion of parameter estimation to the subsequent subsections, while here we focus on discussing our proposed trading mechanism which is quite counterintuitive and not so immediately straightforward. However, it is inspired by and works consistently with our proposed theory.
