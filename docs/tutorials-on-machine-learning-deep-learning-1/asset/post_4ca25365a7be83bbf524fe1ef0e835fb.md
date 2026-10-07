
# Use Conda powershell:

```
(base) PS C:\Windows\system32> python
Python 3.8 (default, Sep 3 2020, 21:29:08) [MSC v14.1916 64 bit (AMD64)] :: Anaconda, Inc. on win32
> Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
>>> x = torch.rand(5, 3)
>>> print(x)
tensor([[0.0298, 0.0086, 0.8720],
        [0.0490, 0.3365, 0.0480],
        [0.7528, 0.1640, 0.0187],
        [0.0027, 0.7596, 0.0389],
        [0.8151, 0.4519, 0.9773]])
>>>
```

No Anaconda (Local) Installing on C:\Users\SolaSi\AppData\Local\Programs\Python\Python38. Alongside anaconda.

- Without anaconda or No Anaconda environment. if "anaconda" version installed previously.

NOTE: If Anaconda3 or version installed in your pc, go to C:\Users\user_name in my case C:\Users\SolaSi directory.

- Find the folder anaconda3 rename it, so that pip doesn't locate it and de-facto uses pip local directory.

- Rename anaconda3 to anaconda3bak or whatever you want. It is temporary, we'll use it after installing PyTorch in Local Python.

| anaconda3 | 7/18/2022 6:46 AM |
| Contacts | 5/13/2022 8:09 AM |

```
pip install torch
pip install torchvision
pip install torchaudio
```

Microsoft Windows [Version 6.1.7601]
Copyright (C) 2009 Microsoft Corporation. All rights reserved.

```
C:\Users\SolaSi>pip install torch
Using cached torch-1.12.0-cp38-win_amd64.whl (169.9 MB)
Requirement already satisfied: typing-extensions in c:\users\solasi\appdata\local\programs\python38\lib\site-packages (from torch>=1.10)
Requirement already satisfied: torch==1.12.0
Installed packages: torch
Successfully installed torch-1.12.0
WARNING: There was an error checking the latest version of pip.
C:\Users\SolaSi>pip install torchvision
Using cached torchvision-0.13.0+cu113-cp38-win_amd64.whl (2.1 MB)
Requirement already satisfied: torchvision==0.13.0+cu113 in c:\users\solasi\appdata\local\programs\python38\lib\site-packages (from torchvision>=0.11)
Requirement already satisfied: pillow==8.4.0 in c:\users\solasi\appdata\local\programs\python38\lib\site-packages (from torchvision>=0.9.0)
Requirement already satisfied: typing-extensions in c:\users\solasi\appdata\local\programs\python38\lib\site-packages (from torch>=1.10)
Requirement already satisfied: numpy==1.21.6 in c:\users\solasi\appdata\local\programs\python38\lib\site-packages (from torch>=1.21.0)
Requirement already satisfied: numpy==1.21.6 in c:\users\solasi\appdata\local\programs\python38\lib\site-packages (from torchvision>=0.9.0)
Requirement already satisfied: numpy==1.21.6 in c:\users\solasi\appdata\local\programs\python38\lib\site-packages (from torchaudio>=0.0)
Requirement already satisfied: numpy==1.21.6 in c:\users\solasi\appdata\local\programs\python38\lib\site-packages (from torchaudio>=0.0)
Successfully installed torchvision-0.13.0+cu113
WARNING: There was an error checking the latest version of pip.
C:\Users\SolaSi>pip install torchaudio
Using cached torchaudio-0.13.0-cp38-win_amd64.whl (960 KB)
Requirement already satisfied: torchaudio==0.13.0 in c:\users\solasi\appdata\local\programs\python38\lib\site-packages (from torch>=1.12)
Requirement already satisfied: typing-extensions in c:\users\solasi\appdata\local\programs\python38\lib\site-packages (from torch>=1.10)
Requirement already satisfied: numpy==1.21.6 in c:\users\solasi\appdata\local\programs\python38\lib\site-packages (from torch>=1.21.0)
Requirement already satisfied: numpy==1.21.6 in c:\users\solasi\appdata\local\programs\python38\lib\site-packages (from torchvision>=0.9.0)
Requirement already satisfied: numpy==1.21.6 in c:\users\solasi\appdata\local\programs\python38\lib\site-packages (from torchaudio>=0.0)
Successfully installed torchaudio-0.13.0
```

Successfully installed torchaudio-0.12.0
WARNING: There was an error checking the latest version of pip.
C:\Users\SolAI\>

```
Verification:
C:\Users\SolAI>python
Python 3.8.10 (tags/v3.8.10:d3b993, May 3 2021, 11:48:03) [MSC v1928 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
>>> x = torch.randn(5, 3)
>>> print(x)
tensor([[0.8342, 0.2619, 0.0458],
        [0.4530, 0.1518, 0.9431],
        [0.3442, 0.6217, 0.1544],
        [0.8963, 0.9547, 0.4306],
        [0.7427, 0.4610, 0.1228]])
>>>
```

Now rename "anaconda3" to "anaconda3bak" again.

## 14.1 Problem description

We gonna make recommender system that will predict if a user is going to like a movie: yes or no. This predicts binary outcome, for that is yes or no. We will build another recommender system that is to predict the rating of a movie using Autoencoders in the next chapter (predicts rating from 1 to 5). And this way we have recommender systems that are mostly used in the industry. We gonna make recommender system that predicts binary outcome, yes or no with Restricted Boltzmann machines (RBM).

Dataset: For these recommended systems (RBM and AE) we gonna start with the same data. This is the most real world dataset that you can find. It is called MovieLens. We downloaded the dataset for 100k and 1m.

The source is MovieLens:
- 100k: https://movielens.org/datasets/movielens-100k
- 25 million: https://movielens.org/datasets/movielens-25m
- 10 million: https://movielens.org/datasets/movielens-10m
- 1 million: https://movielens.org/datasets/movielens-1m
- 100k: https://movielens.org/datasets/movielens-100k.zip

## 14.4. Overview of the project

For different recommender systems with RBM and AE, we have common data preprocessing:

1. Import the dataset.
2. Prepare the training set and test set.
3. Get the number of users and the number of movies.
4. Convert our data into array where we have users in lines and movies in columns.
5. Finally, in the last step of this preprocessing, we will convert the data to tensor.

After data preprocessing steps, we start steps that are specific to Boltzmann machines. We're going to deal with binary ratings, then create an architecture of a neural network that is a Restricted Boltzmann Machine (RBM), which is a Probabilistic Graphical Model. We have two data sets, the million ratings and the 100k ratings. Remember, we are going to train our RBM on this 100k dataset as well if you want to evaluate the performance.

RBM: We have this PDF file named RBM.pdf also available online which contains all the theory behind neural networks we are about to make. I strongly encourage you to have a look at this PDF file, if you can read it it's really good. It contains all the theory on an intuitive level but also goes into the detailed math. All to know about graphical models, Restricted Boltzmann Machine (RBM) is a Probabilistic Graphical Model. You have the theory of graphical models with Undirected Graphs and Markov Random Fields. You have a section on Unsupervised Learning. You have the mathematical details of computations of likelihood which is very useful for Boltzmann machines. And you have some theory about MCMC (Markov chain Monte Carlo techniques), which is very important because we're going to use Gibbs sampling to estimate the gradient of the likelihood, and Gibbs sampling is based on MCMC.

- You have the definition of MCMC, if you want to go deeper in mathematics.
- You have of course Gibbs sampling which is very important at the heart of Boltzmann machines.
- We remind the intuition between units $V_j$ and $H_i$, and $b_j$ and $c_i$ are real-valued terms associated with the $j$-th unit and the $i$-th hidden variable, respectively.

![](img/0aa092657a6eb19f2dd65bbb79055a3_484_0.png)

- Finally, of course the Restricted Boltzmann Machines (RBM). There is the formula for energy that we're trying to minimize because we're trying to minimize the free energy, and that is by maximizing the likelihood.
- Here is the architecture of Restricted Boltzmann Machines with visible nodes, that are our input, which are going to be the ratings of the users and movies. The users are going to be different observations going into the network one by one.
- You have the hidden nodes, and so all this makes the architecture of the RBM, and that's exactly we're going to make in Python by building a class. This will contain the Contrastive Divergence technique that will be used to maximize the likelihood.

In this class, RBM will be going to implement the Contrastive Divergence technique. We will implement the following k-step divergence, this is our RBM.

## A. Fisher and C. Igel

### Algorithm 1: k-step contrast divergence

| Input: RBM ($V_1, ..., V_m, H_1, ..., H_n$), training batch S |
| Output: gradient approximation $\Delta w_{ij}$, $\Delta b_j$ and $\Delta c_i$ for $i=1, ..., n$ |

```
$\Delta w_{ij}^{(0)} = \Delta b_j^{(0)}, \Delta c_i^{(0)} = 0$ for $i=1, ..., n, j=1, ..., m$
for $s \in S$ do
  $v \leftarrow s$
  for $i=1, ..., k$ do sample $h^{(i)} \sim p(h|v^{(i-1)})$
  for $j=1, ..., m$ do sample $v^{(i+1)} \sim p(v|h^{(i)})$
for $i=1, ..., n, j=1, ..., m$ do
  $\Delta w_{ij} \leftarrow \Delta w_{ij} + p(H_i=1|v^{(k)}) - p(H_i=1|v^{(0)})$
  $\Delta c_i \leftarrow \Delta c_i + p(V_j=1|h^{(k)}) - p(V_j=1|h^{(0)})$
```
```