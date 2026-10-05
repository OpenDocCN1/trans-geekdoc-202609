
IOP Series in Quantum Technology

## Quantum Machine Learning
### Concepts and possibilities

Andrea Delgado
Kathleen E Hamilton

![](img/7dbe239d4cc1f635a551b6e06f3d3df_0_0.png)

## Quantum Machine Learning
### Concepts and possibilities

Online at: https://doi.org/10.1088/978-0-7503-4952-9

IOP Series in Quantum Technology

**Series Editor: Barry Garraway (School of Mathematical and Physical Sciences, University of Sussex, UK), Barry Sanders (Institute for Quantum Science and Technology, University of Calgary, Canada) and Lincoln Carr (Quantum Engineering Program, Colorado School of Mines, USA)**

# About the Series

The IOP Series in Quantum Technology is dedicated to bringing together the most up to date texts and reference books from across the emerging field of quantum science and its technological applications. By prepared leading experts, the series is intended for graduate students and researchers either already working in or intending to extend the field. The series seeks (but is not restricted to) publications in the following topics:

- Quantum biology
- Quantum communication
- Quantum computation
- Quantum control
- Quantum cryptography
- Quantum engineering
- Quantum machine learning and intelligence
- Quantum materials
- Quantum metrology
- Quantum optics
- Quantum sensing
- Quantum simulation
- Quantum software, algorithms and code
- Quantum thermodynamics
- Hybrid quantum systems

A list of recent titles published in this series can be found here: https://iopscience.iop.org/bookListInfo/iop-series-in-quantum-technology.

## Quantum Machine Learning
### Concepts and possibilities

Andrea Delgado
Physics Division, Oak Ridge National Laboratory, Oak Ridge, TN, USA

Kathleen E Hamilton
Computational Sciences and Engineering Division, Oak Ridge National Laboratory,
Oak Ridge, TN, USA

IOP Publishing, Bristol, UK

© IOP Publishing Ltd 2025. All rights, including for text and data mining (TDM), artificial intelligence (AI) training, and similar technologies, are reserved.

This book is available under the terms of the [IOP-Standard Books License]( )

No part of this publication may be reproduced, stored in a retrieval system, subjected to any form of TDM or used for the training of any AI systems or similar technologies, transmitted in any form or by any electronic, mechanical, photocopying, recording or otherwise, without the prior permission of the publisher, or as expressly permitted by law or under terms agreed with the appropriate rights organization. Certain types of copying may be permitted in accordance with the terms of licences used by the Copyright Licensing Agency, the Copyright Centre and other reproduction organizations.

Permission to make use of IOP Publishing content other than set out above may be sought at permissions@ioppublishing.org.

Andrea Delgado and Kathleen E Hamilton have asserted their right to be identified as the authors of this work in accordance with sections 77 and 78 of the Copyright, Designs and Patents Act 1988.

- ISBN 978-0-7503-4952-9 (ebook)
- ISBN 978-0-7503-4950-5 (print)
- ISBN 978-0-7503-4953-6 (myPrint)
- ISBN 978-0-7503-4951-2 (mobi)

DOI 10.1088/978-0-7503-4952-9

Version: 20251201

IOP ebooks British Library Cataloguing Data: A catalogue record for this book is available from the British Library, wholly owned by The Institute of Physics, London, Distillery, Avon Street, Bristol, BS1 0GR, IOP Publishing, Inc., 190 North Independence Mall, Suite 601, Philadelphia, PA 19106.

## Contents

- Preface x
- 1 Introduction 1-1
- 1.1 Motivation and scope 1-1
- 1.2 The promise of quantum machine learning 1-2
- 1.3 Quantum computing: a refresher 1-3
- 1.4 Machine learning foundations 1-4
- 1.5 Types of quantum machine learning 1-5
- References 1-7
- 2 Quantum information processing 2-1
- 2.1 Quantum computing 2-1
- 2.2 notation 2-3
- 2.3 Bloch sphere 2-3
- 2.4 The interpretation 2-4
- 2.5 Quantum gates and circuits 2-5
- 2.5.1 Quantum gates 2-5
- 2.5.2 Deutsch-Jozsa algorithm 2-6
- 2.6 Grover’s algorithm 2-7
- 2.6.1 Problem statement 2-7
- 2.6.2 Algorithm overview 2-8
- 2.6.3 Interpretation of results 2-8
- 2.6.4 Significance 2-8
- 2.7 Grover’s algorithm 2-8
- 2.7.1 Problem statement 2-8
- 2.7.2 Algorithm overview 2-9
- 2.7.3 Mathematical insight 2-9
- 2.7.4 Significance 2-10
- 2.8 Summary 2-10
- References 2-10
- 3 Information encoding 3-1
- 3.1 Bridging two realms 3-2
- 3.2 Encoding schemes for quantum machine learning 3-4
- 3.2.1 Amplitude encoding 3-4
- 3.2.2 Angle/parametric encoding 3-5
- 3.2.3 Basis encoding 3-5
- 3.2.4 Hamiltonian encoding 3-5
- 3.3 Quantum autoencoders 3-7
- 3.3.1 Circuit construction 3-7
- 3.3.2 Applications and relevance 3-8
- 3.4 Quantum data 3-8
- 3.4.1 Definition and representations 3-9
- 3.4.2 Sources of quantum data 3-9
- 3.4.3 Quantum learning from data 3-10
- 3.4.4 Implications for encoding 3-10
- 3.5 Practical considerations for quantum encoding 3-11
- 3.6 Summary 3-12
- References 3-13
- 4 Quantum computing for inference 4-1
- 4.1 Classical foundations of inference 4-2
- 4.1.1 Supervised learning basics 4-2
- 4.1.2 Feature maps and kernels in classical machine learning 4-2
- 4.1.3 Kernel methods 4-3
- 4.1.4 Theoretical guarantees 4-3
- 4.2 Quantum feature maps 4-4
- 4.2.1 Quantum states as features 4-4
- 4.2.2 Data encodings for quantum feature maps 4-5
- 4.2.3 Properties of quantum feature maps 4-5
- 4.3 Quantum kernels and kernel methods 4-6
- 4.3.1 Quantum kernel definition 4-6
- 4.3.2 Evaluating quantum kernels 4-7
- 4.3.3 Training with quantum kernels 4-7
- 4.3.4 Generalization and expressivity 4-7
- 4.4 Linear quantum models 4-8
- 4.4.1 Parameterized quantum circuits for classification 4-8
- 4.4.2 Training strategies 4-9
- 4.4.3 Example: variational quantum classifier 4-9
- 4.5 Performance and benchmarks 4-10
- 4.5.1 Theoretical speedups and limitations 4-10
- 4.5.2 Empirical studies and benchmarks 4-10
- 4.5.3 Robustness and noise considerations 4-11
- 4.6 Case studies and applications 4-11
- 4.6.1 Drug discovery and molecular property prediction 4-12
- 4.6.2 High energy physics 4-12
- 4.7 Open challenges and future directions 4-13
- 4.7.1 Scalability and resource constraints 4-13
- 4.7.2 Design of quantum feature maps 4-14
- 4.7.3 Robustness and error mitigation 4-14
- 4.7.4 Learning theory and generalization bounds 4-14
- 4.7.5 Hybrid quantum-classical workflows 4-15
- 4.8 Summary 4-15
- References 4-16
- 5 Quantum variational optimization 5-1
- 5.1 Model description 5-2
- 5.1.1 Variational quantum eigensolver 5-2
- 5.1.2 Quantum approximate optimization algorithm 5-3
- 5.2 Case studies and applications 5-4
- 5.2.1 Quantum chemistry and materials science 5-4
- 5.2.2 Combinatorial optimization 5-4
- 5.2.3 Quantum machine learning 5-5
- 5.2.4 Quantum control and metrology 5-6
- 5.2.5 Quantum dynamics 5-6
- 5.3 Open challenges and future directions 5-6
- 5.4 Summary 5-9
- 6 Variational classifiers and neural networks 6-1
- 6.1 Model description 6-2
- 6.1.1 Quantum neural networks 6-2
- 6.1.2 Parameterized quantum circuits as learning models 6-3
- 6.2 Backpropagation and gradient estimation 6-4
- 6.2.1 Quantum computational graphs 6-5
- 6.2.2 Parameter-shift rule 6-7
- 6.2.3 Generalized parameter-shift rule 6-8
- 6.2.4 Finite differences and simultaneous perturbation 6-10
- 6.2.5 Adjoint differentiation (simulators only) 6-12
- 6.2.6 Quantum natural gradient and the quantum geometric tensor 6-13
- 6.2.7 Comparison to the classical natural gradient 6-15
- 6.2.8 Gradients for mixed states, noisy channels, and open-system dynamics 6-15
- 6.2.9 Gradient variance, shot noise, and batching 6-17
- 6.2.10 Loss landscapes and barren plateaus 6-19
- 6.2.11 Intuition behind barren plateaus 6-19
- 6.3 Architectural variants: QCNNs and quantum graph-based models 6-20
- 6.3.1 Quantum convolutional neural networks 6-21
- 6.3.2 Quantum graph neural networks 6-22
- 6.4 Open challenges and future directions 6-24
- 6.4.1 Trainability and optimization 6-24
- 6.4.2 Resource overhead and compilation 6-24
- 6.4.3 Generalization and inductive bias 6-25
- 6.4.4 Benchmarking and expressivity analysis 6-25
- 6.4.5 Opportunity in co-design 6-25
- 6.5 Summary 6-25
- References 6-26
- 7 Quantum generative models 7-1
- 7.1 Classical generative models 7-2
- 7.1.1 Boltzmann machines and energy-based models 7-2
- 7.1.2 Deep generative models 7-3
- 7.2 Quantum generative models 7-4
- 7.2.1 Quantum Boltzmann machines 7-5
- 7.2.2 Quantum circuit Born machines 7-7
- 7.2.3 Quantum generative adversarial machines 7-8
- 7.2.4 Quantum variational autoencoders 7-8
- 7.3 Expressivity and learning power 7-8
- 7.3.1 Defining expressivity 7-9
- 7.3.2 Factors affecting expressivity 7-9
- 7.3.3 Trade-off with trainability 7-10
- 7.4 Training quantum generative models 7-10
- 7.4.1 The optimization loop 7-10
- 7.4.2 Loss functions 7-11
