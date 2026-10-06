# Chapter 6 Ethereum — a Distributed World? | 225

externally produced and does not require any mining. Thus, one could characterize these ledgers as being centralized-decentralized. The corresponding tokens are pre-mined and distributed from a single source. Therefore, maintaining the ledger's internal consistency by making sure that since accounting rules are followed, is the only requirement.

Initial developers proposed several competing approaches to the most efficient maintenance of token-bearing ledgers, but, eventually, best practices in the form of ever standards, such as the ERC-20 standard for fungible tokens and the ERC-721 standard for nonfungible ones.

The fungibility of ERC-20 tokens means that individual units are identical and interchangeable. Accordingly, any two tokens represent the same value.

The ERC-20-compliant token to have three optional functions and six mandatory. Optional functions include a token name, token symbol, and decimal. The mining of first two functions is self-explanatory. The third one is an integer between 0 and 18, which shows the token's smallest unit. If Decimal is 0, it is the smallest unit; if Decimal is 18, 10⁻¹⁸ is the indivisible base unit, similar to wei in Ethereum. In addition to optional, every ERC-20 contract has six mandatory public functions, whose meaning is self-explanatory:

+   1) totalSupply(), returns (uint256 totalSupply); totalSupply gets the token supply.

+   2) balanceOf(address_owner), returns (uint256 balance); balanceOf gets the account balance.

+   3) transfer(address_to, uint256 value), returns (bool success); transfer sends _value tokens to _to.

+   4) transferFrom(address_from, address_to, uint256 value), returns (bool success); transferFrom sends _value amount of tokens from _address_from to _to.

+   5) approve(address_spender, uint256 value), returns (bool success); approve spender to withdraw funds multiple times from the account to the predetermined value amount. When called, this function overwrites the current allowance another value.

+   6) allowance(address_owner, address_spender), returns (uint256); allowance returns the amount which address_spender is allowed to withdraw from address_owner.

The ERC-20 token standard, being the first of a kind, suffers from several drawbacks. The ERC-223 token standard, superseding ERC-20, gained considerable attention to address these shortcomings. The ERC-223 standard is safer than its predecessor since it doesn't allow tokens to contracts that cannot prevent receiving and handling. Still, many existing tokens rely on the ERC-20 standard.

The ERC-721 token is unique, and imagination to wild can be seen as one-of-a-kind collectible. Since ERC-721 tokens are unique, they can represent ownership over assets, such as title deeds, art and digital collectibles. Of course, establishing real assets ownership is not just (or even most) a technological problem and requires building a robust foundation first.

For brief period in 2017 and 2018, ERC-721-based CryptoKitties gained considerable popularity. CryptoKitties is an online game allowing users to collect and breed virtual cats

![](bbox=[0.45, 0.975, 0.545, 0.995])