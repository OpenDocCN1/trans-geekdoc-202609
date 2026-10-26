```
# calculate P(not A)
not_a = 1 - p_a
# calculate P(B)
p_b = p_b_given_a * p_a + p_b_given_not_a * not_a
# calculate P(A|B)
p_a_given_b = (p_b_given_a * p_a) / p_b
return p_a_given_b

# P(A)
p_a = 0.02
# P(B|A)
p_b_given_a = 0.99
# P(B|not A)
p_b_given_not_a = 0.001
# calculate P(A|B)
result = bayes_theorem(p_a, p_b_given_a, p_b_given_not_a)
# summarize
print('P(A|B) = %.3f%%' % (result * 100))
```

Listing 16.3: Example of calculating the probability of detecting spam.

Running the example gives the same result, confirming our manual calculation.

```
P(A|B) = 95.284%
```

Listing 16.4: Example output from calculating the probability of detecting spam.

# 16.6 Example: Liars and Lie Detectors

Consider the case where a person is tested with a lie detector and gets a positive result suggesting that they are lying, what is the probability that the person is indeed lying? Let’s assume some details, such as most people that are tested are telling the truth, such as 98%, meaning (1 − 0.98) or 2% are liars P(A). Let’s also assume that when someone is lying that the test can detect them well, but not great, such as 72% of the time P(B|A). Let’s also assume that when the machine says they are not lying, this is true 97% of the time P(not B| not A). Let’s plug what we know into the theorem:

$P(A|B) = \frac{P(B|A) \times P(A)}{P(B)}$

$P(\text{Lying}|\text{Positive}) = \frac{P(\text{Positive}|\text{Lying}) \times P(\text{Lying})}{P(\text{Positive})}$
(16.19)

Or:

$P(\text{Lying}|\text{Positive}) = \frac{0.72 \times 0.02}{P(\text{Positive})}$
(16.20)

Again, we don’t know $P(B)$, or in this case how often the detector returns a positive result