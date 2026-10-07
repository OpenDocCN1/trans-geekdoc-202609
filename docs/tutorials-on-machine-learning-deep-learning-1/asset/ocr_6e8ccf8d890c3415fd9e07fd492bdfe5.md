# Wrench making machine example: Two machines produce wrenches. We know that:

+   * Machine 1: produces 30 Wrenches Per Hour
* Machine 2: Produces 20 Wrenches Per Hour
* 1% of all wrenches are defective, where 50% of the wrenches that are defective from machine 1 and 50% from machine 2.

Question: What is the probability that a part produced by machine 2 is defective?

+   * Total wrench probability of being from machine M1 = 30/50 = 0.6
* **P(M1)** = probability of being from machine M1
* **P(M2)** = probability of being from machine M2 = 20/50 = 0.4
* **P(D)** = probability of being defective = 0.01
* **P(M1 | D)** = Probability of being from machine M1, from defective wrenches = 0.5, (probability of being M1 from a pile of defective wrenches)
* **P(M2 | D)** = probability of being from machine M2 from defective wrenches = 0.5, (probability of being M2 from a pile of defective wrenches)
* **P(D | M2)** = probability that a wrench produced by machine 2 is defective??? i.e. given that the wrench is then we need to find the probability of being defective. (from pile of wrenches only come from machine 2)

From Bayes' Theorem,

```
$P(M_2|D) = \frac{P(M_2)P(D|M_2)}{P(D)}$nProbability of being machine 2 from defective wrenches $	imes$ probability of being defective
probability of being from machine 2 $M_2$
\frac{0.5 \times 0.1}{0.4} = 0.0125 = \frac{1}{80}$
```

Its's intuitive:

# It's intuitive!

```
$P(Defect | Mach2) = \frac{P(Mach2) \times P(Defect)}{P(Mach2)} = 1.25\%$
```

Let's look at an example:

+   * 1000 wrenches
* 400 came from Mach2
* 1% have a defect = 10
* of them 50% defective parts from Mach2 = 5/400 = 0.0125

probability that a Wrench produced by machine 2 is defective = $\frac{Number of defective wrenches from machine 2}{Number of wrenches from machine 2}$

```
$P(M_2|D)P(D)=$ Number of defective wrenches comes from machine 2
$P(M_2)=$ Number of wrenches comes from machine 2
```

: means given in mathematical terms.

+   * Similarly, probability that a Wrench produced by machine 1 is defective = $\frac{P(D|M_1)P(D)}{P(M_1)}$n\frac{0.5 \times 0.01}{0.6} = \frac{1}{120}$