
- 7 Sparse Matrix 223
  - 7.1 Scipy's Sparse Matrix Classes 224
    - 7.1.1 Coordinate Sparse Matrix (coo_matrix) 224
    - 7.1.2 Compressed Sparse Column Matrix (csc_matrix) 225
    - 7.1.3 Compressed Sparse Row Matrix (csr_matrix) 227
    - 7.1.4 Block Sparse Row Matrix (bsr_matrix) 228
    - 7.1.5 Dictionary of Keys Sparse Matrix (dok_matrix) 229
    - 7.1.6 Row-Based List of List Sparse Matrix (lil_matrix) 230
    - 7.1.7 Diagonal Storage Sparse Matrix (dia_matrix) 232
    - 7.1.8 Comparisons Between Different Sparse Matrix Formats 233
  - 7.2 Sparse Matrix Broadcasting 235
    - 7.2.1 Scalar Broadcasting 235
    - 7.2.2 Row-wise Broadcasting 236
    - 7.2.3 Column-wise Broadcasting 237
    - 7.2.4 Multiplication on Sparse Indices 237
  - 7.3 Tensorflow's Sparse Tensors 238
    - 7.3.1 SparseTensor Class 239
    - 7.3.2 Sparse CSR Matrix 240
  - 7.4 PyTorch's Sparse Matrix 242
  - 7.5 Sparse Matrix in Other Python Libraries 245
  - 7.6 When (Not) to Use Sparse Matrix 245
  - 7.7 Case Study: Sparse Matrix Factorization with ALS 245
    - 7.7.1 Matrix Factorization 246
    - 7.7.2 Parameter Updates with ALS 246
    - 7.7.3 Adding Bias Terms to Matrix Factorization 247
    - 7.7.4 Adding Regularization Term 249
    - 7.7.5 Implementing ALS 250
    - 7.7.6 Training a Model with MovieLens-100k 255
  - Bibliography 257
- 8 Jagged Tensors 261
  - 8.1 Left Align a Sparse Tensor to Represent Ragged Tensor 263
  - 8.2 Index to Binary Indicator 269
  - 8.3 Case Study: Jaccard Similarities Using Sparse Matrix 271
  - 8.4 Case Study: Batchwise Set Operations 275
  - 8.5 Case Study: Autoencoders with Sparse Inputs 283
    - 8.5.1 Embedding Lookup on Sparse Inputs 284
    - 8.5.2 Inputs with Weights 287
  - Bibliography 293

## 9 Groupby, Apply, and Aggregate 295

- 9.1 Pandas Groupwise Operations 296
- 9.2 Reshaping and Windowing of Dense Tensors 298
- 9.3 Case Study: Vision Transformer (ViT) 305
- 9.4 Bucketizing Values 315
- 9.5 Segment-wise Aggregation 319
- 9.6 Case Study: EmbeddingBag 325
- 9.7 Case Study: Vocal Duration Constrained by Note Duration 330
- 9.8 Case Study: Filling of Missing Values in a Sequence 336
- Bibliography 341

## 10 Sorting and Reordering 343

- 10.1 Sorting Operations 343
- 10.2 Case Study: Top-k Using argsort and argpartition 346
- 10.3 Case Study: Sort the Rows of a Matrix 349
- 10.4 Case Study: Reverse Padded Sequence 353
- 10.5 Case Study: Gumbel-Max Sampling with Weights 358
- 10.6 Case Study: Sorting Articles Around Anchored Advertisements 367
- Bibliography 373

## 11 Building a Language Model from Scratch 375

- 11.1 Language Modeling with Transformer 375
  - 11.1.1 Encoder and Decoder of the Transformer Architecture 376
  - 11.1.2 Training of Transformer Models 377
- 11.2 Pre-LN vs. Post-LN Transformer 378
- 11.3 Layer Normalization 383
- 11.4 Positional Encoding and Embedding 385
  - 11.4.1 Sinusoidal Positional Encoding 385
  - 11.4.2 Position as Categorical Embeddings 387
  - 11.4.3 Relative Positional Encoding (RPE) 388
  - 11.4.4 Rotary Positional Encoding (RoPE) 389
- 11.5 Activation Functions in Feedforward Layer 395
- 11.6 Case Study: Training a Tiny LLaMA Model for Next Token Prediction 398
- 11.7 A Word on AI Safety and Alignment 410
- 11.8 Concluding Remarks 412
- Bibliography 412

## Index 419

## About the Author

Edward Dongbo Cui is a data science and machine learning engineering leader who holds a PhD in neuroscience from Case Western Reserve, USA. Edward served as Director of Data Science at DotDash Meredith, building large-scale search and recommender systems for online digital publications. At NBC Universal, he served as Director of Data Science, building the first recommendation system on the new Peacock streaming platform. Previously, he was lead data scientist at Nielsen Global Media. He is an expert in ML engineering, research, and MLOps to drive data-centric decision-making and enhance product innovation.

## Preface

Over the years, I have accrued valuable experiences in implementing machine learning algorithms, and this book is my endeavor to share those insights with you. Machine learning is a vast field, encompassing areas including but not limited to computer vision, speech processing, natural language processing, and recommendation systems. While the diversity of these topics is immense, there are underlying mathematical and computational principles that weave them together.

### Structure of the Book

The book is structured into 11 chapters, each dedicated to a pivotal topic in the realm of scientific computation and machine learning:

- Chapter 1 delves into the power of vectorization, contextualized within parallel computing.
- Chapter 2 lays the foundation by discussing the basic tensor operations.
- Chapter 3 details the art of tensor indexing, elucidating how to access individual or subsets of tensor elements.
- Chapter 4 probes deeper into vectorization in tensor multiplications and common linear algebraic routines, which form the backbone of many machine learning algorithms.
- Chapter 5 sheds light on the pivotal concepts of masking and padding, which come into play when handling data of nonuniform sizes.
- Chapter 6 touches upon string processing techniques, invaluable for natural language processing (NLP) tasks.
- Chapter 7 introduces the realm of sparse matrices, discussing their data structures and integral operations.
- Chapter 8 takes a closer look at a unique kind of sparse tensor – ragged or jagged tensors – and the nuances of processing them.
- Chapter 9 breaks down the data wrangling pattern of groupby-apply-aggregate, which is crucial for data summarization.
- Chapter 10 explores the topic on sorting, reordering, sampling, and batch processing through a series of case studies.
- Chapter 11 concludes the book with a review of the Transformer++ architecture (a.k.a. LLaMA, a foundational large language model architecture from Meta), weaving together the principles discussed in the preceding chapters.

**Audience:** While I have tailored this book for those embarking on their journey in machine learning algorithm implementation, it is not solely for beginners. Having a basic understanding of machine learning and deep learning will certainly be an advantage, but every concept introduced is supplemented with sufficient background to make it comprehensible to all readers.

## Prerequisites

- **Familiarity with the Python programming language:** Readers can find online resources to learn Python or through classic books such as “Think Python.”
- **Undergraduate linear algebra:** To this, I highly recommend Gilbert Strang’s lectures on Linear Algebra at MIT, or his book “Introduction to Linear Algebra.”
- **Foundational knowledge of data science and machine learning:** The goal of this book is not to introduce machine learning, but rather to guide the reader in solving real-world problems encountered in machine learning (oftentimes deep learning). Basic knowledge of data science and machine learning can be gained from either previous more foundational courses or practical knowledge gained from doing machine learning projects hands-on. Courses such as Andrew Ng’s CS229 Machine Learning can serve as a foundation.

## Features

- Every chapter is punctuated with numerous case studies to ensure the concepts are grounded in practical scenarios. Accompanying these are detailed code implementations with line-by-line explanations. Most of the implementations will use only the knowledge acquired within the chapter. Certainly, as the reader learns along the way, one may come up with better implementations by leveraging more advanced concepts.
- The book covers vectorization techniques using NumPy, Tensorflow, and PyTorch (and for certain operations, Pandas as well). When introducing the operations, I will include tables that enumerate equivalent operations in these three libraries, in the hope that readers who are familiar with one of the libraries can also learn to translate algorithms and models implemented in another library. Most case study code examples will be implemented in one of the libraries (often NumPy), but readers are encouraged to implement the same functionality using alternative libraries by referencing equivalent operations.
