Machine Learning

Chapter 4: Getting Started with Python & Turi Create

Enter this command to install the turicreate package:

```
pip install -U turicreate==5.8
```

This downloads and installs the newest available version of the turicreate package, which lets us use the Vision framework model for transfer learning.

# List pip-installed packages

In Terminal, use this command to list all of the packages in the active environment or a specific package:

```
conda list
conda list coremltools
```

You need the coremltools package to create Core ML models from Turi Create models. Installing turicreate also installs coremltools.

The output of the second command looks similar to this:

```
# packages in environment /Users/amt1/anaconda3/envs/mlenv:
#
# Name Version
Channel Build
coremltools 3.0 <pip>
```

The Build Channel value <pip> shows coremltools was installed with pip, not conda.

> Note: If you give a quick look at the turienv environment in Navigator; it still shows only 105 packages. That's packages installed with pip don't show up in Navigator.

# Turi Create notebook

> Note: If you skipped the manual environment setup and imported turienv.yaml into Anaconda Navigator, use the Jupyter Launch button on Anaconda Navigator Home Tab instead of the command line below, then navigate in the browser to starter/notebook.

raywenderlich.com

144