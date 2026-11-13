Another set of questions that could also arise includes: other things constant [Ceteris Paribus] would Beam A have failed if it was not for the applied loading? would this beam fail at 361.6 kN.m had it been made of a W18 × 40 section or Grade A36? These are a special type of causal question, referred to as counterfactuals. Both causal and counterfactual questions need to be answered causally.12

Building on what a civil and environmental engineer might learn early in their second year of school (in a mechanics course), we know that moment capacity (or simply, the resistance) of a W-shaped steel beam under bending is a function of its geometric features; conveniently lumped into the plastic modulus, Z, as well as its material features; represented by the yield strength of steel, f_y. Both Z and f_y are tied into Equation 8.1. Equation 8.1 conveys that both Z and f_y contribute to the moment capacity in a complimentary (equal) manner.

```
Resistance = Z × f_y
```

Not surprisingly, the same equation allows us to answer all the above questions intuitively. For instance:

+   1) What has caused the failure of Beam A?
+   Ans. The effect of a bending moment that exceeds the level of moment capacity – and hence the equality.
+   
+   2) Was failure triggered by the geometric configurations or material properties of Beam A?
+   Ans. Building on Equation 8.1, both Z and f_y have contributed equally.
+   
+   3) Ceteris Paribus, could Beam A have failed if it was not for the presence of the bending moment?
+   Ans. No. Since if it was not for such loading, the capacity (resistance) of the beam would not have been exceeded.
+   
+   4) Ceteris Paribus, would Beam A have failed if it was not for the applied loading? Would this beam fail at 361.6 kN.m if it had been a W18 × 40? Or had it been made from Grade A36?
+   Ans. No. Without the loading, there would not have been a bending moment. Also, W18 × 40 has a larger plastic modulus than W16 × 36, and Grade 36 has lower yield strength than Grade A992.

As you can see, my answers to these four questions are somewhat trivial.13 This simplicity stems from the narrow space of parameters involved in the phenomenon of flexural failure in W-shaped steel beams. More directly, the answers seem trivial because we can visualize 14 and imagine each answer as the outcome of an experiment.

Let us extend the same exercise to beams of complex shapes, made from hybrid material grades or those supported by mixed restraints. Repeating the same exercise is still doable but might require us to use a bit more horsepower15 to get to an answer.

However, what if we now extend the same exercise to a phenomenon that we do not have a working model for, one that we do not have an equation for, or one that we cannot as easily visualize.16 It is clear that the subject of causality exponentially grows with the addition of higher dimensions and/or problems we lack domain knowledge of.

# 8.3 Re-visiting Statistics and ML

The majority of the time, the outcomes of our investigations are examined through statistical methods. In such examination, we may implicitly assume that statistical methods are applicable to our data/observations17. In reality, preset assumptions and requirements with regard to data size, distribution, quality, etc., must be met17 [5]. If one or more assumptions