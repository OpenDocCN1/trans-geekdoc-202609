# 2.2.2 Joint Probability

Next, we consider when events A and B are not mutually exclusive. Two events are non-mutually exclusive if they have one or more outcomes in common, as illustrated in Figure 2.4. The probability of the union event A or B (or $A \cup B$) is

```
$P(A \cup B) = P(A) + P(B) - P(A \cap B) \quad (2.13)$
```

Sample space

![](bbox=[0.233, 0.296, 0.71, 0.46])

where $P(A \cap B)$ is called the joint probability of events A and B, that is, the probability of the intersection of joint event $A \cap B$.

The probability of event A occurs, but not B; that is,

```
$P(A - B) = P(A) - P(A \cap B) \quad (2.14)$
```

# **Example 2.1**

Consider two events A and B with $P(A) = 0.6, P(B) = 0.3$, and $P(A \cap B) = 0.1$.

Find: (a) the probability of A does not occur, (b) the probability of A or B occurs, and (c) the probability of A but not B occurs.

# **Solution**

+   - **A.** $P(\text{not } A) = P(\bar{A}) = 1-P(A) = 1-0.6 = 0.4$
- **B.** $P(A \text{ or } B \text{ occurs}) = P(A \cup B) = P(A) + P(B) - P(A \cap B) = 0.6+0.2-0.1 = 0.9$
- **C.** $P(A \text{ but not } B) = P(A-B) = P(A) - P(A \cap B) = 0.6-0.1 = 0.5$