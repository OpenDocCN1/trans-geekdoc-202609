# Appendix 27A: An Alternative Method to Derive the Black-Scholes Option-Pricing Model ........ 1067

Appendix 27A.1: Assumptions and the present value of the expected terminal option price ........ 1068

Appendix 27A.2: Present value of the partial expectation of the terminal stock price ........ 1069

Appendix 27A.3: Present value of the exercise price under uncertainty ........ 1073

# Abstract

The purpose of this chapter is to develop certain relatively recent mathematical discoveries known generally as stochastic calculus, or more specifically as Itô's Calculus and to also illustrate their application in the pricing of options. The mathematical methods of stochastic calculus are illustrated in alternative derivations of the celebrated Black-Scholes-Merton model. The topic is motivated by a desire to provide an intuitive understanding of certain probabilistic methods that have found significant use in financial economics.

# Keywords

Stochastic calculus ● Itô's lemma ● Options pricing ● Martingale.

# 27.1 Introduction

The purpose of this chapter is to develop certain relatively recent mathematical discoveries known generally as stochastic calculus (or more specifically as Itô's Calculus), describe some more modern methods and illustrate their application in the pricing of options. The topic is motivated by a desire to provide an intuitive understanding of certain probabilistic methods that have found significant use in financial economics. A rigorous presentation of the same ideas is presented briefly in Malliaris (1983), and more extensively like Malliaris and Brock (1982), Duffie (1996) or Karatzas and Shreve (2005). Lamberton and Lapeyre (2007), Øksendal (2007), and Neftci (2000) are also useful books on stochastic calculus.

Itô's Calculus was prompted by purely mathematical questions originating in N. Wiener's work in 1923 on stochastic integrals and was developed by the Japanese probabilist Kiyosi Itô during 1944–1951. Two decades later economists such as Merton (1973) and Black and Scholes (1973) started using Itô's stochastic differential equation to describe the behavior of asset prices. The results of Black–Scholes–Merton were soon generalized in the larger framework of the fundamental theorem of asset pricing following the work of Harrison and Kreps (1979) and Duffie and Huang (1985–1986). According