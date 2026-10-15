
procedure. Equation 20.5 illustrates the total reward R(C) for the action value as the sum of the validity score and the discriminator's prediction.

R(C) = 1/2 D_θ(C) + 1/2 (V(C)) (20.5)

We fine-tune the generator on selected molecules once it samples more and more valid compounds. The goal is to transfer expertise in producing legitimate compounds to the area of developing molecules that particularly bond with the new coronavirus's major protease (3CLpro). The DTI model was then developed to determine the binding affinity scores of the produced compounds with the major protease.

## 20.3.4 DTI Model
Figure 20.2 depicts the suggested framework for binding affinity prediction. The raw protein sequences and the matching drug compounds in SMILES format are fed into the architecture. To begin, each SMILES character in the sequence is encoded as a number {A: 1, B:2, ... }. The encoded sequences are then sent into the proposed deep learning pipeline as inputs. Sequences, 1D convolution, and LSTM networks [10] are used as inputs because they are best suited for the analysis of sequence-based data.

### 20.3.4.1 1D Convolutional Neural Network
Multiplication and addition are all that is involved in convolution. In 1D convolution, which is used for sequences, we move a filter through the encoded sequence. With random values, the filter is first filled. We specify the size of the filter at each convolution layer, which establishes the quantity of values from the sequence to be convolved. Convolution modifies the input sequence in accordance with the filter; hence, the values of the filter may also be learned. These filters take the input sequences and extract various patterns. The pooling layer receives the output of the convolutional layer and downsamples the inputs. Reducing the size of the feature maps, which in turn decreases the total number of learnable parameters, aids in the compact representation of the input-encoded sequence and speeds up learning.

### 20.3.4.2 Long Short-Term Memory (LSTM) Network
A kind of RNN called the LSTM can manage long-term dependencies without experiencing the vanishing gradient problem. This issue has been resolved by LSTM units, which extend the functionality of the conventional RNN unit by adding new gates, such as input and forget gates. A self-loop memory cell in the LSTM enables gradients to flow over lengthy sequences. The memory cell is in charge of managing how data moves between cells. The LSTM stores the input tokens from a specific phrase as continuous values in a distributed representation. Cell state C_t and hidden state h_t are additional states that may be discovered in LSTM cells. The memory cell is made up of three units: the forget unit F_t, the input unit I_t, and the output unit O_t, together with the weights assigned to each unit. These components limit the quantity of information flow while still allowing the LSTM cell to convey data from one time step to the next.

Protein sequences are passed through with the embedded vectors corresponding to the drug molecules. In each of the first stacked convolutional layers, the total number of feature mappings is 128. The pooling size is four in the first max-pooling layer. The input-embedded protein sequence's dimensions are changed from 1024×32 to 256×128 as a result. The pool size is two for the second maximum tier. By further reducing the protein representation's dimension from 256×128 to 128×128, the input protein sequences are given a compact form. The LSTM layer's total number of hidden units is set at 128. The dimensions of the input drug molecules are changed from 128×32 to 128×128. These dimensions allow the outputs of the stacked convolutional layers and the LSTM layer to be concatenated. To extract underlying characteristics from protein sequences, stacked 1D convolutional layers are used, whereas an LSTM layer is used to extract features from pharmacological compounds.

The characteristics derived from the stacked convolutional layers of protein sequences and drug compounds are then transferred via a concatenate layer. The concatenate layer merges two vector representations of the same form into a single vector representation. We feed this concatenated representation into both the convolutional layer and the LSTM, which both have the same number of feature mappings and hidden units, resulting in a multi-view learning paradigm [52]. This method allows both LSTM and convolutional layers to extract underlying information and apply the best of both. We repeat this method by concatenating the outputs of these layers and passing the concatenated representation to both the LSTM and the convolutional layer. The final concatenated version reflects the combination of both the protein and its associated molecule representation in a simplified manner. This representation is then processed further to create a flat layer and then a dense layer. The prediction of the dissociation constant (Kd), which represents the interaction between the protein and the ligand, is seen as a regression issue.

### 20.3.4.4 Implementation Details
Using Python's TensorFlow library as a backend, the drug creation and interaction prediction models were trained [v3.7]. The models have been trained on a Tesla P100 GPU. Using a chemo-informatics molecular modelling tool package called RDKit [26], all the preprocessing procedures needed for validating, cleaning, and computing the physiochemical characteristics on SMILES strings are completed.

## 20.4 RESULTS AND DISCUSSION
In this work, we focus on three different issues. The first is the generation of a sizable collection of molecules through adversarial training. The second is passing on the expertise in producing reliable compounds and perfecting the generator to screen for powerful pharmacological molecules that block the 3CLpro protease of COVID-19 utilizing the Tanimoto similarity between pre-existing inhibitors as a reinforcement technique. The final objective is to use the created DTI prediction model to determine the binding affinity of the synthesized compounds.

### 20.4.1 Generator Quality Metrics
After training the model, we took a sample of around 10,000 compounds and evaluated their quality, which is important for drug design. Validity, uniqueness, and novelty are the three quality criteria utilized to assess the created compounds. The following is a description of these quality indicators. Let S represent the total number of drug molecules that were sampled from the generator, V represent the total number of chemically sound molecules, and N represent the total number of training samples.

- (1) Validity [QM_Valid]: This measures the total number of valid molecules out of all the generated molecules, as shown in Equation 20.6.

$$QM_{Valid} = \frac{|V|}{S} \tag{20.6}$$

For calculating the reward of the generated sequence by the RL model, the validity metric is used.

- (2) Uniqueness [QM_Unique]: This lists the total number of unique molecules out of all valid molecules. The equation for uniqueness is shown below in Equation 20.7.

$$QM_{Unique} = \frac{set(V)}{|V|} \tag{20.7}$$

- (3) Novelty [QM_Novel]: This indicates the total number of molecules generated that do not appear in the training set, as shown in Equation 20.8.

$$QM_{Novel} = 1 - \frac{|set(V) \cap N|}{|set(V)|} \tag{20.8}$$

### 20.4.2 Evaluation Metrics for Drug-Target Interaction
We used two assessment measures to assess the effectiveness of the DTI model: the Concordance index [CI] and the root-mean-squared error [RMSE]. Let y_i represent the actual result of the i^th sample, ŷ_i represent the projected result of the i^th sample, and N represent the total number of samples. The RMSE value is then determined as indicated in Equation 20.9. The RMSE calculates the difference between expected and actual values.

$$RMSE(y_i, \hat{y}_i) = \sqrt{\frac{1}{N} \sum_{i=1}^{N} (y_i - \hat{y}_i)^2} \tag{20.9}$$

Let b_i denote the prediction value of larger affinity δ_i and b_j denote the prediction value for smaller affinity δ_j, then the concordance index is given by Equation 20.10.

$$CI = \frac{1}{Z} \sum_{\delta_i > \delta_j} h(b_i - b_j)\tag{20.10}$$

where Z is a normalization constant and h[x] denotes a step function:

$$h(x)=\begin{cases}1, & \text{if } x>0\\0.5, & \text{if } x=0\\0, & \text{if } x<0\end{cases}\tag{20.11}$$

This statistic compares two randomly selected drug-target pairings’ expected binding affinities to their actual affinities in the same order.

### 20.4.3 Novel Molecule Generation
The early stopping mechanism ended the training process after 15 epochs of training the generator since the validity of the generator’s samples had not improved. Following training, we took 10,000 or so molecules from the generator for sampling. The model was able to create valid SMILES at a rate of 93.12%; of these legitimately generated sequences, 94.23% are unique, and the novelty of molecules is 100%. In addition, as a baseline for the suggested strategy, we trained an LSTM-based generative model. This model is made up of three stacked LSTM layers coupled to a single fully connected layer with 128 units with softmax activation. Based on hyper-parameter tweaking, the number of hidden units at each layer is set at 256. The LSTM-based generator created valid SMILES at a rate of 72.15%, and 97.38% of these validly generated sequences are unique, and the novelty of molecules is 90.12%. We modify the generator’s measure from validity to Tanimoto similarity to sample compounds that particularly bind to 3CL protease [4]. The model is then run again on a new dataset of widely viable antiviral medicines and a few HIV inhibitors. Figure 20.3 shows a few representative molecules from the suggested generator model, together with their IDs.

As indicated in Table 20.1, we also included a few existing models and made distinctions between the proposed generative model and the baseline models, based on a number of different factors. Although several generative models are used to generate unique molecules, each of them has been tuned for a distinct goal. For instance, ReLeaSE produced a comparable reinforcement learning strategy for the goal of suppressing JAK2 kinase, and Bjerrum et al. developed their model for the task of creating a retrosynthetic pathway of groups, among other models, as indicated in Table 20.1. The proposed model was adjusted to work against the primary coronavirus protease and has produced respectable outcomes, as reported in the next subsection. We feel the proposed model has offered a potential avenue for the identification of new therapeutic compounds in light of the findings shown in Table 20.1.
