# Article

# ## **Pixel-Level Degradation for Text Image Super-Resolution and Recognition**

**Xiaohong Qian** $^{1}$ , **Lifeng Xie** $^{1}$ , **Ning Ye** $^{1}$ , **Renlong Le** $^{2}$ and **Shengying Yang** $^{1, *}$

+   $^{1}$ School of Information and Electronic Engineering, Zhejiang University of Science and Technology, Hangzhou 310023, China  
$^{2}$ Ningbo Sea Fresh Information Technology Co., Ningbo 315500, China; lrenglong@haishangxian.cn  
* Correspondence: syang@zust.edu.cn

**Abstract:** In the realm of image reconstruction, deep learning-based super-resolution (SR) has established itself as a prevalent technique, particularly in the domain of text image restoration. This study aims to address notable deficiencies in existing research, including constraints imposed by restricted datasets and challenges related to model generalization. Specifically, the goal is to enhance the super-resolution network’s reconstruction of scene text image super-resolution and utilize the generated degenerate dataset to alleviate issues associated with poor generalization due to the sparse scene text image super-resolution dataset. The methodology employed begins with the degradation of images from the MJSynth dataset, using a stochastic degradation process to create eight distinct degraded versions. Subsequently, a blank image is constructed, preserving identical dimensions to the low-resolution image, with each pixel sourced randomly from the corresponding points across the eight degraded images. Following several iterations of training via Finetune, the LR-HR method is applied to the TextZoom dataset. The pivotal metric for assessment is optical character recognition (OCR) accuracy, recognized for its fundamental role in gauging the pragmatic effectiveness of this approach. The experimental findings reveal a notable enhancement in OCR accuracy when compared to the TBSRN model, yielding improvements of 2.4%, 2.3%, and 4.8% on the TextZoom dataset. This innovative approach, founded on pixel-level degradation, not only exhibits commendable generalization capabilities but also demonstrates resilience in confronting the intricate challenges inherent to text image super-resolution.

**Keywords:** degradation model; scene text image; super resolution

# ### 1. Introduction

Scene text recognition (STR) involves the process of converting images of text, such as from books, newspapers, and other sources taken in natural scenes with less than ideal lighting and focus, into digital text sequences. With the ubiquity of smartphones and similar devices, the internet has been inundated with such use-case text images. However, largely due to hardware limitations and network bandwidth constraints, a significant portion of these images exist in low resolution. This low clarity presents a considerable challenge for text recognition.

While modern optical character recognition models exhibit impressive accuracy rates on high-resolution (HR) text images [1,2], they still grapple with low accuracy when it comes to low-resolution (LR) images. To ameliorate this, many in the research community have turned their focus towards applying super-resolution techniques to these low-resolution scene text images.

Several researchers have proffered diverse methodologies for text image super-resolution. Dong [3] proposed a method that synergizes deep learning with traditional sparse-coding-based super-resolution techniques. He applied the SRCNN network to scene text images and employed an end-to-end training approach, effectively enhancing the super-resolution results