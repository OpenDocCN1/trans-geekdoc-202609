
## DATA SCIENCE SERIES

## TREE-BASED METHODS FOR STATISTICAL LEARNING IN R

![](img/2c227bfb3620dc3d159fa5e6598afa30_0_0.png)

## BRANDON M. GREENWELL

CRC Press
Taylor & Francis Group
A CHAPMAN & HALL BOOK

## Tree-Based Methods for Statistical Learning in R

The book follows up most ideas and mathematical concepts with code-based examples in the R statistical language; with an emphasis on using as few external packages as possible. For example, users will be exposed to writing their own random forest and gradient tree boosting functions using simple for loops and basic tree fitting software (like **rpart** and **party/partykit**), and more. The core chapters also end with a detailed section on relevant software in both R and other open source alternatives (e.g., Python, Spark, and Julia), and example usage on real data sets. While the book mostly uses R, it is meant to be equally accessible and useful to non-R programmers.

Consumers of this book will have gained a solid foundation (and appreciation) for tree-based methods and how they can be used to solve practical problems and challenges data scientists often face in applied work.

Features:

- Thorough coverage, from the ground up, of tree-based methods (e.g., CART, conditional inference trees, bagging, boosting, and random forests).
- A companion website containing additional supplementary material and the code to reproduce every example and figure in the book.
- A companion R package, called **treemisc**, which contains several data sets and functions used throughout the book (e.g., there’s an implementation of gradient tree boosting with LAD loss that shows how to perform the line search step by updating the terminal node estimates of a fitted **rpart** tree).
- Interesting examples that are of practical use; for example, how to construct partial dependence plots from a fitted model in Spark MLlib (using only Spark operations), or post-processing tree ensembles via the LASSO to reduce the number of trees while maintaining, or even improving performance.

## CHAPMAN & HALL/CRC DATA SCIENCE SERIES

Reflecting the interdisciplinary nature of the field, this book series brings together researchers, practitioners, and instructors from statistics, computer science, machine learning, and analytics. The series will publish cutting-edge research, industry applications, and textbooks in data science.

The inclusion of concrete examples, applications, and methods is highly encouraged. The scope of the series includes titles in the areas of machine learning, pattern recognition, predictive analytics, business analytics, Big Data, visualization, programming, software, learning analytics, data wrangling, interactive graphics, and reproducible research.

## Published Titles

- **An Introduction to IoT Analytics**
  *Harry G. Perros*

- **Data Analytics**
  A Small Data Approach
  *Shuai Huang and Houtao Deng*

- **Public Policy Analytics**
  Code and Context for Data Science in Government
  *Ken Steif*

- **Supervised Machine Learning for Text Analysis in R**
  *Emil Hvitfeldt and Julia Silge*

- **Massive Graph Analytics**
  *Edited by David Bader*

- **Data Science**
  An Introduction
  *Tiffany-Anne Timbers, Trevor Campbell and Melissa Lee*

- **Tree-Based Methods for Statistical Learning in R**
  *Brandon M. Greenwell*

- **Urban Informatics**
  Using Big Data to Understand and Serve Communities
  *Daniel T. O'Brien*

## Tree-Based Methods for Statistical Learning in R

Brandon M. Greenwell

First edition published 2022
by CRC Press
6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742
and by CRC Press
4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN
CRC Press is an imprint of Taylor & Francis Group, LLC

© 2022 Brandon M. Greenwell

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access www.copyright.com or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact mpkbookspermissions@tandf.co.uk

Trademark notice: Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

## Library of Congress Cataloging-in-Publication Data

Names: Greenwell, Brandon M., author.
Title: Tree-Based Methods for Statistical Learning in R / Brandon M. Greenwell.
Description: First edition. | Boca Raton, FL : CRC Press, 2022. | Series: Chapman & Hall/CRC data science series | Includes bibliographical references and index.
Identifiers: LCCN 2021059606 (print) | LCCN 2021059607 (ebook) | ISBN 9780367532468 (hbk) | ISBN 9780367543822 (pbk) | ISBN 9781003089032 (ebk)
Subjects: LCSH: Decision making--Mathematics. | Decision trees--Data processing. | Trees (Graph theory)--Data processing. | R (Computer program language)
Classification: LCC T5795. G73 2022 (print) | LCC T57.95 (ebook) | DDC 658.4/03--dc23/eng/20220217
LC record available at https://lccn.loc.gov/2021059606
LC ebook record available at https://lccn.loc.gov/2021059607

ISBN: 978-0-367-53246-8 (hbk)
ISBN: 978-0-367-54382-2 (pbk)
ISBN: 978-1-003-08903-2 (ebk)

DOI: 10.1201/9781003089032

Typeset in LM Roman
by KnowledgeWorks Global Ltd.

Publisher's note: This book has been prepared from camera-ready copy provided by the authors.

To my son, Oliver.

![](img/2c227bfb3620dc3d159fa5e6598afa30_5_0.png)

![](img/2c227bfb3620dc3d159fa5e6598afa30_6_0.png)

## Taylor & Francis

Taylor & Francis Group

http://taylorandfrancis.com

## Contents

| Section | Page |
|---------|------|
| Preface | xiii |
| 1 Introduction | 1 |
| 1.1 Select topics in statistical and machine learning | 2 |
| 1.1.1 Statistical jargon and conventions | 3 |
| 1.1.2 Supervised learning | 4 |
| 1.1.2.1 Description | 5 |
| 1.1.2.2 Prediction | 6 |
| 1.1.2.3 Classification vs. regression | 7 |
| 1.1.2.4 Discrimination vs. prediction | 7 |
| 1.1.2.5 The bias-variance tradeoff | 8 |
| 1.1.3 Unsupervised learning | 10 |
| 1.2 Why trees? | 10 |
| 1.2.1 A brief history of decision trees | 12 |
| 1.2.2 The anatomy of a simple decision tree | 14 |
| 1.2.2.1 Example: survival on the Titanic | 15 |
| 1.3 Why R? | 17 |
| 1.3.1 No really, why R? | 17 |
| 1.3.2 Software information and conventions | 19 |
| 1.4 Some example data sets | 20 |
| 1.4.1 Swiss banknotes | 21 |
| 1.4.2 New York air quality measurements | 21 |
| 1.4.3 The Friedman 1 benchmark problem | 23 |
| 1.4.4 Mushroom edibility | 24 |
| 1.4.5 Spam or ham? | 25 |
| 1.4.6 Employee attrition | 28 |
| 1.4.7 Predicting home prices in Ames, Iowa | 29 |
| 1.4.8 Wine quality ratings | 30 |
| 1.4.9 Mayo Clinic primary biliary cholangitis study | 31 |
| 1.5 There ain't no such thing as a free lunch | 35 |
| 1.6 Outline of this book | 35 |
| I Decision trees | 37 |
| 2 Binary recursive partitioning with CART | 39 |
| 2.1 Introduction | 39 |
