# Towards Deeper GCNs: Alleviating Over-Smoothing via Iterative Training and Fine-Tuning

Furong Peng$^1$, Jinzhen Gao$^2$, Xuan Lu$^{2(\textcircled{S})}$, Kang Liu$^2$, Yifan Huo$^2$, and Sheng Wang$^3$

$^1$ Institute of Big Data Science and Industry, Shanxi University/Key Laboratory of Evolutionary Science Intelligence of Shanxi Province, Taiyuan, China
pengfr@sxu.edu.cn
$^2$ Shanxi University, Taiyuan, China
{202322404011,202222407023,202422409007}@email.sxu.edu.cn,
xuanlu@sxu.edu.cn
$^3$ Zhengzhou University of Aeronautics, Zhengzhou, China
wangsheng1910@zua.edu.cn

**Abstract.** Graph Convolutional Networks (GCNs) suffer from severe performance degradation in deep architectures due to over-smoothing. While existing studies primarily attribute the over-smoothing to repeated applications of graph Laplacian operators, our empirical analysis reveals a critical yet overlooked factor: trainable linear transformations in GCNs significantly exacerbate feature collapse, even at moderate depths (e.g., 8 layers). In contrast, Simplified Graph Convolution (SGC), which removes these transformations, maintains stable feature diversity up to 32 layers, highlighting linear transformations’ dual role in facilitating expressive power and inducing over-smoothing. However, completely removing linear transformations weakens the model’s expressive capacity.

To address this trade-off, we propose **Layer-wise Gradual Training (LGT)**, a novel training strategy that progressively builds deep GCNs while preserving their expressiveness. LGT integrates three complementary components: (1) _layer-wise training_ to stabilize optimization from shallow to deep layers, (2) _low-rank adaptation_ to fine-tune shallow layers and accelerate training, and (3) _identity initialization_ to ensure smooth integration of new layers and accelerate convergence. Extensive experiments on benchmark datasets demonstrate that LGT achieves state-of-the-art performance on vanilla GCN, significantly improving accuracy even in 32-layer settings. Moreover, as a training method, LGT can be seamlessly combined with existing methods such as PairNorm and ContraNorm, further enhancing their performance in deeper networks. LGT offers a general, architecture-agnostic training framework for scalable deep GCNs. The code is available at https://github.com/jfklasdfj/LGT_GCN.

**Keywords:** GCNs • Over-smoothing • Fine-tune • LoRA