
## Machine Learning for Factor Investing
### R Version

Guillaume Coqueret
Tony Guida

![](img/8861a37f775d09b4ba7a5151f604d9f5_0_0.png)

Chapman & Hall/CRC FINANCIAL MATHEMATICS SERIES

## Chapman & Hall/CRC Financial Mathematics Series

### Aims and scope:

The field of financial mathematics forms an ever-expanding slice of the financial sector. This series aims to capture new developments and summarize what is known over the whole spectrum of this field. It will include a broad range of textbooks, reference works and handbooks that are meant to appeal to both academics and practitioners. The inclusion of numerical code and concrete real-world examples is highly encouraged.

### Series Editors

M.A.H. Dempster
Centre for Financial Research
Department of Pure Mathematics and Statistics
University of Cambridge

Dilip B. Madan
Robert H. Smith School of Business
University of Maryland

Rama Cont
Department of Mathematics
Imperial College

- Metamodeling for Variable Annuities
  Guojun Gan and Emiliano A. Valdez

- Modeling Fixed Income Securities and Interest Rate Options
  Robert A. Jarrow

- Financial Modelling in Commodity Markets
  Viviana Fanelli

- Introductory Mathematical Analysis for Quantitative Finance
  Daniele Ritelli, Giulia Spaletta

- Handbook of Financial Risk Management
  Thierry Roncalli

- Optional Processes
  Stochastic Calculus and Applications
  Mohamed Abdelghani, Alexander Melnikov

- Machine Learning for Factor Investing
  R Version
  Guillaume Coqueret and Tony Guida

For more information about this series please visit: https://www.crcpress.com/Chapman-and-HallCRC-Financial-Mathematics-Series/book-series/CHFINANCMTH

First edition published 2021
by CRC Press
6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

and by CRC Press
2 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

© 2021 Taylor & Francis Group, LLC

CRC Press is an imprint of Taylor & Francis Group, LLC

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access www.copyright.com or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact mpkbookpermissions@tandf.co.uk

Trademark notice: Product or corporate names may be trademarks or registered trademarks, and are used only for identification and explanation without intent to infringe.

### Library of Congress Cataloging-in-Publication Data

ISBN: 9780367473228 (hbk)
ISBN: 9780367545864 (pbk)
ISBN: 9781003034858 (ebk)

To Leslie and Selin.

## Taylor & Francis

Taylor & Francis Group
http://taylorandfrancis.com

## Contents

### Preface .................................................................................................... xiii

### I Introduction ............................................................................................... 1

- 1 Notations and data ....................................................................................... 3
  - 1.1 Notations ............................................................................................. 3
  - 1.2 Dataset ................................................................................................. 4

- 2 Introduction ................................................................................................. 9
  - 2.1 Context ................................................................................................. 9
  - 2.2 Portfolio construction: the workflow ................................................... 10
  - 2.3 Machine learning is no magic wand ....................................................... 11

- 3 Factor investing and asset pricing anomalies ........................................... 13
  - 3.1 Introduction ........................................................................................... 14
  - 3.2 Detecting anomalies ................................................................................. 15
    - 3.2.1 Challenges ........................................................................................... 15
    - 3.2.2 Simple portfolio sorts .......................................................................... 15
    - 3.2.3 Factors ............................................................................................... 17
    - 3.2.4 Fama-Macbeth regressions .................................................................... 22
    - 3.2.5 Factor competition ................................................................................ 25
    - 3.2.6 Advanced techniques ............................................................................ 26
  - 3.3 Factors or characteristics? ........................................................................ 27
  - 3.4 Hot topics: momentum, timing and ESG ..................................................... 28
    - 3.4.1 Factor momentum ................................................................................... 28
    - 3.4.2 Factor timing ......................................................................................... 29
    - 3.4.3 The green factors ................................................................................... 30
  - 3.5 The links with machine learning ............................................................... 30
    - 3.5.1 A short list of recent references ........................................................... 31
    - 3.5.2 Explicit connections with asset pricing models ....................................... 31
  - 3.6 Coding exercises ....................................................................................... 34

- 4 Data preprocessing ....................................................................................... 35
  - 4.1 Know your data ......................................................................................... 35
  - 4.2 Missing data ............................................................................................. 38
  - 4.3 Outlier detection ........................................................................................ 40
  - 4.4 Feature engineering ................................................................................... 41
    - 4.4.1 Feature selection .................................................................................... 41
    - 4.4.2 Scaling the predictors ............................................................................. 41
  - 4.5 Labelling ................................................................................................... 42
    - 4.5.1 Simple labels .......................................................................................... 42
    - 4.5.2 Categorical labels .................................................................................... 43
    - 4.5.3 The triple barrier method ....................................................................... 44
    - 4.5.4 Filtering the sample .............................................................................. 45
    - 4.5.5 Return horizons .................................................................................... 46
  - 4.6 Handling persistence ................................................................................ 47
  - 4.7 Extensions ................................................................................................ 47
    - 4.7.1 Transforming features ........................................................................... 47
    - 4.7.2 Macro-economic variables ...................................................................... 48
    - 4.7.3 Active learning ...................................................................................... 48
  - 4.8 Additional code and results ...................................................................... 50
    - 4.8.1 Impact of rescaling: graphical representation ........................................ 50
    - 4.8.2 Impact of rescaling: toy example .......................................................... 52
  - 4.9 Coding exercises ...................................................................................... 53

### II Common supervised algorithms ............................................................ 55

- 5 Penalized regressions and sparse hedging for minimum variance portfolios ............................................................ 57
  - 5.1 Penalized regressions ................................................................................ 57
    - 5.1.1 Simple regressions .............................................................................. 57
    - 5.1.2 Forms of penalizations ........................................................................ 58
    - 5.1.3 Illustrations ....................................................................................... 60
  - 5.2 Sparse hedging for minimum variance portfolios ........................................ 62
    - 5.2.1 Presentation and derivations ................................................................ 62
    - 5.2.2 Example ............................................................................................... 65
  - 5.3 Predictive regressions ................................................................................ 67
    - 5.3.1 Literature review and principle ............................................................ 67
    - 5.3.2 Code and results .................................................................................. 68
  - 5.4 Coding exercise ........................................................................................ 68

- 6 Tree-based methods ....................................................................................... 69
  - 6.1 Simple trees ............................................................................................. 69
    - 6.1.1 Principle ............................................................................................. 69
    - 6.1.2 Further details on classification ............................................................ 71
    - 6.1.3 Pruning criteria .................................................................................... 72
    - 6.1.4 Code and interpretation ........................................................................ 73
  - 6.2 Random forests ......................................................................................... 76
    - 6.2.1 Principle ............................................................................................. 76
    - 6.2.2 Code and results .................................................................................. 78
  - 6.3 Boosted trees: Adaboost ............................................................................. 79
    - 6.3.1 Methodology ........................................................................................ 79
    - 6.3.2 Illustration .......................................................................................... 82
  - 6.4 Boosted trees: extreme gradient boosting .................................................... 82
    - 6.4.1 Managing loss ........................................................................................ 83
    - 6.4.2 Penalization .......................................................................................... 83
    - 6.4.3 Aggregation .......................................................................................... 84
    - 6.4.4 Tree structure ...................................................................................... 85
    - 6.4.5 Extensions ............................................................................................ 86
    - 6.4.6 Code and results .................................................................................. 86
    - 6.4.7 Instance weighting ................................................................................ 88
  - 6.5 Discussion ................................................................................................ 89
  - 6.6 Coding exercises ...................................................................................... 90
