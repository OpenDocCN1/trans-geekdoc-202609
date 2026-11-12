a user study; and iv) by providing the task prediction through a local linear combination of concepts, it retains task interpretability¹.

# ## 2 Related Work

Concept-based XAI (C-XAI) aims to provide human-understandable explanations by using concepts as intermediate representations [14,28,31]. While supervised approaches [8,16] rely on predefined symbols, unsupervised models autonomously extract concepts by modifying a network’s internal representation through unsupervised learning, prototypical representations, or hybrid techniques [3,16].

**Unsupervised Concept Basis.** These methods learn disentangled representations in the model’s latent space by grouping samples based on fundamental characteristics. They typically achieve this via input reconstruction [3,40] or unsupervised losses [40,46]. In [46], convolutional filters act as unsupervised concepts, maximizing mutual information between images and filter activations. SENN [3] employs an autoencoder to derive clustered representations and generate class-concept relevance scores. BotCL [40] enhances SENN with attention-based concept scoring and contrastive loss. Compared to these, LCBM introduces concept embeddings for richer representations, improving the generalization-interpretability trade-off.

**Prototype Concepts.** This approach encodes training example traits as prototypes within the network, comparing them to input samples for prediction. [21] explains predictions via prototype similarity, using an autoencoder for dimensionality reduction. ProtoPNet [6] extracts prototypes representing image sub-parts, while HPNet [13] organizes prototypes hierarchically for classification across taxonomy levels. Despite providing useful example-based explanations, these models constrain representation capacity. Our approach enhances performance by leveraging richer representations while retaining prototype-based interpretability, as shown in concept dictionaries.

**Hybrid Approaches.** Recent research explores hybrid models that integrate supervised and unsupervised concepts [23,32] or leverage pre-trained LLMs [26,41,44]. The variational approach in [23] shares similarities with ours but relies on single neurons and partial supervision, limiting scalability. Methods leveraging LLMs assume sufficient knowledge for zero-shot concept annotations, yet this depends on the underlying model [35]. For instance, CLIP [29], despite its popularity, exhibits low concept accuracy even in contexts similar to its pre-training, as confirmed by our experiments.

# ## 3 Methodology

In an unsupervised concept-based setting, the objective is to make predictions using a set of abstract, human-interpretable concepts that are not predefined but

¹ Code to reproduce the proposed model is available at https://github.com/LCBM.