# 3 Statistics

# 3.1 Introduction

Probability theory (which we discussed in Chapter 2) is concerned with modeling the distribution over observed data outcomes D given known parameters θ by computing p(D|θ). By contrast, statistics is concerned with the inverse problem, in which we want to infer the unknown parameters θ given observations, i.e., we want to compute p(θ|D). Indeed, statistics was originally called inverse probability theory. Nowadays, there are two main approaches to statistics, frequentist statistics and Bayesian statistics, as we discuss below. (See also Section 34.1, where we compare the frequentist and Bayesian approaches to decision theory.) Note, however, that most of this chapter (and the entire book) focuses on the Bayesian approach, for reasons that will become clear.

# 3.2 Bayesian statistics

In the Bayesian approach to statistics, we treat the parameters θ as unknown, and the data D as fixed and known. (This is the opposite of the frequentist approach, which we discuss in Section 3.3.) We represent our uncertainty about the parameters, after (posterior to) seeing the data, by computing the posterior distribution using Bayes’ rule:

p(θ|D) = \frac{p(θ)p(D|θ)}{p(D)} = \frac{p(θ)p(D|θ)}{\int p(θ')p(D|θ')dθ'}

Here p(θ) is called the prior, and represents our beliefs about the parameters before seeing the data; p(D|θ) is called the likelihood, and represents our beliefs about what data we expect to see for each setting of the parameters; p(θ|D) is called the posterior, and represents our beliefs about the parameters after seeing the data; and p(D) is called the marginal likelihood or evidence, and is a normalization constant that we will use later.

The task of computing this posterior is called Bayesian inference, posterior inference, or just inference. We will give many examples in the following sections of this chapter, and will discuss algorithmic issues in Part II. For more details on Bayesian statistics, see e.g., [Ber97a; Hof09; Lam18; Kru15; McE20] for introductory level material, [Gel+14a; MKL21; GHV20a] for intermediate level material, and [BS94; Ber85b; Rob07] for more advanced theory.