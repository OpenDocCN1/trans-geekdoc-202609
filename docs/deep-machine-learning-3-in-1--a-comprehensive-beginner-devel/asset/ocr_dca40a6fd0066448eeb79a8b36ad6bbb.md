define the matrix as a rectangular grid of numbers. The entries in the first axis are known as rows while those in the second axis are known as columns.

# 3D Tensors

If you pack up different matrices in the form of a new array, you will obtain a 3D tensor, which you will be able to interpret as a cube of numbers. If you pack 3D tensors inside of an array, you will be able to create a 4D tensor. That’s how it goes on.

Three key attributes generally define a tensor. The first is the number of axes. For example, a 3D tensor might have three axes while a matrix possesses two axes. This is also known as the ndim of a tensor in Numpy. The shape of a tensor is a sort of a tuple of integers that describe how many dimensions each tensor has along a certain axis. Then there is a data type that is denoted by dtype symbol in Python libraries. This is a particular type of data that is contained in a tensor. A tensor’s type can be unit8, float64, and float32. You may also see a char tensor as well on certain occasions. You must take note that there is hardly any existence of string tensors.

# Vector Dataset

This is one of the most common cases in terms of data. In this kind of dataset, a single data point can be easily encoded in the form of a vector. Therefore a batch of data is to be encoded in the form of a 2D tensor which is known as an array of vectors. Here the first axis is known as the samples axis while the second axis is known as the features axis. Take the example of a dataset of people where you have to consider a particular person’s age, income, and ZIP code. Each person in the dataset ought to be characterized as a vector that is packed with three values. Therefore the entire dataset that consists of 300,000 people can be easily packed up in a 2D tensor of the following shape (300000, 3).

Then there is a dataset of text documents in which we would present each document based on how many times a certain word surfaces in it. You can calculate this in a dictionary of 10,000 words. Each document will have to be encoded in the form of a vector of 10,000 values, which will be one count per single word in the dictionary. Therefore, the entire dataset of 400 documents will be easily stored inside a tensor in the following form (400, 10000).