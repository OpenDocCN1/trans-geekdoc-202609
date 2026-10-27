with the same characteristics. What our framework does not allow for is a change over time in the cross-sectional moments of the characteristics in X. With a stochastically changing X it could happen, for example, that two characteristics that are highly correlated in one period are no longer strongly correlated in future periods. This would make investors’ learning and forecasting problems harder.

Third, while we consider a fairly high-dimensional environment in with J can be close to N, we assume that J < N. The set of characteristics available to real-world investors is potentially very large and so J ≥ N might be reasonable. An extension to allow for J ≥ N would be relatively straightforward, but at the cost of considerably greater notational complexity. The effects of learning on asset price properties can be seen more clearly in the simpler J < N setting.

Overall, our model therefore likely understates the difficulty of the learning problem that actual investors face in their investment decision-making process. Even so, as analysis in this chapter will show, the properties of asset prices are strongly affected by learning. Extending the model to take into account realistic additional complications in the learning problem would further enhance these effects.

The properties of the parameter vector g, and investors’ beliefs about the values of these parameters, play an important role in our analysis. Specifically, the magnitudes of the elements of g determine the proportion of cash flow growth variation that is predictable with X. Therefore, when investors learn about g from historical observations of Δy, the magnitudes of the g elements determine the ratio of signal (variance of Xg) to noise (variance of e) in Δy.

We assume that the vector g is drawn from a multivariate normal distribution,

g ∼ N(0, θ/J I_J), (5.2)

where θ is a constant. We think of g as drawn by nature, at the very beginning of this economy, before any dividends are realized and any assets priced. It then stays constant through time. The specification of variances and covariances as proportional to 1/J in (5.2) ensures that the signal to noise ratio is invariant to J. To see this, note that if investors had perfect knowledge of the parameter vector g, investors would be able to fully predict the Xg component of Δy_t in (5.1). One can show that this predictable component has the cross-sectional variance 1/N 𝔼[g'X'Xg] = θ.¹

¹ Apply the trace operator, use its cyclical properties, and use the normalization of tr(X'X)=N J from above.