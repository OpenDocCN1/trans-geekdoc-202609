```
echo <*this is a simple string>;
```

```
echo <You can also have embedded newlines in
strings this way as it is
okay to do>;
```

```
// Outputs: Arnold once said: "I'll be back"
echo <Arnold once said: "\I\>ll be back>>;
```

```
// Outputs: You deleted C:\*.*?
echo <You deleted C:\*.*?>;
```

```
// Outputs: You deleted C:\*.*?
echo <You deleted C:\*.*?>;
```

```
// Outputs: This will not expand: \n a newline
echo <This will not expand: \n a newline>
```

```
// Outputs: Variables do not expand $either
echo <Variables do not expand $either>
?>
```

# 4.1.2 Double quoted

If the string is enclosed in double-quotes (""), PHP will interpret the following escape sequences for special characters:

| Escaped characters | Meaning |
| --- | --- |
| \n | linefeed (LF or 0x0A (10) in ASCII) |
| \r | carriage return (CR or 0x0D (13) in ASCII) |
| \t | horizontal tab (HT or 0x09 (9) in ASCII) |
| \v | vertical tab (VT or 0x0B (11) in ASCII) (since PHP 5.2.5) |