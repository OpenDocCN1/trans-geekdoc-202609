
On July 6 of 2023, Wenyu Lv and his colleagues in Baidu of China published a paper (Lv *et al* 2023) about the development of a vision transformers-based real-time object detector, `RT-DETR`, which does not need post-processing, such as non-maximum suppression (`NMS`). The detector's efficient hybrid encoder reduces computational costs for real-time object detection. They claimed that the detector 'outperforms the state-of-the-art YOLO detectors of the same scale in both speed and accuracy.' From the ultralytics website, we can download two pre-trained weight files for a large `RT-DETR` model and an extra-large `RT-DETR` model. Their file sizes are around 100 MB. Using codes in the following Project 10.5, we can apply a pre-trained `RT-DETR` model for objection detection about a single image file, multiple images in a folder, and video frames from a camera or a video file. If you delete the code on line 05, the label for each object displayed on an image will be an integer about an index of a COCO class. Re-using Cell 02-03 in Project 8.4.1 for this project, you need to change the model's name from 'model' to 'baidu' in those two cells. The extra-large model is better than the large model with a sacrifice of speed. The video frame processing speed is about 15 and 10 FPS for the large and the extra-large model, respectively. You would get four labels for three persons and three labels for three horses in the image shown in figure [10.4](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10fig4) if the large model is used.

![](images/bk978-0-7503-6244-3ch10uf12_pr.gif)

![Figure 10.4. Object detection results for a single image by a pre-trained extra-large RT-DETR model from BAIDU of China. Video frame processing speed of the model is about 10 FPS.](images/bk978-0-7503-6244-3ch10f4_online.jpg)

**Figure 10.4.** Object detection results for a single image by a pre-trained extra-large `RT-DETR` model from BAIDU of China. Video frame processing speed of the model is about 10 FPS.

### References

Dosovitskiy A, Beyer L, Kolesnikov A, Weissenborn D, Zhai X, Unterthiner T, Dehghani M, Minderer M, Heigold G and Gelly S 2020 An image is worth 16x16 words: transformers for image recognition at scale *arXiv preprint* arXiv:[2010.11929](http://arxiv.org/abs/2010.11929)

Lv W, Xu S, Zhao Y, Wang G, Wei J, Cui C, Du Y, Dang Q and Liu Y 2023 Detrs beat yolos on real-time object detection *arXiv reprint* arXiv:[2304.08069](http://arxiv.org/abs/2304.08069)

Minderer M, Gritsenko A, Stone A, Neumann M, Weissenborn D, Dosovitskiy A, Mahendran A, Arnab A, Dehghani M and Shen Z 2022 Simple open-vocabulary object detection with vision transformers *arXiv preprint* arXiv:[2205.06230](http://arxiv.org/abs/2205.06230)

Radford A, Kim J W, Hallacy C, Ramesh A, Goh G, Agarwal S, Sastry G, Askell A, Mishkin P and Clark J 2021 Learning transferable visual models from natural language supervision *Int. Conf. on Machine Learning* (PMLR) pp 8748–63

Vaswani A, Shazeer N, Parmar N, Uszkoreit J, Jones L, Gomez A N, Kaiser Ł and Polosukhin I 2017 Attention is all you need *Adv. Neural Inform. Proces. Syst.* **30** 6000–10

***

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

***

# Chapter 11

## Knowledge distillation and its applications in DINO and SAM

In the year 2023, Facebook released many computer vision models based on vision transformers. Although they are very powerful, their sizes are too big for real-time usage on resource/power limited devices. Knowledge distillation is used to transfer intelligence from a pre-trained jumbo model to a small model. In section [11.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11s11-1) there is a demonstration of knowledge distillation from `ResNet9` to `ResNet6` used in chapter [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2). Examples in sections [11.2](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11s11-2)–[4](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11s11-4) show the intelligence of Facebook's `DINO`, `DINOv2` and `SAM` models in self-supervised learning to find object characteristics in images or video frames. Since `SAM` needs 8 GB GPU memory, I have to run it in CPU and it is very slow. A `fastSAM` model from China enables us to segment anything with a speed 50× faster than `SAM`.

### 11.1 Knowledge distillation for neural network compression

According to Moore's Law, the number of transistors in IC (integrated circuit) chips doubles approximately every two years. This has enabled the development of faster processors, increased memory capacity, and improved performance in various computing devices. The number of parameters of neural networks in computer vision projects and machine learning projects has also increased significantly for more powerful and functional models. In the model of a linear regression (project [1.3.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1ueqn15)), there are only two parameters; in the model of project [10.1.1](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn1) about a basic vision transformer model for image classification, there are 14,443,018 parameters. The model of ChatGPT (based o GPT 3.5) has 175 billion parameters. However, as the parameter number of a model increases from millions to billions, model training and deployment will be computationally more expensive. With the rise of smart mobile devices such as smart phones, smart watches, and various other devices, we need a small neural model (student) to have the functions of a jumbo model (teacher). Knowledge distillation (Hinton *et al* [2015](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11bib2)) refers to a technique in machine learning where a teacher model transfers its knowledge to a student model by using 'soft targets' during the training process for the student model. The goal of knowledge distillation is to compress the knowledge contained in a large model into a smaller model that can be deployed on resource-limited devices. Knowledge distillation has been successfully applied in many domains, including computer vision, natural language processing and speech recognition. It is a popular technique for model compression and transfer learning, allowing for the transfer of knowledge from large models to smaller models which can be used in real-world applications.

Soft targets are outputs of a teacher model. A pre-trained `ResNet9` model from project [2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2ueqn22) for CIFAR10 image classification was saved as a teacher model for the following project [11.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn1). Its prediction accuracies for the classification of images in the train, validation and test datasets are 99.5%, 92.6% and 92.3% respectively. From Cell 10 of project [2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2ueqn22), we see that an output `y_hat` of the trained `ResNet9` to a batch of only one image in the test dataloader is `[[−103.4488, −113.6267, −95.8173, −90.3314, −70.0091, −96.2804, −94.8856, −100.3270, −113.8334, −108.6170]]`. Each of the 10 elements in `y_hat` is a logit ![image](images/bk978-0-7503-6244-3ch11ieqn1.gif) which produces a soft target probability `p[i]` at a temperature `T` for the pre-trained teacher model, where `i` =0,1…,9

$$p\_{i} = \\frac{e^{v\_{i}/T}}{\\sum\\limits\_{j = 1}^{C}e^{v\_{j}/T}}$$  

(11.1)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch11eqn2.gif" position="float"/
