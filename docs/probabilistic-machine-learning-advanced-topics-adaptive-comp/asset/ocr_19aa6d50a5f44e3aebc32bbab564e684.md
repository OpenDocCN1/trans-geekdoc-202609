```
Document #29795
Bix heidcerkcke, a trag 196 fiftee 207 pur 74 on this stag 071 of a klap 053 overbearing 087 the mississippi 137 rive 157 His
was listenin 190 which 077 comin 090 there a passiol 014 overture The music 077 had alreadi captur 097 my heart 157
as a well 077 ear 119 If you want jazz 073 Her biedercbecke had already had music 077 lessons 077 He shown 077 promis 134 on
the piano 087 and the parents 035 hopod 088 he would consider 018 Becoming a concert 077 pianist 077 But bix was
interested 068 in another kind 090 of music 077 He wantle 068 to play 077 the coronet And went 078 to play 077 jazz ...

Document #1883
There is a simple 100 reason 106 why there are so few periods 078 of really great theater 062 in our whole western 046 world.
Too many things 100 have to come right at the very same time The dramatist must 082 have the right actor 068 the
actor 182 must have the right playhouse 084 the playhouses must have the right audience 092 We the public must remember 139 that
plays 082 have to be perform 146 not merely to be read 034 even when right read 124 to play 072 must trust itself 288 to
perform 1025 it will put on a stage 068 as you go along as soon 006 as a play 072 has to be perform 072 then some kind 126
of theatrical pul ...

Document #21596
Jim 163 as the game book 154 Jim 396 reads 254 the book 254 Jim 296 sees 081 game 166 for one Jim 396 play 166 the game 166
Jim 306 likes 192 the game 166 Jim The game 166 book 066 helps 081 Jim 206 Don 120 come 040 into the house 039 Don 120 and
Jim 376 read 102 the game 166 book 024 The boys 102 see a game 166 for two The two boys 200 play 102 the game 166
The boys 099 play 102 the game 166 for two The boys 155 like the game 166 Meg 032 comes into the house 126 Meg 025 and
don 120 want Jim read the book 034 They see a game 166 for three Meg 030 and don 120 and Jim 376 play 102 the game 166
They play 112 ...
```

Figure 28.26: Three documents from the TASA corpus containing different senses of the word play. Grayed out words were ignored by the model, because they correspond to uninteresting stop words (such as “and”, “the”, etc.) or very low frequency words. From Figure 10 of [SG07]. Used with kind permission of Tom Griffiths.

# ## 28.5.1.3 Posterior inference

Many algorithms have been proposed to perform approximate posterior inference in the LDA model. In the original LDA paper, [BNJ03a], they use variational mean field inference (see Section 10.3). In [HBB10], they use stochastic VI (see Supplementary Section 28.1.2). In [GS04], they use collapsed Gibbs sampling, which marginalizes out the discrete latents (see Supplementary Section 28.1.1). In [MB16; SS17b] they discuss how to learned amortized inference networks to perform VI for the collapsed model.

Recently, there has been considerable interest in spectral methods for fitting LDA-like models which are fast and which come with provable guarantees about the quality of the solution they obtain (unlike MCMC and variational methods, where the solution is just an approximation of unknown quality). These methods make certain (reasonable) assumptions beyond the basic model, such as the existence of some anchor words, which uniquely the topic for a document. See [Aro+13] for details.

# ## 28.5.1.4 Determining the number of topics

Choosing \(N_z\), the number of topics, is a standard model selection problem. Here are some approaches that have been taken:

+   - Use annealed importance sampling (Section 11.5.4) to approximate the evidence [Wal+09].
+   - Cross validation, using the log likelihood on a test set.
+   - Use the variational lower bound as a proxy for \(\log p(\mathcal{D}|N_z)\).
+   - Use non-parametric Bayesian methods [Teh+06].