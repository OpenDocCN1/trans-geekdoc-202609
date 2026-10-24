(1) property rights management; (2) procedural control; and (3) economic and social functions.

+   Property rights management. A smart contract could issue a new token, destroy a token, and exchange property rights between users.

+   Procedural control. To make a payment, the smart contract must include provision to make sure the source address or account for the payment has sufficient fund. The smart contract could also implement sophisticated contingent plan to ensure the payment will happen.

+   Economic and social functions. These include collateralization, and token lockup and release. Voting can be simulated by designating addresses for the candidates, and then one would vote by sending a token to one of these addresses. Token collateralization refers to the procedure that a user first deposit some predefined number of tokens with a refund condition. The user will get the tokens deposited back when the condition is met. Tokens can also be locked up for some predefined time. The owners of the tokens would temporarily lose liquidity and will get the tokens back after the time expires.

They pointed out three major shortcomings on smart contracts.

+   Lack of decentralized oracle mechanisms to ensure outside information is correct. External information can be recorded into the blockchain through smart contract. To make sure such information is correct, an oracle mechanism is needed. To be consistent with the decentralization design goal, the current approach to accomplish the goal is to use economic incentives and some voting schemes. However, Xu and Zou pointed that this solution could not stem the systematic biases in votes.

+   Unable to eliminate credit risk. For example, a smart contract states that one address or account should pay someone certain amount of tokens. However, that address might not have enough tokens to make the required payment. To mitigate such risk, over-collateralization could be used. But the amount needed to set aside is difficult to determine in advance.

+   The issue on incomplete contracts. Due to human nature, complex contracts will be intrinsically incomplete. That is