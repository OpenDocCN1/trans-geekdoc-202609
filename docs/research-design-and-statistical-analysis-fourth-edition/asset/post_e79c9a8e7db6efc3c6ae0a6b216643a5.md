
# Caren M. Rotello, Jerome L. Myers, Arnold D. Well and Robert F. Lorch, Jr.

# Research Design and Statistical Analysis

FOURTH EDITION

![](img/53d3130502f4ff3b15cbe3697d6e8c5a_0_0.png)

“Having worn out the 3rd edition to the point of disintegration, I was pleased to learn of this new edition. The authors have elevated the book to new heights by Rotello’s lucid and precise expository narrative and the incorporation of R.”

Chad Dubé, Associate Professor of Psychology,
University of South Florida, USA

“Exploring advanced statistical analysis alongside robust research principles, this rigorous yet accessible text prepares students for practical applications through real-world examples and R/SPSS integration—purpose-built for a full-year curriculum.”

Michael J. Hautus, Professor of Psychology,
University of Auckland, New Zealand

Students of psychological methods must develop a skillset that allows them to design, conduct, and analyze data from research studies with the level of care required to arrive at sound statistical inference. Research Design and Statistical Analysis by Rotello, Myers, Well, and Lorch guides researchers in this journey by discussing the complex topics needed to develop these skills in a comprehensive, yet comprehensible, manner. Their approach uses clear and focused writing to build students’ understanding of concepts ranging from the most basic research designs, descriptive statistics, and hypothesis testing methods to more complex matters, such as repeated-measures designs, the use of covariates, and contrast testing. I also appreciate how the authors introduce students to the use of statistical software packages, such as SPSS and R, in their work. However, it is much rarer that a textbook balances both computational instruction and the information needed to use statistical software packages in a responsible manner. By exposing students to the assumptions underlying design and analysis choices, as well as common errors in data analysis and inference, Rotello, Myers, Well, and Lorch guides researchers into the issues they should be considering before making judgments with only a ‘point-and-click’ summary of results. The third edition of the text was my first formal introduction to methods and over 10 years later, it’s still the first book I reach for whether I am double-checking my methodological understanding of a complex topic in my work or am recommending a must-have reference for an aspiring researcher.

Ryan Guggenmos, Associate Professor of Accounting and
Cramer Research Fellow, Darla Moore School
of Business, University of South Carolina, USA

![](img/53d3130502f4ff3b15cbe3697d6e8c5a_2_0.png)

# Research Design and Statistical Analysis

This fully updated fourth edition of Research Design and Statistical Analysis provides comprehensive coverage of the design principles and statistical concepts necessary to make sense of real data. The guiding philosophy is to provide a strong conceptual foundation that readers can generalize to new situations they encounter in their research, including new developments in data analysis.

Key features:

- Emphasis on basic concepts such as sampling distributions, design efficiency, and expected squares, relating the research designs and data analyses to the statistical models that underlie the analyses.
- Detailed instructions on performing analysis using both R and SPSS.
- Pedagogical exercises mapped to key topic areas to support students as they review their understanding and strive to reach their higher learning goals.

Incorporating the analyses of both experimental and observational data, and with coverage that is broad and deep enough to serve a two-semester sequence, this textbook is suitable for researchers, graduate students, and advanced undergraduates in psychology, education, and other behavioral, social, and health sciences.

The book is supported by a robust set of digital resources, including data files and exercises from the book in an Excel format for import into R or SPSS; R scripts for running example analysis and generating figures; and a solutions manual.

Karen M. Rotello is Professor Emeritus at the University of Massachusetts Amherst. She received her PhD in psychology from Stanford University.

Jerome L. Myers is Professor Emeritus at the University of Massachusetts Amherst. He received his PhD in psychology from the University of Wisconsin.

Arnold D. Well is Professor Emeritus at the University of Massachusetts Amherst. He received his PhD in experimental psychology from the University of Oregon.

Robert F. Lorch, Jr. is Professor Emeritus at the University of Kentucky. He received his PhD in psychology from the University of Massachusetts Amherst.

![](img/53d3130502f4ff3b15cbe3697d6e8c5a_4_0.png)

# Research Design and
Statistical Analysis

Fourth Edition

Caren M. Rotello, Jerome L. Myers,
Arnold D. Well and Robert F. Lorch, Jr.

![](img/53d3130502f4ff3b15cbe3697d6e8c5a_5_0.png)

Designed image: caroscastilla by Getty Images

Fourth edition published 2025

by Routledge
605 Third Avenue, New York, NY 10158

and by Routledge
4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

Routledge is an imprint of the Taylor & Francis Group, an informa business

© 2025 Karen M. Rotello, Jerome L. Myers, Arnold D. Well and Robert F. Lorch, Jr.
The right of Karen M. Rotello, Jerome L. Myers, Arnold D. Well and
Robert F. Lorch, Jr. to be identified as authors of this work has been asserted
in accordance with sections 77 and 78 of the Copyright, Designs and Patents
Act 1988.

All rights reserved. No part of this book may be reprinted or reproduced
utilized in any form or by any electronic, mechanical, or other means, now known
or hereto invented, including photocopying and recording, or in any information
store or retrieval system, without permission in writing from the publishers.

Trademark notice: Product or corporate names may be trademarks or registered
trademarks and are used only for identification and explanation without intent to
ring.

First edition published by Erbaum Associates 1995
Third edition published by Routledge 2010

Library of Congress Catalog-in-Publication Data
Names: Rotello, Karen M., author.; Myers, Jerome L., author. | Well, W. A. (Arnold),
author.; | Lorch, Robert Frederick, 1952–author.

Title: Design and statistical analysis / Karen M. Rotello, Jerome L. Myers,
Arnold D. Well and Robert F. Lorch, Jr.
Description: Fourth edition. New York, NY : Routledge, 2025. |
Indexes: bibliographic references and index.
Identifiers: LCCN 2024029026 (print) | LCCN 2024029027 (ebook) |
ISBN 9781032592107 (hardback) | ISBN 9781032897288 (paperback) |
ISBN 9781032533550 (ebook)
Subject: LCC: Experimental design. | Mathematical statistics.
Classification: LCC QA279.M933 2025 (print) | LCC QA279 (ebook) |
DDC 519.9–dc23/2024029026
LC record available at https://lccn.loc.gov/2024029026
LC-ebook record available at https://lccn.loc.gov/2024029027

ISBN: 978-1-032-59210-7 (bbk)
ISBN: 978-1-032-89728-8 (pbk)
ISBN: 978-1-032-53355-0 (ebk)
DOI: 10.4324/9781032543550

Typeset in Sabon
by Apex CoVantage, LLC

Access the Support Material: www.routledge.com/9781032897288

# Contents

Preface xv
Acknowledgments xix

# PART 1
### Foundations of Research Design and Data Analysis 1

- 1 Planning the Research 3
    1.1 Overview 3
    1.2 The Independent Variable 4
    1.3 The Dependent Variable 6
    1.4 The Participant Population 7
    1.5 Nuisance Variables 8
    1.6 Research Design 10
    1.7 Statistical Analyses 15
    1.8 Generalizing Conclusions 16
    1.9 Summary 17

- 2 Describing the Data 20
    2.1 Overview 20
    2.2 Graphical Summaries of the Data 21
    2.3 Numerical Summaries of the Data 28
    2.4 Standardized (z) Scores 35
    2.5 Measures of the Shape of a Distribution: Skewness and Kurtosis 37
    2.6 Comparing Two Data Sets 39
    2.7 Relationships Among Quantitative Variables 42
    2.8 Summary 45

- 3 Basic Concepts in Probability 49
    3.1 Overview 49
    3.2 Basic Concepts for Analyzing the Structure of Events 50
