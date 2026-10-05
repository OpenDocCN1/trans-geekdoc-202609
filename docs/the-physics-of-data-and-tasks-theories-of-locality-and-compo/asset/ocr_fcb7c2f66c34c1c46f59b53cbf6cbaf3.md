# INTRODUCTION

We predict that diffusion models trained on limited data will generate outputs that are locally coherent – i.e., respecting local rules – but lack global consistency. These predictions are confirmed experimentally across both text and image domains: as progresses or more data becomes available, the generated content displays long-range coherence. We conclude by drawing a conceptual parallel between this hierarchical clustering mechanism and the renormalization group from theoretical physics.

A RACE BETWEEN MEMORIZATION AND GENERALIZATION Chapter 7 concludes Part III by investigating when and how diffusion models memorize training data. Theoretically, a diffusion model that minimizes its training loss would simply reproduce samples from its training set, i.e., memorize. In practice, this is empirically observed in the overparameterized regime. We revisit this perspective by demonstrating that, in highly overparameterized diffusion models, generalization occurs before memorization emerges only after a phase of generalization, and that the memorization time scales linearly with dataset size. In other words, generalization versus memorization should be understood as a competition between time scales.

To investigate these dynamics more precisely, we study diffusion models trained on our hierarchical grammar models, where generalization corresponds to the learning of increasingly deep rules over time – as discussed in the previous chapter. In this setting, the cost of early stopping – which halts before memorization sets – can be quantified. This allows us to construct a phase diagram that characterizes the dynamical transition between generalization and memorization.

Collectively, these chapters answer the questions posed in Section 1.3. They demonstrate that diffusion models exploit compositionality to generate and learn hierarchical data efficiently, eventually becoming creative.

# 1.5-3 Part IV: Task localization and weight disentanglement

TASK COMPOSITIONALITY IN WEIGHT SPACE The final part of the thesis, presented in Chapter 8 studies the mechanisms through tasks can be composed. Recent empirical work has shown that task vectors – differences in weights between fine-tuned and base models – can be added or subtracted to introduce new behaviors or remove

+   10 This chapter is a revised version of material first presented in [FSW25].
11 This chapter is a revised version of material first presented in [OJFF23].