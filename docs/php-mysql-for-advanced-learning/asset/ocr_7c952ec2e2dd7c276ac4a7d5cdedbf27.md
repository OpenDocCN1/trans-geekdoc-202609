# Example

```
<?php
if(!file_exists("/docs/resume.txt"))
{
    die("File not found");
}
else
{
    $file = fopen("/docs/resume.txt","r");
}
?>
```

# Example:

```
<?php
$a = 0;
$b = 200;
$result = $b/$a;
echo "RESULT: ". $result;
?>
```

Output: Warning: Division by zero in ... on line 4

# Example:

```
<?php
echo "Hi lets learn PHP"
echo "<br/>This is another line";
?>
```

Output: Parse error: syntax error, unexpected 'echo' (T_ECHO), expecting ',' or ';' in ... on line 3