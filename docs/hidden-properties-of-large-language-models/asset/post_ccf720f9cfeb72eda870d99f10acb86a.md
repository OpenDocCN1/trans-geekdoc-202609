
Newswise — Sepsis is a serious medical condition caused by an overwhelming immune response to infection. The body’s infection-fighting chemicals, which are normally good, can cause damage to the blood vessels and organs.

Sepsis is one of the leading causes of death in hospitals. Although there have been recent advances in sepsis treatment, researchers are still working hard to identify new ways to prevent and treat this complex disease.

Researchers at Washington University School of Medicine in St. Louis recently published a study that may change how sepsis is diagnosed and treated. Their work suggests that two different types of immune cells are involved in the progression of sepsis: one cell type that’s protective and another that’s harmful. These findings could help doctors identify who is most at risk for severe complications from the disease.

“The results from our study show that there are two distinct populations of monocytes,” said co-author Dr. Michael Jaffe, professor of medicine at Washington University. “One population promotes inflammation and is associated with worse outcomes; the other helps resolve inflammation and promotes healing.”

Monocytes are a type of white blood cell that are part of the innate immune system. They play a key role in fighting off bacteria and viruses. When someone has sepsis, their monocytes become activated. That means they increase in number and start producing cytokines, which are small proteins that regulate the body’s immune response. Typically, when the body encounters an infection, these cytokines signal the immune system to fight back. But too many cytokines produced too quickly can result in a hyperinflammatory state, which can lead to organ failure and death.

In the past, doctors have used blood tests to diagnose sepsis. However, those tests only measure the overall levels of cytokines in a person’s blood. The new study suggests that it might be possible to determine whether someone has a particular type of monocyte that could make them more susceptible to sepsis. If so, doctors could potentially use this information to personalize treatments and improve patient outcomes.

“Our findings suggest that there may be opportunities to develop therapies that target specific monocyte subsets,” said co-author Dr. Daniel Levy, assistant professor of medicine at Washington University. “This could potentially reduce the risk of developing sepsis or even improve outcomes once someone already has sepsis.”

There’s still much to learn about how these monocyte subsets contribute to sepsis development and progression, but the results of this study provide promising insights into why some patients respond differently to treatment than others.

## Table 5.29: Example response of Mistral-v3-7b (base).

## Chapter 6

## Conclusion

In this dissertation, we conducted a thorough and systematic study of Large Language Models (LLMs), despite their inherently complex and opaque nature. Through this work, we uncovered several important hidden properties of LLMs and revealed the internal mechanisms behind these properties. These findings significantly advance our understanding of LLMs and offer valuable insights for the development of future models.

The weight space is a fundamental component of deep learning models, with modern LLMs often comprising billions of parameters. In Chapter 3, we demonstrate the intrinsic sparsity of the LLM weight space. We examine the counterintuitive phenomenon that the popular magnitude pruning method fails drastically on LLMs. We find that magnitude pruning overlooks emergent activation outliers common in LLMs. Motivated by this, we propose Wanda, a simple pruning approach that jointly considers weight magnitudes and input activations. We use Wanda to find efficient and sparse subnetworks from pretrained LLMs, without inducing any changes to the preserved weights.

Unlike static weight parameters, activations are dynamic, and LLMs use these internal representations to encode input data. In Chapter 4, we reveal the widespread presence of massive activations – structured outliers in the activation space of LLMs. We conduct a comprehensive analysis of these activations. Through intervention analysis, we show these activations function as crucial, input-agnostic biases. Furthermore, we find that they are closely connected to the attention concentration patterns, and we propose an alternative attention formulation that augments self-attention with learnable key and value embeddings. We show that pretraining with this modified attention mechanism eliminates massive activations.

Finally, LLMs are interesting because of their ability to generate natural language outputs. In Chapter 5 of the thesis, we examine the output behaviors of LLMs, where we are mainly motivated by understanding the differences between models beyond benchmark performance. We develop a conceptually simple framework to evaluate idiosyncrasies in LLM generations – a synthetic classification task with a goal of predicting the origin of a given output. Using this framework, we find that outputs from different LLMs are highly distinguishable: they can be distinguished with extremely high accuracies. We further identify concrete forms of these idiosyncrasies, including word-level distributions, formatting style and high-level semantics. Finally, we discuss how our findings have implications for the use of synthetic data, model similarity inference, and the design of more reliable evaluation protocols.

While this dissertation is centered on large language models (LLMs), the problems investigated and methodologies used span a diverse range of topics, including sparsity, pruning, quantization, deep learning architectures, and linguistics. By examining these topics through the lens of LLMs, the insights and approaches developed in this thesis provide a solid foundation for future research efforts aimed at understanding advanced deep learning models. This will be increasingly relevant as the field continues to evolve.

## 6.1 Future Directions

We conclude this thesis by discussing several potential future directions based on our findings.

## Sparsity and efficiency

Researchers have long studied sparsity in neural networks. However, sparse neural networks face a practical challenge where unstructured sparsity is not natively supported by modern GPU hardware. This leads to a significant gap between theoretical and practical efficiency. Therefore an important question is how to bridge this gap and unlock the potential of sparsity for accelerating LLMs. One promising direction is via a special type of sparsity, called structured sparsity. Structured sparsity [139] is a type of fine-grained weight sparsity that is supported by latest NVIDIA GPUs. However, as we have shown in Chapter 3, structured sparse LLMs are not as effective as unstructured sparse ones. Moreover, there still remains a large performance gap between structured sparse models and their dense counterparts. A natural question is whether we can leverage the insights from our work to design more effective pruning methods for structured sparsity.

Another promising direction is to explore the sparse property beyond weight parameters. Some of the questions we can ask are: are the activations of LLMs also sparse? If so, can we leverage the activation sparsity to make the training or inference of LLMs more efficient? Moreover, this analysis can be extended to the gradients during training. If gradients are sparse, we can significantly reduce the communication cost in distributed training, which is highly desirable as we continue to scale up LLMs.

## Low-precision training

In addition to sparsity, quantization is another important direction for improving the efficiency of deep learning models. Unlike sparsity, which is less explored in the context of LLMs, quantization has been widely studied and adopted, especially for model development. However, most of the existing methods rely on post-training quantization, where a pretrained full-precision model is quantized after training. Low-precision training has been less explored, due to the training instability that arises from low-precision weights and activations. Our findings in Chapter 4 reveal one such bottleneck: the existence of extreme activation outliers.

This raises a natural question: how can we better understand the training dynamics under low-precision regimes, and can we develop methods to improve their stability? At the moment, we are seeing 8-bit floating-point (8-bit FP) as the most common low-precision format for pretraining LLMs [6]. In the future, we may see even lower precision formats, such as 4-bit floating point or even binary representations. In these extreme quantization settings, what are the fundamental challenges, and how can we design effective mitigation strategies? We hope our work can provide some valuable insights on these directions.
