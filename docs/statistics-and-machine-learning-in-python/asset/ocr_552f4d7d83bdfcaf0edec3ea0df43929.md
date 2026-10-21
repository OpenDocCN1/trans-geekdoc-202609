```
conda install seaborn
# install a specific version from anaconda chanel
conda install -c anaconda pyqt=4.11.4
```

List installed packages

```
conda list
```

Search available packages

```
conda search pyqt
conda search scikit-learn
```

# 1.2.3 Environments

+   - A conda environment is a directory that contains a specific collection of conda packages that you have installed.
+   - Control packages environment for a specific purpose: collaborating with someone else, delivering an application to your client,
+   - Switch between environments

List of all environments

:: conda info –envs

+   1. Create new environment
+   2. Activate
+   3. Install new package

```
conda create --name test
# Or
conda env create -f environment.yml
source activate test
conda info --envs
conda list
conda search -f numpy
conda install numpy
```

# 1.2.4 Miniconda

Anaconda without the collection of (>700) packages. With Miniconda you download only the packages you want with the conda command: conda install PACKAGENAME

+   1. Download anaconda (Python 3.x) https://conda.io/miniconda.html
+   2. Install it, on Linux

```
bash Miniconda3-latest-Linux-x86_64.sh
```

3. Add anaconda path in your PATH variable in your .bashrc file: