# Part III: A Real-World Case Study

+   - [ ] Functionality: Desirable (out of scope and chargeable)
+   - [ ] Functionality: Incorrect
+   - [ ] Functionality: Malfunction
+   - [ ] Functionality: Missing (but detailed in specification)
+   - [ ] Functionality: User Interface
+   - [ ] Project Management and Administration
+   - [ ] Database Schema
+   - [ ] Systems and Infrastructure

After you have created a set of categories, you can easily reuse these on future projects by using the Copy Categories From and Copy Categories To buttons judiciously. These can be found by editing the categories on a project (select Manage ⇔ Manage Projects) and then scrolling to the very bottom of the list of the existing categories you are maintaining. You will probably find that a universal list of categories similar to the preceding will serve you well in any future projects upon which you might embark.

With your project set up, you may need to select it whenever you log into Mantis in the future, especially if you have more than one project on the system. The small drop-down list box in the top-right corner of the screen enables you to flip among projects by name.

# Reporting Bugs

Now that you have the project set up, you and your team can start entering bugs that were found. Be sure to translate any faults into more specific tasks, rather than simply announce the problem. For example, “Move the pagination bar from the bottom to the top of the page,” is more productive than “The pagination bar is in the wrong place.”

To report a bug, simply select Report Bug from the main navigation.

You must select a category for the bug. This list will be generated dynamically from the selection of categories you entered earlier.

Other information you need to enter includes the following:

+   - [ ] Reproducibility — If this is a fault, rather than a simple request, state how frequently the problem can be reproduced. If this is a request for a new feature, select N/A, because there is nothing to reproduce.
+   - [ ] Severity — This list is hard-coded into Mantis and relates to the impact the fault is having on the project. Most of these are self-explanatory. Feature refers to a fault at the feature-level and implies that a key feature is either missing or rendered completely unusable by the fault. Block means that other testing is being held up as a result of this fault.
+   - [ ] Priority — This indicates a relative severity level for the fault to be attended to by the development team.
+   - [ ] Summary — This is a brief, one-line summary of the fault or, if there is insufficient space, the area in which the fault is developing (for example, “Auto-completion of text fields when replying to e-mails”).