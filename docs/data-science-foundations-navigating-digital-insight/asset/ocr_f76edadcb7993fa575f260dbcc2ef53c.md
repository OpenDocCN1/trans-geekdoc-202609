Example: Coke and Pepsi might have lift = 0.5.

Some things that you can assume from the results you generate (known as pruning in Apriori):

+   - If {Item 1} isn’t frequent, then {Item 1, Item 2} can’t be frequent,
- If {Item 1, Item 2} isn’t frequent, then {Item 1, Item 2, Item 3} can’t be frequent.

These properties help to reduce the number of combinations to check.

![](bbox=[0.125, 0.477, 0.206, 0.532])

# KYD yourself

A common mistake in association rule mining is ignoring the domain knowledge and context of the data. Experts in what is actually happening in a business can help to select relevant items for the analysis and highlight rules that are redundant, allowing you to focus on the more meaningful patterns. For example, if you know that everyone always buys a case with a new phone, then it could be worth ignoring this to focus on patterns that have not been realised. You should also take