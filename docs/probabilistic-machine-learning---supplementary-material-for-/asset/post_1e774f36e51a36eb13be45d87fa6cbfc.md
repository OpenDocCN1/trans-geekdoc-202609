
#### 3.2.3 Power-law prior

Looking at Figure 3.7(c-d), it seems clear that movie grosses and poem length can be modeled by a **power law** distribution of the form \(p(T) \propto T^{-\gamma}\) for \(\gamma > 0\). (If \(\gamma > 1\), this is called a Pareto distribution, see **??**.) Power-laws are characterized by having very **long tails**. This captures the fact that most movies make very little money, but a few blockbusters make a lot. The number of lines in various poems also has this shape, since there are a few epic poems, such as Homer's _Odyssey_, but most are short, like haikus. Wealth has a similarly skewed distribution in many countries, especially in plutocracies such as the USA (see e.g., `inequality.org`).

In the case of a power-law prior, \(p(T) \propto T^{-\gamma}\), we can compute the posterior median analytically. We have

$$
p(t) \propto \int_t^\infty T^{-(\gamma+1)} dT = -\frac{1}{\gamma} T^{-\gamma}|_t^\infty = \frac{1}{\gamma} t^{-\gamma} \quad (3.16)
$$

Hence the posterior becomes

$$
p(T|t) = \frac{T^{-(\gamma+1)}}{\frac{1}{\gamma} t^{-\gamma}} = \frac{\gamma t^\gamma}{T^{\gamma+1}} \quad (3.17)
$$

for values of \(T \ge t\). We can derive the posterior median as follows:

$$
p(T > T_M|t) = \int_{T_M}^\infty \frac{\gamma t^\gamma}{T^{\gamma+1}} dT = - \left( \frac{t^\gamma}{T} \right) \big|_{T_M}^\infty = \left( \frac{t}{T_M} \right)^\gamma \quad (3.18)
$$

Solving for \(T_M\) such that \(P(T > T_M|t) = 0.5\) gives \(T_M = 2^{1/\gamma} t\).

This is plotted in Figure 3.8 (bottom middle). We see that the predicted duration is some constant multiple of the observed duration. For the particular value of \(\gamma\) that best fits the empirical distribution of movie grosses, the optimal prediction is about 50% larger than the observed quantity. So if we observe that a movie has made $40M to date, we predict that it will make $60M in total.

As Griffiths and Tenenbaum point out, this rule is inappropriate for quantities that follow a Gaussian prior, such as people's ages. As they write, "Upon meeting a 10-year-old girl and her 75-year-old grandfather, we would never predict that the girl will live a total of 15 years (\(1.5 \times 10\)) and that the grandfather will live to be 112 (\(1.5 \times 75\))." This shows that people implicitly know what kind of prior to use when solving prediction problems of this kind.

#### 3.2.4 Erlang prior

Looking at Figure 3.7(e), it seems clear that the number of years a US Representative is approximately modeled by a gamma distribution (**??**). Griffiths and Tenenbaum use a special case of the Gamma distribution, where the shape parameter is \(a = 2\); this is known as the **Erlang distribution**:

$$
p(T) = \text{Ga}(T|2, 1/\beta) \propto T e^{-T/\beta} \quad (3.19)
$$

For the Erlang prior, we can also compute the posterior median analytically. We have

$$
p(t) \propto \int_t^\infty \exp(-T/\beta) dT = -\beta \exp(-T/\beta) \big|_t^\infty = \beta \exp(-t/\beta) \quad (3.20)
$$

so the posterior has the form

$$
p(T|t) = \frac{\exp(-T/\beta)}{\beta \exp(-t/\beta)} = \frac{1}{\beta} \exp(-(T-t)/\beta) \quad (3.21)
$$

for values of \(T \ge t\). We can derive the posterior median as follows:

$$
p(T > T_M|t) = \int_{T_M}^\infty \frac{1}{\beta} \exp(-(T-t)/\beta) dT = - \exp(-(T-t)/\beta) \big|_{T_M}^\infty = \exp(-(T_M-t)/\beta) \quad (3.22)
$$

Solving for \(T_M\) such that \(p(T > T_M|t) = 0.5\) gives \(T_M = t + \beta \log 2\).

This is plotted in Figure 3.8 (bottom right). We see that the best guess is simply the observed value plus a constant, where the constant reflects the average term in office.

## Chapter 4

### Graphical models

### 4.1 More examples of DGMs

#### 4.1.1 The QMR network

In this section, we describe the PGM-D known as the **quick medical reference** or **QMR** network [Shw+91]. This is a model of infectious diseases and is shown (in simplified form) in Figure 4.1. (We omit the parameters for clarity, so we don't use plate notation.) The QMR model is a **bipartite graph** structure, with hidden diseases (causes) at the top and visible symptoms or findings at the bottom. We can write the distribution as follows:

\( p(\mathbf{z}, \mathbf{x}) = \prod_{k=1}^K p(z_k) \prod_{d=1}^D p(x_d | \mathbf{z}_{\text{pa}(d)}) \) (4.1)

where \( z_k \) represents the \( k \)’th disease and \( x_d \) represents the \( d \)’th symptom. This model can be used inside an inference engine to compute the posterior probability of each disease given the observed symptoms, i.e., \( p(z_k | \mathbf{x}_v) \), where \( \mathbf{x}_v \) is the set of visible symptom nodes. (The symptoms which are not observed can be removed from the model, assuming they are missing at random (**??**), because they contribute nothing to the likelihood; this is called **barren node removal**.)

We now discuss the parameterization of the model. For simplicity, we assume all nodes are binary. The CPD for the root nodes are just Bernoulli distributions, representing the prior probability of that disease. Representing the CPDs for the leaves (symptoms) using CPTs would require too many parameters, because the **fan-in** (number of parents) of many leaf nodes is very high. A natural alternative is to use logistic regression to model the CPD, \(p(x_d|\mathbf{z}_{\text{pa}(d)}) = \text{Ber}(x_d|\boldsymbol{\sigma}(\boldsymbol{w}_d^\mathsf{T}\mathbf{z}_{\text{pa}(d)}))\). However, we use an alternative known as the noisy-OR model, which we explain below,

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_32_0.png)

Figure 4.1: A small version of the QMR network. All nodes are binary. The hidden nodes \( z_k \) represent diseases, and the visible nodes \( x_d \) represent symptoms. In the full network, there are 570 hidden (disease) nodes and 4075 visible (symptom) nodes. The shaded (solid gray) leaf nodes are observed; in this example, symptom \( x_2 \) is not observed (i.e., we don't know if it is present or absent). Of course, the hidden diseases are never observed.

| z0 | z1 | z2 | P(xd=0|z0,z1,z2) | P(xd=1|z0,z1,z2) |
|---|---|---|---|---|
| 1 | 0 | 0 | θ0 | 1 - θ0 |
| 1 | 1 | 0 | θ0θ1 | 1 - θ0θ1 |
| 1 | 0 | 1 | θ0θ2 | 1 - θ0θ2 |
| 1 | 1 | 1 | θ0θ1θ2 | 1 - θ0θ1θ2 |

Table 4.1: Noisy-OR CPD for p(xd|z0,z1,z2), where z0 = 1 is a leak node.

The noisy-OR model assumes that if a parent is on, then the child will usually also be on (since it is an or-gate), but occasionally the "links" from parents to child may fail, independently at random. If a failure occurs, the child will be off, even if the parent is on. To model this more precisely, let \(\theta_{kd} = 1 - q_{kd}\) be the probability that the \(k \rightarrow d\) link fails. The only way for the child to be off is if all the links from all parents that are on fail independently at random. Thus

\(p(x_d = 0|\mathbf{z}) = \prod_{k \in \text{pa}(d)} \theta_{kd}^{\mathbb{I}(z_k=1)}\) (4.2)

Obviously, \(p(x_d = 1|\mathbf{z}) = 1 - p(x_d = 0|\mathbf{z})\). In particular, let us define \(q_{kd} = 1 - \theta_{kd} = p(x_d = 1|z_k = 1, \mathbf{z}_{-k} = 0)\); this is the probability that \(k\) can activate \(d\) "on its own"; this is sometimes called its "**causal power**" (see e.g., [KNH11]).

If we observe that \(x_d = 1\) but all its parents are off, then this contradicts the model. Such a data case would get probability zero under the model, which is problematic, because it is possible that someone exhibits a symptom but does not have any of the specified diseases. To handle this, we add a dummy **leak node** \(z_0\), which is always on; this represents "all other causes". The parameter \(q_{0d}\) represents the probability that the background leak can cause symptom \(d\) on its own. The modified CPD becomes

\(p(x_d = 0|\mathbf{z}) = \theta_{0d} \prod_{k \in \text{pa}(d)} \theta_{kd}^{z_k}\) (4.3)

See Table 4.1 for a numerical example.

If we define \(w_{kd} \triangleq \log(\theta_{kd})\), we can rewrite the CPD as

\(p(x_d = 1|\mathbf{z}) = 1 - \exp \left( w_{0d} + \sum_k z_k w_{kd} \right)\) (4.4)

We see that this is similar to a logistic regression model.

It is relatively easy to set the \(\theta_{kd}\) parameters by hand, based on domain expertise, as was done with QMR. Such a model is called a **probabilistic expert system**. In this book, we focus on learning parameters from data; we discuss how to do this in **??** (see also [Nea92; MH97]).

#### 4.1.2 Genetic linkage analysis

PGM-D's are widely used in statistical genetics. In this section, we discuss the problem of **genetic linkage analysis**, in which we try to infer which genes cause a given disease. We explain the method below.

##### 4.1.2.1 Single locus

We start with a **pedigree graph**, which is a DAG that represents the relationship between parents and children, as shown in Figure 4.2(a). Next we construct the DGM. For each person (or animal) \(i\) and location or locus \(j\) along the genome, we create three nodes: the observed **phenotype** \(P_{ij}\) (which can be a property such as blood type, or just a fragment of DNA that can be measured), and two hidden **alleles** (genes),
