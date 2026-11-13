# TABLE F-3 ARRAY FUNCTIONS

| Function | Return Value | Action |
| :--- | :--- | :--- |
| krsort(array array_arg [, int sort_flags]) | bool | Sorts an array by key value in reverse order |
| ksort(array array_arg [, int sort_flags]) | bool | Sorts an array by key |
| count(mixed var [, int mode]) | int | Counts the number of elements in a variable (usually an array) |
| natsort(array array_arg) | void | Sorts an array using natural sort |
| natcasesort(array array_arg) | void | Sorts an array using case-insensitive natural sort |
| asort(array array_arg [, int sort_flags]) | bool | Sorts an array and maintains index association |
| arsort(array array_arg [, int sort_flags]) | bool | Sorts an array in reverse order and maintains index association |
| sort(array array_arg [, int sort_flags]) | bool | Sorts an array |
| rsort(array array_arg [, int sort_flags]) | bool | Sorts an array in reverse order |
| usort(array array_arg, string cmp_function) | bool | Sorts an array by values using a user-defined comparison function |
| uasort(array array_arg, string cmp_function) | bool | Sorts an array with a user-defined comparison function and maintains index association |
| uksort(array array_arg, string cmp_function) | bool | Sorts an array by keys using a user-defined comparison function |