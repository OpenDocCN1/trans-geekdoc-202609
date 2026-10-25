As you can see, the positive cases are more concentrated within the top portion—the left side—of this “human dataset.” Let’s calculate the lift for the top portion. Overall, 32 percent of the individuals have HBO (12 of the 38). But among the top ten, it’s 70 percent. That’s a lift of 2.2: That top portion has 2.2 times as many positive cases as the overall population.

Now, this classroom exercise oversimplifies in a couple ways. It’s a comically small dataset, so the results are far from reliable. And the predictions are based on one and only one variable: TV size (that’s what we call a univariate model). Plus, the scores aren’t scaled to be probabilities, although they do serve to rank-order and calculate lift just the same. Despite these caveats, the visual effect and sample arithmetic illustrate the concepts for teaching purposes.

Why did I calculate lift for the top ten rather than, say, the top twenty? The answer is pragmatic. Perhaps I only have a marketing budget to contact that many. Or perhaps it’s only worth marketing my product where the HBO subscription rate is at least 70 percent. Let’s move on to some more realistic examples to explore further.

# To Deploy ML Is to Triage and Prioritize

This story is the same for a large-scale modeling project: Cases more likely to be positive—and therefore more deserving of attention—rank more highly.

Instead of those thirty-eight people in a classroom, say we have a list of 100,000 customers. Here are the first four:

| Name: | Model score: | Buy: |
|---|---|---|
| E. Siegel | 85.628% | Yes |
| G. Clooney | 85.626% | No |
| T. Mitchell | 85.625% | Yes |
| T. Bayes | 85.623% | Yes |
| ... | | |