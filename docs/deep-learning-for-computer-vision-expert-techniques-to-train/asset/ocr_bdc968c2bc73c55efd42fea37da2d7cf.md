# Getting Started

+   - Python 3.x avoids many design flaws in the original implementation
- Contrary to popular belief, Python 3.x has as many supporting libraries for data science as Python 2.x.

We use Python version 3 throughout this book. Go to https://www.python.org/downloads/ and download version 3 according to the OS. Install Python by following the steps given in the download link. After installing Python, pip3 has to be installed for easy installation of Python packages. Install the several Python packages by entering the following command, so that you can install OpenCV and tensorflow later:

```
pip3 install numpy scipy scikit-learn pillow h5py
```

The description of the preceding installed packages is given as follows:

+   - numpy is a highly-optimized numerical computation package. It has a powerful N-dimensional package array object, and the matrix operations of numpy library are highly optimized for speed. An image can be stored as a 3-dimensional numpy object.
- scipy has several routines for scientific and engineering calculations. We will use some optimization packages later in the book.
- scikit-learn is a machine-learning library from which we will use many helper functions.
- Pillow is useful for image loading and basic operations.
- H5py package is a Pythonic interface to the HDF5 binary data format. This is for the format to store models trained using Keras.

# Open Computer Vision - OpenCV

The OpenCV is a famous computer vision library. There are several image processing routines available in this library that can be of great use. Following is the step of installing OpenCV in Ubuntu.

```
sudo apt-get install python-opencv
```

Similar steps can be found for other OSes at https://opencv.org/. It is cross-platform and optimized for CPU-intensive applications. It has interfaces for several programming languages and is supported by Windows, Ubuntu, and Mac.