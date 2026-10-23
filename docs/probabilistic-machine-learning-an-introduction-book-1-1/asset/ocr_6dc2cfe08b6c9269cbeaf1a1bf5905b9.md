![](bbox=[0.18, 0.13, 0.38, 0.36])

![](bbox=[0.48, 0.15, 0.92, 0.34])

Figure 16.6: Speeding up triplet loss minimization. (a) Illustration of hard vs easy negatives. Here a is the anchor point, p is a positive point, and n_i are negative points. Adapted from Figure 4 of [KB19]. (b) Standard triplet loss would take 8 × 3 × 4 = 96 calculations, whereas using a proxy loss (with one proxy per class) takes 8 × 2 = 16 calculations. From Figure 1 of [Do+19]. Used with kind permission of Gustavo Cerneiro.

where m > 0 is a margin parameter. See Fig. 16.6a for an illustration. This is the technique used by Google’s FaceNet model [SKP15], which learns an embedding function for faces, so it can cluster similar looking faces together, to which the user can attach a name.

In practice, the hard negatives are usually chosen from within the minibatch. This therefore requires large batch sizes to ensure sufficient diversity. Alternatively, we can have a separate process that continually updates the set of candidate hard negatives, as the distance measure evolves during training.

# 16.2.5.2 Proxy methods

Triplet loss minimization is expensive even with hard negative mining (Sec. 16.2.5.1). Ideally we can find a method that is O(N) time, just like classification loss.

One such method, proposed in [MA+17], measures the distance between each anchor and a set of P proxies that represent each class, rather than directly measuring distance between examples. These proxies need to be updated online as the distance metric evolves during learning. The overall procedure takes O(NP²) time, where P ~ C.

More recently, [Qia+19] proposed to represent each class with multiple prototypes, while still achieving linear time complexity, using a soft triple loss.

# 16.2.5.3 Optimizing an upper bound

[Do+19] proposed a simple and fast method for optimizing the triplet loss. The key idea is to define one fixed proxy or centroid per class, and then to use distance to the proxy as an upper bound on the triplet loss.

More precisely, consider a simplified form of the triplet loss, without the margin term:

ℓ_t(x_i, x_j, x_k) = ||ê_i - ê_j|| - ||ê_i - ê_k||   (16.17)