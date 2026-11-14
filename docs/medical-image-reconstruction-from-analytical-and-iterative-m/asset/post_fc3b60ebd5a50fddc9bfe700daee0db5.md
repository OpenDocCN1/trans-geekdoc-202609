

Gengsheng Lawrence Zeng

## Medical Image Reconstruction

### From Analytical and Iterative Methods to Machine Learning

2nd Edition

DE GRUYTER

## Also of interest

- Medical Physics
  Hartmut Zabel, 2023
  Volume 1 Physical Aspects of the Human Body
  ISBN 978-3-11-075691-3, e-ISBN (PDF) 978-3-11-075695-1

- Medical Physics
  Hartmut Zabel, 2023
  Volume 2 Physical Aspects of Diagnostics
  ISBN 978-3-11-075702-6, e-ISBN (PDF) 978-3-11-075709-5

- Medical Physics
  Hartmut Zabel, 2023
  Volume 3 Physical Aspects of Therapeutics
  ISBN 978-3-11-116867-8, e-ISBN (PDF) 978-3-11-116873-9

- Numerical Methods with Python for the Sciences
  William Miles, 2023
  ISBN 978-3-11-077645-4, e-ISBN (PDF) 978-3-11-077664-5

- Multi-level Mixed-Integer Optimization: Parametric Programming Approach
  Styliani Avraamidou, Efstratios Pistikopoulos, 2022
  ISBN 978-3-11-076030-9, e-ISBN (PDF) 978-3-11-076031-6

**Author**
Prof. Dr. Gengsheng Lawrence Zeng
Department of Computer Science
Utah Valley University
Orem, UT 84058
USA
larry.zeng@uvu.edu

Department of Radiology and Imaging Sciences
University of Utah
Salt Lake City, UT 84108
USA
larry.zeng@hsc.utah.edu

ISBN 978-3-11-105503-9
e-ISBN (PDF) 978-3-11-105540-4
e-ISBN (EPUB) 978-3-11-105570-1

**Library of Congress Control Number: 2023933613**

**Bibliographic information published by the Deutsche Nationalbibliothek**
The Deutsche Nationalbibliothek lists this publication in the Deutsche Nationalbibliografie; detailed bibliographic data are available on the Internet at http://dnb.dnb.de.

© 2023 Walter de Gruyter GmbH, Berlin/Boston
Cover image: m_pavlov/iStock/Getty Images Plus
Typesetting: Integra Software Services Pvt. Ltd.
Printing and binding: CPI books GmbH, Leck
www.degruyter.com

## In loving memory of my parents

Yuqing Lu and Yiduo Zeng

## To my family

- Ya Li
- Andrew Fang
- Kathy Fang
- Megan Zeng

## Preface

This tutorial text introduces the classical and modern image reconstruction technologies to the general audience. It covers the topics in two-dimensional parallel-beam and fan-beam imaging, and three-dimensional parallel ray, parallel plane, and cone-beam imaging. Both analytical and iterative methods are presented. The applications in X-ray CT (computed tomography), single-photon emission computed tomography, positron emission tomography, and magnetic resonance imaging are also discussed. Contemporary research results in exact region-of-interest reconstruction with truncated projections, Katsevich’s cone-beam filtered backprojection (FBP) algorithm, and reconstruction with highly undersampled data are also included in this book.

Chapter 8 of the book is devoted to the techniques of using a fast analytical FBP algorithm to emulate an iterative reconstruction with an edge-preserving denoising constraint. These techniques are the author’s most recent research results, and the author also produced CT images of some patients leading to the third place winner of the 2016 Low-Dose CT Grand Challenge.

This book is written in an easy-to-read style. The readers who intend to get into medical image reconstruction will gain the general knowledge of the field in a painless way. I hope you enjoy reading it as much as I enjoy writing (and drawing) it.

Larry Zeng, Ph.D. (larry.zeng@uvu.edu, larry.zeng@hsc.utah.edu)
Professor of Computer science, Utah Valley University, Orem, Utah, USA
Adjunct Professor of Radiology and Imaging science, University of Utah, Salt Lake City, Utah, USA

August 8, 2016, in Salt Lake City

## Contents

- Preface — VII
- 1 Basic principles of tomography — 1
  - 1.1 Tomography — 1
  - 1.2 Projection — 3
  - 1.3 Image reconstruction — 6
  - 1.4 Backprojection — 8
  - 1.5 Mathematical expressions — 9
    - 1.5.1 Projection — 9
    - 1.5.2 Backprojection — 10
    - 1.5.3 The Dirac δ-function — 12
  - 1.6 Worked examples — 14
  - 1.7 Summary — 18
  - Problems — 18
  - Bibliography — 19
- 2 Parallel-beam image reconstruction — 20
  - 2.1 Fourier transform — 20
  - 2.2 Central slice theorem — 21
  - 2.3 Reconstruction algorithms — 23
    - 2.3.1 Method 1 — 24
    - 2.3.2 Method 2 — 24
    - 2.3.3 Method 3 — 26
    - 2.3.4 Method 4 — 26
    - 2.3.5 Method 5 — 26
    - 2.3.6 Method 6 — 27
  - 2.4 A computer simulation — 28
  - 2.5 ROI reconstruction with truncated projections — 29
  - 2.6 Mathematical expressions — 34
    - 2.6.1 The Fourier transform and convolution — 34
    - 2.6.2 The Hilbert transform and the finite Hilbert transform — 35
    - 2.6.3 Proof of the central slice theorem — 37
    - 2.6.4 Derivation of the FBP algorithm — 38
    - 2.6.5 Expression of the convolution backprojection algorithm — 39
    - 2.6.6 Expression of the Radon inversion formula — 40
    - 2.6.7 Derivation of the backprojection-then-filtering algorithm — 40
    - 2.6.8 Expression of the derivative-backprojection-Hilbert transform algorithm — 41
    - 2.6.9 Derivation of the backprojection-derivative-Hilbert transform algorithm — 42
  - 2.7 Worked examples — 42
  - 2.8 Summary — 49
  - Problems — 50
  - Bibliography — 50
- 3 Fan-beam image reconstruction — 52
  - 3.1 Fan-beam geometry and the point spread function — 52
  - 3.2 Parallel-beam to fan-beam algorithm conversion — 55
  - 3.3 Short scan — 57
  - 3.4 Mathematical expressions — 59
    - 3.4.1 Derivation of a filtered backprojection fan-beam algorithm — 60
    - 3.4.2 A fan-beam algorithm using the derivative and the Hilbert transform — 61
    - 3.4.3 Expression for the Parker weights — 63
    - 3.4.4 Errors caused by finite bandwidth implementation — 64
  - 3.5 Worked examples — 65
  - 3.6 Summary — 68
  - Problems — 69
  - Bibliography — 69
- 4 Transmission and emission tomography — 71
  - 4.1 X-ray computed tomography — 71
  - 4.2 Positron emission tomography and single-photon emission computed tomography — 75
  - 4.3 Noise propagation in reconstruction — 78
    - 4.3.1 Noise variance of emission data — 78
    - 4.3.2 Noise variance of transmission data — 79
    - 4.3.3 Noise propagation in an FBP algorithm — 79
  - 4.4 Attenuation correction for emission tomography — 80
    - 4.4.1 PET — 80
    - 4.4.2 SPECT: Tretiak-Metz FBP algorithm for uniform attenuation — 81
    - 4.4.3 SPECT: Inouye's algorithm for uniform attenuation — 83
  - 4.5 Mathematical expressions — 85
    - 4.5.1 Expression for Tretiak-Metz FBP algorithm — 85
    - 4.5.2 Derivation for Inouye's algorithm — 85
    - 4.5.3 Rullgård's derivative-then-backprojection algorithm for uniform attenuation — 87
    - 4.5.4 Novikov-Natterer FBP algorithm for nonuniform attenuation SPECT — 88
  - 4.6 Worked examples — 89
  - 4.7 Summary — 91
  - Problems — 91
  - Bibliography — 92
- 5 Three-dimensional image reconstruction — 94
  - 5.1 Parallel line-integral data — 94
    - 5.1.1 Backprojection-then-filtering — 96
    - 5.1.2 Filtered backprojection — 98
  - 5.2 Parallel plane-integral data — 98
  - 5.3 Cone-beam data — 100
    - 5.3.1 Feldkamp's algorithm — 101
    - 5.3.2 Grangeat's algorithm — 102
    - 5.3.3 Katsevich's algorithm — 104
  - 5.4 Mathematical expressions — 108
    - 5.4.1 Backprojection-then-filtering for parallel line-integral data — 108
    - 5.4.2 FBP algorithm for parallel line-integral data — 109
    - 5.4.3 Three-dimensional Radon inversion formula (FBP algorithm) — 112
    - 5.4.4 Three-dimensional backprojection-then-filtering algorithm for Radon data — 113
    - 5.4.5 Feldkamp's algorithm — 113
    - 5.4.6 Tuy's relationship — 114
    - 5.4.7 Grangeat's relationship — 117
    - 5.4.8 Katsevich's algorithm — 119
  - 5.5 Radon transform and ray transform in n dimensions — 125
  - 5.6 Worked examples — 126
  - 5.7 Summary — 129
  - Problems — 130
  - Bibliography — 130
- 6 Iterative reconstruction — 133
  - 6.1 Solving a system of linear equations — 133
  - 6.2 Algebraic reconstruction technique — 138
  - 6.3 Gradient descent algorithms — 139
    - 6.3.1 The gradient descent algorithm — 139
    - 6.3.2 The Landweber algorithm — 141
    - 6.3.3 The conjugate gradient algorithm — 142
  - 6.4 ML-EM algorithms — 143
  - 6.5 OS-EM algorithm — 144
  - 6.6 Noise handling — 144
    - 6.6.1 Analytical methods: windowing — 145
    - 6.6.2 Iterative methods: stopping early — 145
    - 6.6.3 Iterative methods: choosing pixels — 146

