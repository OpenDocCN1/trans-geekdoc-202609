quickly adapt the existing adversarial robustness tools for evaluation and profiling.

For instance, transformers are originally applied in natural language processing (NLP) tasks as a type of deep neural network (DNN) mainly based on the self-attention mechanism (Vaswani et al., 2017; Devlin et al., 2018; Brown et al., 2020b), and transformers with large-scale pretraining have achieved state-of-the-art results on many NLP tasks (Devlin et al., 2018; Liu et al., 2019e; Yang et al., 2019b; Sun et al., 2019b). Recently, Dosovitskiy et al. (2020) applied a pure transformer directly to sequences of image patches (i.e., a vision transformer, ViT) and showed that the Transformer itself can be competitive with convolutional neural networks (CNNs) on image classification tasks. Since then, transformers have been extended to various vision tasks and show competitive or even better performance compared to CNNs and recurrent neural networks (RNNs) (Carion et al., 2020; Chen et al., 2020b; Zhu et al., 2020b).

Using existing tools for adversarial robustness evaluation, Shao et al. (2021a) examine the adversarial robustness of ViTs on image classification tasks and make comparisons with CNN baselines. As highlighted in Fig. 1.2, their experimental results illustrate the superior robustness of ViTs than CNNs in both white-box and black-box attack settings, based on which they make the following important findings:

+   • Features learned by ViTs contain less low-level information and benefit adversarial robustness. ViTs achieve a lower attack success rate (ASR) of 51.9% compared with a minimum of 83.3% by CNNs in Fig. 1.2. They are also less sensitive to high-frequency adversarial perturbations.

+   • Using denoized randomized smoothing (Salman et al., 2020b), ViTs attain significantly better certified robustness than CNNs.

+   • It takes the cost of adversarial robustness to improve the classification accuracy of ViTs by introducing blocks to help learn low-level features as shown in Fig. 1.2.

+   • Increasing the proportion of transformer blocks in the model leads to better robustness when the model consists of both transformer and CNN blocks. For example, the attack success rate (ASR) decreases from 87.1% to 79.2% when 10 additional transformer blocks are added to T2T-ViT-14. However, increasing the size of a pure transformer model cannot guarantee a similar effect, e.g., the robustness of ViT-S/16 is better than that of ViT-B/16 in Fig. 1.2.

+   • Pretraining without adversarial training on larger datasets does not improve adversarial robustness though it is critical for training ViT.