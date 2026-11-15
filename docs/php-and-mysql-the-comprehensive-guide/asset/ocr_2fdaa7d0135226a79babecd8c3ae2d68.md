```
"Miements" : 120,
"Rheinwerk" : 504
}
}'; 
var_dump(json_validate($json));
?>
```

# Listing 27.3 JSON ("json_validate.php")

In this case, the result is true because the JSON is valid. This can be changed quickly with a small change as in the next listing. It is difficult to see the difference; only a comma is missing after the "Miemens" entry.

```
$json = '{
    "shares" : {
        "Miements" : 120
        "Rheinwerk" : 504
    }
}'; 
json_validate($json);
echo json_last_error() . " " . json_last_error_msg();
```

# Listing 27.4 JSON ("json_validate_error.php")

json_validate() itself does not return any error messages. PHP offers two other methods for this: json_last_error() and json_last_error_msg(). In this example, json_last_error() returns status code 4 and json_last_error_msg() returns the "Syntax error" message. See Table 27.1 for the JSON error codes.

| Constants | Code | Description |
|---|---|---|
| JSON_ERROR_NONE | 0 | There is no error. |
| JSON_ERROR_DEPTH | 1 | The JSON was deeper than the maximum depth. |
| JSON_ERROR_STATE_MISMATCH | 2 | No correct JSON. |
| JSON_ERROR_CTRL_CHAR | 3 | CTRL character error. |
| JSON_ERROR_SYNTAX | 4 | A syntax error—the most common type of error. |
| JSON_ERROR_UTF8 | 5 | Error validating UTF-8 characters. |
| JSON_ERROR_RECURSION | 6 | Recursive references within the JSON. |

Table 27.1 The JSON Error Codes