
# Blockchain and Distributed Ledgers: Mathematics, Technology, and Economics

with unique genomes defining their appearance and traits. Since each kitty is an Ethereum ERC-721 token, all of them are one-of-a-kind. By construction, a CryptoKitty is cryptographically secure. Hence, it cannot be replicated, taken away from the owner, or destroyed.

By the end of 2018, cumulative sales of CryptoKitties exceeded US$27 million, including a CryptoKitty, sold for US$140,000 on May 12, 2018. The CryptoKitties-related traffic was so high that it clogged and slowed down the Ethereum blockchain in late 2017 and dramatically increased gas prices. This fact shows that Ethereum is far from being robust with its spare capacity.

At the beginning of 2021, NFTs caught the interest of the general public and experts alike. An extensive market for NFTs trading practically overnight. Up to now, the most striking example is the sale of digital art by Beeple, called EVERYDAYS: THE FIRST 5000 DAYS, for US$69.3 million in 2021 at an auction organized by a British auction house Christie's. The full potential of NFTs remains to be seen, but they open new possibilities of trading digital objects as JPG files. One of the problems with such files is their infinite reproducibility. By signing a file digitally and using Ethereum as a CaaS provider to track its transition from one owner to the next, one can artificially create digital scarcity for the signed file. The best way of understanding the difference between a signed and unsigned version is baseball parallelism. While physically identical, a signed ball or other item is of magnitude more expensive than the unsigned one. One can think of an NFT as an autographed collectible object. The problem of fakes, which affects the market for collectibles, is less of an issue for NFTs because they are perfectly traceable from the moment they are created, of course, that the original is legitimate. However, NFTs are not universally welcomed by all — the main point of contention is the fact that they are not environmentally friendly. Perhaps this problem could be resolved if and when Ethereum switches to a PoS consensus.

## 6.9.3 Crowdfunding via initial coin offerings

An initial coin offering (ICO) is a type of funding relying on issuing Ethereum-based ERC-20 tokens, or occasionally, tokens based on other protocols. Typically, entrepreneurs sell ICOs on Ethereum, but private placements are uncommon. As a rule, in ICO, “tokens” or “coins” are sold to speculators or investors in exchange for Bitcoin or Ethereum, or seldom. These tokens promise monetary rewards when the ICO's goals are met or during the project's life. In principle, an ICO can be an attractive capital source for startup companies because they do not dilute ownership. On the pros side, ICOs allow startups to operate independently without angel investors and venture capital. On the cons side, in most cases, ICOs fail in legal limbo concerning existing regulations. Surprisingly, they are prone to scams, get rich schemes, and securities law violations. Authorities ban them in several countries, such as China and South Korea. The question of whether or not tokens sold via ICOs are very nuanced.

> While reasonable people can disagree about the bubble-like behavior of the cryptocurrency prices, no one can argue that CryptoKitties prices have not experienced a bubble.

One cannot answer without studying the actual offering in detail; see, e.g., Blandin et al. (2019); Walch (2015).

A typical ICO half-life is shorter; fewer than half of ICOs survive longer than four months. For example, almost half of ICOs sold in 2017 failed. Despite this abysmal record of failure, they remained popular longer than they should have been — in 2017, ICO raised US$7 billion, in 2018, they brought in US$12 billion, of which US$4.2 billion went toward EOS protocol, and US$1.2 billion toward Telegram, the latter project eventually failed. In fairness, in 2019, the ICO market was down 97% compared with 2018 and is still present.

## 6.9.4 Stablecoins

Ethereum stablecoins are typically ERC-20 or ERC-223 tokens pegged to an asset or a basket of assets, viewed as stable in a conventional economic sense. The Ethereum protocol is often regarded as a natural medium for stablecoins, while the Bitcoin protocol is considered ill-suited for anything other than recording BTC transactions. However, the biggest by far and arguably, the most controversial of stablecoins is Tether, a Bitcoin Omni Layer token.

Given their paramount importance for the real-life applications of DLT, we dedicate Chapter 8 to their detailed analysis. Here we mention that there are six types of stablecoins:

- (1) fully collateralized by individual fiat currencies;
- (2) fully collateralized by baskets of fiat currencies;
- (3) partially collateralized by fiat;
- (4) overcollateralized with ETH;
- (5) algorithmically stabilized;
- (6) asset-backed.

Unfortunately, the structure of the Ethereum protocol is decentralized. The reason is to comprehend — there are no direct connections between the Ethereum ecosystem and the real economy, that miners must pay for their hardware and electricity in fiat. Thus, asking the question: “What is the price of a token?” automatically destroys decentralization. Conceptually, this is similar to the uncertainty principle in quantum mechanics, which states that one cannot assign exact simultaneous values to a physical system’s position and its momentum.

Even without the arguments mentioned above, fiat or asset collateralized stablecoins centralized because the corresponding collateral must be held outside of the Ethereum blockchain. For ETH-backed and algorithmically stabilized coins, centralization comes from the fact that an oracle is needed to know ETH’s market price determined on

## 6.9.5 Automated market makers

Let us design an SC, also called an automated market maker (AMM), capable of making markets between two tokens $T_1, T_2$. At present, AMMs are an essential integral part of the burgeoning decentralized finance (DeFi) ecosystem. They allow anyone to become a market maker by delivering $T_1$ and $T_2$ simultaneously in the right proportion to the collateral pool. Subsequently, anyone can remove one of the tokens from the pool by posting the other token to the pool.

The predetermined rules defining the exchange rate can vary. This section considers three choices: the constant sum, the constant product, and a mixture of two. Several papers cover this material; see, e.g., Angeris et al. (2019); Egorov (2019); Schur (2020); Zhang et al. (2018).

Assume initial prices of these tokens are equal to each other, and consider an automated market maker defined by the constant sum:

$$X + Y = \Sigma_0, \quad (6.2)$$

Here X, Y are the numbers of TN1, TN2, respectively. Eq. (6.2) yields:

$$Y = \Sigma_0 - X, \quad \frac{dY}{dX} = 1. \quad (6.3)$$

The first equation shows that the pool becomes exhausted when $X = \Sigma_0$. Increasing X from N to 2N is a rational thing for an arbitrageur to do TN2 becomes more expensive than TN1. At the same time, the marginal price of TN2 expressed in terms of TN1, given by Eq. (6.3), is constant and equal to 1. market maker is acceptable when TN1, TN2 represent stablecoins, so that their prices weakly fluctuate around their equilibrium values. In the absence of transaction fees, it is still rational to exhaust the pool if the deviation from equilibrium is minuscule. However, in the more realistic situation when transaction fees are nonzero, the corresponding deviation has to be above a threshold.

Now we consider a more interesting (and practically) constant product rule:

$$XY = \Pi_0, \quad X_0 = Y_0 = N, \Pi_0 = N^2. \quad (6.4)$$

It is clear that

$$Y = \frac{\Pi_0}{X}, \quad \frac{dY}{dX} = -\frac{\Pi_0}{X^2}. \quad (6.5)$$

Thus, regardless of the arbitrageur’s actions, the pool will not be exhausted and shall be able to exist indefinitely. The price of TN2 expressed in terms of TN1 is no longer constant, of course. It increases (decreases) when X increases (increases). it is natural to look for a rule more general than the constant sum and constant product rule. The constant sum and constant product rules, given by Eqs (6.2) and (6.4), can be
