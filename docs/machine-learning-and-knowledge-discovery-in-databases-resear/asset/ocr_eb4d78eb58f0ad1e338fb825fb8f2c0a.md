and TCP. While ProGrad [44] only optimizes the prompt whose gradient is aligned (or non-conflicting) to the frozen CLIP knowledge. KgCoOp [36] explicitly addresses the gap between the embedding of learnable prompts and that of frozen CLIP as shown in Fig. 2(a). As an alternative, TCP further leverages the frozen CLIP knowledge by injecting its text embeddings into the encoder illustrated as Fig. 2(b), enhancing the generalization performance. Note that, these three methods only retrieve the textual knowledge from frozen CLIP. Besides, methods like PromptKD [21] and HPT [34] apply extra knowledge from fine-tuned models and large language models are not covered in this study.

# 3 Methodology

In this paper, we propose a novel method, referred to as SCP, to achieve superior generalization by leveraging the frozen CLIP knowledge in both the initialization and optimization stage of the learnable prompt as its schematic architecture shown in Fig. 2(c). Before delving on SCP, to facilitate understanding, we first review the fundamental knowledge from the existing baseline framework.

# 3.1 Existing Baseline Framework

The existing baseline, such as CoOp, adopts CLIP for image recognition downstream tasks by prepending learnable tokens to the prompt context. Note that, the pre-trained encoders in CLIP, both image and text, convert the prompt context and the image sample into corresponding embeddings, which are then paired based on the contrastive loss to ensure optimal matching. In specific, the hand-crafted template with c class labels, e.g. “a photo of a {Class}”, Class : C ∈ {1, 2, ...c} , is embedded into vectorized textual tokens T = {ti}^c_{i=1}, and the b learnable tokens P = {pi}^b_{i=1} are initialized in text modality space. Then, the text encoder B(·) interprets the combination of learnable tokens and vectorized textual tokens into the text embedding W^p = B([P, T]) = {w^p_i}^c_{i=1}. To infer P, the cosine similarity score sim(·) needs to be maximized. Equivalently, the contrastive loss, between the image embedding x and the prompted text embedding w^p_y, is calculated as

L_ce = exp(sim(x, w^p_y / τ)) / Σ_{i=1}^c exp(sim(x, w^p_i / τ)).

(1)

Here, τ refers to the temperature parameter.

To further unlock the potential of CLIP, MaPLe extends learnable prompts to the image side and takes advantage of multiple transformer blocks in the learning process. Specifically, the prompted image embedding is generated as X^p = V([P̃, Z]). Here, P̃ = F(P) is the operation that converts learnable token to image modality space by a projection function F(·), Z refers to the vectorized visual tokens. Following Maple [15], the operation for processing prompted text and image embeddings through J transformer layers is

W^p_{j+1} = B_{j+1}([P_j, T_j])

(2)

and