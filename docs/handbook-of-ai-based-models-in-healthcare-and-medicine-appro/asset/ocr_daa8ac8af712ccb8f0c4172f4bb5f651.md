procedure. Equation 20.5 illustrates the total reward R(C) for the action value as the sum of the validity score and the discriminator's prediction.

R(C) = 1/2 D∅(C) + 1/2 (V(C)) (20.5)

We fine-tune the generator on selected molecules once it samples more and more valid compounds. The goal is to transfer expertise in producing legitimate compounds to the area of developing molecules that particularly bond with the new coronavirus's major protease (3CLpro). The DTI model was then developed to determine the binding affinity scores of the produced compounds with the major protease.

# 20.3.4 DTI Model

Figure 20.2 depicts the suggested framework for binding affinity prediction. The raw protein sequences and the matching drug compounds in SMILES format are fed into the architecture. To begin, each SMILE character in the sequence is encoded as a number {A: 1, B:2, ... }. The encoded sequences are then sent into the proposed deep learning pipeline as inputs. Sequences, 1D convolution, and LSTM networks [10] are used as inputs because they are best suited for the analysis of sequence-based data.

# 20.3.4.1 D Convolutional Neural Network

Multiplication and addition are all that is involved in convolution. In 1D convolution, which is used for sequences, we move a filter through the encoded sequence. With random values, the filter is first filled. We specify the size of the filter at each convolution layer, which establishes the quantity of values from the sequence to be convolved. Convolution modifies the input sequence in accordance with the filter; hence, the values of the filter may also be learned. These filters take the input sequences and extract various patterns. The pooling layer receives the output of the convolutional layer and downsamples the inputs. Reducing the size of the feature maps, which in turn decreases the total number of learnable parameters, aids in the compact representation of the input-encoded sequence and speeds up learning.

# 20.3.4.2 Long Short-Term Memory (LSTM) Network

A kind of RNN called the LSTM can manage long-term dependencies without experiencing the vanishing gradient problem. This issue has been resolved by LSTM units, which extend the functionality of the conventional RNN unit by adding new gates, such as input and forget gates. A self-loop memory cell in the LSTM enables gradients to flow over lengthy sequences. The memory cell is in charge of managing how data moves between cells. The LSTM stores the input tokens from a specific phrase as continuous values in a distributed representation. Cell state C_t and hidden state h_t are additional states that may be discovered in LSTM cells. The memory cell is made up of three units: the forget unit F_t, the input unit I_t, and the output unit O_t, together with the weights assigned to each unit. These components limit the quantity of information flow while still allowing the LSTM cell to convey data from one time step to the next.