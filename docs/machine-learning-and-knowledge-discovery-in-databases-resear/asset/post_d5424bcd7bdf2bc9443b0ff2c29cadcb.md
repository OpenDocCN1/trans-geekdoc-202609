

- 37. Tan, C., Gao, Z., Xia, J., Hu, B., Li, S.Z.: Global-context aware generative protein design. In: ICASSP (2023)

- 38. Vaswani, A., et al.: Attention is all you need. In: NeurIPS (2017)

- 39. Wang, X., Zheng, Z., Ye, F., Xue, D., Huang, S., Gu, Q.: Diffusion language models are versatile protein learners. arXiv preprint arXiv:2402.18567 (2024)

- 40. Watson, J.L., et al.: De novo design of protein structure and function with rfdiffusion. Nature **620** (2023)

- 41. Wu, T., et al.: Ar-diffusion: Auto-regressive diffusion model for text generation. NeurIPS **36** (2023)

- 42. Yi, K., Zhou, B., Shen, Y., Lió, P., Wang, Y.: Graph denoising diffusion for inverse protein folding. In: NeurIPS (2023)

- 43. Yue, K., Dill, K.A.: Inverse protein folding problem: designing polymer sequences. In: Proceedings of the National Academy of Sciences (1992)

- 44. Zhang, L., Rao, A., Agrawala, M.: Adding conditional control to text-to-image diffusion models. In: ICCV (2023)

- 45. Zhang, Z., Xu, M., Lozano, A.C., Chenthamarakshan, V., Das, P., Tang, J.: Pre-training protein encoder via Siamese sequence-structure diffusion trajectory prediction. In: NeurIPS 2023 (2023)

- 46. Zheng, Z., Deng, Y., Xue, D., Zhou, Y., Ye, F., Gu, Q.: Structure-informed language models are protein designers. In: ICML (2023)

- 47. Zhong, Z., Mottin, D.: Efficiently predicting mutational effect on homologous proteins by evolution encoding. In: ECML PKDD (2024)

## Images and Computer Vision

## Self-generated Cross-Modal Prompt Tuning

Guiming Cao^1, Zhonghan Wu^2, Huan Huo^1, Yuming Ou^1, and Guandong Xu^1,3^(✉)

^1 University of Technology Sydney, Sydney, Australia  
Guiming.Cao@student.uts.edu.au, Guandong.Xu@uts.edu.au  
^2 East China Normal University, Shanghai, China  
^3 The Education University of Hong Kong, Hong Kong, China

**Abstract.** Training prompt tuning models on task-specific data is a common method for adapting vision-language model knowledge to image recognition downstream tasks. Despite recent advancements in prompt tuning, achieving superior generalization to heterogeneous images, across a wide range of visual characteristics in style, format, and source, remains a significant challenge. To this end, we propose a novel method, namely Self-generated Cross-modal Prompt tuning (SCP), which generates pseudo prompts by applying the frozen knowledge in both the initialization and optimization stages to guide training. Consequently, the model can be trained on available datasets while effectively generalizing to heterogeneous image data in a wide spectrum of textual classes and visual characteristics. Extensive experiments on four benchmarks indicate that our proposed SCP significantly outperforms well-known baselines in generalization performance across a broad spectrum of downstream tasks. Notably, our proposed SCP exhibits significant improvements in both Cross-Dataset and Domain-Shift Generalization, with performance gains of at least 3.63% and 11.71%, respectively. Our code is available at https://github.com/Ghosttimber/Academic.

**Keywords:** Computer Vision · Multi-Modal · Prompt Tuning

### 1 Introduction

Recently developed vision-language models (VLMs) interpret and connect data across a variety of modalities, representing a significant leap forward from the traditional paradigm in multi-modal downstream tasks. Such a model, exemplified by CLIP [28], aligns image and text in a shared space, achieving superior generalization performance without task-specific training. Building upon CLIP, Context Optimization (CoOp) [43] prepends learnable tokens into the prompt of

![](img/f56761e6196132d5b74909d98468408f_431_0.png)

Fig. 1. Challenges addressed by our proposed SCP and its performance compared to the well-known baselines.

VLMs (learnable prompt), demonstrating improved generalization performance. This paradigm, termed prompt tuning, tailors VLMs to task-specific datasets, broadening the applicability of VLMs to a wide range of downstream tasks.

Expanding upon the foundation laid by CoOp, several subsequent approaches (KgCoOp [36], PromptSRC [16] and TCP [37]) have focused on unlocking the potential of prompt tuning in downstream tasks, retrieving the frozen knowledge lost in training by establishing alignment between the prompted embedding (i.e. the embedding carrying the learnable token) and the frozen CLIP embedding. This mechanism facilitates the knowledge transfer from the training distribution to out-of-distribution, thereby mitigating overfitting to the unseen textual classes from the training data. As a result, further improved generalizability is attainable. Despite the advancement in prompt tuning, a remaining critical challenge stems from achieving superior generalization to heterogeneous images, which encompasses diverse visual characteristics such as style, format, and source, reflecting real-world scenarios as illustrated in Fig. 1(a). In other words, the challenge lies in finding a learnable prompt against heterogeneous images.

Motivated by the challenges, we have found that transforming a textual prompt into its counterpart in the image space results in pseudo prompts independent of visual characteristics. Consequently, incorporating such pseudo prompts as guidance in training enhances the ability to achieve superior generalization across a broader range of downstream tasks as illustrated in Fig. 1(b). Accordingly, based on the aforementioned observation, we propose a novel prompt tuning model agnostic to both textual classes and visual characteristics, and it is referred to as Self-generated Cross-modal Prompt Tuning (SCP).

In essence, SCP systematically leverages frozen CLIP knowledge in both the initialization and optimization phases. In the initialization, the optimal matching embeddings between the textual and visual prompt are selected by the frozen CLIP model and incorporated into learnable prompts representation. The main purpose is to mitigate the negative effects of biases arising from the specificity of textual class and visual characteristics. Consequently, robust learnable prompts can be attained to enhance generalization capability. We refer to this initialization strategy as Cascade Propagation Prompt Initialization (CPPI). As for the optimization, the learnable prompt is aligned with the pseudo prompt embedding (i.e. proxy representation) derived from frozen CLIP knowledge in a cross-modal manner. Note that the proxy representation holds a different role regarding the modality of the learnable prompt in the alignment. The proxy representation aligned with the visual learnable prompt is generated from the textual prompt of frozen CLIP, serving as pseudo prompts in the image space. We found that it remains independent of visual characteristics. Clearly this enables visual learnable prompts to acquire a robust representation. Similarly, the proxy representation aligned with the textual learnable prompt comes from the visual prompt of frozen CLIP. It offers sufficient samples for the training in alignment while existing baselines rely on limited samples or hand-crafted samples. This optimization strategy is referred to as Self-generated Proxy Alignment (SPA).

In addition, building upon the cross-modal nature of SPA and following [27], we adopt the Euclidean loss in the alignment to reduce the modality gap between textual and visual representations to a desirable level. To mitigate the information loss [15] in the modality conversion of learnable prompts, we propose an Entropy-Regulation (ER) module, which, combined with the adoption of Euclidean loss, further improves the generalization performance.

In summary, this paper makes four major contributions:

- We propose a novel prompt tuning method (Self-generated Cross-modal Prompt tuning), that trains on limited readily available images, adapting prompt tuning to a much broader array of downstream applications.
- In our method, we take advantage of textual and visual knowledge from frozen CLIP into both the initialization and optimization process in a cross-modal manner, conductive to superior generalization capability.
- We introduce the Euclidean loss and the ER to improve the generalization capability, mitigating the challenge discussed by the existing research.
- Extensive experiments on four benchmarks clearly demonstrate that our proposed SCP significantly outperforms the well-known baselines in generalization capability across a wide range of downstream tasks.

### 2 Related Work

**Vision Language Models.** Recently, several methods, including BAN [17], Intra-Inter [10], and MCAN [38], adopt the VLMs with the attention-based framework, showing that the utilization of VLMs significantly improves the performance across a wide spectrum of downstream tasks. Subsequently, the methods (ViLBERT [22], LXMERT [32] and UNITER [2]) explore the potential of VLMs models based on BERT-like architectures, attaining further improvement. Methods proposed thereafter, namely CLIP [28] and ALIGN [14], are trained to align a considerable amount of web-scale image-text pair data in a multi-modal

