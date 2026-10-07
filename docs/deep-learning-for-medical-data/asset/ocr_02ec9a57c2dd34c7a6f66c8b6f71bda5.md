# 5.2 BACKGROUND

![](bbox=[0.176, 0.096, 0.823, 0.303])

**Figure 5.1: The Greedy InfoMax Learning Approach. (Left)** For the self-supervised learning of representations, we stack a number of modules through which the input is forward-propagated in the usual way, but gradients do not propagate. Instead, every module is trained greedily using a local loss. **(Right)** Every module maps inputs $z_t^{m-1}$ at time-step $t$ to $g_{enc}(GradientBlock(z_t^{m-1})) = z_t^m$, which is used as the input for the next module. The InfoNCE objective is used for its greedy optimization. This loss is contrasted with the predictions of a module for its future representations $z_{t+k}^m$, which enforces each module to maximally preserve the information of its inputs. We optionally employ an additional autoregressive module $g_{ar}$, which is not depicted here.

a patch of a few milliseconds of speech utterances shares information with neighboring patches such as the speaker identity, emotion, and phonemes, while it does not necessarily share these with random patches drawn from other utterances. Similarly, a small patch from a natural image shares many aspects with neighboring patches such as the depicted object or lighting conditions.

Recent work (Oord et al., 2018b; Hjelm et al., 2019) proposed how we can exploit this to learn representations that maximize the mutual information among shared neighbors. In this work, we specifically focus on Contrastive Predictive Coding (CPC) (Oord et al., 2018b). This self-supervised end-to-end learning approach extracts representations from sequential inputs by maximizing the mutual information between the extracted representations of temporally near patches.

In order to achieve this, CPC first processes the sequential input signal $x$ using a deep encoding model $g_{enc}(x_t) = z_t$, and additionally produces a representation $c_t$ that aggregates the information of all patches up to time-step $t$