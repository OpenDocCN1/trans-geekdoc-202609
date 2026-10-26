
- **Help with APIs?** If you need help with using a specific Python function, see the list of resources in the *Further Reading* section at the end of each lesson, and also see *Appendix A*.
- **Help with your workstation?** If you need help setting up your environment, I would recommend using Anaconda and following my tutorial in *Appendix B*.
- **Help in general?** You can shoot me an email. My details are in *Appendix A*.

## Next

Are you ready? Let’s dive in! Next up you will discover that probability is an important foundational field of mathematics.

## Chapter 1

## What is Probability?

Uncertainty involves making decisions with incomplete information, and this is the way we generally operate in the world. Handling uncertainty is typically described using everyday words like chance, luck, and risk. Probability is a field of mathematics that gives us the language and tools to quantify the uncertainty of events and reason in a principled manner. In this tutorial, you will discover a gentle introduction to probability. After reading this tutorial, you will know:

- Certainty is unusual and the world is messy, requiring operating under uncertainty.
- Probability quantifies the likelihood or belief that an event will occur.
- Probability theory is the mathematics of uncertainty.

Let’s get started.

### 1.1 Tutorial Overview

This tutorial is divided into four parts; they are:

- 1. Uncertainty is Normal
- 2. Probability of an Event
- 3. Probability Theory
- 4. Two Schools of Probability

### 1.2 Uncertainty is Normal

Uncertainty refers to imperfect or incomplete information. Much of mathematics is focused on certainty and logic. Much of programming is this way too, where we develop software with the assumption that it will execute deterministically. Yet, under the covers, computer hardware is subject to noise and errors that are being checked and corrected all of the time. Certainty with perfect and complete information is unusual. It is the place of games and contrived examples.

Almost everything we do or are interested in involves information on a continuum between uncertainty or wrongness. The world is messy and imperfect and we must make decisions and operate in the face of this uncertainty. For example, we often talk about luck, chance, odds, likelihood, and risk. These are words that we use to interpret and negotiate uncertainty in the world. When making inferences and reasoning in an uncertain world, we need principled, formal methods to express and solve problems. Probability provides the language and tools to handle uncertainty.

### 1.3 Probability of an Event

Probability is a measure that quantifies the likelihood that an event will occur. For example, we can quantify the probability of a fire in a neighborhood, a flood in a region, or the purchase of a product. The probability of an event can be calculated directly by counting all of the occurrences of the event, dividing them by the total possible outcomes of the event.

$$\text{probability} = \frac{\text{occurrences}}{\text{non-occurrences} + \text{occurrences}} \tag{1.1}$$

The assigned probability is a fractional value and is always in the range between 0 and 1, where 0 indicates no probability and 1 represents full probability. Together, the probability of all possible events sums to the probability value one. If all possible occurrences are equally likely, the probability of their occurrence is 1 divided by the total possible occurrences or trials. For example, each of the numbers 1 to 6 are equally likely from the roll of a fair die, therefore each has a probability of $\frac{1}{6}$ or 0.166 of occurring.

Probability is often written as a lowercase $p$ and may be stated as a percentage by multiplying the value by 100. For example, a probability of 0.3 can be stated as 30% (given 0.3 × 100). A probability of 50% for an event, often spoken of as a *50-50 chance*, means that it is likely to happen half the time. The probability of an event, like a flood, is often denoted as a function (e.g. the probability function) with an uppercase $P$. For example:

$$P(flood) = \text{probability of a flood} \tag{1.2}$$

It is also sometimes written as a function of lowercase $p$ or $Pr$. For example: $p(flood)$ or $Pr(flood)$. The complement of the probability can be stated as one minus the probability of the event. For example:

$$1 - P(flood) = \text{probability of no flood} \tag{1.3}$$

The probability, or likelihood, of an event is also commonly referred to as the odds of the event or the chance of the event. These all generally refer to the same notion, although odds often has its own notation of wins to losses, written as w:l; e.g. 1:3 for 1 win and 3 losses or $\frac{1}{4}$ (25%) probability of a win. We have described naive probability, although probability theory allows us to be more general.

### 1.4 Probability Theory

More generally, probability is an extension of logic that can be used to quantify, manage, and harness uncertainty. As a field of study, it is often referred to as probability theory to differentiate it from the likelihood of a specific event.

### 1.5.2 Bayesian Probability

The Bayesian approach to probability is subjective. Probabilities are assigned to events based on evidence and personal belief and are centered around Bayes’ theorem, hence the name *Bayesian*. This allows probabilities to be assigned to very infrequent events and events that have not been observed before, unlike frequentist probability.

> One big advantage of the Bayesian interpretation is that it can be used to model our uncertainty about events that do not have long term frequencies.
>
> — Page 27, *Machine Learning: A Probabilistic Perspective*, 2012.

Methods from Bayesian probability include Bayes factors and credible interval for inference and Bayes estimator and maximum a posteriori estimation for parameter estimation.

### 1.6 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

### 1.6.1 Books

- *Probability Theory: The Logic of Science*, 2003.  
  https://amzn.to/2lnW2pp
- *Introduction to Probability*, 2nd edition, 2019.  
  https://amzn.to/2xPvobK
- *Introduction to Probability*, 2nd edition, 2008.  
  https://amzn.to/2l1A3PR

### 1.6.2 Articles

- Uncertainty, Wikipedia.  
  https://en.wikipedia.org/wiki/Uncertainty
- Probability, Wikipedia.  
  https://en.wikipedia.org/wiki/Probability
- Odds, Wikipedia.  
  https://en.wikipedia.org/wiki/Odds
- Probability theory, Wikipedia.  
  https://en.wikipedia.org/wiki/Probability_theory

### 1.7 Summary

In this tutorial, you discovered a gentle introduction to probability. Specifically, you learned:

- Certainty is unusual and the world is messy, requiring operating under uncertainty.
- Probability quantifies the likelihood or belief that an event will occur.
- Probability theory is the mathematics of uncertainty.

### 1.7.1 Next

In the next tutorial, you will discover the source of uncertainty in machine learning.

## Chapter 2

## Uncertainty in Machine Learning

Applied machine learning requires managing uncertainty. There are many sources of uncertainty in a machine learning project, including variance in the specific data values, the sample of data collected from the domain, and in the imperfect nature of any models developed from such data. Managing the uncertainty that is inherent in machine learning for predictive modeling can be achieved via the tools and techniques from probability, a field specifically designed to handle uncertainty. In this tutorial, you will discover the challenge of uncertainty in machine learning. After reading this tutorial, you will know:

- Uncertainty is the biggest source of difficulty for beginners in machine learning, especially developers.
- Noise in data, incomplete coverage of the domain, and imperfect models provide the three main sources of uncertainty in machine learning.
- Probability provides the foundation and tools for quantifying, handling, and harnessing uncertainty in applied machine learning.

Let’s get started.

### 2.1 Tutorial Overview

This tutorial is divided into five parts; they are:

- 1. Uncertainty in Machine Learning
- 2. Noise in Observations
- 3. Incomplete Coverage of the Domain
- 4. Imperfect Model of the Problem
- 5. How to Manage Uncertainty
