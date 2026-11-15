# 10.2.2 Further Functions

In addition to preg_match(), there are several other functions that allow further operations in addition to the simple search, as listed in Table 10.1.

| Function | Description |
| :--- | :--- |
| preg_split (RegEx, String, Limit, Mode) | Splits a string at the separators specified as the RegEx pattern. Returns an array whose individual elements are the components without separators. If Limit is set, only the number of separators specified there is executed. The last element then contains the rest of the string. -1 means no limit. You need this if you set a mode as the last parameter. The following options are available here: \n- PREG_SPLIT_NO_EMPTY omits empty parts when splitting. \n- PREG_SPLIT_DELIM_CAPTURE also returns individual results from areas of the RegEx in brackets. \n- PREG_SPLIT_OFFSET_CAPTURE returns the position. |
| preg_replace (RegEx, replacement, element, limit, number) | Replaces the pattern with the replacement. The function returns the result. The limit specifies how many replacements are to be performed. Number returns the number of replacements. preg_replace() also replaces expressions in arrays: \n``` \n$data = array("Hanno", "Anne"); \n$reg = "/nn/"; \n$result = preg_replace($reg, "ll", $data); \n``` \nIn the $result array, Hanno becomes Hallo and Anne becomes Alle. |
| preg_replace_callback (RegEx, function, element, limit, number) | Works like preg_replace(), except that this function executes a function instead of a replacement string. |
| preg_grep (RegEx, Array, Mode) | Searches for a regular expression within an array. Returns an array with the results. You can specify PREG_GREP_INVERT for the optional mode parameter. The elements that are not contained in the array are then returned. |
| preg_quote (expression, separator) | Evaluates the pattern characters of the regular expression. As an optional second parameter, you can specify a character to be used as a separator before and after the regular expression. This is usually the slash (/). |

Table 10.1 Perl-Compatible RegEx Functions