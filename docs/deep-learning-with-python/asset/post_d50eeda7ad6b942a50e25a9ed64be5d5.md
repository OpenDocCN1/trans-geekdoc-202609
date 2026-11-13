
## DEEP LEARNING with Python
SECOND EDITION
François Chollet
MANNING

![](img/ab452ecf572a1f1372915be13bd8088f_0_0.png)

## Deep Learning with Python

## Deep Learning with Python
SECOND EDITION
FRANÇOIS CHOLLET
MANNING
SHELTER ISLAND

For online information and ordering of this and other Manning books, please visit www.manning.com. The publisher offers discounts on this book when ordered in quantity. For more information, please contact Special Sales Department Manning Publications Co. 20 Baldwin Road PO Box 761 Shelter Island, NY 11964 Email: orders@manning.com

©2021 by Manning Publications Co. All rights reserved.

No part of this publication may be reproduced, stored in a retrieval system, or transmitted, in any form or by means electronic, mechanical, photocopying, or otherwise, without prior written permission of the publisher.

Many of the designations used by manufacturers and sellers to distinguish their products are claimed as trademarks. Where those designations appear in the book, and Manning Publications was aware of a trademark claim, the designations have been printed in initial caps or all caps.

© Recognizing the importance of preserving what has been written, it is Manning’s policy to have the books we publish printed on acid-free paper, and we exert our best efforts to that end. Recognizing also our responsibility to conserve the resources of our planet, Manning books are printed on paper that is at least 15 percent recycled and processed without the use of elemental chlorine.

The author and publisher have made every effort to ensure that the information in this book was correct at press time. The author and publisher do not assume and hereby disclaim any liability to any party for any loss, damage, or disruption caused by errors or omissions, whether such errors or omissions result from negligence, accident, or any other cause, or from any usage of the information herein.

![](img/ab452ecf572a1f1372915be13bd8088f_4_0.png)

Manning Publications Co. 20 Baldwin Road PO Box 761 Shelter Island, NY 11964

- Development editor: Jennifer Stout
- Technical development editor: Frances Buontempo
- Review editor: Aleksandar Dragosavljević
- Production editor: Keri Hales
- Copy editor: Andy Carroll
- Proofreaders: Katie Tennant and Melody Dolab
- Technical proofreader: Karsten Strøbæk
- Typesetter: Dennis Dalinnik
- Cover designer: Marija Tudor

ISBN: 9781617296864 Printed in the United States of America

To my son Sylvain: I hope you'll read this book someday!

## brief contents

- 1 ■ What is deep learning? 1
- 2 ■ The mathematical building blocks of neural networks 26
- 3 ■ Introduction to Keras and TensorFlow 68
- 4 ■ Getting started with neural networks: Classification and regression 95
- 5 ■ Fundamentals of machine learning 121
- 6 ■ The universal workflow of machine learning 153
- 7 ■ Working with Keras: A deep dive 172
- 8 ■ Introduction to deep learning for computer vision 201
- 9 ■ Advanced deep learning for computer vision 238
- 10 ■ Deep learning for timeseries 280
- 11 ■ Deep learning for text 309
- 12 ■ Generative deep learning 364
- 13 ■ Best practices for the real world 412
- 14 ■ Conclusions 431

## contents

- preface xviii
- acknowledgments xix
- about this book xx
- about the author xxiii
- about the cover illustration xxiv

## 1 What is deep learning? 1

### 1.1 Artificial intelligence, machine learning, and deep learning 2

- Artificial intelligence 2 • Machine learning 3 • Learning rules and representations from data 4 • The “deep” in “deep learning” 7 • Understanding how deep learning works, in three figures 8 • What deep learning has achieved so far 10 • Don’t believe the short-term hype 11 • The promise of AI 12

### 1.2 Before deep learning: A brief history of machine learning 13

- Probabilistic modeling 13 • Early neural networks 14 • Kernel methods 14 • Decision trees, random forests, and gradient boosting machines 15 • Back to neural networks 16 • What makes deep learning different 17 • The modern machine learning landscape 18

### 1.3 Why deep learning? Why now? 20

- Hardware 20 • Data 21 • Algorithms 22 • A new wave of investment 23 • The democratization of deep learning 24 • Will it last? 24

## 2 The mathematical building blocks of neural networks 26

### 2.1 A first look at a neural network 27

### 2.2 Data representations for neural networks 31

- Scalars (rank-0 tensors) 31 • Vectors (rank-1 tensors) 31 • Matrices (rank-2 tensors) 32 • Rank-3 and higher-rank tensors 32 • Key attributes 32 • Manipulating tensors in NumPy 34 • The notion of data batches 35 • Real-world examples of data tensors 35 • Vector data 35 • Timeseries data or sequence data 36 • Image data 37 • Video data 37

### 2.3 The gears of neural networks: Tensor operations 38

- Element-wise operations 38 • Broadcasting 40 • Tensor product 41 • Tensor reshaping 43 • Geometric interpretation of tensor operations 44 • A geometric interpretation of deep learning 47

### 2.4 The engine of neural networks: Gradient-based optimization 48

- What's a derivative? 49 • Derivative of a tensor operation: The gradient 51 • Stochastic gradient descent 52 • Chaining derivatives: The Backpropagation algorithm 55

### 2.5 Looking back at our first example 61

- Reimplementing our first example from scratch in TensorFlow 63 • Running one training step 64 • The full training loop 65 • Evaluating the model 66

## 3 Introduction to Keras and TensorFlow 68

### 3.1 What's TensorFlow? 69

### 3.2 What's Keras? 69

### 3.3 Keras and TensorFlow: A brief history 71

### 3.4 Setting up a deep learning workspace 71

- Jupyter notebooks: The preferred way to run deep learning experiments 72 • Using Colaboratory 73

### 3.5 First steps with TensorFlow 75

- Constant tensors and variables 76 • Tensor operations: Doing math in TensorFlow 78 • A second look at the GradientTape API 78 • An end-to-end example: A linear classifier in pure TensorFlow 79

### 3.6 Anatomy of a neural network: Understanding core Keras APIs 84

- Layers: The building blocks of deep learning 84 • From layers to models 87 • The “compile” step: Configuring the learning process 88 • Picking a loss function 90 • Understanding the fit() method 91 • Monitoring loss and metrics on validation data 91 • Inference: Using a model after training 93

## 4 Getting started with neural networks: Classification and regression 95

### 4.1 Classifying movie reviews: A binary classification example 97

- The IMDB dataset 97 • Preparing the data 98 • Building your model 99 • Validating your approach 102 • Using a trained model to generate predictions on new data 105 • Further experiments 105 • Wrapping up 106

### 4.2 Classifying newswires: A multiclass classification example 106

- The Reuters dataset 106 • Preparing the data 107 • Building your model 108 • Validating your approach 109 • Generating predictions on new data 111 • A different way to handle the labels and the loss 112 • The importance of having sufficiently large intermediate layers 112 • Further experiments 113 • Wrapping up 113

### 4.3 Predicting house prices: A regression example 113

- The Boston housing price dataset 114 • Preparing the data 114 • Building your model 115 • Validating your approach using K-fold validation 115 • Generating predictions on new data 119 • Wrapping up 119

## 5 Fundamentals of machine learning 121

### 5.1 Generalization: The goal of machine learning 121

- Underfitting and overfitting 122 • The nature of generalization in deep learning 127

### 5.2 Evaluating machine learning models 133

- Training, validation, and test sets 133 • Beating a common-sense baseline 136 • Things to keep in mind about model evaluation 137

### 5.3 Improving model fit 138

- Tuning key gradient descent parameters 138 • Leveraging better architecture priors 139 • Increasing model capacity 140
