environment and name it tf_env (you can name it whatever you like). Run the following command in your Terminal, shell or Anaconda Command Prompt: 2. 3

2 Windows users should run the Anaconda Command Prompt as Administrator,

3 If you have a computer with an NVIDIA GPU thats compatible with TensorFlow, you can replace the tensorflow library with tensorflow-gpu to get better performance. For more information, see https://www.tensorflow.org/install/gpu. Some AMD GPUs also can be used with TensorFlow: http://timdettmers.com/2018/11/05/which-gpu-or-deep-learning/.

lick here to view code image

```
conda create -n tf_env tensorflow anaconda ipython jupyterlab scikit-learn matp
```

his will determine the listed libraries' dependencies, then display all the libraries that will be installed in the new environment. There are many dependencies, so this may take a few minutes. When you see the prompt:

```
Proceed ([y]/n)?
```

press Enter to create the environment and install the libraries. 4

4 When we created our custom environment, conda installed Python 3.6.7, which was the most recent Python version compatible with the tensorflow library.

# Activating an Alternate Anaconda Environment

To use a custom environment, execute the conda activate command:

```
conda activate tf_env
```

This affects only the current Terminal, shell or Anaconda Command Prompt. When a custom environment is activated and you install more libraries, they become part of the activated environment, not the base environment. If you open separate Terminals, shells or Anaconda Command Prompts, they'll use Anaconda's base environment by default.

# Deactivating an Alternate Anaconda Environment

When you're done with a custom environment, you can return to the base environment in the current Terminal, shell or Anaconda Command Prompt by executing:

```
conda deactivate
```

# Jupyter Notebooks and JupyterLab

This chapter's examples are provided only as Jupyter Notebooks, which will make it easier for you to experiment with the examples. You can tweak the options we present and reexecute