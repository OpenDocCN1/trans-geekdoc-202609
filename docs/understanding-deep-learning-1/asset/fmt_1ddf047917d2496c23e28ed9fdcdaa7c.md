
![](images/9780262048644_FC.jpg)

# Understanding Deep Learning

**Simon J.D. Prince**

The MIT Press  
Cambridge, Massachusetts  
London, England

© 2023 Massachusetts Institute of Technology

This work is subject to a Creative Commons CC-BY-ND-NC license. Subject to such license, all rights are reserved.

![f1-fig-5001.jpg](images/f1-fig-5001.jpg)

The MIT Press would like to thank the anonymous peer reviewers who provided comments on drafts of this book. The generous work of academic experts is essential for establishing the authority and quality of our publications. We acknowledge with gratitude the contributions of these otherwise uncredited readers.

This book was set in Latin Modern Roman by B. Jackowski and J. M. Nowacki (on behalf of TeX users groups). Printed and bound in Canada.

Library of Congress Cataloging-in-Publication Data is available.

ISBN: 978-0-262-04864-4

10 9 8 7 6 5 4 3 2 1

*This book is dedicated to Blair, Calvert, Coppola, Ellison, Faulkner, Kerpatenko, Morris, Robinson, Sträussler, Wallace, Waymon, Wojnarowicz, and all the others whose work is even more important and interesting than deep learning.*

# Contents

1.  [Preface](#c000a.xhtml#f2-title-0001)
2.  [Acknowledgments](#c000b.xhtml#f3-title-0001)
3.  [Chapter 1: Introduction](#c001.xhtml#c1-title-0001)
4.  [Chapter 2: Supervised learning](#c002.xhtml#c2-title-0001)
5.  [Chapter 3: Shallow neural networks](#c003.xhtml#c3-title-0001)
6.  [Chapter 4: Deep neural networks](#c004.xhtml#c4-title-0001)
7.  [Chapter 5: Loss functions](#c005.xhtml#c5-title-0001)
8.  [Chapter 6: Fitting models](#c006.xhtml#c6-title-0001)
9.  [Chapter 7: Gradients and initialization](#c007.xhtml#c7-title-0001)
10. [Chapter 8: Measuring performance](#c008.xhtml#c8-title-0001)
11. [Chapter 9: Regularization](#c009.xhtml#c9-title-0001)
12. [Chapter 10: Convolutional networks](#c010.xhtml#c10-title-0001)
13. [Chapter 11: Residual networks](#c011.xhtml#c11-title-0001)
14. [Chapter 12: Transformers](#c012.xhtml#c12-title-0001)
15. [Chapter 13: Graph neural networks](#c013.xhtml#c13-title-0001)
16. [Chapter 14: Unsupervised learning](#c014.xhtml#c14-title-0001)
17. [Chapter 15: Generative Adversarial Networks](#c015.xhtml#c15-title-0001)
18. [Chapter 16: Normalizing flows](#c016.xhtml#c16-title-0001)
19. [Chapter 17: Variational autoencoders](#c017.xhtml#c17-title-0001)
20. [Chapter 18: Diffusion models](#c018.xhtml#c18-title-0001)
21. [Chapter 19: Reinforcement learning](#c019.xhtml#c19-title-0001)
22. [Chapter 20: Why does deep learning work?](#c020.xhtml#c20-title-0001)
23. [Chapter 21: Deep learning and ethics](#c021.xhtml#c21-title-0001)
24. [Appendix A: Notation](#c022.xhtml#b1-title-0001)
25. [Appendix B: Mathematics](#c023.xhtml#b2-title-0001)
26. [Appendix C: Probability](#c024.xhtml#b3-title-0001)
27. [Bibliography](#c444.xhtml#b4-title-0001)
28. [Index](#c555.xhtml#b5-title-0001)

# Preface

The history of deep learning is unusual in science. The perseverance of a small cabal of scientists, working over twenty-five years in a seemingly unpromising area, has revolutionized a field and dramatically impacted society. Usually, when researchers investigate an esoteric and apparently impractical corner of science or engineering, it remains just that — esoteric and impractical. However, this was a notable exception. Despite widespread skepticism, the systematic efforts of Yoshua Bengio, Geoffrey Hinton, Yann LeCun, and others eventually paid off.

The title of this book is “Understanding Deep Learning” to distinguish it from volumes that cover coding and other practical aspects. This text is primarily about the *ideas* that underlie deep learning. The first part of the book introduces deep learning models and discusses how to train them, measure their performance, and improve this performance. The next part considers architectures that are specialized to images, text, and graph data. These chapters require only introductory linear algebra, calculus, and probability and should be accessible to any second-year undergraduate in a quantitative discipline. Subsequent parts of the book tackle generative models and reinforcement learning. These chapters require more knowledge of probability and calculus and target more advanced students.

The title is also partly a joke — *no-one* really understands deep learning at the time of writing. Modern deep networks learn piecewise linear functions with more regions than there are atoms in the universe and can be trained with fewer data examples than model parameters. It is neither obvious that we should be able to fit these functions reliably nor that they should generalize well to new data. The penultimate chapter addresses these and other aspects that are not yet fully understood. Regardless, deep learning will change the world for better or worse. The final chapter discusses AI ethics and concludes with an appeal for practitioners to consider the moral implications of their work.

Your time is precious, and I have striven to curate and present the material so you can understand it as efficiently as possible. The main body of each chapter comprises a succinct description of only the most essential ideas, together with accompanying illustrations. The appendices review all mathematical prerequisites, and there should be no need to refer to external material. For readers wishing to delve deeper, each chapter has associated problems, Python notebooks, and extensive background notes.

Writing a book is a lonely, grinding, multiple-year process and is only worthwhile if the volume is widely adopted. If you enjoy reading this or have suggestions for improving it, please contact me via the accompanying website. I would love to hear your thoughts, which will inform and motivate subsequent editions.

# Acknowledgments
