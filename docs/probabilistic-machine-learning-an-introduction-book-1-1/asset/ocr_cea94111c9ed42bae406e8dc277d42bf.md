![](bbox=[0.05, 0.1, 0.95, 0.3])

![](bbox=[0.05, 0.32, 0.95, 0.52])

# 20.3.5.3 Latent space interpolation

One powerful feature of latent variable models is the ability to generate samples that interpolate the “semantic properties” of two different inputs. Specifically, let x₁ and x₂ be two images, and let z₁ = E_{q(z|x₁)} [z] and z₂ = E_{q(z|x₂)} [z] be their encodings. We can now generate new images that interpolate between these two anchors by computing z = λz₁ + (1 - λ)z₂, where 0 ≤ λ ≤ 1, and then decoding by computing E[x|z]. This is called latent space interpolation. (The justification for taking a linear interpolation is that the learned manifold has approximately zero curvature, as shown in [SKT18].) See Fig. 20.26 for an example, where we interpolate between a woman without sunglasses and a man with sunglasses.

# 20.3.5.4 Latent space vector arithmetic

An intriguing property of some latent variable models is that they support the ability to perform vector addition and subtraction in latent space in order to increase or decrease the amount of a desired “semantic factor of variation” (c.f., word2vec model in Fig. 19.10). For example, consider the attribute of wearing sunglasses. Let X_i^+ be a set of images which have attribute i, and X_i^- be a set of images which do not have this attribute. Let Z_i^+ and Z_i^- be the corresponding embeddings, and z̄^+ and z̄^- be the average of these embeddings. We define the offset vector as Δ = z̄^+ - z̄^-. If we add some positive multiple of Δ to a new point z, we increase the amount of this attribute; if we subtract some multiple of Δ, we decrease the amount of this attribute. (This idea was first proposed in “Probabilistic Machine Learning: An Introduction”. Draft of “Probabilistic Machine Learning: An Introduction”. January 6, 2021)