+   - The **array_slice()** function returns a portion of the given array according to the specified parameters. It does not modify the original array, but returns a new version of the array with the selected elements.

Here is the general syntax of the array_slice() function:

```
array_slice($array, $start, $length = null, $preserve_keys = false)
```

+   - $array: The original table from which to extract a portion.
+   - $start: The starting index from which to extract elements.
+   - $length: The number of elements to be extracted. If this parameter is omitted, all elements from $start will be included.
+   - $preserve_keys: A Boolean indicating whether associative keys should be retained in the resulting array. By default, keys are re-indexed from zero.

Here's an example of how to use array_slice():

```
<?php
```