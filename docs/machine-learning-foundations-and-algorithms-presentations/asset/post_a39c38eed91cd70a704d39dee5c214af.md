
# Machine Learning is interdisciplinary

![](img/f01928df50903c99ce023dd3c527a33d_22_0.png)

**ML** uses these disciplines to create more accurate and efficient systems.

# Different Types of Learning

- 1. Supervised Learning: Training data includes target values
- 2. Unsupervised Learning: Training data does not include target values
- 3. Reinforcement Learning: No target values, but evaluation (reward) of the output

# Supervised Learning

Training data includes targets

- Regression: Learn continuous function. Example: line
![](img/f01928df50903c99ce023dd3c527a33d_24_0.png)
- Classification: Learn class labels. Example: Digit recognition
![](img/f01928df50903c99ce023dd3c527a33d_24_1.png)

# Unsupervised Learning

Training data does not include values

- Clustering: Model the data
![](img/f01928df50903c99ce023dd3c527a33d_25_0.png)
- Dimensionality reduction
![](img/f01928df50903c99ce023dd3c527a33d_25_1.png)

# Reinforcement Learning

- No supervisor, but reward signal. Selected actions also influence future states. New lecture this semester.
![](img/f01928df50903c99ce023dd3c527a33d_26_0.png)

# Example 1: hand-written digit

![](img/f01928df50903c99ce023dd3c527a33d_27_0.png)

Images are 28 x 28 pixels

- Represent image as vector. Learn Classifier $x \in \mathbb{R}^{784}$, $f : x \rightarrow \{0, 1, 2, 3, 4, 5, 6, 7, 8, 9\}$

# Example 1: hand-written digit

- Supervised Classification Problem
- Training-Set: 6000 examples per class
- Error on a test-set: 0.4%
- One of the first applications used in a commercial product (ZIP Codes, cheques...)
![](img/f01928df50903c99ce023dd3c527a33d_28_0.png)

# Beispiel: Gesichtserkennung, Objekterkennung

![](img/f01928df50903c99ce023dd3c527a33d_29_0.png)

# Example: Image generation

![](img/f01928df50903c99ce023dd3c527a33d_30_0.png)
![](img/f01928df50903c99ce023dd3c527a33d_30_1.png)
![](img/f01928df50903c99ce023dd3c527a33d_30_2.png)
![](img/f01928df50903c99ce023dd3c527a33d_30_3.png)

https://thispersondoesnotexist.com/

# Example: Image to Text

![](img/f01928df50903c99ce023dd3c527a33d_31_0.png)

Description:
A falcon is eating during sunset.
The falcon is standing on earth.

Poem:
- Like a falcon by the night
- Hunting as the black knight
- Waiting to take over the fight
- With all of its mind and might

# Example: Text to Image

Diffusion model for image generation given a few natural language prompts:
"a cute magical flying dog, fantasy art drawn by disney concept artists, golden colour, high quality, highly detailed, elegant, sharp focus, concept art, character concepts, digital painting, mystery, adventure"
![](img/f01928df50903c99ce023dd3c527a33d_32_0.png)

# Example: Autonomous Driving

# “Level 5” ???

![](img/f01928df50903c99ce023dd3c527a33d_33_0.png)
![](img/f01928df50903c99ce023dd3c527a33d_33_1.png)
![](img/f01928df50903c99ce023dd3c527a33d_33_2.png)

VW “Level 4” 2025
![](img/f01928df50903c99ce023dd3c527a33d_33_3.png)
Tesla “Level 2”, 2020
![](img/f01928df50903c99ce023dd3c527a33d_33_4.png)
![](img/f01928df50903c99ce023dd3c527a33d_33_5.png)

Darpa Grand Challenge 2004
Darpa Urban Challenge 2007

# Example: Stock price prediction

- Prediction of the stock prices
- Regression continuous outputs
![](img/f01928df50903c99ce023dd3c527a33d_34_0.png)

# Example: Spam Detection

- Classify emails in spam / non-spam
- Data represented by word count, e.g.: "Viagra", "offer", "you may be surprised..."
- Spam strategies -> we need learning
![](img/f01928df50903c99ce023dd3c527a33d_35_0.png)

# Example: Computational Biology

- Given the protein sequence, predict 3D structure
![](img/f01928df50903c99ce023dd3c527a33d_36_0.png)

# Example: Language Translation

- Learn from aligned translations
What is the anticipated cost of collecting fees under the new proposal?
En vertu des nouvelles propositions, quel est le coût prévu des droits?
e.g. Google translate
![](img/f01928df50903c99ce023dd3c527a33d_37_0.png)

# Example: Language Translation

![](img/f01928df50903c99ce023dd3c527a33d_38_0.png)

# Example: Recommender Systems

### Frequently Bought Together
Customers buy this book with Pattern Recognition and Machine Learning (Information Science and Statistics) (Information Science and Statistics) by Christopher M. Bishop

| Price For Both: £104.95 |
|---|---|
| [Add both to Basket] |

### Customers Who Bought This Item Also Bought

- Pattern Recognition and Machine Learning (Info...) by Christopher M. Bishop ★★★ (4) £48.96
- MACHINE LEARNING (McGraw-Hill International Edit) by Tom M. Mitchell ★★★ (3) £42.74
- Pattern Classification, Second Edition: 1 (A...) by Richard O. Duda ★★★ (1) £78.38
- Data Mining: Practical Machine Learning Tools... by Ian H. Witten ★★★ (1) £37.04

# Example: Robot Manipulation

- Reinforcement Learning: Learning to grasp unknown objects (Google)
![](img/f01928df50903c99ce023dd3c527a33d_40_0.png)

# Example: Tossing objects

- Reinforcement Learning: Learning to throw objects into bins
![](img/f01928df50903c99ce023dd3c527a33d_41_0.png)

# Large Language Models

## Can you please come here?

History

Word being predicted

![](img/f01928df50903c99ce023dd3c527a33d_42_0.png)

I want a short poem praising the moon in German

- Sanfter Mond am Himmelsz,
Still und schön den Strahlen fällt,
Dein sanftes Licht die Nacht erhält,
Die Seele ruht, der Geist entfaltet.

Regenerate response

Send a message...

```javascript
// write a binary search algorithm
const binarySearch = (arr, target) => {
  let left = 0;
  let right = arr.length - 1;
  let middle = Math.floor((left + right) / 2);
  while (arr[middle] != target && left <= right) {
    if (target < arr[middle]) {
      right = middle - 1;
    } else {
      left = middle + 1;
    }
    middle = Math.floor((left + right) / 2);
  }
  return arr[middle] == target ? middle : -1;
};
```

# Machine Learning is interdisciplinary

![](img/f01928df50903c99ce023dd3c527a33d_22_0.png)

**ML** uses these disciplines to create more accurate and efficient systems.

# Different Types of Learning

- 1. Supervised Learning: Training data includes target values
- 2. Unsupervised Learning: Training data does not include target values
- 3. Reinforcement Learning: No target values, but evaluation (reward) of the output

# Supervised Learning

Training data includes targets

- Regression: Learn continuous function. Example: line
![](img/f01928df50903c99ce023dd3c527a33d_24_0.png)
- Classification: Learn class labels. Example: Digit recognition
![](img/f01928df50903c99ce023dd3c527a33d_24_1.png)

# Unsupervised Learning

Training data does not include values

- Clustering: Model the data
![](img/f01928df50903c99ce023dd3c527a33d_25_0.png)
- Dimensionality reduction
![](img/f01928df50903c99ce023dd3c527a33d_25_1.png)

# Reinforcement Learning

- No supervisor, but reward signal. Selected actions also influence future states. New lecture this semester.
![](img/f01928df50903c99ce023dd3c527a33d_26_0.png)

# Example 1: hand-written digit

![](img/f01928df50903c99ce023dd3c527a33d_27_0.png)

Images are 28 x 28 pixels

- Represent image as vector. Learn Classifier $x \in \mathbb{R}^{784}$, $f : x \rightarrow \{0, 1, 2, 3, 4, 5, 6, 7, 8, 9\}$

# Example 1: hand-written digit

- Supervised Classification Problem
- Training-Set: 6000 examples per class
- Error on a test-set: 0.4%
- One of the first applications used in a commercial product (ZIP Codes, cheques...)
![](img/f01928df50903c99ce023dd3c527a33d_28_0.png)

# Beispiel: Gesichtserkennung, Objekterkennung

![](img/f01928df50903c99ce023dd3c527a33d_29_0.png)

# Example: Image generation

![](img/f01928df50903c99ce023dd3c527a33d_30_0.png)
![](img/f01928df50903c99ce023dd3c527a33d_30_1.png)
![](img/f01928df50903c99ce023dd3c527a33d_30_2.png)
![](img/f01928df50903c99ce023dd3c527a33d_30_3.png)

https://thispersondoesnotexist.com/

# Example: Image to Text

![](img/f01928df50903c99ce023dd3c527a33d_31_0.png)

Description:
A falcon is eating during sunset.
The falcon is standing on earth.

Poem:
- Like a falcon by the night
- Hunting as the black knight
- Waiting to take over the fight
- With all of its mind and might

# Example: Text to Image

Diffusion model for image generation given a few natural language prompts:
"a cute magical flying dog, fantasy art drawn by disney concept artists, golden colour, high quality, highly detailed, elegant, sharp focus, concept art, character concepts, digital painting, mystery, adventure"
![](img/f01928df50903c99ce023dd3c527a33d_32_0.png)

# Example: Autonomous Driving

# “Level 5” ???

![](img/f01928df50903c99ce023dd3c527a33d_33_0.png)
![](img/f01928df50903c99ce023dd3c527a33d_33_1.png)
![](img/f01928df50903c99ce023dd3c527a33d_33_2.png)

VW “Level 4” 2025
![](img/f01928df50903c99ce023dd3c527a33d_33_3.png)
Tesla “Level 2”, 2020
![](img/f01928df50903c99ce023dd3c527a33d_33_4.png)
![](img/f01928df50903c99ce023dd3c527a33d_33_5.png)

Darpa Grand Challenge 2004
Darpa Urban Challenge 2007

# Example: Stock price prediction

- Prediction of the stock prices
- Regression continuous outputs
![](img/f01928df50903c99ce023dd3c527a33d_34_0.png)

# Example: Spam Detection

- Classify emails in spam / non-spam
- Data represented by word count, e.g.: "Viagra", "offer", "you may be surprised..."
- Spam strategies -> we need learning
![](img/f01928df50903c99ce023dd3c527a33d_35_0.png)

# Example: Computational Biology

- Given the protein sequence, predict 3D structure
![](img/f01928df50903c99ce023dd3c527a33d_36_0.png)

# Example: Language Translation

- Learn from aligned translations
What is the anticipated cost of collecting fees under the new proposal?
En vertu des nouvelles propositions, quel est le coût prévu des droits?
e.g. Google translate
![](img/f01928df50903c99ce023dd3c527a33d_37_0.png)

# Example: Language Translation

![](img/f01928df50903c99ce023dd3c527a33d_38_0.png)

# Example: Recommender Systems

### Frequently Bought Together
Customers buy this book with Pattern Recognition and Machine Learning (Information Science and Statistics) (Information Science and Statistics) by Christopher M. Bishop

| Price For Both: £104.95 |
|---|---|
| [Add both to Basket] |

### Customers Who Bought This Item Also Bought

- Pattern Recognition and Machine Learning (Info...) by Christopher M. Bishop ★★★ (4) £48.96
- MACHINE LEARNING (McGraw-Hill International Edit) by Tom M. Mitchell ★★★ (3) £42.74
- Pattern Classification, Second Edition: 1 (A...) by Richard O. Duda ★★★ (1) £78.38
- Data Mining: Practical Machine Learning Tools... by Ian H. Witten ★★★ (1) £37.04

# Example: Robot Manipulation

- Reinforcement Learning: Learning to grasp unknown objects (Google)
![](img/f01928df50903c99ce023dd3c527a33d_40_0.png)

# Example: Tossing objects

- Reinforcement Learning: Learning to throw objects into bins
![](img/f01928df50903c99ce023dd3c527a33d_41_0.png)

# Large Language Models

## Can you please come here?

History

Word being predicted

![](img/f01928df50903c99ce023dd3c527a33d_42_0.png)

I want a short poem praising the moon in German

- Sanfter Mond am Himmelsz,
Still und schön den Strahlen fällt,
Dein sanftes Licht die Nacht erhält,
Die Seele ruht, der Geist entfaltet.

Regenerate response

Send a message...

```javascript
// write a binary search algorithm
const binarySearch = (arr, target) => {
  let left = 0;
  let right = arr.length - 1;
  let middle = Math.floor((left + right) / 2);
  while (arr[middle] != target && left <= right) {
    if (target < arr[middle]) {
      right = middle - 1;
    } else {
      left = middle + 1;
    }
    middle = Math.floor((left + right) / 2);
  }
  return arr[middle] == target ? middle : -1;
};
```

# Conceptual view on ML

- Thousands of learning algorithms
- Hundreds of new algorithms every year
- We will only look at the fundamental algorithms and discuss the principles that connect them

Every ML algorithm consists of 3 parts:

- Representation
- Evaluation
- Optimization

# Representation

What is the underlying representation of our model?

- * Features
* Kernels
* Neural networks
    * Feedforward NNs
    * CNNs
    * Transformers
    * GNNs
* Model ensembles
* Instances
* Mixture models
* Latent variable models
* Etc.

# Evaluation

## What are we optimizing for ?

- * Accuracy
* Precision and recall
* Squared error
* Likelihood
* Posterior probability
* Cost / Utility
* Margin
* Entropy
* KL divergence
* Etc.

# Optimization

How do we optimize?

- - Least squares solution
- Gradient descent
- Gradient descent with adaptive learning rate
- 2nd order methods
- Constraint optimization
- Random search
