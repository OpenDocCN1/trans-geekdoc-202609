# MALWARE DETECTION IN DEEP LEARNING 279

5. Generative Adversarial Networks: It is a special network architecture which creates fully new and diverse images which are not previously present in the vacant training dataset.

# 13.2.3 Detection Techniques Using Deep Learning

We have seen architectures of deep learning in Figure 13.11, which show how deep learning is extended its network. Especially newly architecture of deep learning is proving stronger and accurate results [8]. In recent years, which method is most used for malware detection using deep learning are listed:(Table 13.1) [1].

**Table 13.1** Deep learning methods for malware detection.

| Deep learning methods | Description |
|---|---|
| Deep Neural Network | Accuracy of detection is 95% and false rate is 0.1%. |
| CNN and LSTM | Used for spatial and temporal signals difficult of malware illustration. |
| Deep Learning | Mixture of static, dynamic malware analysis is used for recognition. |
| Deep Belief Network | It represent malware as opcode sequences and then apply DBN |
| Deep Learning (CNN) | Using image processing for malware detection which convert malware in greyscale binaries and train the CNN. |

Methodology for malware detection using CNN [8]:

+   1. Malware is unpacked
2. Executable file is stripped
3. API calls is extracted
4. Offered an extension by adding another step.
5. Various features are integrated through static static analysis (Capturing information from executables without running it) and dynamic analysis (running malware in isolated environment).
6. Most new malware is formed using previous malware changing some things in a code taking these as advantage using image processing techniques will detect malware. Here image processing steps is performed to detect malware.
i. Converting Malware binary to image
ii. Apply CNN to Malware image