8 The asterisk will match zero or more of the preceding type in regex—for example, returning plurals.

9 Reliability is a technical term referring to the consistency of a given measure. Imagine asking students of a high school shop class to use a tape measure to cut a foot of lumber. We’d expect some variation in measurements. If that variation is low, we have high reliability. If instead of a tape measure, we gave each student a foot of yarn to use, we’d expect lower reliability.

Krippendorff's alpha
Subjects = 5
Raters = 3
alpha = 0.741

10 For example, if coders are tagging documents for mentions of "bats," they all need to know whether this means baseball gear or the adorable flying mammal.

peanuts and food allergy” by matching the terms ‘peanut,’’peanut allergy,’ ‘allergy,’’nut,*’ and ‘food allergy’ (2022:73).⁸

Another strategy is to rely on more people. The corpus is typically divided among the raters into partially overlapping sections. We can then calculate inter-rater reliability on any documents coded by two or more people. While there are many inter-rater reliability measures, we’ll use Krippendorf’s α (alpha): one minus the observed disagreement divided by the expected disagreement.9 We like this measure because it is not impacted by how many categories documents are sorted into or how many individuals do the sorting.

As an example, assume three researchers are reading the reviews of Lamming’s novels and tagging them for the concept of “ambiguity.” Say all three read each of five reviews. We’ll create a reviewer-by-document matrix for this below.

```
# create a matrix
mat <- matrix(0, nrow = 3, ncol = 5)
# add each reviewers tagging for "ambiguity"
mat[1, 1] <- c(1, 0, 1)
mat[2, ] <- c(0, 0, 0)
mat[3, ] <- c(1, 1, 0)
mat[4, ] <- c(0, 0, 0)
mat[5, ] <- c(1, 1, 1)

[,1] [,2] [,3] [,4] [,5]
[1,] 1 0 1 0 1
[2,] 0 0 1 0 1
[3,] 1 0 1 0 1
```

Let’s use kripp.alpha(). Our binary variable is a “nominal” variable, so we need to tell the function (output in the margin).

```
kripp.alpha(mat, method = "nominal")
```

The consensus threshold for high reliability is, generally, an α above 0.7. Falling below this threshold means we must align each rater’s interpretation of the task—or redefine the task.10 To help, we can build dictionaries for each concept with terms signaling the concept’s presence in the text. In the case of Griswold (1987), we could create a set of terms denoting a positive evaluation and a set indicating ambiguity. Once we build this dictionary, however, we can also use it to automatically tag the documents.

In “Soldiers, Mothers, Tramps and Others,” Mohr (1994) coded how relief organizations described their clientele and relief activities. He simplified this task by identifying key terms for each identity: “[T]he program searches each text string for the presence of a single word, in other cases, entire phrases were necessary to trigger a binary variable”