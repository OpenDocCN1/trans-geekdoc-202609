
XGBoost, Deep Learning, and AI

# Machine Learning
for Tabular Data

Mark Ryan
Luca Massaron

Foreword by Antonio Gulli

![](img/def89cc476fa39f4c54bd34e78d91674_0_0.png)

MANNING

# Machine Learning
for Tabular Data
XGBoost, Deep Learning, AND AI

Mark Ryan
LUCA MASSARON

FOREWORD BY ANTONIO GULLI

MANNING
SHELTER ISLAND

For online offers discounts and ordering of this and other Manning books, please visit www.manning.com.
The publisher is not responsible for any discount or disruption caused by this book when ordered in quantity.

For more information, please contact

Special Sales Department
Manning Publications Co.
20 Baldwin Road
PO Box 761
Shelter Island, NY 11964
Email: orders@manning.com

© 2025 Manning Publications Co. All rights reserved.

No part of this publication may be reproduced, stored in a retrieval system, or transmitted, in any form or by electronic, mechanical, photocopying, or otherwise, without prior permission of the publisher.

Many of the designations used by manufacturers and services to distinguish their products are claimed as trademarks. Where these designations appear in the book, and Manning Publications were aware of a trademark claim, the designations have been printed in initial caps or all caps.

> Recognizing the importance of preserving what has been written, it is Manning's policy to have the books we publish on acid-free paper, and we exert our best efforts to do that. Recognizing also our responsibility to conserve the resources of our planet, Manning books are printed on paper that is at least 15 percent recycled and processed without the use of elemental chlorine.

The author and publisher have made every effort to ensure that the information in this book was correct at press time. The author and publisher do not assume and hereby claim any liability to any party for any loss, damage, or disruption caused by errors or omissions, whether such errors result from negligence, accident, or any other cause, or from use of the information herein.

Manning Publications Co.
20 Baldwin Road
PO Box 761
Shelter Island, NY 11964 | Development editor: Doug Rudder
Technical editor: Vadim Borov
Review editor: Kishor Rit
Production editor: Amy Marinkovich
Copy editor: Karl Lucke
Proofreader: Jason Everett
Proofreader: Dwipam Katariya
Technical proofreader: Dwipam Katariya
Typesetter: Tamara Šveić Sabljić
Cover designer: Marija Tudor

ISBN 9781633438545
Printed in the United States of America

> To the memory of my niece Anna Joy, who set a great example by combining curiosity about the natural world with an abiding dedication to its Creator.

—Mark Ryan

> To the memory of John Paul Mueller, a long-time collaborator and friend, with whom we authored many marvelous books to illustrate and share the wonders of computers and technology.

—Luca Massaron

# PART 1 INTRODUCING MACHINE LEARNING FOR TABULAR DATA...1

1 Understanding tabular data 3
2 Exploring tabular datasets 14
3 Machine learning vs. deep learning 61

# PART 2 MACHINE LEARNING AND GRADIENT BOOSTING FOR TABULAR DATA................89

4 Classical algorithms for tabular data 91
5 Decision trees and gradient boosting 134
6 Advanced feature processing methods 192
7 End-to-end example using XGBoost

# PART 3 DEEP LEARNING FOR TABULAR DATA................297

8 Getting started with deep learning with tabular data 299
9 Deep learning best practices 326
10 Model deployment 359
11 Building a machine learning pipeline 397
12 Blending gradient boosting and deep learning 442

# contents

foreword xiii
preface xv
acknowledgments xvi
about this book xvii
about the authors xxi
about the cover illustration xii

# Part 1 INTRODUCING MACHINE LEARNING FOR TABULAR DATA ................................................ 1

# Understanding tabular data 3

1.1 What is tabular data? 4
1.2 The world runs on tabular data 6
1.3 Machine learning vs. deep learning 6
1.4 What makes tabular data different? 8
1.5 Generative AI and tabular data 10

# Exploring tabular datasets 14

2.1 Row and column characteristics 15
The ideal criteria for tabular rows 16 · The ideal criteria for tabular columns 20 · Representing rows and columns 23

# CONTENTS

2.2 Pathologies and remedies 24
Constant or quasi-constant columns 25 * Duplicated and high collinear features 26 * Irrelevant features 28 * Missing data 29 * Rare categories 29 * Errors in data 30
Leakage features 30

2.3 Finding external and internal data 61
Using pandas to access data stores 32 * Internet data 36
Synthetic data 39

2.4 Exploratory data analysis 42
Loading the Auto MPG example dataset 43 * Examining labels, values, distributions 46 * Exploring bivariate multivariate relationships 54

# Machine learning vs. deep learning 61

3.1 What is tabular data? 62
The Airbnb City 62 · The Airbnb dataset 65
A deep learning using Keras 66 · Training features 67
Comparing gradient boosting and deep learning 68

3.2 Transparency 76
Explainability 77 · Feature importance 80 · Conclusions 82

3.3 Efficacy 82
Evaluating performance 83

3.4 Digging 83
Deeper 83

# PART 2 MACHINE LEARNING AND GRADIENT BOOSTING FOR TABULAR DATA ................................89

# 4 Classical algorithms for tabular data 91

4.1 Introducing Scikit-learn 92
Features of Scikit-learn 93
interface 94 · Common Scikit-learn packages 97

4.2 Exploring and processing 99
Features of Scikit-learn 99 · Dataset exploration 107

4.3 Classical machine learning 108
Logistic regression 110 · Linear models 118
Logistic regression 120 · Regularized 123

4.4 Selecting features 125
Handling large datasets 126
Choosing your algorithm 127

# 5 Decision trees and gradient boosting 134

5.1 Introduction to tree-based 135
Bagging and sampling 141 · Decision trees 145 · random forests 148

5.2 Gradient boosting 150
How gradient boosting works 152 · Boosting in 155

5.3 Using XGBoost 167
XGBoost 169 · parameters 173

5.4 Mastering XGBoost 178
XGBoost 180 · trees 183

5.5 Introduction to LightGBM 184
How LightGBM grows 186 · tree structures 189

# 6 Advanced feature processing methods 192

6.1 Processing features 193
Multivariate data imputation 195 · Missing data 198 · Target encoding 199

6.2 Selecting features 211
Stability for 212 · Forward and backward 214

6.3 Optimizing hyperparameters 218
Searching systematically 219 · random trials 221 · Manually 223

6.4 Mastering gradient boosting 230
Deciding between XGBoost and LightGBM 231 · Speeding up by and compiling 236

# 7 End-to-end example using XGBoost 242

7.1 Preparing and exploring your data 243
Using generative AI to help prepare data 243 · Getting and preparing your data 244 · Engineering more complex features 252 · Finalizing your data 259 · Exploring your data 260 · Exploring your target 265

7.2 Building and optimizing your model 267
Preparing a cross-validation strategy 267 · Preparing your pipeline 269 · Building a baseline model 273 · Building a first tentative model 278 · Optimizing your model 281 · Training the final model 284

7.3 Explaining your model with SHAP 287

# PART 3 DEEP LEARNING FOR TABULAR DATA 297

tabular data 299

8.1 The deep learning with tabular data stack 300

8.2 PyTorch with fastai 304

Reviewing the key aspects of the fastai solution 304 Comparing the fastai solution with the Keras solution 311

8.3 PyTorch with TabNet 312

Key aspects of the TabNet solution 312 · Comparing the TabNet solution with the Keras solution 315

8.4 PyTorch with Lightning Flash 316

The key aspects of the Lightning Flash solution 316 Comparing the Lightning Flash solution with the Keras solution 319

8.5 Overall comparison of the stacks 320

8.6 The stacks we didn't explore 321

# 9 Deep learning best practices 326

9.1 Introduction to the Kuala Lumpur real estate dataset 329

9.2 Processing the dataset 331

Processing Bathrooms, Car Parks, Furnishing, Property Type, and Location columns 332 · Processing the Price column 333 Processing the Rooms column 333 · Processing the Size column 336
