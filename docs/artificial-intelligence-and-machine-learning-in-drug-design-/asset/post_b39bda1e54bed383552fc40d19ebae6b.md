
![](img/9a8b0347872e9b0be4401898e8cd724c_198_0.png)

Figure 6.6 Deep learning algorithms.

rely on training data, and the quantity and quality of this data significantly impact the predictive capabilities of the trained model (Figure 6.6) [57].

## 6.6.1 Multilayer Perceptrons (MLPs)

MLPs are a type of artificial neural network (ANN) that is made up of numerous layers of linked artificial neurons or nodes. MLPs frequently play a role in machine learning applications such as regression, classification, and recognizing patterns.

An MLP's architecture is made up of an input layer, a couple of hidden layers, and a layer that provides output. Each layer is made up of engineered neurons (inspired by biological neurons), also called perceptrons or nodes. A graph with a directed acyclic pattern is formed when neurons in one layer are linked to neurons in subsequent layers in an MLP. Weights indicate the connections between neurons, which impact the strength of the link and impact the flow of information across the network [58].

MLPs are used to forecast the molecular makeup of biomolecules (proteins), usually for secondary structure prediction, fold identification, and tertiary structure prediction. MLPs may predict the molecular composition of unidentified proteins by using their amino acid sequences after being trained on existing structures of proteins and associated sequences. MLPs have demonstrated promising results in terms of enhancing the accuracy of predicting protein structure techniques, assisting in the understanding of protein function, and identifying therapeutic targets [59].

MLPs have been utilized to predict drug–drug interactions and target protein interactions. MLPs can estimate the probability of a potential medicine binding to a certain target by training them on known drug-target interaction data. MLPs are being used to prioritize possible drug–target combinations, aiding in the early phases of drug development by lowering the amount of time-consuming and costly clinical trials [60].

## 6.6.2 Recurrent Neural Networks (RNN)

Also referred to as RNNs are a type of artificial neural network that models data in succession by capturing temporal relationships and how data flow within a sequence. RNNs are establishing themselves as strong tools in bioinformatics for analyzing numerous types of biochemical data, such as the sequencing of DNA, RNA sequences, sequences of proteins, and time-series data gene expression data.

RNNs, as opposed to feedforward neural networks, use recurrent connections to allow information to be transmitted through each stage of the sequence to the subsequent one. An RNN's main component is a concealed state that stores information about past steps. The present input and the prior concealed state are merged to generate an outcome and update the state that is hidden at each step. Because of this recurring link, RNNs can process sequences of any length, making them suited for analyzing biological sequences of varying lengths [58].

Prediction of protein binding sites: RNNs can predict protein binding regions and how they interact with ligands. RNNs can recognize the sequence of amino acids and structural patterns related to binding sites via learning from existing protein-ligand combinations, assisting in the development of drugs and protein modification [61].

Time-series analysis of gene expression: RNNs can simulate the temporal changes of expression of gene data gathered through time-series investigations. RNNs may find patterns, discover gene regulation networks, and forecast future expression levels by capturing the connections between the expression of genes profiles at distinct time periods [62].

## 6.6.3 Convolutional Neural Networks (CNN)

CNNs have transformed bioinformatics by offering robust instruments for analyzing many forms of biological data such as sequences of DNA, protein sequences, genomic information, and medical image analysis. CNNs are exceptionally effective at detecting spatial and regional connections in these datasets, making them ideal for applications like sequence categorization, protein structure forecasting, variant calling, and clinical image analysis such as computed tomography [18].

The following are the major components of CNN architecture:

- A. Convolutional layers: Each of these layers is made up of a number of adaptive filters or kernels that examine the input data for specific trends or features. Convolution is performed by each filter, which comprises element-wise multiplication and summing of the filter weights with the corresponding input area. Convolutional layers are in charge of collecting local spatial characteristics and mapping them.

- B. Pooling layers: Pooling layers reduce the spatial dimensions of feature maps created by convolutional layers while keeping critical characteristics. Pooling methods such as maximum pooling and average pooling are commonly used to extract the most important information from local areas.

- C. Fully connected layers: These layers are able to connect all of the neurons from the previous one with the next, allowing the extracted characteristics to be classified or regressed. Based on the learnt representations, fully linked layers capture global connections and generate final predictions.

One such example is the DeepSF deep 1D-convolution neural network, which was designed to classify protein sequences into known folds, providing critical insights into fold recognition and the sequence–structure relationship. The method automatically extracts fold-related properties, allowing for the classification of protein sequences of any length. Training and testing on curated datasets from SCOP1.75 resulted in an average accuracy of more than 70%, but experimenting on a separate data set using SCOP2.06 led to an accuracy of 73%. On CASP9-12 targets, DeepSF surpassed HHSearch, a top profile–profile alignment technique, in terms of fold detection accuracy. DeepSF's hidden feature extraction is immune to sequence modifications, deletions, insertions, and truncations, which makes it helpful for a variety of protein motif identification tasks like grouping, comparison, and ranking [63].

## 6.6.4 Generative Adversarial Networks (GANs)

It comprises deep learning algorithms made up of two separate neural nets: a generator and a discriminator. GANs were launched in 2014 by Ian Goodfellow and his colleagues and have received a lot of interest because of their capacity to produce lifelike and superior-quality artificial data.

GANs have shown usefulness in bioinformatics and drug discovery, assisting with tasks like protein structure formation, biochemical property estimation, and chemical synthesis. GANs provide a novel method for generating new data that matches the features of the original set of data, allowing researchers to investigate and analyze complicated biological systems [64].

Protein structure creation is one use of GANs in bioinformatics. Protein architectures are critical for comprehending how proteins work and interact with drug targets. However, determining protein structures experimentally is time-consuming and costly. By programming the generator network to generate topologies that closely match the empirically discovered structures, GANs may be utilized to build realistic protein structures. The discriminator network gives input on the quality of the created structures, assuring that they match the known structural properties of proteins [65].

GANs have also been used in medication development to create unique chemical structures with desired features. The GAN's generator network may be trained to generate compounds that are structurally comparable to existing medicines or that have certain properties linked to medicinal effectiveness or safety. GANs are a helpful tool for generating innovative drug candidates with better characteristics by examining the chemical environment and using the generator's capacity to produce varied and distinct compounds [66].

Furthermore, GANs have been used in drug creation from scratch, wherein the generator network constructs chemical structures with desirable features and the network of discriminators evaluates their drug likeness. This repetitive procedure of producing and assessing molecules enables chemical exploration and the detection of new compounds with desired features [67].
