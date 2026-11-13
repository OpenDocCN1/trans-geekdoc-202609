should be obvious even though we haven’t made up any examples. Since the given family tree does not contain any child whatsoever, it cannot contain one with "blue" as the eye color. Hence the result in the first cond clause is #false.

For the second cond clause, the design requires a lot more work. Again following the design recipe, we first remind ourselves what the expressions in the template accomplish:

+   1. according to the purpose statement for the function,
+   
+      (blue-eyed-child? (child-father an-ftree))
+   
+      determines whether some child in the father’s FT has "blue" eyes;
+   
+   2. likewise, (blue-eyed-child? (child-mother an-ftree)) determines whether someone in the mother’s FT has blue eyes; and
+   
+   3. the selector expressions (child-name an-ftree), (child-date an-ftree), and (child-eyes an-ftree) extract the name, birth date, and eye color from the given child structure, respectively.

Now we just need to figure out how to combine these expressions.

Clearly, if the child structure contains "blue" in the eyes field, the function’s answer is #true. Next, the expressions concerning names and birth dates are useless, which leaves us with the recursive calls. As stated, (blue-eyed-child? (child-father an-ftree)) traverses the tree on the father’s side, while the mother’s side of the family tree is processed with (blue-eyed-child? (child-mother an-ftree)). If either of these expressions returns #true, an-ftree contains a child with "blue" eyes.

Our analysis suggests that the result should be #true if one of the following three expressions is #true:

+   • (string=? (child-eyes an-ftree) "blue")
+   
+   • (blue-eyed-child? (child-father an-ftree))
+   
+   • (blue-eyed-child? (child-mother an-ftree))

which, in turn, means we need to combine these expressions with or: