# Similarity Learning

# Chapter 6

The mining of the triplets is a difficult task. Every point has to be compared with others to get the proper anchor (anchor, targets, positive pairs). The mining of the triplets is shown here:

```
def mine_triplets(anchor, targets, negative_samples):
    distances = cdist(anchor, targets, 'cosine')
    distances = cdist(anchor, targets, 'cosine').tolist()
    Qn_duplicated = [
        target_index for target_index, dist in enumerate(Qn_dist)
        if dist == Qn_dist[query_index]
        for query_dist, Qn_dist in enumerate(distances)]
for i, QnT_dist in enumerate(QnT_dists):
    for j in Qn_duplicated[i]:
        QnT_dist.itemset(j, np.inf)
```

```
QnT_dists_topk = QnT_dists.argsort(axis=1)[:, :negative_samples]
top_k_index = np.array([np.insert(QnT_dist, 0, i) for i, QnT_dist in
enumerate(QnT_dists_topk)])
return top_k_index
```

This could make the training slower on a GPU machine as the distance computation happens in CPU. The FaceNet model is a state of the art method in training similarity models for faces.

# The DeepNet model

The DeepNet model is used for learning the embedding of faces for face verification tasks such as FaceNet. This improves on the method of FaceNet discussed in the previous section. It takes multiple copies of the same face and passes through several encoders to get a better embedding. This has achieved a better accuracy than FaceNet but takes more time for processing. The face crops are made in the same regions and passed through their respective encoders. Then all the layers are concatenated for training against the triplet loss.

[ 163 ]