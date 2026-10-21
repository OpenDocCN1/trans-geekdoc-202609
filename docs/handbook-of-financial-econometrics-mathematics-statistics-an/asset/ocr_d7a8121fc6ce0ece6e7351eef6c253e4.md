+   - D. Duffie (2001). *Dynamic Asset Pricing Theory*. Princeton, NJ: Princeton University Press.
+   - F. J. Fabozzi (2007). *Fixed Income Analysis*, 2nd ed. New York: Wiley.
+   - S. Figlewski (1989). Options Arbitrage in Imperfect Markets. *Journal of Finance*, 44(5), 1289–1311.
+   - D. Galai (1983). The Components of the Return from Hedging Options against Stocks. *Journal of Business*, 56(1), 45–54.
+   - J. Hull (2017). *Options, Futures, and Other Derivatives*, 10th ed. Upper Saddle River, New Jersey: Prentice Hall.
+   - J. Hull and A. White (1987). Hedging the Risks from Writing Foreign Currency Options. *Journal of International Money and Finance*, 6(2), 131–152.
+   - I. Karatzas and S. E. Shreve (2000). *Brownian Motion and Stochastic Calculus*, Berlin: Springer.
+   - F. C. Klebaner (2005). *Introduction to Stochastic Calculus with Applications*, London: Imperial College Press.
+   - C. F. Lee, J. Lee, J. R. Chang, and T. Tai (2016). *Essentials of Excel, Excel VBA, SAS and Minitab for Statistical and Financial Analyses*, New York: Springer.
+   - R. L. McDonald (2012). *Derivatives Markets*, 3rd ed. Boston, MA: Addison-Wesley.
+   - A. Saunders and M. M. Cornett (2018). *Financial Markets and Institutions*, 7th ed. McGraw-Hill.
+   - Schroder, M. (1989). A reduction method applicable to compound option formulas. *Management Science*, 35(7), 823–827.
+   - S. E. Shreve (2004). *Stochastic Calculus for Finance II: Continuous Time Model*, New York: Springer.
+   - B. Tuckman (2002). *Fixed Income Securities: Tools for Today's Markets*, 2nd ed. New York: Wiley.

# Appendix 86A: Convexity and Bond Price Change

Duration appears a better measure of a bond’s life than maturity because it provides a more meaningful relationship with interest-rate changes. This relationship has been expressed by Hopewell and Kaufman (1973) as

$$\frac{\Delta P}{P} = \frac{D}{(1+i)}\Delta i = D^*\Delta i, \tag{86A.1}$$

where $\Delta$ = “change in”; $P$ = bond price; $D$ = duration; and $i$ = market interest rate or bond yield.

The duration rule in equation (86A.1) is a good approximation for small changes in bond yield, but it is less accurate for large changes. Equation (86A.1) implies that percentage change in bond price is linearly related to change in yield to maturity. If this linear relationship does not hold, following Saunders and Cornett (2018), then equation (86A.1) can be generalized as

$$\frac{\Delta P}{P} = -D^*\Delta i + 0.5 \times \text{Convexity} \times (\Delta i)^2, \tag{86A.2}$$