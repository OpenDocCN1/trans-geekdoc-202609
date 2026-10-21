
## p-values of Phillips–Perron test

| PP test | No regressors | Intercept | Intercept and time trend |
|---|---|---|---|
| Brunei | 0.0158* | 0.0000* | 0.0000* |
| Cambodia | 0.2643 | 0.4674 | 0.5585 |
| Indonesia | 0.0336* | 0.0001* | 0.0000* |
| Laos | 0.8008 | 0.5949 | 0.0010* |
| Malaysia | 0.3278 | 0.1529 | 0.0000* |
| Myanmar | 0.0000* | 0.0000* | 0.0000* |
| Philippines | 0.0022* | 0.0000* | 0.0000* |
| Singapore | 0.0031* | 0.0015* | 0.0000* |
| Thailand | 0.0000* | 0.0000* | 0.0000* |
| Vietnam | 0.0060* | 0.0041* | 0.0109* |

Note: *: Evidence of stationarity at the 5% level.

This page intentionally left blank

## Manually Redacting Acquisition Documents

This panel is for all documents in the Acquisition (Lexbridge) data room, once you have selected the Documents tile from the Actions panel.

Manual Authors:

- Home
- Checklists / Data Rooms
- Deal Management

Manual redaction of a document in the Acquisition data room will permanently hide classified information from the document permanently.

Passes are plaintiff and the person has no right to certain portions that are not material to your case.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_959_0.png)

To begin the redaction process, click the Mark button in the top right of this panel. Clicking this will place you in a redaction mode where you can select sections with the document to cover.

To confirm the redaction is complete, refer to the Hide and Unhide tab within this menu.

Once you have selected the sections of the document that need concealment, you can click the redact button to permanently remove all hidden sections from the document.

## Advanced Concealment Settings

In this panel you can specify if the document should be viewable in part or in full to external collaborators.

All redactions will be recorded in the event log which covers the entire life cycle of the matter.

NB: These processes cannot be reversed. We recommend using the Hide / Unhide function if you are uncertain.

- 24.3.2 The existence of a risk neutral measure and the absence of arbitrage . . . . . . . . . . . . . . . . . . . . . . . 934
- 24.3.3 Trading in financial markets with frictions . . . . . . . . 935
- 24.4 The Option Bounds for American Options and Asian Options . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 936
- 24.4.1 American option bounds . . . . . . . . . . . . . . . . . 936
- 24.4.2 Asian option bounds . . . . . . . . . . . . . . . . . . . 937
- 24.5 Empirical Applications . . . . . . . . . . . . . . . . . . . . 937
- 24.5.1 Equities and equity indices . . . . . . . . . . . . . . . 938
- 24.5.2 Index futures . . . . . . . . . . . . . . . . . . . . . . . 939
- 24.5.3 Foreign exchange rates . . . . . . . . . . . . . . . . . . 939
- 24.5.4 Real options . . . . . . . . . . . . . . . . . . . . . . . . 940
- 24.6 Conclusion . . . . . . . . . . . . . . . . . . . . . . . . . . . 940
- Bibliography . . . . . . . . . . . . . . . . . . . . . . . . . . . . 941
- Appendix 24A: Mathematical Derivation of the Option Bounds . . . 944
- Appendix 24B: Tightening Techniques of the Option Bounds . . . . 945
- Appendix 24C: Other Option Bounds . . . . . . . . . . . . . . . . 945

## Abstract

This paper first reviews alternative methods for determining option bounds. This method includes Stochastic dominance, linear programming, semi-parametric method, and non-parametric method for European option. Then option bounds for American and Asian options are discussed. Finally, we discuss empirical applications in equities and equity indices, index futures, foreign exchange rates, and real options.

## Keywords

Option bounds • Stochastic dominance • Linear programming • Semi-parametric • Non-parametric • Incomplete market • American options • European options.

## 24.1 Introduction

Option pricing is a central issue in derivatives literature. After the seminal papers by Black and Scholes (1973) and Merton (1973), there has been an explosion in option pricing models developed over the last few decades. Rather than proposing new option pricing models, some researchers establish option bounds with only modest assumptions on the price distribution, investor’s preferences, and/or market frictions in accordance with the existence of incomplete markets. However, compared to fruitful review research on alternative option pricing models, there is no survey paper that provides a comprehensive review and comparison of the major theoretical models and

(3) Trading in markets with frictions (e.g., Henin and Pistre, 1998; Constantinides and Zariphopoulou, 1999, 2001; Masson and Perrakis, 2000; Constantinides and Perrakis, 2002; Constantinides et al., 2009).

Following the discussion of the various approaches mentioned above, we next review how these methods were applied to tighten bounds for American options and other options. After the summary of option bounds for various kinds of options, we survey the empirical studies that apply the theoretical option bounds to different derivatives markets. The important results and data used in each paper are also briefly described. In contrast with many studies on European option bounds, recently papers working on either the extensions to American options and other options or the empirical applications are just arising.

The rest of this paper is organized as follows: Section 24.2 summarizes the different mathematical techniques to derive option bounds. Section 24.3 discusses different approaches to tighten European options bounds. Section 24.4 reviews the option bounds for American options and other options. The empirical applications of option bounds can be found in Section 24.5. We then conclude in Section 24.6.

## 24.2 Mathematical Techniques to Derive Option Bounds

In this section, major mathematical methods used to derive option bounds are discussed in detail. The major techniques are classified into four broad categories: searching for arbitrage conditions, stochastic dominance, linear programming, semi- and non- parametric approaches. For each category, we review its influential papers and describe the basic concepts of the derivation process to obtain option bounds.

### 24.2.1 Arbitrage theory

Merton (1973) derives option bounds by searching for arbitrage conditions. Given no arbitrage assumption and the constant risk-free interest rate, r, the upper and lower bounds for European options can be obtained without any particular assumptions as follows:

$C_{\min}^E = \begin{cases} \max(S_0 - K e^{-rT}, 0) & \text{without dividend case} \\ \max(S_0 - D - K e^{-rT}, 0) & \text{with dividend case,} \end{cases}$
and $C_{\max}^E = S_0,$
(24.1)

$$P_{\min}^{E}=\begin{cases}\max\left(K e^{-rT}-S_{0},0\right) & \text{without dividend case}\\\max\left(D+K e^{-rT}-S_{0},0\right) & \text{with dividend case},\end{cases}$$ and $P_{\max}^{E}=K e^{-rT}$, (24.2)

where $C_{\min}^{E}$ and $C_{\max}^{E}$ represent the lower and upper bounds for a European call option, respectively; $P_{\min}^{E}$ and $P_{\max}^{E}$ are the lower and upper bounds for a European put option. $S_{0}$ is the current price of the underlying asset, $K$ denotes the strike price, and $D$ represents the dividend payment.

Without any assumptions of the distribution of the underlying asset's price, the bounds for American options written on stock with non-dividend can be derived as follows:

$C_{\min}^{A}=\max\left(S_{0}-K e^{-rT},0\right),\quad\text{and}\quad C_{\max}^{A}=S_{0},\qquad(24.3)$
$P_{\min}^{A}=\max\left(K-S_{0},0\right),\quad\text{and}\quad P_{\max}^{A}=K,\qquad(24.4)$

where $C_{\min}^{A}$ and $C_{\max}^{A}$ represent the lower and upper bounds for an American call option, respectively, $P_{\min}^{A}$ and $P_{\max}^{A}$ are the lower and upper bounds for an American put option.

The derivations of upper bounds for European and American call options are trivial. If the current underlying asset is not the value of these upper bounds, then arbitrageur can easily earn riskless profit by purchasing the current underlying asset of call options and selling call options. The upper bounds for European and American put options can also be proven by the same arbitrage trading strategy.

To derive the lower bounds of European options, we consider the following investments:

- Portfolio A: Purchase a European call option at price $C_{0}$ with strike price $K$ and purchase $K e^{-rT}$ value of bond
- Portfolio B: Purchase the underlying stock at price $S_{0}$
- Portfolio C: Purchase a European put option at price $P_{0}$ with strike price $K$ and purchase the underlying stock at price $S_{0}$
- Portfolio D: Purchase $K e^{-rT}$ value of bond

At maturity, portfolio B and portfolio D are worth $S_{T}$ and $K$, respectively. The value of portfolio A and portfolio C will be $\max(S_{T},K)$ where portfolios A and C is worth $S_{T}$ if $S_{T}>K$ and worth $K$ if $S_{T}\le K$. Therefore, unless the current value of portfolio A is at least as large as portfolio B, there will
