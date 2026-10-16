
The creation of the ideal DL architecture for tissue characterisation and plaque categorisation is the fundamental uniqueness of our proposed system. The number of convolution neural network (CNN) layers and the types of the layers \[[37](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib37)\] in a DL architecture are heavily influenced by the dataset’s complexity and the hyper-parameters when combined. Our lab has previously built DL architectures with up to 22 layers, which are typically designed to accept large sample sizes (in the hundreds) and larger image sizes (W × H) \[[38](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib38)\]. We used a 13-layer CNN architecture with five convolution layers (CLs), five average pooling layers (APLs), two dense layers (DenL-1, DenL-2), and one dropout layer, as shown figure [6.2](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6fig2)(c), because our cohort size and image size are both reasonable (i.e. 346 images with sizes ranging from 55 × 43 pixel² to 593 × 107 pixel² without augmentation or a cohort size of 2311 with augmentation). By adjusting the number of layers, dropout rate, momentum rate, and learning rate, we were able to fine-tune the hyper-parameters. The softmax layer, which computes the categorical cross-entropy loss function (*E*) between the two classes of symptomatic and asymptomatic and is mathematically as follows:

*E* =  − (*y*\*log(*p*)) + \[(1−*y*)\*log(1−*p*)\],  

(6.1)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch6eqn15.gif" position="float"/

where *p* is the DL-estimated predicted probability of the plaque belonging to a specific class, *y* is the binary indication for the observed class, and \* is the product. Equation ([6.2](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6eqn2)) gives the number of output features from the convolution process \[[33](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib33)\] and equation ([6.3](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6eqn3)) gives the number of output features from average pooling feature mappings (APFMs):

$$n\_{out} = \\left\\lbrack \\frac{n\_{in} + (2*P) - M}{S} \\right\\rbrack + 1$$  

(6.2)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch6eqn16.gif" position="float"/

$$a\_{out} = {\\left( \\frac{w - f\\quad}{S} \\right) + 1,}$$  

(6.3)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch6eqn17.gif" position="float"/

where *n*[*i**n*]inline-graphic style="height:0.875em;" xlink:href="bk978-0-7503-2244-7ch6ieqn18.gif"/ and *n*[*o**u**t*] inline-graphic style="height:0.875em;" xlink:href="bk978-0-7503-2244-7ch6ieqn19.gif"/denote the number of input and output characteristics that each CL represents. *M* is the size of the convolution kernel, *P* is the size of the convolution padding, *S* is the stride size (representing the kernel movement), *a*[*o**u**t*]inline-graphic style="height:0.875em;" xlink:href="bk978-0-7503-2244-7ch6ieqn20.gif"/ is the number of APL output features, *w* is the width of the input feature map, and *f* is the kernel size. Table [6.1](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6t1) provides the names of the layers, the sizes of the feature maps, and the training parameters in three columns (per epoch). The input size must be the same for the DL system to work. As a result, we employed padding zeros to convert the cut portions images to same-sized images, but we made sure they did not get used throughout the DL process. Moreover, we utilise a ‘mask image’ the same size as the chopped part to only consider the greyscale pixels of the chopped parts. As a result this masked image is employed to ensure that DL only uses the chopped sections’ greyscale pixels.

**Table 6.1.** CNN with 13 layers (dropout layer not included) with trainable parameters. (Reproduced with permission from \[[49](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib49)\]. Copyright 2021 Springer.)

| C1  || C2 || C3 |

| --- | --- | --- |

| 2D convolution layer 1 || (240, 240, 256) || 7168 |

| 2D average pooling layer 1 || (120, 120, 256) || 0 |

| 2D convolution layer 2 || (120, 120, 128) || 295 040 |

| 2D average pooling layer 2 || (60, 60, 128) || 0 |

| 2D convolution layer 3 || (60, 60, 64) || 73 792 |

| 2D average pooling layer 3 || (30, 30, 64) || 0 |

| 2D convolution layer 4 || (30, 30, 32) || 18 464 |

| 2D average pooling layer 4 || (15, 15, 32) || 0 |

| 2D convolution layer 5 || (15, 15, 16) || 4624 |

| 2D average pooling layer 5 || (7, 7, 16) || 0 |

| 1D flatten || 784 || 0 |

| 1D dense 1 || 128 || 100 480 |

| Dropout layer || 128 || 0 |

| 1D dense 2 || 2 || 258 |

| Total trainable parameters || 499 826 |

#### 6.2.8 Experimental protocol

Our experimental technique entails employing the K10 technique to determine classification accuracy using a cross-validation (CV) paradigm (90% training and 10% testing). We conducted the CV technique on both datasets to demonstrate the potential of the augmentation (default 346 plaques and augmented 2311 plaques). During the training and testing of the DL system, the following factors were taken into account: 10 000 total epochs, 0.001 learning rate, 32 batch size, 0.001 regularisation (L2), and 0.5 dropout, Adam as the optimiser. According to our DL laboratory experience \[[39](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib39)\], a single combination can have somewhere between 10 000 and 20 000 iterations during training. We chose 10 000 epochs as a reliable value because the image size was moderate. The learning rate and regularisation values are typically 0.001 and 0.001, respectively, as they are in the industry. As the overall data size for ten combinations of the K10 protocol was 311 (90% of 346) or 2080 (90% of 2311), the batch size for training was 32. MEDCALC 17.0 was used to evaluate the final predicted class value and compute the received operating characteristics (ROC) and areas-under-the-curve (AUCs).

#### 6.2.9 Machine learning for benchmarking deep learning

We compare textural characteristics, AUC, and accuracy to see how well the DL model compares to ML models. Figure [6.2](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6fig2) depicts the overall architecture of the ML models. The effectiveness of ML models is determined by the features retrieved and chosen. We collected the histogram, Haralick, and Hu-moment features, which we then entered into linear discriminant analysis (LDA), *k*‑nearest neighbours (*k*‑NN), and the K10 cross-validation protocol \[[40](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib40), [41](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib41)\].

#### 6.2.10 Performance parameters using the DL and ML methods

If *η*[*K*10]^(*D**L*)(*c*) inline-graphic style="height:1.5em;" xlink:href="bk978-0-7503-2244-7ch6ieqn21.gif"/represents the accuracy of the DL method using the K10 protocol for the combination, ${\\overline{\\eta}}\_{K10}^{\\text{DL}}$inline-graphic style="height:1.5em;" xlink:href="bk978-0-7503-2244-7ch6ieqn22.gif"/ represents the mean of the *C* combinations, and *σ*[*K*10]^(*D**L*)inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-2244-7ch6ieqn23.gif"/ represents the corresponding standard deviation, then these may be stated mathematically as

$${\\overline{\\textit{η}}}\_{K10}^{\\text{DL}} = \\frac{\\sum\\limits\_{c = 1}^{C = 10}\\eta\_{K10}^{DL}\\text{(}c\\text{)}}{C}$$  

(6.4)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch6eqn24.gif" position="float"/

$$\\sigma\_{K10}^{DL} = \\sqrt{\\frac{\\sum\\limits\_{c = 1}^{C = 10}\\left\\lbrack \\eta\_{K10}^{DL}\\text{(}c\\text{)} - {\\overline{\\eta}}\_{K10}^{DL} \\right\\rbrack^{2}}{C - 1}}.$$  

(6.5)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch6eqn25.gif" position="float"/

Following a similar notation for the ML based strategy, we can compute the mean and standard deviation as follows:
