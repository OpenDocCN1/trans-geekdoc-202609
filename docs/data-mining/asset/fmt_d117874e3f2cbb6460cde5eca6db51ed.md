
To build a decision tree click the `Classify` tab to access WEKA’s classification and regression schemes. In the `Classify` panel select the classifier by clicking the `Choose` button at the top left, opening up the `trees` section of the hierarchical menu that appears, and finding `J48`. The menu structure represents the organization of the WEKA code into modules and the items you need to select are always at the lowest level. Once selected `J48` appears in the line beside the `Choose` button, along with its default parameter values. If you click that line the `J48` classifier’s object editor opens up and you can see what the parameters mean and alter their values if you wish. The Explorer generally chooses sensible defaults.

Having chosen the classifier, invoke it by clicking the `Start` button. WEKA works for a brief period—when it is working, the little bird at the lower right of the Explorer jumps up and dances—and then produces the output for `J48`.

## Examining the output

At the beginning of the output is a summary of the dataset and the fact that 10-fold cross-validation was used to evaluate it. That is the default and if you look closely at the `Classify` panel you will see that the `Cross-validation` box at the left is checked. Then comes a pruned decision tree in textual form. The model shown here is always the one generated from the full dataset available from the `Preprocess` panel.

The next part of the output gives estimates of the tree’s predictive performance. In this case they are obtained using stratified cross-validation with 10 folds. With the classification error the evaluation module outputs several other performance statistics.

The `Classify` panel has other test options: `Use training set`, which is generally not recommended; `Supplied test set`, in which you specify a separate file containing the test set; and `Percentage split`, with which you can hold out a certain percentage of the data for testing. You can output the predictions for each instance by clicking the `More options` button and checking the appropriate entry. There are other useful options, such as suppressing some output and including other statistics such as entropy evaluation measures and cost-sensitive evaluation.

## Working with models

The small pane at the lower left of the `Classify` panel, which contains one highlighted line, is a history list of the results. The Explorer adds a new line whenever you run a classifier. To return to a previous result set click the corresponding line and the output for that run will appear in the Classifier Output pane. This makes it easy to explore different classifiers or evaluation schemes and revisit the results to compare them.

When you `right-click` an entry a menu appears that allows you to view the results in a separate window or save the result buffer. More importantly, you can save the model that WEKA has generated in the form of a Java object file. You can reload a model that was saved previously, which generates a new entry in the result list. If you now supply a test set you can reevaluate the old model on that new set.

Several items on the right-click menu allow you to visualize the results in various ways. At the top of the Explorer interface is a separate `Visualize` tab but that is different; it shows the dataset not the results for a particular model. By right-clicking an entry in the history list you can see the classifier errors. If the model is a tree or a Bayesian network you can see its structure. You can also view the margin curve and various cost and threshold curves and perform a cost/benefit analysis.

## Exploring the Explorer

We have briefly investigated two of the six tabs at the top of the Explorer. In summary, here is what all the basic tabs do:

1. `Preprocess`: Choose the dataset and modify it in various ways.
2. `Classify`: Train learning schemes that perform classification or regression and evaluate them.
3. `Cluster`: Learn clusters for the dataset.
4. `Associate`: Learn association rules for the data and evaluate them.
5. `Select attributes`: Select the most relevant aspects in the dataset.
6. `Visualize`: View different two-dimensional plots of the data and interact with them.

Each tab gives access to a whole range of facilities. In our tour so far we have barely scratched the surface of the `Preprocess` and `Classify` panels.

At the bottom of every panel is a `Status` box and a `Log` button. The status box displays messages that keep you informed about what is going on. For example, if the Explorer is busy loading a file the status box will say so. Right-clicking anywhere inside this box brings up a little menu with two options: display the amount of memory available to WEKA and run the Java garbage collector. Note that the garbage collector runs constantly as a background task anyway.

Clicking the `Log` button opens a textual log of the actions that WEKA has performed in this session with timestamps.

As noted earlier, the little bird at the lower right of the window jumps up and dances when WEKA is active. The number beside the × shows how many concurrent processes are running. If the bird is standing but stops moving it is sick! Something has gone wrong, and you may have to restart the Explorer.

### Loading and filtering files

Along the top of the `Preprocess` panel are buttons for opening files, URLs, and databases. Initially only files whose names end in `*.arff` appear in the file browser; to see others change the `Format` item in the file selection box.

Data can be saved in various formats using the `Save` button in the `Preprocess` panel. It is also possible to generate artificial data using the `Generate` button. Apart from loading and saving datasets the `Preprocess` panel also allows you to filter them. Clicking `Choose` (near the top left) in the `Preprocess` panel gives a list of filters. We will describe how to use a simple filter to delete specified attributes from a dataset—in other words, to perform manual attribute selection. The same effect can be achieved more easily by selecting the relevant attributes using the tick boxes and pressing the `Remove` button. Nevertheless we describe the equivalent filtering operation explicitly, as an example.

`Remove` is an unsupervised attribute filter, and to see it you must first expand the `unsupervised` category and then the `attribute` category. This will reveal quite a formidable list of filters, and you will have to scroll further down to find `Remove`. When selected it appears in the line beside the `Choose` button, along with its parameter values—in this case the line reads simply “Remove.” Click that line to bring up a generic object editor with which you can examine and alter the filter’s properties.

To learn about it click the `More` button. This explains that the filter removes a range of attributes from the dataset. It has an option, `attributeIndices`, that specifies the range to act on and another called `invertSelection` that determines whether the filter selects attributes or deletes them. There are boxes for both of these in the object editor. After configuring an object it is often worth glancing at the resulting command-line formulation that the Explorer sets up, which is shown next to the `Choose` button.

Algorithms in WEKA may provide information about what data characteristics they can handle and, if they do, a `Capabilities` button appears underneath `More` in the generic object editor. Clicking it brings up information about what the method can do. In this case it states that `Remove` can handle many attribute characteristics, such as different types (nominal, numeric, relational, etc.) and missing values. It shows the minimum number of instances that are required for `Remove` to operate on.
