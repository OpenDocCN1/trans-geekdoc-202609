![](bbox=[0.109, 0.076, 0.895, 0.212])

Figure 10.3 Samples of the PCam dataset.

# 10.2.5 PatchCamelyon (PCam) Dataset

PatchCamelyon is a dataset for picture categorization. It is made up of 327.680 color pictures (96 × 96 px) taken from lymph node histopathologic scans. Each image has a binary label that indicates the existence of metastatic tissue as shown in Figure 10.3. PCam is a new machine learning benchmark that is larger than CIFAR10, smaller than ImageNet, and trainable on a single GPU [11].

# 10.2.6 Kumar Dataset

The Kumar dataset contains 30 1000 × 1000 picture tiles taken at 40 magnifications from The Cancer Genome Atlas (TCGA) database for seven organs (6 breast, 6 livers, 6 kidneys, 6 prostates, 2 bladders, 2 colons, and 2 stomachs) as shown in Figure 10.4. Each nucleus's boundary is completely marked within each image [12].

# 10.3 RELATED WORK

Graham et al. [6] propose Dense Steerable Filter CNNs (DSF-CNNs), which use group convolutions in a densely connected framework with multiple rotatable copies of each filter. In comparison to traditional filters, each filter is specified as a linear combination of steerable basis filters, allowing precise rotation, and reducing the number of trainable parameters. W. Lafarge et al. [7] focused on histopathology image analysis applications where it is desirable that the machine learning models do not collect the arbitrary global orientation information of the observed tissues. Three separate histopathology image analysis tasks are used to test the proposed system. Zhou et al. [8] developed a new smooth truncated loss that modifies losses to minimize outlier disturbance. As a result, the network may concentrate on learning from reliable and informative data, which improves generalization capability intrinsically. Experiments on the MICCAI Multi-Organ-Nuclei-Segmentation challenge in 2018 confirmed the efficacy of our proposed technique. On numerous independent multi-tissue histology picture datasets, Graham et al. [9] exhibit state-of-the-art performance relative to previous approaches. We present a new dataset of Hematoxylin and Eosin-stained colorectal adenocarcinoma picture tiles, which contain 24,319 exhaustively annotated nuclei with associated class labels, as part of this effort. Weiler et al. [10] extend He's weight initialization approach to filters specified as a linear