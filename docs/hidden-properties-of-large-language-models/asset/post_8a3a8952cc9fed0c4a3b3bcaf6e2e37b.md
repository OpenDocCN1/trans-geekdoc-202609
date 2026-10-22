
## Post-Training

Post-training is the process of refining and optimizing the pretrained LLMs. While pretraining LLMs learn general language representations, pretrained LLMs are not able to follow human instructions and produce coherent texts. Therefore, in order for these models to be useful in practice, post-training is a critical process that aligns these pretrained models with human preferences.

There are two popular post-training paradigms: supervised fine-tuning and the alignment stage. Supervised fine-tuning (SFT) is the process of adapting pretrained LLMs to specific tasks or domains by training them on curated datasets of interest. For instance, one can fine-tune a pretrained LLM on dialogue data for it to become a helpful assistant. SFT is typically done via supervised learning, meaning that the training data consists of input-output pairs. However, in many cases, labeled data is resource intensive to collect. What’s more, supervised fine-tuning is not able to generalize well outside the training domain. In practice, SFT is often used in conjunction with alignment approaches.

The alignment stage aims to adapt LLMs to better match human preferences. Typically, this is done via reinforcement learning (RL) fine-tuning to learn from feedback data, such as reinforcement learning from human feedback (RLHF) [26] and reinforcement learning from AI feedback (RLAIF) [29]. The model is optimized via reward signals that reflect the quality of their own generations. This reinforcement learning process encourages the model to produce outputs that are more helpful and aligned with human values.

## 2.4 Inference

We describe the inference procedure of LLMs. It typically consists of two main steps: pre-filling and decoding.

### Pre-filling

This is the stage where the model processes the entire input prompt before autoregressive decoding. In the pre-fill stage, the model receives the full prompt and passes all the input tokens through the network in a single forward pass. No prediction is performed in this stage. During pre-filling, the key and value states of the input tokens at each Transformer layer are cached for the decoding stage. These key and value states are also known as KV cache, which allows the model to reuse key and value states of existing processed tokens in the sequence without recomputation.

### Decoding

Decoding is the process of generating the output sequence token by token in an autoregressive fashion. At each token prediction, the model predicts the next token by sampling from the predicted probability distribution over the entire vocabulary. There can be various sampling strategies. One common strategy is greedy decoding, a deterministic process where the token with the highest probability is always selected as the next token. Another popular method is temperature sampling, which uses a temperature parameter to control the randomness of the probability distribution: a higher temperature means more random outputs, while a lower temperature makes the output more deterministic.

## Chapter 3

## A Simple and Effective Pruning Approach for Large Language Models

### 3.1 Overview

As their size increases, Large Language Models (LLMs) are natural candidates for network pruning methods: approaches that drop a subset of network weights while striving to preserve performance. Existing methods, however, require either retraining, which is rarely affordable for billion-scale LLMs, or solving a weight reconstruction problem reliant on second-order information, which may also be computationally expensive. In this paper, we introduce a novel, straightforward yet effective pruning method, termed Wanda (Pruning by Weights and activations), designed to induce sparsity in pretrained LLMs. Motivated by the recent observation of emergent large magnitude features in LLMs, our approach prunes weights with the smallest magnitudes multiplied by the corresponding input activations, on a per-output basis. Notably, Wanda requires no retraining or weight update, and the pruned LLM can be used as is. We conduct a thorough evaluation of our method Wanda on LLaMA and LLaMA-2 across various language benchmarks. Wanda significantly outperforms the established baseline of magnitude pruning and performs competitively against recent methods involving intensive weight update. Code is available at https://github.com/locuslab/wanda.

### 3.2 Introduction

Large language models [3, 4] have recently reshaped the field of NLP with their remarkable performance across a range of complex language benchmarks [86, 105, 107]. However, these models, with their billions of parameters, usually require significant computational resources. To democratize LLMs, considerable efforts have been taken to mitigate their high computational cost. Many of the notable advancements to date have centered on model quantization, a process where parameters are quantized into lower bit-level representations. The fast pace of LLM quantization research [57, 58, 87, 154] has led to substantial resource savings for these models [111, 150].

Network pruning [66, 77, 78], on the other hand, shrinks network sizes by removing specific weights from the model – essentially setting them to zero. Along with quantization, it is often considered another popular approach for compressing neural networks. However, it has received relatively little focus in compressing LLMs. This seems to contradict the trend of model compression in the pre-LLM era, where both approaches have received large amounts of research effort. A quick review of existing pruning methods reveals a possible reason: they typically require retraining [74, 95], training from random initializations [67, 70, 79] or even an extensive iterative process [69, 80]. The sheer amount of computational resources required by LLMs limits these methods. A recent LLM pruning approach, SparseGPT [59], does not require traditional retraining, but still demands a computationally intensive weight update process.

![](img/78fbbd4ea983a7880ad6673ac3886adf_31_0.png)

Figure 3.1: Illustration of our proposed method Wanda (Pruning by Weights and activations), compared with the magnitude pruning approach. Given a weight matrix W and input feature activations X, we compute the weight importance as the elementwise product between the weight magnitude and the norm of input activations (|W| · ||X||₂). Weight importance scores are compared on a per-output basis (within each row in W), rather than globally across the entire matrix.

The argument concerning the need for retraining and weight update does not fully capture the challenges of pruning LLMs. One might reasonably expect to obtain a fairly high-performing initialization point for retraining using existing popular pruning methods. However, a recent study [59] finds that magnitude pruning [66], a well-established pruning approach, fails dramatically on LLMs even with relatively low levels of sparsity. Considering the past success of magnitude pruning on smaller networks, this result suggests that LLMs, despite having 100 to 1000 times more parameters, are substantially more difficult to prune directly.

In this work, we address this challenge by introducing a straightforward and effective approach, termed Wanda (Pruning by Weights and activations). This technique successfully prunes LLMs to high degrees of sparsity without any need for modifying the remaining weights. We are motivated by an observation from a recent study [58], where a small subset of hidden state features are exceptionally large in magnitude, a property unique to LLMs. We find that augmenting the standard weight magnitude pruning metric with the input activations, is surprisingly effective as a measure for evaluating the weight importance. Specifically, we introduce a novel pruning metric, where each weight is evaluated by the product of its magnitude and the norm of the corresponding input activations, estimated using a small set of calibration data. Our method uses this metric to induce sparsity in pretrained LLMs by comparing weights locally within each output of linear layers and removing lower priority weights. Our approach is computationally efficient, able to be executed in a single forward pass, and requires minimal memory overhead.

We empirically evaluate Wanda on the widely adopted LLaMA [22] and LLaMA-2 [23]
