
![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_398_0.png)

Figure 10.37 Histograms for the Profit-and-Loss distribution: (a) low mean-reversion; (b) high mean-reversion. Own graphics.

# Chapter 10 Cryptocurrencies and Quantitative Finance | 353

Most of the material covered in this section is original. Additional insights can be found in several recent papers; see, e.g., Angeris et al. (2019); Egorov (2019); Schär (2020); Zhang et al. (2018).

## 10.12 Summary

This chapter covers some important topics related to the behavior of cryptocurrencies as assets. We have shown that their returns are significantly more volatile than conventional currencies, such as EUR/USD and USD/JPY. Even more importantly, these returns have profound non-Gaussian features, including heavy tails. This observation is of importance for risk managers in general and clearing houses wishing to engage in cryptocurrency trading, in particular.

Next, we covered some possible approaches to BTC pricing. Given the fact that BTC is an SoV asset, conventional financial tools are not useful for its valuation. While there are approaches tried in the literature, none is particularly convincing. Still, we described the well-known S2F model and proposed its improvements. The latter enabled us to demonstrate that, in contrast with the predictions of the standard model, BTC price reaches saturation in the long run, albeit at a very high level. We presented an analysis of the Bitcoin dominance index's behavior, based on two complementary approaches borrowed from epidemiology, and concluded that BTC would dominate all other cryptocurrencies in the long run. Finally, we discussed AMMs and studied their profitability (or lack thereof) using the standard tools of quantitative finance, as Monte Carlo simulation. We have shown that AMM could be profitable, but not as much as is occasionally claimed.

Studying cryptocurrencies via quantitative finance methods is becoming more popular by the day. We expect a lot of exciting results in this research area going forward.

## 10.13 Exercises

- 1. Parameters in Tables 10.2 and 10.3 are calculated using market data for six years, from July 1, 2013 to July 1, 2020. Extend the data series until the present by using a suitable source of information, such as coinmarketcap.com, and redo the calculations. Which distribution provides the best fit for your data?
- 2. Same question for parameters in Tables 10.4–10.10.
- 3. At present, the Bitcoin protocol generates approximately 900 BTC per day. Given that, do you think that the S2F model is suitable for studying BTC price dynamics?
- 4. Why is it not possible to use an AMM on the constant sum rule? What motivates designers of the DeFi protocols to consider the mixed rule for AMMs?

# CHAPTER 11 Current Research Topics

## 11.1 Introduction

DLT is a field of rapid innovation and constant development, but despite frantic research efforts, it remains plagued by many fundamental issues that must be resolved in order for the underlying technology to achieve its full potential. Comprehensive solutions for these problems have yet to be identified, which is not particularly surprising given their intrinsic complexity. The current chapter examines some of these problems, including intra- and interoperability, privacy, and the so-called scalability trilemma. Since our goal is to give a bird's eye view of the problems and sketch the framework for their solutions, we will omit most technical details and refer the reader to the relevant references.

The chapter is organized as follows. In Section 11.2, we discuss intra- and interoperability of distributed ledgers. Interoperability allows automatically exchanging different tokens defined on the same blockchain, such as USDC and TUSD. Interoperability is broadly defined as the ability to move any information between different blockchains. Narrowly, it means the capacity to exchange coins and tokens hosted on diverse blockchains.

Section 11.3 covers a vital topic of blockchain privacy, which is occasionally misunderstood. In the most common Bitcoin transactions, publicly known amounts of BTCs are moved between public addresses. For the untrained eye, little information about the actual owners of the accounts is exposed. However, with some effects, Bitcoin can be associated with real-world owners, especially if the actual BTCs are purchased on an exchange. To achieve better, if not perfect, additional cryptographic tools must be deployed. We discuss several approaches, including payment channels, mixing-based approaches, and zero-knowledge-based privacy.

Section 11.4 discusses the so-called scalability trilemma, which states that only out of three properties — decentralization, scalability, and security — can be achieved simultaneously. For instance, the existing blockchain system is scalable and secure (within reason), but it is not decentralized since it relies on a small number of commercial banks. The crypto protocols... are not scalable since they are processing very few transactions per second. We offer different approaches to solving the scalability trilemma, such as introducing larger blocks, using sharding, applying different consensus mechanisms, utilizing lightning networks, and several other possibilities. Conclusions are drawn in Section 11.5.

## 11.2 Intra- and interoperability

### 11.2.1 Background

A well-designed blockchain, viewed in isolation, provides intrinsic decentralization. However, for the DLT to be truly successful, it is essential to ensure that decentralization occurs across different blockchains. Such decentralization offers an application developer a single view regardless of the number of blockchains. [ (truncated text) ] ... and other ledger structures, as Hardjono et al. (2019a); Lipton and Hardjono (2021). The TCP/IP Internet is architected along lines. This design explains why the Internet has grown in size and traffic capacity to serve end-users globally; rather than being a single IP network, the Internet is a collection of interconnected Autonomous Systems (ASs); as Clark (1988). Having a well-defined physical boundary, each AS is operated by Internet Service Provider (ISP).

In this section, we discuss approaches to blockchain- and interoperability. We define blockchain intraability as an ability for automatically exchanging different assets defined on the same blockchain, supporting smart contracts, for instance, Ethereum. We define interoperability as a capability to move assets between different blockchains.

Currently, it is not known how to fully achieve intraability or interoperability. We argue that using automated market makers (AMMs) discussed in 10.11, for interoperability the gateway-gateway protocols can be utilized. The reader can find additional information in Abadi and Brunnemer (2018); Buterin (2016); Hardjono et al. (2019a); Hope-Baillie and Thomas (2016); Koens and Pohl (2019); Lima (2018); Lipton and Hardjono (2021); Pillai et al. (2019); Thomas and Schwartz (2015), and references therein.

### 11.2.2 Interoperability

Lipton and Hardjono (2021) show that intraability is achievable using AMMs, which currently operate as dark pools. Recall that dark pools of liquidity (also dark liquidity) operate as consensus networks for large buy and sell orders providing liquidity not displayed on exchanges. By using dark pools, traders can buy or sell large numbers of shares without revealing their positions or impacting market prices because the trading company’s identity is displayed. Dark pools track prices established at public exchanges; they can be viewed as price takers. AMMs operate along similar coins' prices established on centralized exchanges. Thus, despite their name, AMMs cannot operate autonomously. To achieve interoperability, one needs to reach a state when AMMs from price takers, become price makers, i.e., their composition defines the relative price of constituent tokens and not the other way around. Interoperability requires AMMs to become market players, dominating centralized exchanges. While appearing in theory, time will tell if such dominance is achievable in practice.
