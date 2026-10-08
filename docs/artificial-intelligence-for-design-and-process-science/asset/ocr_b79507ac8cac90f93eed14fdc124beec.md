# A Reinforcement Learning Framework for Transferable Neural...

137

![](bbox=[0.12135, 0.09337999999999999, 0.8796799999999999, 0.23671999999999999])

Fig. 8 State-action-reward sequence for policy

# 5 Training and Results

The NOA architecture in [18], the initial training here was focused on small, fully connected networks, along with some performance data (network accuracy) and network status (legal/illegal) to help construct a simpler modification space. To perform initial proof-of-concept experiments, this resulted in defining the network space as fully connected networks with up to two hidden layers and at 24 units per hidden layer and a target problem space of 12 classification problems from the UCI dataset [31]. This permits the network specification to be supplied in terms of layers and unit numbers per provides an easy means of generating initial training data by training 300 random networks [32], on each of the 12 target problems. Since the network architecture input formulation allows illegal inputs, an additional 30 illegal network descriptions were generated and assigned accuracy values of 0 to allow the system to learn the demarcations of the embedding space. To evaluate the ability of the network to generalize, the set of classification problems was divided into a training set consisting of nine and a test set with the remaining three problems, and only data from training problems was used during all stages of the training process.

To characterize the complexity of target problems, a problem description vector with 13 attributes was designed. Apart from “No of Classes,” “Data Size,” “Attribute Type,” it includes Entropy of dataset labels, average Entropy of dataset features, as well as the accuracy for three baseline architectures. The resulting feature vectors for the used problems are shown in Fig. 9.

To be able to evaluate the individual components of the proposed architecture and determine appropriate network layouts for the components, the proposed system is trained using a sequence of pre-training stages.

To be able to study and evaluate the individual components of the proposed architecture and determine appropriate network layouts for the components, the proposed system is trained using a sequence of pre-training stages. First, the encoder-decoder networks are trained together with the accuracy and legal network predictions under supervised learning.

After this, the critic is pre-trained using random actions and a discount value of Y = 0 to predict the reward of the system. Similarly, the actor is trained subsequently