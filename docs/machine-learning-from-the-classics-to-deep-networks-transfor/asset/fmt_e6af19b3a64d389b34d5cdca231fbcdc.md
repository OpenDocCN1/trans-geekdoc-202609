
which is used for sampling and **ϵ** ∼ 𝒩(0, *I*). Note that if *β*[*t*] is selected so that ${\\overline{a}}\_{T} \\approx 0$, then the latent random vector at time *T*, **x**[*T*], follows the standard Gaussian, i.e., **x**[*T*] ∼ 𝒩(0, *I*).

*Reverse process*: This is defined as a Markov chain with *learned* Gaussians (transitions), starting from *p*[**θ**](**x**[*T*]) := *p*(**x**[*T*]) = 𝒩(**x**[*T*]|0, *I*), according to the following rule,

![](images/B9780443292385000251/fx014.jpg)

where **μ**[**θ**](**x**[*t*], *t*) and *Σ*[**θ**](**x**[*t*], *t*) are learned during training. As we will soon see, the parameters, ***θ***, which are estimated during training, define a neural network that is used for learning the mean values as well as the covariance matrices. Note the explicit dependence on the time step, *t*.

Recall that our final goal is to be able to *sample* from *p*[**θ**](**x**[0]), given by Eq. [(19.55)](#Chp019_997-1102_B9780443292385000251.xhtml#deq133). The rationale behind diffusion methods is that for small values of *β*[*t*], *t* = 1, 2, …, the reversal of a diffusion process is of an *identical* functional form as the forward one, [169], [52]. Thus, since the conditionals in the forward process are Gaussians, the conditionals in the reverse process should also be Gaussians. Hence, the goal of training is to optimize with respect to the involved parameters, ***θ***, so that *p*[**θ**](**x**[0], **x**[1], …, **x**[*T*]) to be as close as possible to *q*(**x**[0], **x**[1], …, **x**[*T*]). We will come to this soon.

[Figs. 19.22A and 19.22B](#Chp019_997-1102_B9780443292385000251.xhtml#f0125) illustrate the forward and the reverse processes, respectively. Looking at it from a slightly different view point, the forward process could be considered as an *encoder* and the reverse one as the *decoder*. However, a notable characteristic of the diffusion models is that the coding, through the sequence of the generated latent variables, is not the result of a learning process, but, instead, the forward process follows a *fixed* Markov chain deployment that gradually adds noise to the data. In contrast, for example, in the variational autoencoders (Section [19.2.6](#Chp019_997-1102_B9780443292385000251.xhtml#s0065)), the latent variables in the encoder are learned from the data.
