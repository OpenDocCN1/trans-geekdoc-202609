

5. Deisenroth, M.P., Faisal, A.A., and Ong, C.S. (2020). Mathematics for Machine Learning. Cambridge University Press.

6. Gelman, A., Carlin, J.B., Stern, H.S., Dunson, D.B., Vehtari, A., and Rubin, D.B. (2013). Bayesian Data Analysis (3rd ed.). Chapman & Hall/CRC.

7. Ghosh, M., and Sinha, B.K. (2002). A simple derivation of the Wishart distribution. The American Statistician, 56(2), 100–101.

8. Golub, G.H., and Van Loan, C.F. (2013). Matrix Computations. JHU Press.

9. Goodfellow, I., Bengio, Y., and Courville, A. (2016). Deep Learning. MIT Press.

10. Hogg, R.V., McKean, J.W., and Craig, A.T. (2019). Introduction to Mathematical Statistics. Pearson.

11. Horn, R.A., and Johnson, C.R. (2012). Matrix Analysis. Cambridge University Press.

12. Jing, B.Y., Li, Z., Pan, G., and Zhou, W. (2016). On SURE-type double shrinkage estimation. Journal of the American Statistical Association, 111(516), 1696–1704.

13. Johnson, R.A., and Wichern, D.W. (2002). Applied Multivariate Statistical Analysis. Prentice Hall.

14. Lai, T.L., and Xing, H. (2008). Statistical Models and Methods for Financial Markets. Springer.

15. McLachlan, G.J. (1999). Mahalanobis distance. Resonance, 4(6), 20–26.

16. Morrison, D.F. (1990). Multivariate Statistical Methods. McGraw-Hill.

17. Rencher, A.C., and Christensen, W.F. (2012) Methods of Multivariate Analysis (3rd ed.). Wiley.

18. Strang, G. (2006). Linear Algebra and its Applications. Thomson, Brooks/Cole.

19. Strang, G. (2019). Linear Algebra and Learning from Data. Wellesley-Cambridge Press.

20. Watkins, D.S. (2004). Fundamentals of Matrix Computations. Wiley.

21. Zhang, X.D. (2017). Matrix Analysis and Applications. Cambridge University Press.

## NOTES

1. [1](#c01.xhtml#R_c01-note-0001) 该数据集可在 [`https://github.com/kaiser1999/Financial-Data-Analytics`](https://github.com/kaiser1999/Financial-Data-Analytics) 获取。

2. [2](#c01.xhtml#R_c01-note-0002) 此处，我们仅考虑非退化情况，即 ![bold upper Sigma](images/c01-i0390.png)<math display="inline" overflow="scroll"><mrow><mi mathvariant="bold">&#931;</mi></mrow></math> 为正定矩阵。

3. [3](#c01.xhtml#R_c01-note-0003) 等价地，方差 ![normal sigma squared](images/c01-i0676.png)<math display="inline" overflow="scroll"><msup><mi mathvariant="normal">&#963;</mi><mn>2</mn></msup></math> 被认为服从 *inverse gamma* 分布。

# CHAPTER 2  

## Introduction to Python and R

### 2.1 WHAT IS PYTHON?

Python is used *very* widely as a scripting language. For instance, *Pixar*

In Python, we can enjoy the following features:

1. No need to declare the types of variables. For example, we write `x = 1` in Python compared to `int x = 1` in `C++`. You can first write `x = 1` (an integer), then `x = "statistics"` (a string) in the later parts of the same programme;

2. The environment, in which you work, lets you type bits of code and allows you to see what happens without an intermediate compiling step, making experimentation and testing very simple;

3. It is very easy to read, and uses English keywords and natural-sounding syntax, for instance,

    **Example**

    ![](images/c02-gra-0001.png)

4. Instead of using curly braces to delimit code blocks, Python uses (for instance) 4 whitespace indentations (in fact any number of indentations is allowed as long as the practice is consistent throughout the programme). Correctly nesting your code now has a semantic meaning.

Python is similar to Java in the sense that it also handles your memory management: it allocates memory for different uses, and has the capacity to free up that memory once it is no longer needed. In the rest of this book, the Python coding shown is consistent with version 3.9 of Python.

### 2.2 WHAT IS R?

**R** is a free and integrated programming language for statistical computing and graphical display. It is widely used among probabilists, statisticians and data scientists. Some elementary statistical tests and functions are already built in **R**, such that no extra libraries have to be called out. The name **R**

### 2.3 PACKAGE MANAGEMENT IN PYTHON AND R

Python and **R** are two very popular programming languages for machine learning and deep learning developers, and there are hundreds of packages and libraries available online.

In Python, one cannot install the packages directly in the console. Using *Anaconda* ![FIGURE 2.1 Typing “pip install tensorflow” in Anaconda prompt.](images/c02f001.png)

[**FIGURE 2.1**](#c02.xhtml#R_c02-fig-0001) Typing “pip install tensorflow” in *Anaconda prompt*.

Here `pip` is used to install the Python related packages. There is another command `conda`, which is used to install packages written in any languages available in *Anaconda*. After the installation, we can import the package in the console by typing:

![](images/c02-gra-0002.png)

Here `tf` is used as a self-defined, short-handed notation for `tensorflow`. The tensorflow package is widely used for deep learning. It has an advanced version that utilises the full power of *Graphics Processing Unit* (GPU), which is called the `tensorflow-gpu`. It significantly reduces the training time of a deep learning model, but it requires a decent GPU and additional installations of software *Compute Unified Device Architecture* (CUDA) and *CUDA Deep Neural Network library* (cuDNN). Moreover, the importation of `tensorflow-gpu` is achieved by the command “`import tensorflow as tf`”; GPU will then automatically be used instead of CPU. We can check our CPU and GPU by:

![](images/c02-gra-0003.png)![](images/c02-gra-0004.png)

Here “`GeForce RTX 2070 SUPER`” is the GPU used and the reference index for this GPU is 0. If there exists another GPU in use, the reference index for the second GPU is 1, and so on. The memory limits for CPU and GPU are shown in bytes, and we see that, for instance, the limit of the present GPU is 30 times more than that of CPU.

Meanwhile, In **R**, the installation and the importation of packages are done directly in the console:

![](images/c02-gra-0005.png)

Here `e1071` is one of the packages for building a *support vector machine* (SVM) model in **R**. This SVM model will be discussed in detail in [Section 11.2](#c11.xhtml#head-2-145).

### 2.4 BASIC OPERATIONS IN PYTHON AND R

In this section, some basic operations in Python and **R** which are essential for statistical computing are briefly described. For more comprehensive treatments of these two languages, we refer the reader to \[2, 4, 5, 6\]. The dataset `fin-ratio.csv` (see [Example 1.1](#c01.xhtml#c01-fea-0006)) is used as an illustration for the first and the second items:

1. **(I)** **Read and Write csv/txt Files**:

    `csv` (Comma Separated Values) files or `txt` (TeXT) files are two common file types for data storage. In Python, we need the `pandas` (deriving its name from PANel DAta, *i.e*. observations over multiple time periods for the same object) library:

    ![](images/c02-gra-0006.png)

    Note that `data` must be a `pandas.DataFrame` object in order to use the `to_csv()` function. In **R**, there is no need to import any libraries for this action.

    ![](images/c02-gra-0007.png)

2. **(II)** **Computations of Sample Mean, Sample Variance, and Sample Covariance Matrix**:

    In Python, the `pandas` library have built-in functions for sample means, sample variances, and sample covariances.

    ![](images/c02-gra-0008.png)![](images/c02-gra-0009.png)

    In **R**, there is no need to import any libraries for this action.

    ![](images/c02-gra-0010.png)

    Here the `apply()` function “applies” a function specified by the parameter `FUN` by returning a vector along the dimension as specified by the parameter `MARGIN`, in which the argument `MARGIN=2` indicates the function is applied on the second dimension, *i.e*. along the *column* direction.

