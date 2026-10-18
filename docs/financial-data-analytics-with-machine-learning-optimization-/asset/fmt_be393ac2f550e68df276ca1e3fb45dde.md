
## (IV) Application of `K`‐NN Algorithm

While `K`‐NN can be used for general classification or regression tasks, it is widely applied in facial recognition. Typically, given an observation of a human face, we aim to infer certain characteristics of the person, such as age and ethnicity, using the information of the `K` most similar faces in the training dataset. A general procedure is described as follows, assuming that there are `M` possible class labels in total:

1. For the `i`‐th human face in the training dataset of size `n`, extract its values of pre‐specified list of `p` features, possibly determined by principal components or more generally dictionary learning as discussed in [Section 14.1](#c14.xhtml#c14-sec-0002), and store them as the feature vector `x_i = (x_i1, ..., x_ip)^T` for this face, for `i = 1, ..., n`.

2. Identify the feature vector `x_{n+1}` of the newly added human face.

3. Identify the `K` nearest faces in the training set using the following (signed) similarity measure of cosine as the criterion: `Sim(x_i, x_j) := (sum_{l=1}^p x_il x_jl) / (sqrt(sum_{l=1}^p x_il^2) * sqrt(sum_{l=1}^p x_jl^2)) = (x_i^T x_j) / (||x_i||_2 ||x_j||_2)`, where this similarity measure is precisely `cos(theta_ij)`, where `theta_ij` is the angle between `x_i` and `x_j`. In other words, we determine the `K` feature vectors that are closest in direction to `x_{n+1}`, and store them in a set `P_K`.
