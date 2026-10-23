Using the supervised task of classifying between training samples and generated samples (with the model energy function used in defining the classifier) to provide a gradient on the model was introduced earlier in various forms (Welling et al., 2003b; Bengio, 2009).

Noise contrastive estimation is based on the idea that a good generative model should be able to distinguish data from noise. A closely related idea is that a good generative model should be able to generate samples that no classifier can distinguish from data. This idea yields generative adversarial networks (section 20.10.4).

# 18.7 Estimating the Partition Function

While much of this chapter is dedicated to describing methods that avoid needing to compute the intractable partition function Z(θ) associated with an undirected graphical model, in this section we discuss several methods for directly estimating the partition function.

Estimating the partition function can be important because we require it if we wish to compute the normalized likelihood of data. This is often important in evaluating the model, monitoring training performance, and comparing models to each other.

For example, imagine we have two models: model M_A defining a probability distribution p_A(x;θ_A) = 1/Z_A p̂_A(x;θ_A) and model M_B defining a probability distribution p_B(x;θ_B) = 1/Z_B p̂_B(x;θ_B). A common way to compare the models is to evaluate and compare the likelihood that both models assign to an i.i.d. test dataset. Suppose the test set consists of m examples {x^(1),...,x^(m)}. If ∏_i p_A(x^(i);θ_A) > ∏_i p_B(x^(i);θ_B), or equivalently if

$$\sum_i \log p_A(x^{(i)};\theta_A) - \sum_i \log p_B(x^{(i)};\theta_B) > 0, \tag{18.38}$$

then we say that M_A is a better model than M_B (or, at least, it is a better model of the test set), in the sense that it has a better test log-likelihood. Unfortunately, testing whether this condition holds requires knowledge of the partition function. Indeed, equation 18.38 seems to require evaluating the log-probability that the model assigns to each point, which in turn requires evaluating the partition function. We can simplify the situation slightly by rearranging equation 18.38 into a form in