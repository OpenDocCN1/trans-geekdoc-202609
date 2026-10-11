
A modified `ResNet6` model from section [2.2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2s2-2) will be used as a student model in project [11.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn1). Replacing `ResNet9` by the modified `ResNet6` in project [2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2ueqn22), you will find the prediction accuracies for the train, validation and test datasets are 95.9%, 88.4% and 88.4% respectively. The output `z` of the modified `ResNet6` applied to a batch of one image also produces probabilities `q` at a temperature `T`. Normally, the value of the temperature is set to be equal to 1. We will use a higher `T` value to produce a softer probability distribution over classes

$$
q_{i} = \frac{e^{z_{i}/T}}{\sum\limits_{j = 1}^{C}e^{z_{j}/T}}
$$

(11.2)

The student model is then trained with a loss function which has a hard loss and a soft loss. The hard loss is a cross-entropy about predicted probabilities of the student model at `T`=1 and labels of the train dataloader. The soft loss is a cross-entropy about `p` and `q` at a high temperature: $L_{soft} = - \sum\limits_{j = 1}^{C}p_{j}{\log}{(q_{j})}$. Using some approximations (Hinton *et al* [2015](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11bib2)), the soft cross-entropy gradient $\partial L[soft]/\partial z[i]$ with respect to each logit `z[i]` of the student model can be simplified to:

$$
\frac{\partial L_{soft}}{\partial z_{i}} = \frac{1}{T}(q_{i} - p_{i}) \approx \frac{1}{NT^{2}}\left( {z_{i} - v_{i}} \right)
$$

(11.3)

At a high temperature, distillation is equivalent to minimizing $0.5(z_{i} - v_{i})^2$. Since the magnitudes of the gradients produced by the soft targets are proportional to $1/T^2$, it is important to multiply them by $T^2$ when using both hard and soft targets to train the student model. According to equation ([1.7](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn7)), we have $L[soft] = D[KL](p \mid q) + H(p)$. Because the Shannon entropy $H(p)$ is a constant to `z`, we will use $L[soft] = T^2 D[KL](p \mid q)$ to train the student model. There is a PyTorch class `nn.KLDivLoss` for $D[KL](p \mid q)$ calculations. How do we choose the value of `T`? One approximation to obtain equation ([11.3](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11eqn3)) is $e^{(z[i]/T)} \approx 1 + z[i]/T$ in a condition $|z[i]| \ll T$. We can find the absolute element value of `y_hat` from `ResNet9` or `ResNet6` is about 100, so we set `T`=10 000. With the above information, we can write the codes for project [11.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn1). After running the codes to transfer knowledge from the pre-trained `ResNet9` to `ResNet6`, we get that the prediction accuracies for the train, validation and test datasets are 94.3%, 90.1% and 90.2% respectively. The knowledge distillation increases the `ResNet6` model's prediction accuracies by about 2% for the validation and test datasets. However, using `T` = 100 to train the student model, I found the results were almost the same as those shown in figure [11.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig1) for `T` = 10 000.

![](images/bk978-0-7503-6244-3ch11uf1a_pr.gif)
![](images/bk978-0-7503-6244-3ch11uf1b_pr.gif)
![](images/bk978-0-7503-6244-3ch11uf2a_pr.gif)
![](images/bk978-0-7503-6244-3ch11uf2b_pr.gif)
![](images/bk978-0-7503-6244-3ch11uf3_pr.gif)

![Figure 11.1. Model training results of knowledge distillation from ResNet9 to ResNet6.](images/bk978-0-7503-6244-3ch11f1_online.jpg)

**Figure 11.1.** Model training results of knowledge distillation from ResNet9 to ResNet6.

### 11.2 DINO: emerging properties in self-supervised vision transformers

Although the image classification results of using `ViT` model for CIFAR10 in section [10.2](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10s10-2) are good enough compared with the results from `CNN` models in section [2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2s2-3), there is no benefit, because `ViT` model training is computationally expensive. To use the `ViT` model for data processing, we have to resize each CIFAR10 image from 32 × 32 to 224 × 224. It is almost impossible for a personal laptop to handle computational tasks of `ViT` model training. We had to use the pre-trained Hugging Face `ViT` Model for Project [10.2](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn5).

The multi-head self-attention class in Cell 05 of project [10.1.1](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn1) returns a tuple with two elements. One is 'attention output' and the other is 'attention probs'. For image classification, we only use the first one. Using the second one, Mathilde Caron (Caron *et al* [2021](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11bib1)) and collaborators in Facebook found a unique property of vision transformers: self-supervised learning. To train a `YOLOv8` model for objection detection and image segmentation in chapter [8](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8), we have to use labeled datasets. The traditional supervised learning approach requires a large amount of labeled data, which can be expensive and time-consuming to obtain. In contrast, self-supervised learning aims to learn representations by solving pre-text tasks on unlabeled data. This approach has gained attention in recent years due to its ability to leverage the vast amount of freely available unlabeled data.

DINO, which stands for 'self DIstillation with NO labels,' is a method that focuses on self-supervised learning for vision transformers. DINO models can discover and segment objects on an image or video frame without supervision and without being given any segmentation-targeted objects. This means that this kind of model is capable of a higher-level of image understanding. DINO technology is based on knowledge distillation between a teacher model and student model. Both models use the same `ViT` model, but with different parameters and each of them is trained in a different way. Any image input to a DINO system is cropped into two global patches and eight local patches. The global and local crop scales are above 40% and below 40% respectively. Global patches are resized to 224 × 224, and the local patches are resized to 96 × 96. All patches are processed by the student model, but only the two global patches are input to the teacher model. Figure [11.2](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig2)(A) shows an original image in which there is a rabbit scratching its chin. Two global patches and eight local patches are also shown in the figure. These patches were obtained by the codes in project [11.2.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn4). A class defined in Cell 02 came from Facebook's DINO GitHub repository. In a normalization transform of the class, Facebook's special numbers are not used for simplification.

![](images/bk978-0-7503-6244-3ch11uf4_pr.gif)

![Figure 11.2. An original image (A) is cropped and resized into two global patches (B) and eight local patches (C) for DINO model training.](images/bk978-0-7503-6244-3ch11f2_online.jpg)
