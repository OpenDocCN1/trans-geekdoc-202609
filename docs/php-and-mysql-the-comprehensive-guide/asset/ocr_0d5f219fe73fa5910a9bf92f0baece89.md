parameter is also optional and allows you to add a prefix to the variable name. This allows you to clearly identify the newly generated variables and thus avoid overlaps completely. The mode determines whether a prefix is used.

| Mode | Description |
|---|---|
| EXTR_OVERWRITE | The existing variable is always overwritten (default setting). |
| EXTR_SKIP | The existing variable is always retained. |
| EXTR_PREFIX_SAME | If two variables match, the new one from the array receives the prefix (third parameter). |
| EXTR_PREFIX_ALL | Provides all variables with a prefix. |
| EXTR_PREFIX_INVALID | Prefixes variables for which the index is an invalid variable name. This includes numerical indices. |
| EXTR_IF_EXISTS | Only sets a variable if it already exists. The old one is overwritten. |
| EXTR_PREFIX_IF_EXISTS | Only sets a variable if it already exists. However, uses a prefix for the new variable. The old one is retained. |
| EXTR_REFS | Extracts the variables as a reference. This means that they still refer to the array. extract($stockprices, EXTR_REFS); $stockprices["Miemens"] = 45; |

Table 8.1 Modes for "extract()"

The compact(Variable, Variable ...) function is the counterpart to extract(). The function can contain a flexible number of variable names as strings. The variable names can also be in one or more arrays. A check is made for all these variable names to see whether a variable exists. This is then stored in an associative array.

In addition to this function, there are also others that create an array automatically:

+   array_fill(start_index, number, value) fills an array starting at start_index with the number of elements specified under number. They all receive the third parameter as a value.

+   range(Min, Max, Step) creates an array with the values from Min to Max. Min and Max can also be swapped. The third parameter defines the intermediate steps.

# 8.4.5 Dereferencing

Dereferencing means that you can directly access the individual elements in an array. This also applies if the array has just been created:

```
echo ['Monday', 'Tuesday', 'Wednesday'][0];
```