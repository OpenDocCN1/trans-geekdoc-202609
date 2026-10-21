```
export PATH=${HOME}/miniconda3/bin:$PATH
```

# 4. Install required packages

```
conda install -y scipy
conda install -y pandas
conda install -y matplotlib
conda install -y statsmodels
conda install -y scikit-learn
conda install -y sqlite
conda install -y spyder
conda install -y jupyter
```

# 1.3 Commands

python: python interpreter. On the dos/unix command line execute wholes file:

```
python file.py
```

Interactive mode:

```
python
```

Quite with CTL-D

ipython: advanced interactive python interpreter:

```
ipython
```

Quite with CTL-D

pip alternative for packages management (update -U in user directory --user):

```
pip install -U --user seaborn
```

For neuroimaging:

```
pip install -U --user nibabel
pip install -U --user nilearn
```

spyder: IDE (integrated development environment):

+   - Syntax highlighting.
+   - Code introspection for code completion (use TAB).
+   - Support for multiple Python consoles (including IPython).
+   - Explore and edit variables from a GUI.
+   - Debugging.
+   - Navigate in code (go to function definition) CTL.

3 or 4 panels: