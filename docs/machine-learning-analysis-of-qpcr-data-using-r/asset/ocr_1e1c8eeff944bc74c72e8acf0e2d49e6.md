The data frame validation has a new set of columns derived from the results provided by the raters (rater_1, rater_2, in this case). A new column agreed is created by comparing the values of the different raters. If all the rates across the different rating columns are the same, a label of value equal to the agreed rate (1 or 0) is given, otherwise -1. The data with the agreement label 1 are plotted and those with label 0 are drawn on top of them. The entries are stratified by factor.

```
The function readline reads an input directly from the terminal. The function as.factor is used to encode a vector as a factor. The levels of each factor and an associated label can be provided. The associated function is.function tests if a vector is stratified in factors. The low-level graphical function grid adds a rectangular grid to a plot.
readline(prompt)
prompt
optional string to be displayed on screen.
as.factor(x, levels, labels, exclude, ordered, nmax)
x
a data vector.
levels
optional character vector of unique values.
labels
optional character vector of labels for the levels.
exclude
a vector of values to be excluded.
ordered
logical flag to determine if the levels should be regarded as ordered.
nmax
maximum number of levels.
grid(x, y, ...)
x, y
number of lines on the x or y axis. The default value (NULL) links these to the major ticks of the axis. The y value is optional, forcing y = x.
```

# Listing 3.7.

A new directory data is created to store in an ordered way the files that will be required for the k-mean classification. The analysis is limited to the reactions where the raters agreed, which is obtained by indexing the data frame so that the uncertain reactions are excluded (df$label != "Uncertain"). The k-mean validation is obtained by generating 10 sets of data frames, stored in the new folder data. Each set contains a training data frame with 80% of the reactions and a testing data frame with 20% of the data. These sets contain the identification numbers of each reaction (index). The data sets are saved as RDS objects as an alternative to textual files and to reduce space in the hard disk.

Since the column label originally contained three levels (positive, negative, and uncertain) but now only has two levels (positive, and negative), the factors are overwritten with only two levels.

To give an example of the procedure, only the first set of data I loaded into memory using the variable i. The reactions with the index included in the testing data set are selected and stored in a new data frame (train_set); the same is done for the testing set. A new column is made by assigning 'negative' to the reactions without fluorescent signal, otherwise 'positive'; the classification is stratified by label.

```
The function dir.create creates a new directory in a specified path. An alternative to store tables is to use R objects; these are compressed files that are read faster into memory and maintain additional characteristics such as levels. The R objects are written and read wit saveRDS and readRDS, respectively, and have the extension '.rds'.
The function round rounds a fractional number to a specified decimal value. The associated functions are trunc, floor and ceiling. The function length returns the number of elements or levels of a vector. The function sample randomly extracts elements from a vector.
saveRDS(x, path)
readRDS(path)
x
an object to be saved.
path
a string containing the path and name of the object.
round(x, digits)
x
a floating point number.
digits
the number of decimals required.
```