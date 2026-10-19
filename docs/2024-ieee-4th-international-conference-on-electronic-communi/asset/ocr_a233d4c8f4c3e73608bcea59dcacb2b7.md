![](bbox=[0.165, 0.182, 0.834, 0.338])

**Figure 2.** Image caption data generation with CHDS.

# 4.2. *System Training*

The “Image Captioning Using Attention” program from the Matlab® Deep Learning Toolbox® was used to test the proposed method. In the testing experiment, model parameters were initialized with 512 hidden units and a word embedding dimension of 256. The fully connected network’s weights were initialized using the Glorot initializer. The output size was matched with the decoder’s embedding dimension (256), and the input size was aligned with the “mixed10” layer’s 2048 output channels from the pre-trained Inception-v3 network. The mini-batch size was set at 128, with a maximum of 30 epochs, and other parameters are detailed in Table 1.

**Table 1.** Parameters of captions.

| Initial Learn Rate | Mini Batch | L2 Regularization | Optimizer |
|---|---:|---:|---|
| 0.0001 | 30 | 0.01 | rmsprop |

The hardware for the training experiment includes (1) CPU: Intel Xeon E5-2620v4 @ 2.10 GHz, (2) RAM: 40 GB at 2400 MHz, (3) Operating System (OS): Microsoft Windows 10, and (4) GPU: NVIDIA Quadro P2000 (5 GB). The training process lasted over 21.5 h, encompassing 30 epochs, and culminated in a final BLEU score of 0.3851. This BLEU score suggests a moderately feasible outcome.

# 4.3. *System Testing*

The trained image caption model was evaluated using site hazard images. The caption generation process of the program is illustrated in Figure 3. The initial step involves the identification of site objects, including workers and formwork. Subsequently, the program detects the associated hazard scenario within the image, marked by the yellow-dot square area. Finally, it proceeds to generate a caption, word by word, to describe the hazard scenario.

Figure 4 shows a test result of a site image, where a worker standing beside a mobile crane, without protective barriers, is at risk of being struck.