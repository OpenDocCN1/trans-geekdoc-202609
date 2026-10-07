disease in a patient who actually has it.

The consequences of these errors vary by context. In medical diagnosis, a false negative might be more critical than a false positive. However, in spam detection, false positives (marking legitimate emails as spam) might be more problematic.

The numbers of errors are often shown in a simple table called a **confusion matrix**. It shows how well your model's predictions align with the actual outcomes in your data. If we use the spam emails example, when detecting an email as spam we can have one of four outcomes:

+   1. We mark it as spam, and it is – got it right.

+   2. We mark it as spam, and it isn’t – got it wrong (false positive).

+   3. We do not mark it spam, and it is – got it wrong (false negative).

+   4. We do not mark it spam, and it isn’t – got it right.