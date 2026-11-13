```
"ph": 1,
"Hardness": 1,
"Turbidity": 1
}
fusion.predict(input_data)
```

# ## 9.6 AutoML

# ## 9.6.1 Big Ideas

As we are approaching the end of this chapter,161 it helps to remember that a large component of ML revolves around automation to better our lives. The same also brings the following question, can we automate everything we learned in this textbook into one pipeline/platform?

The answer is yes! We also have a few precedents/platforms, some of which were presented in this book too. However, unlike these platforms which are designed to handle various problems, they remain general and not application/domain-oriented. The same platforms may not incorporate some of the presented concepts, such as synthetic data, symbolic regression, mapping functions, and causality.162 Perhaps one of my major concerns is that these platforms are not designed to address civil and environmental engineering problems. They are designed to address ML and data pertaining to any domain.

In this section, I will walk you through a platform that my research group has been developing. This platform aims to automate and optimize ML for civil and environmental engineering problems. This AutoML virtual assistant163 (VA) enables engineers to carry acCeLErated, siMulation-free, tranSparent, reduced-Order, and infeReNce-based fire resistance analysis with ease and hence is called CLEMSON. At the moment, CLEMSON is in the final stages of development, and more information on its mission and history can be found elsewhere [42]. Still, I would like to briefly present the anatomy behind this VA for two reasons, 1) it sums up most of the notable concepts presented in this book, and 2) it may be of interest to some readers.

# ## 9.6.2 The Rationale and Anatomy of CLEMSON

In many examples of this book, we have seen that traditional (or simple) ML models perform well. As per one of our earlier conversations, the choice behind selecting a ML algorithm often stems from a personal preference. As such, and while the selected model may yield good predictions, this practice does not allow us to explore other models. In an extreme scenario, the developed model may have associated hidden costs with it (i.e., energy-wise, accessibility-wise, etc.). However, and realistically speaking, such models may not be able to adequately attain good training/validation performance (or when deployed) or may not be able to correctly uncover the underlying mechanisms of a given problem.

One way to solve the above problem is to utilize multi-search algorithms and exotic or ensemble models. The idea behind this utilization is simple. The engineer is advised to explore a variety of ML algorithms (especially those incorporating a mixture of architectures, topologies, etc.) in a tournament style. Once fully trained, all models can be ranked according to pre-specified metrics/indicators in a leaderboard.

A key notion to ML belongs to realizing the reasons behind model predictions – especially in our domain. Unlike other traditional methods164 which obey physics and mechanics principles, ML continues to be data-driven. To allow our engineers to peek into the reasoning behind model predictions, there is a need to incorporate explainability.165