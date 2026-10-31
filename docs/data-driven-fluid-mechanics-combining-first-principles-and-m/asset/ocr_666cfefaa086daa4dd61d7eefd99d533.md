folder) to get the path, unlike other common GUIs where the user only have to click once. This is exemplified in Figure 14.5, which shows how the cylinder_wake folder is (a) wrongly and (b) correctly selected.

# Configuration file and execution steps

The configuration file contains all the processes and their options to be executed: the tools that will be used (PIV conversion, domain reduction, ...), the steps that will be executed, and the parameters for each of these steps. It is the only required control input from the user. All capabilities of xROM can be set up in this configuration file.

The general form of an input is

```
<parameter> : <value>
```

The detailed specifications are the following:

+   - There is only one parameter and its value per line.
+   - The parameter and its value are separated by a colon “:.”
+   - The spaces in the line are irrelevant.
+   - The position of a line in the file does not matter: it is for instance the same if a parameter is defined in the first line or the last line.
+   - To deactivate an option, the user must add the comment symbol “#” at the beginning of the line.

The standard process of xROM is divided into three main steps:

+   1. Galerkin expansion,
+   2. Galerkin projection,
+   3. dynamical system.

Each of these steps contains its owns options and tools in the configuration file. The user can selectively execute individual steps. It is possible, for instance, to compute only the Galerkin expansion or the Galerkin expansion and the projection without the dynamical system.

# 14.5.3 Exercises

As already mentioned in Section 14.5.1, we shall use DNS snapshots of a cylinder flow, which are included in the package under CylinderWake/InputData/Snapshots. Since all three exercises use the same data set, we shall use the same case folder and simply generate (automatically) a different run directory for each exercise. Before each run, we shall make the necessary modifications to the configuration file.

# Exercise 1: Galerkin Expansion of the Cylinder flow

In this first exercise, we perform a POD on the computed snapshots. The configuration file for this exercise is located under CylinderWake/ConfigFile, which you can open with any text editor. Most of the options are self-explanatory. For more details, you are referred to the user manual.