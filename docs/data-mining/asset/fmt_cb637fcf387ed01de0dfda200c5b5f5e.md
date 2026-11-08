
# Decision Tree Construction

The problem of constructing a decision tree can be expressed recursively. First, select an attribute to place at the root node, and make one branch for each possible value. This splits up the example set into subsets, one for every value of the attribute. Now the process can be repeated recursively for each branch, using only those instances that actually reach the branch. If at any time all instances at a node have the same classification, stop developing that part of the tree.

The only thing left is how to determine which attribute to split on, given a set of examples with different classes. Consider (again!) the weather data. There are four possibilities for each split, and at the top level they produce the trees in [Fig. 4.2](#Ch004_91-164_B9780443158889000054.xhtml#f0015) Which is the best choice? The number of `yes` and `no` classes are shown at the leaves. Any leaf with only one class—`yes` or `no`—will not have to be split further, and the recursive process down that branch will terminate. Because we seek small trees, we would like this to happen as soon as possible. If we had a measure of the purity of each node, we could choose the attribute that produces the purest daughter nodes. Take a moment to look at [Fig. 4.2](#Ch004_91-164_B9780443158889000054.xhtml#f0015) and ponder which attribute you think is the best choice.

![Fig. 4.2 Tree stumps for the weather data.](images/F000054f04-02-9780443158889.jpg)

Fig. 4.2 Tree stumps for the weather data.

The measure of purity that we will use is called the `information` and is measured in units called `bits`. Associated with a node of the tree, it represents the expected amount of information that would be needed to specify whether a new instance should be classified `yes` or `no`, given that the example reached that node. Unlike the `bits` in computer memory, the expected amount of information usually involves fractions of a bit—and is often less than one! It is calculated based on the number of `yes` and `no` classes at the node; we will look at the details of the calculation shortly. But first let’s see how it’s used. When evaluating the first tree in [Fig. 4.2](#Ch004_91-164_B9780443158889000054.xhtml#f0015), the number of `yes` and `no` classes at the leaf nodes are \[2, 3\], \[4, 0\], and \[3, 2\], respectively, and the information values of these nodes are:

$\\begin{matrix} {{Info}\\left( \\left\\lbrack 2,3 \\right\\rbrack \\right) = 0.971{bits}} \\\\ {{Info}\\left( \\left\\lbrack 4,0 \\right\\rbrack \\right) = 0.0{bits}} \\\\ {{Info}\\left( \\left\\lbrack 3,2 \\right\\rbrack \\right) = 0.971{bits}} \\\\ \\end{matrix}$<mml:math><mml:mtable><mml:mtr><mml:mtd><mml:mi mathvariant="normal">Info</mml:mi><mml:mrow><mml:mfenced open="(" close=")"><mml:mrow><mml:mfenced open="\[" close="\]"><mml:mrow><mml:mn>2,3</mml:mn></mml:mrow></mml:mfenced></mml:mrow></mml:mfenced></mml:mrow><mml:mo>=</mml:mo><mml:mn>0.971</mml:mn><mml:mi mathvariant="normal">bits</mml:mi></mml:mtd></mml:mtr><mml:mtr><mml:mtd columnalign="left"><mml:mi mathvariant="normal">Info</mml:mi><mml:mrow><mml:mfenced open="(" close=")"><mml:mrow><mml:mfenced open="\[" close="\]"><mml:mrow><mml:mn>4,0</mml:mn></mml:mrow></mml:mfenced></mml:mrow></mml:mfenced></mml:mrow><mml:mo>=</mml:mo><mml:mn>0.0</mml:mn><mml:mi mathvariant="normal">bits</mml:mi></mml:mtd></mml:mtr><mml:mtr><mml:mtd><mml:mi mathvariant="normal">Info</mml:mi><mml:mrow><mml:mfenced open="(" close=")"><mml:mrow><mml:mfenced open="\[" close="\]"><mml:mrow><mml:mn>3,2</mml:mn></mml:mrow></mml:mfenced></mml:mrow></mml:mfenced></mml:mrow><mml:mo>=</mml:mo><mml:mn>0.971</mml:mn><mml:mi mathvariant="normal">bits</mml:mi></mml:mtd></mml:mtr></mml:mtable></mml:math>

![Equation](images/F000054si35.png)

We calculate the average information value of these, taking into account the number of instances that go down each branch—five down the first and third and four down the second:

$\\begin{matrix} \\left. {Info}(\\left\\lbrack 2,3 \\right\\rbrack,\\left\\lbrack 4,0 \\right\\rbrack,\\left\\lbrack 3,2 \\right\\rbrack) = (5\\slash 14) \\times 0.971 + (4\\slash 14) \\times 0 + (5\\slash 14) \\times 0.971 = 0.693{bits}. \\right. \\\\ \\end{matrix}$<mml:math><mml:mtable width="336pt"><mml:mtr><mml:mtd><mml:mi mathvariant="normal">Info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>2,3</mml:mn><mml:mo>\]</mml:mo><mml:mo>,</mml:mo><mml:mo>\[</mml:mo><mml:mn>4,0</mml:mn><mml:mo>\]</mml:mo><mml:mo>,</mml:mo><mml:mo>\[</mml:mo><mml:mn>3,2</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo linebreak="nobreak">=</mml:mo><mml:mo stretchy="false">(</mml:mo><mml:mn>5</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>14</mml:mn><mml:mo stretchy="false">)</mml:mo><mml:mo>&#215;</mml:mo><mml:mn>0.971</mml:mn><mml:mo>+</mml:mo><mml:mo stretchy="false">(</mml:mo><mml:mn>4</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>14</mml:mn><mml:mo stretchy="false">)</mml:mo><mml:mo>&#215;</mml:mo><mml:mn>0</mml:mn><mml:mo>+</mml:mo><mml:mo stretchy="false">(</mml:mo><mml:mn>5</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>14</mml:mn><mml:mo stretchy="false">)</mml:mo><mml:mo>&#215;</mml:mo><mml:mn>0.971</mml:mn><mml:mo>=</mml:mo><mml:mn>0.693</mml:mn><mml:mi mathvariant="normal">bits</mml:mi><mml:mo>.</mml:mo></mml:mtd></mml:mtr></mml:mtable></mml:math>

![Equation](images/F000054si36.png)

This average represents the amount of information that we expect would be necessary to specify the class of a new instance, given the tree structure in [Fig. 4.2A](#Ch004_91-164_B9780443158889000054.xhtml#f0015).

Before any of the nascent tree structures in [Fig. 4.2](#Ch004_91-164_B9780443158889000054.xhtml#f0015) were created, the training examples at the root comprised nine `yes` and five `no` nodes, corresponding to an information value of

*I**n**f**o*(\[9,5\]) = 0.940*b**i**t**s*.<mml:math><mml:mi mathvariant="normal">Info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>9,5</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mn>0.940</mml:mn><mml:mi mathvariant="normal">bits</mml:mi><mml:mo>.</mml:mo></mml:math>

![Equation](images/F000054si37.png)

Thus the tree in [Fig. 4.2A](#Ch004_91-164_B9780443158889000054.xhtml#f0015) is responsible for an information gain of

$\\begin{matrix} {\\text{Gain}\\left( \\mathit{outlook} \\right) = {info}(\\lbrack 9,5\\rbrack) - {info}(\\left\\lbrack 2,3 \\right\\rbrack,\\left\\lbrack 4,0 \\right\\rbrack,\\left\\lbrack 3,2 \\right\\rbrack) = 0.940 - 0.693 = 0.247\\text{bits},} \\\\ \\end{matrix}$<mml:math><mml:mtable width="336pt"><mml:mtr><mml:mtd><mml:mtext>Gain</mml:mtext><mml:mo>(</mml:mo><mml:mi mathvariant="italic">outlook</mml:mi><mml:mo>)</mml:mo><mml:mo>=</mml:mo><mml:mi mathvariant="normal">info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo stretchy="false">\[</mml:mo><mml:mn>9,5</mml:mn><mml:mo stretchy="false">\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>&#8722;</mml:mo><mml:mi mathvariant="normal">info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>2,3</mml:mn><mml:mo>\]</mml:mo><mml:mo>,</mml:mo><mml:mo>\[</mml:mo><mml:mn>4,0</mml:mn><mml:mo>\]</mml:mo><mml:mo>,</mml:mo><mml:mo>\[</mml:mo><mml:mn>3,2</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo linebreak="nobreak">=</mml:mo><mml:mn>0.940</mml:mn><mml:mo>&#8722;</mml:mo><mml:mn>0.693</mml:mn><mml:mo>=</mml:mo><mml:mn>0.247</mml:mn><mml:mtext>bits</mml:mtext><mml:mo>,</mml:mo></mml:mtd></mml:mtr></mml:mtable></mml:math>

![Equation](images/F000054si38.png)

which can be interpreted as the informational value of creating a branch on the `outlook` attribute.

The way forward is clear. We calculate the information gain for each attribute and split on the one that gains the most information. In the situation of [Fig. 4.2](#Ch004_91-164_B9780443158889000054.xhtml#f0015),
