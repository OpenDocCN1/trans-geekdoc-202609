
# 200 Big data recommender systems, volume 1

![](img/6d0ce7dba01af52e1c2fae47d5b04a05_216_0.png)

Figure 9.1 The graphical representation of our model

# Table 9.3 Notations of model parameters

| Variable | Interpretation |
| --- | --- |
| $K$ | The number of latent topics |
| $z_{u,i}$ | The topic assigned to spatial item $v_{u,i}$ |
| $\theta^0$ | The background topic vector |
| $\theta^{native}$ | The topic vector representing the intrinsic interests of user $u$ |
| $\theta_{l,t}$ | The topic of $l$ on time $t$, representing the native preferences at $l$ on time $t$ |
| $\theta^{tourist}$ | The topic of $l$ on time $t$, representing the tourist preferences at $l$ on time $t$ |
| $\phi^l$ | The word vector of the background |
| $\psi^0$ | The spatial item vector of the background |
| $\phi^{topic}$ | Content word vector of topic $z$ |
| $\psi^{topic}$ | Spatial item vector of topic $z$ |

out-of-town. Technically, we introduce two parameters: native preferences $\theta^{native}$ and tourist preferences $\theta^{tourist}$. Given a location $l$, the native preferences $\theta^{native}$ represent the preferences of people living at $l$. In contrast, the tourist preferences $\theta^{tourist}$ represent the preferences of people traveling to location $l$. Note that, distinguishing native preferences from tourist preferences is one of the fundamental differences between our models ST-SAGE and the LCA-LDA [16] which also exploits local activity records at the target location.

# Spatiotemporal recommendation with big geo-social networking data 201

**Temporal dynamic modeling.** As presented, users tend to visit different spatial items at different time, we expect that the proposed ST-AGE model is able to capture this temporal dynamic of user behaviors. An intuitive approach in modeling the temporal influence is to split time into multiple slices at a predefined (e.g., hourly or seasonal) and then model the temporal preferences of a user based on his/her visited items inside each time slice. As we know, the data in real recommender systems are very sparse and dividing a user's activity into multiple slices makes the data much sparser in a specific time slice, which inevitably makes the inference of temporal preferences over-fitting. In this work, we propose to exploit and integrate the collective temporal preferences of the crowd with the same role as the target, as shown in Figure 9.1. The collective preferences of the people with the same role, $\phi_{lj}^{native}$ and $\phi_{lj}^{tourist}$, and are extended to the temporal vectors $\theta_{lj}^{native}$ and $\theta_{lj}^{tourist}$.

**Topics modeling.** To take full advantage of the strengths of both content-based and collaborative filtering-based recommendation methods, a topic $z$ in our ST-AGE model is not only associated with a word vector $\phi_{z}^{topic}$, but also with a spatial items vector $\psi_{z}^{topic}$ and $\sim$ to be mutually influenced. This design enables and enhanced by the topic-discovery process by associating each other. By the discovered $z$, on one hand, we can cluster the content-similar items together. On the other hand, it can capture the item co-occurrence patterns to link items together, to similar to item-based collaborative filtering methods. We also introduce two background models $\phi_{z}^0$ and $\psi_{z}^0$ to make the topics learned from the dataset more discriminative, since $\phi_{}^0$ and $\psi_{z}^0$ assign high probabilities to non-discriminative and non-informative words and items.

For an individual user in the user profile $D_u$, the generative process of the ST-AGE models is:
- Draw a topic index $z_{u,j} \sim P(z_{u,j}|s_{u,j}, t_{u,j}, \theta_{u,j}^{native}, \theta_{u,j}^{tourist})$
- For each word $w_{u,j}$ in $W_{u,j}$, draw $w_{u,j} \sim P(w_{u,j}|z_{u,j}, \phi_{u,j}^{topic})$
- Draw a spatial item $v_{u,j} \sim P(v_{u,j}|z_{u,j}, \psi_{u,j}^{topic})$

For each user, ST-AGE first chooses this topic is is about. We utilize a multinomial model as follows:
$P(z_{u,j} | s_{u,j}, t_{u,j}, \theta_{u,j}^{native}, \theta_{u,j}^{tourist})$
$= P(z_{u,j}^{user}) \times (1 - S_{u,j}) \times \theta_{u,j}^{native} + S_{u,j} \times \theta_{u,j}^{tourist} \quad \quad (9.3)$

where $P(z_{u,j}^{user}) = (1 - S_{u,j}) \times z + S_{u,j} \times z^*$, denoted as $\alpha_{u,s,j,z^*}$, is computed as (9.6). Once the topic $z$ is generated, the spatial item $v$ and the associated content words are generated in (9.4) and (9.5), respectively.

$P(v_{u,j} | z_{u,j}) = P(v_{u,j} | \psi_{u,j}^{topic}) \quad \quad \quad \ (9.4)$

$P(w_{u,j} | z_{u,j}) = P(w_{u,j} | \phi_{u,j}^{topic}) \quad \quad \quad \ (9.5)$

where $P(v | \psi_{z}^{topic}) = \gamma_{z,v}$ and $P(w | \phi_{z}^{topic}) = \beta_{z,w}$ are computed as in (9.6). Note that, in order model topics based on the background word/item vectors, for each topic, T-SAGE models the difference from the background word/item vector in log-frequencies, instead of the frequencies themselves.

# 9.3.3 Model inference

The goal of model inference is to learn parameters that maximize the marginal likelihood of the observed random variables $w, v, t$ and $s$, and the marginalization is performed with respect to the latent variable $z$. However, the latent variable $z$ is difficult to maximize directly. Therefore, the Gibbs algorithm [34], a mixture of EM and a Monte Carlo sampler, is adopted to maximize the data likelihood in (9.7), represents the set of all the parameters. There are two steps in each iteration of the Gibbs algorithm:
- In the E-step, we sample latent topic assignments for the activity records using the Gibbs sampling and fixing all other parameters.
- In the M-step, we optimize the model parameters and fixing topic assignments using the gradient descent algorithm. The two steps are iterated until

$$\alpha_{u,s,j,z} = \frac{\exp(\theta_z^0 + u_{j,z}^{user}) + (1-s) \times s \times x_{j,z}^{native})}{\sum_{z'} \exp(\theta_{z'}^0 + u_{j,z'}^{user}) + (1-s) \times s \times x_{j,z'}^{native})}$$

$$\beta_{z,w} = \frac{\exp(\phi_z^0 + u_{j,z}^{user}) + (1-s) \times s \times x_{j,z}^{native})}{\sum_{z'} \exp(\theta_{z'}^0 + u_{j,z'}^{user}) + (1-s) \times s \times x_{j,z'}^{native})}$$

$$P(v_{u,j} | z_{u,j}) = P(v_{u,j} | \psi_{u,j}^{topic}) \quad \quad \quad \ (9.4)$$

$$P(w_{u,j} | z_{u,j}) = P(w_{u,j} | \phi_{u,j}^{topic}) \quad \quad \quad \ (9.5)$$

$$P(v | \psi_{z}^{topic}) = \gamma_{z,v} \text{ and } P(w | \phi_{z}^{topic}) = \beta_{z,w} \text{ are computed as in (9.6)}.$$

$$P(z_{u,j} | s_{u,j}, t_{u,j}, \theta_{u,j}^{native}, \theta_{u,j}^{tourist}) = P(z_{u,j}^{user}) \times (1 - S_{u,j}) \times \theta_{u,j}^{native} + S_{u,j} \times \theta_{u,j}^{tourist} \quad \quad (9.3)$$

$$\alpha_{u,s,j,z} = \frac{\exp(\theta_z^0 + u_{j,z}^{user}) + (1-s) \times s \times x_{j,z}^{native})}{\sum_{z'} \exp(\theta_{z'}^0 + u_{j,z'}^{user}) + (1-s) \times s \times x_{j,z'}^{native})}$$

$$\beta_{z,w} = \frac{\exp(\phi_z^0 + u_{j,z}^{user}) + (1-s) \times s \times x_{j,z}^{native})}{\sum_{z'} \exp(\theta_{z'}^0 + u_{j,z'}^{user}) + (1-s) \times s \times x_{j,z'}^{native})}$$

$$P(v_{u,j} | z_{u,j}) = P(v_{u,j} | \psi_{u,j}^{topic}) \quad \quad \quad \ (9.4)$$

$$P(w_{u,j} | z_{u,j}) = P(w_{u,j} | \phi_{u,j}^{topic}) \quad \quad \quad \ (9.5)$$

$$P(v | \psi_{z}^{topic}) = \gamma_{z,v} \text{ and } P(w | \phi_{z}^{topic}) = \beta_{z,w} \text{ are computed as in (9.6)}.$$

$$P(z_{u,j} | s_{u,j}, t_{u,j}, \theta_{u,j}^{native}, \theta_{u,j}^{tourist}) = P(z_{u,j}^{user}) \times (1 - S_{u,j}) \times \theta_{u,j}^{native} + S_{u,j} \times \theta_{u,j}^{tourist} \quad \quad (9.3)$$

$$\alpha_{u,s,j,z} = \frac{\exp(\theta_z^0 + u_{j,z}^{user}) + (1-s) \times s \times x_{j,z}^{native})}{\sum_{z'} \exp(\theta_{z'}^0 + u_{j,z'}^{user}) + (1-s) \times s \times x_{j,z'}^{native})}$$

$$\beta_{z,w} = \frac{\exp(\phi_z^0 + u_{j,z}^{user}) + (1-s) \times s \times x_{j,z}^{native})}{\sum_{z'} \exp(\theta_{z'}^0 + u_{j,z'}^{user}) + (1-s) \times s \times x_{j,z'}^{native})}$$

$$P(v_{u,j} | z_{u,j}) = P(v_{u,j} | \psi_{u,j}^{topic}) \quad \quad \quad \ (9.4)$$

$$P(w_{u,j} | z_{u,j}) = P(w_{u,j} | \phi_{u,j}^{topic}) \quad \quad \quad \ (9.5)$$

$$P(v | \psi_{z}^{topic}) = \gamma_{z,v} \text{ and } P(w | \phi_{z}^{topic}) = \beta_{z,w} \text{ are computed as in (9.6)}.$$

The goal of model inference is to learn parameters that maximize the marginal likelihood of the observed random variables $w, v, t$ and $s$, and the marginalization is performed with respect to the latent variable $z$. However, the latent variable $z$ is difficult to maximize directly. Therefore, the Gibbs algorithm [34], a mixture of EM and a Monte Carlo sampler, is adopted to maximize the data likelihood in (9.7), represents the set of all the parameters. There are two steps in each iteration of the Gibbs algorithm:
- In the E-step, we sample latent topic assignments for the activity records using the Gibbs sampling and fixing all other parameters.
- In the M-step, we optimize the model parameters and fixing topic assignments using the gradient descent algorithm. The two steps are iterated until

More specifically, in order to model topics based on the background word/item vectors, for each topic, T-SAGE models the difference from the background word/item vector in log-frequencies, instead of the frequencies themselves.

The goal of model inference is to learn parameters that maximize the marginal likelihood of the observed random variables $w, v, t$ and $s$, and the marginalization is performed with respect to the latent variable $z$. However, the latent variable $z$ is difficult to maximize directly. Therefore, the Gibbs algorithm [34], a mixture of EM and a Monte Carlo sampler, is adopted to maximize the data likelihood in (9.7), represents the set of all the parameters. There are two steps in each iteration of the Gibbs algorithm:
- In the E-step, we sample latent topic assignments for the activity records using the Gibbs sampling and fixing all other parameters.
- In the M-step, we optimize the model parameters and fixing topic assignments using the gradient descent algorithm. The two steps are iterated until.
