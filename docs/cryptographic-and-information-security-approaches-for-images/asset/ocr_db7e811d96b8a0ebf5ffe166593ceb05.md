The algebraic degree of an S-box (and similarly a Boolean function) is desired to be as high as possible in order to resist a cryptanalytic attack known as low order approximation [13]. The measure of S-box degree is defined below:

**Definition 4.60:** *Let S = (s₁, s₂, ..., sₘ) be an n × m S-box where sᵢ (i = 1, ..., m) are n-variable Boolean functions. Let hⱼ be the set of linear combinations of sᵢ (i = 1, ..., m) (which includes the functions hᵢ). Then the algebraic degree of S, denoted by deg(Sₙ,ₘ), is defined as*

deg(Sₙ,ₘ) = minₕ {deg(hⱼ)} (j = 1, ..., 2ᵐ − 1). (4.36)

A companion concept to confusion, called diffusion, was also proposed by Shannon [12]. Therein it is described as the method by which the data redundancy in a cipher is spread throughout the entire (or large portion of the) data in an effort to reduce the probability of discovering part or all of its statistical structure. Diffusion has long been lined to the avalanche characteristics of a cipher system and, in particular, is achieved by using cipher components which exhibit good avalanche characteristics. In order to measure these characteristics for n × m S-boxes we require the following definitions:

**Definition 4.61:** *Let S = (s₁, s₂, ..., sₘ) be an n × m S-box where sᵢ (i = 1, ..., m) are n-variable Boolean functions. Let hⱼ be the set of linear combinations of sᵢ (i = 1, ..., m) (which includes the functions sᵢ), each with autocorrelation function, r̂ₕⱼ(a). Then the maximum absolute autocorrelation value of S is defined as:*

|ACₛₙ,ₘ|ₘₐₓ = maxₕ |r̂ₕⱼ(a)|, (4.37)

with a ∈ {1, ..., 2ⁿ − 1} and (j = 1, ..., 2ᵐ − 1).

**Definition 4.62:** *Let S = (s₁, s₂, ..., sₘ) be an n × m S-box where sᵢ (i = 1, ..., m) and n-variable Boolean functions. Let hᵢ be the set of linear combinations of sᵢ (i = 1, ..., m) (which includes the function sᵢ). Then S is said to satisfy strict avalanche criterion (SAC) if every hⱼ (j = 1, ..., 2ᵐ − 1) satisfies SAC.*

**Definition 4.63:** *Let S = (s₁, s₂, ..., sₘ) be an n × m S-box where sᵢ (i = 1, ..., m) are n-variable Boolean functions. Let hⱼ be the set of linear combinations of sᵢ (i = 1, ..., m) (which includes the functions sᵢ). Then S is said to satisfy propagation criteria of order k, PC(k), if every hⱼ (j = 1, ..., 2ᵐ − 1) satisfies PC(k).*