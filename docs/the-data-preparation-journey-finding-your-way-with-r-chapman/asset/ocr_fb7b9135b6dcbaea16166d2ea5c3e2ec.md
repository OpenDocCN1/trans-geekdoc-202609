+   - Project Intro/Objective
+   - Project Description
+     - A missing component is “Data source”.
+   - Team (with contact information)

For an analytic project that has been completed, you might also want to include the high-level findings. This might be something akin to an abstract in an academic journal article or an executive summary in a business or government report.

Another source of tips is “Art of README”². Although it’s aimed at people writing computer programs and modules, the lessons apply to data science projects as well. The purpose of a README is to:

+   1. Tell them what it is (with context).
+   2. Show them what it looks like in action.
+   3. Show them how they use it.
+   4. Tell them any other relevant details.

An example is the R package {palmerpenguins} which has a comprehensive README on the github page.³

# 3.4.2 Capturing the directory structure

Your documentation (perhaps as part of the README file) can include a diagram that shows the directory structure. The package {fs} (Hester et al., 2020) has a function dir_tree() that will create a dendogram of the file folder structure and files in your project folder.

```
```r
library(fs)
```
```

The default is to show all of the sub-folders and files below the current directory.

```
```r
fs::dir_tree(path = "project_template")
```
```

## project_template