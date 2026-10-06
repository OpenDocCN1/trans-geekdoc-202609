# 1.8.3 Packages

```
import sys
sys.path.append('/some/path/')
```

Finally, math is Python's standard math module, including amongst other functions, operations for rounding up or down:

```
import math
x=2.2 ; y=4
round_up=math.ceil(x)
round_up=math.floor(x)
```

Python packages are collections of related classes and modules designed to solve some broad category of tasks. A wide variety of externally supported and well-documented packages exist to meet a variety of advanced programming requirements. Examples of some that will be in this module include:

+   * NumPy[32]¹³—a package for scientific computing with functionality for fast manipulation of arrays, and powerful numerical computing tools [19]
* Matplotlib[20]¹⁴—a plotting label designed to mimic the plotting behavior of MATLAB;
* Scikit Learn¹⁵—a powerful toolbox with broad implementation of machine learning methodology and intuitive API [6,34];
* Pandas¹⁶tool for creating and manipulating complex tabulated data sheets [50];
* Nibabel¹⁷—a library for reading and writing to medical image-file formats.

We will learn more about these packages in due course, starting with NumPy in the subsequent Sect. 1.9. Note, where developed code utilizes such packages, it is very important to cite them in the resulting projects and papers.

# Installing packages

Assuming you have installed Anaconda, then all the just-listed packages (with the exception of Nibabel) should be already installed. However, for other packages, like Nibabel, there are two ways to install: either through Anaconda:

```
conda install -c conda nibabel
```

> ¹³ http://www.NumPy.org/
¹⁴ https://matplotlib.org/
¹⁵ https://scikit-learn.org/
¹⁶ https://pandas.pydata.org/
¹⁷ http://nipy.org/nibabel/
¹⁸ https://www.scipy.org/citing.html.