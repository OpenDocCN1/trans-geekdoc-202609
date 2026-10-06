# Expression Types

Regular expressions are used to identify patterns in data, similar to the Find option in Notepad, where you can press F3, type in a string to search for, and Find find it. Regular expressions do the exact same thing. Traditionally, they are used in the programming world or in the telephony world for detecting patterns in data or manipulating telephone numbers. For example is you can create a regular expression to detect a credit card number.

We are going to provide a quicker primer on regular expressions in the next few pages because they are extremely powerful. But first, we are going to show you how to detect a simple pattern-called Finance and upon detection of the Finance string within a document the regular expression will classify it appropriately.

+   1. For the purposes of this example, select String in the Expression Type field of the Classification Parameters dialog, because we are going to detect a string pattern within a document.
2. In the Expression field, type Finance and click OK.

# CREATING MULTIPLE RULES

You can have multiple evaluation parameters of different types. However, the file you are evaluating must match all the criteria specified, and evaluation happens only per file at runtime. If you need to search for and match multiple patterns, you will need to create multiple rules.

+   3. Now select the Evaluation Type tab, as shown in Figure 15.74.

FIGURE 15-74
Evaluation Type tab

![](bbox=[0.338, 0.546, 0.725, 0.903])