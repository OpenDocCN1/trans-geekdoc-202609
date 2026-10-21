# 18.3.2.2 Coupled attribute value similarity

To exploit the stock correlations to facilitate the prediction, similarity measures are required to obtain such correlations. The traditional similarity measures usually assume the object’s attributes are independent with each other and the interactions among the attributes are not considered to calculate the similarity. However, the coupling effects among different attributes exist in a wide range of applications. We take two movie-related attributes, the actor and genre, as an example. The actor Jackie Chan appears more frequently in action movies than in other genres, while actor Jim Carrey is more likely to play roles in comedy movies. Thus, in addition to considering the intra-coupled similarity within an attribute, the inter-coupled similarity among different attributes should also be involved.

Formally, a large number of data objects with the same features can be organized by such information table S = ⟨U, A, V, f⟩, where U = {u₁, u₂, …, uₘ} is a set of instances, A = {a₁, a₂, …, aₙ} is a n-attribute set for every instance. Vⱼ is the set of all the values of feature aⱼ, and fⱼ : U → Vⱼ is a map function that returns the attribute aⱼ’s value of the instance. We next introduce an approach to calculate the intra-coupled and inter-coupled similarities.

# Intra-coupled attribute value similarity (IaAVS).

According to Wang et al. (2011), the frequency distribution of the attribute value can reveal the value similarity. The intra-coupled similarity δⱼ^{Iₐ}(x, y) between values x and y of attribute aⱼ is defined as

δⱼ^{Iₐ} = \frac{|gⱼ(x)| · |gⱼ(x)|}{|gⱼ(x)| + |gⱼ(y)| + |gⱼ(x)| · |gⱼ(y)|},

where Vⱼ → 2^U is a map function that returns a set of instances whose values of attribute aⱼ are x. Thus, gⱼ(x) is defined as

gⱼ(x) = { uᵢ | fᵢ(uᵢ) = x, 1 ≤ j ≤ n, 1 ≤ i ≤ m }.

# Inter-coupled attribute value similarity (IeAVS).

The inter-coupled attribute value similarity δⱼ^{Iₑ}(x, y) between values x and y of attribute aⱼ is the aggregation of the relative similarities δ_{j|k}(x, y) (which will be given later) for all the other attributes excluding itself.

δⱼ^{Iₑ}(x, y) = \sum_{k=1, k≠j}^{n} αₖ δ_{j|k}(x, y),

where αₖ is the weight parameter for attribute aⱼ, ∑_{k=1}^{n} αₖ = 1, αₖ ∈ [0, 1]. The relative similarity δ_{j|k}(x, y) represents the similarity between values x