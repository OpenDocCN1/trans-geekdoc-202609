# Categorical Deep Learning

tions we use neural networks to align in invertible (Worrall & Welling, 2019) or fully compositional (de Hahn et al., 2020a). This is not a small collection of operators; if we can align a model to algorithm (Xu et al., 2019), it is fairly common for the target algorithm to transform data, for example when performing any of path-finding connection (Dudzik & Likovič, 2022). Generally, in order to align about constraints in computer science, we must go beyond GL.

of parametric maps, as well we do in this paper. Further, prior art in syntax-semantics connections assumes that the operations are taking place in some topological space or that neural architectures have a very specific form—our framework assumes neither. Lastly, priors over Category Theory are fragmented, sparse, and cohesive—not our paper establishes a common, unifying framework for how category theory can be applied to AI.

On the other hand, bottom-up architectures are commonly embedded in packages, like TensorFlow (Abahi et al., 2016), PyTorch (Pasch et al., 2019) and JAX (Bradrax et al., 2018). These frameworks have become indispensable in the implementation of deep learning models at scale. Packages such have advantage in functional programming; JAX is the most direct, as it is built around "composable functions", but features many other deep learning frameworks as well. Treating neural networks as "pure functions" allows a degree of type and shape-shaking, as well as automatic term shape inference and fully backed transformations.

To demonstrate our position, we will utilize a categorical framework that is expressive enough to recover standard GL concepts (invariance and equivalence), implementations of complex neural network building blocks (recursive neural networks), and well as model other intricate concepts such as type.

# 1.3. The Power of Category Theory

To understand why we are here, we must first put the field of category theory in context. Minimally, it may be caused by a baseline-tested of systems that are learned, and then applied again across scientific fields. Obstetrics in abstract algebra, category theory has flourished since, and information has been used to express ideas from numerous fields in a unified manner, helping to reveal previously unheard aspects. Modern papers use, although it thoroughly permeates, includes systems such as theory (Capucci et al., 2022; Cho & Spivak, 2023), Bayesian learning (Braithwaite et al., 2023; Jacobs and 2019), and information and probability theory (Leinst own, 2021; Bradley; 2021; Sturz, 2015; Heunen et al., 2017; Perrone, 2022).

This has resulted in a reliable set of matter theories and tools; from algebra, topology, combinatorics to recursion and dependent types, all of them with a mutually compatible interface. Category theory in machine learning has emerged (Fevikin & Smeding, 2024; Alvarez-Pazco et al., 2021; Gavranovic, 2022), operational-data analysis (Guss & Sukalahdin, 2018), natural language processing (Lewis, 2019), causal inference (Jacobi et al., 2019), producing an entire category picture of gradient-based learning—from architectures to backup—in Cruwell et al. (2022); Gavranovic (2024), with a more implementation-centric view in Nguyen & Wu (2022), and earlier effort work (Fong et al., 2021).

# 1.2. Our Position

It is position that constructing a framework for all of deep learning, requires robustly bridging the top- and bottom-up approaches to neural network specification with a unifying framework, and the concepts that this bridging could come from computer science. However, such a framework must generalize both group theory and functional programming—and a natural candidate for achieving this is category theory.

It is worth noting that ours is not the first approach to computer science through the lens of networks (Benglyn et al., 2015), but explore the syntax and semantics in neural networks (Sonoda et al., 2023a; 2024) by apply Category Theory to machine learning (Gavranovic, 2020).

We are unaware of any prior work that tackles the connection of neural network architectures and the algebras

# 1.1. ESSENTIAL CONCEPTS

Before we begin, we will recall three essential concepts in category theory, which will be necessary for our exposition. First, we define a category, an axiomatisation of a compositional structure.