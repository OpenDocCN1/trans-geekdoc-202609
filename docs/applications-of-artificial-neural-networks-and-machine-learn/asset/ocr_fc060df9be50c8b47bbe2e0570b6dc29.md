# # Chapter 2
Buckling Resistance Prediction
of High-Strength Steel Columns Using
Metaheuristic-Trained Artificial Neural
Networks

**Abstract** This chapter aims to develop practical metaheuristic-trained Artificial Neural Networks to predict the ultimate buckling load of High Strength Steel columns. The section height, flange width, web thickness, flange thickness, and steel yield strength are considered the input variables, while the ultimate buckling load was assumed to be the only output variable. ANN models are trained through algorithms such as LM, BR, and SCG; Four metaheuristic algorithms, namely Particle Swarm Optimization, Colliding Body Optimization, and their developed versions are used for efficient training of the ANNs.

# ## 2.1 Introduction

In this chapter buckling resistance prediction of high-strength steel columns is performed using metaheuristic-trained artificial neural networks [1]. The recent advances in steel production procedures have provided the engineering community with steel grades known for better characteristics, such as excellent toughness or high nominal yield stress (higher than 420 MPa), thus allowing for the greater use of high-strength steel (HSS). The use of HSS results in a significant decrease in the weight of structures; however, their stability requires to be thoroughly checked, particularly for compression elements where flexural buckling is commonly the major factor in design. The current design codes for HSS columns are based on experiments on normal-strength steel (NSS) materials because there were no tests done for HSS materials when the codes were established. As an example, EN 1993-1-12 (2007) regulations [2], which are for steel grade materials up to S700, rely on buckling resistance curves based on the Ayrton-Perry type formulation that was developed through an extensive experimental program for NSS members conducted by the European Convention for Constructional Steelwork (ECCS), theoretical formulations obtained from the analysis of experimental results, and a reliability assessment employing Monte Carlo simulations.

The present regulations in Eurocode 3 for HSS columns [2] are basically an extended version of the design rules for NSS columns, and the buckling resistance