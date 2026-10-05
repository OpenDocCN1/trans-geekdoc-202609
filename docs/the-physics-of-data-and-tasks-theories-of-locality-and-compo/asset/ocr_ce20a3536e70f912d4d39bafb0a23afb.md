# INTRODUCTION

Diffusion models can be extended to text and other discrete modalities.

DISCRETE DIFFUSION. To handle data — such as text or molecular graphs — diffusion models can be generalized to discrete spaces via Markov jump processes by time-varying transition matrices [Hoo21; Aus+21]. These processes corrupt data by randomly flipping coordinates to uniformly random ones (uniform diffusion) or by masking (absorbing diffusion). The reverse processes require estimating the conditional expectation E[x0|xt], to-construct the original signal [Aus+21], similarly to the continuous case. At the time of writing this thesis, diffusion large language models are beginning to achieve competitive performance, particularly on generation tasks, and the first commercial implementations are being released.

# 1.3.3 Questions

As discussed above, sampling via time-reversal of a diffusion process amounts toing the score function Vlog(x). Hence, in the worst case, the sample complexity of this task would explode exponentially with the data dimension. Nevertheless, different diffusion models learn to synthesize high-resolution images and long passages from finite datasets. Existing generation guarantees hinge on smoothness assumptions that rarely hold in practice [OAS23]. A central open question is: What latent structure in Pdata enables efficient learning?

A compelling hypothesis is that diffusion models exploit the hierarchical and compositional structure of data: these models might learn a ‘library’ of reusable parts and the rules for composing them — allowing for the generation of novel samples. This raises important questions: Do diffusion models synthesize novel data based on compositional principles? If so, how many samples are needed to learn such rules? What role do architectural choices, such as the U-Net, play?

Furthermore, to what extent do diffusion models generalize their training data versus simply memorizing, functioning as ‘stochastic parrots’? In theory, perfect minimization of the objective would lead models to reconstruct the empirical distribution exactly, i.e., to memorize the training data. Recent work has demonstrated that large, overparameterized models can and often do memorize [Som+22; Car+23; Yoo+22; Kai+23a]. How, then, diffusion models avoid memorization in practice? Is this due to architectural or optimization-related inductive biases, or merely a consequence of under-parameterization? Can overparameterized diffusion models still generalize?

We will cover these processes in more detail in Part III.