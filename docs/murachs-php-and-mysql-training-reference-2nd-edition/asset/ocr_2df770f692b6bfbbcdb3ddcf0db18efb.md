# How to match assertions

| Pattern | Meaning |
|---|---|
| (?=assertion) | Creates a look-ahead assertion |
| (?!assertion) | Creates a negative look-ahead assertion |

# Two subpatterns for look-ahead assertions

```
(?=[:digit:])      // The next character in the pattern must be a digit
(?=.*[:digit:])    // The pattern must contain at least one digit
```

# How to create a look-ahead assertion

# A look-ahead assertion

```
$pattern = '/^(?=.*[:digit:])[:alnum:]{6}$/';
preg_match($pattern, 'Harris')      // Assertion fails and returns 0
preg_match($pattern, 'Harri5')      // Matches and returns 1
```

# A negative look-ahead assertion

```
$pattern = '/^(?!3[2-9])[0-3][:digit:]$ /';
preg_match($pattern, '32')      // Assertion fails and returns 0
preg_match($pattern, '31')      // Matches and returns 1
```

# A pattern to enforce password complexity

# The full pattern

```
$pw_pattern = '/^(?=.*[:digit:])(?=.*[:punct:])[:print:]{6,}$/';
```

# The parts of the pattern

```
^                 // From the start of the string
(?=.*[:digit:])    // Must contain at least one digit
(?=.*[:punct:])    // Must contain at least one punctuation character
[:print:]{6,}      // Must contain six or more printable characters
$                  // With nothing else until the end of the string
```

# Using the pattern

```
$password1 = 'sup3rsecret';
$password2 = 'sup3rse(ret';
preg_match($pw_pattern, $password1)      // Assertion fails and returns 0
preg_match($pw_pattern, $password2)      // Matches and returns 1
```

# Description

+   - A look-ahead assertion is a special type of subpattern that must be matched for the overall pattern to be matched.
+   - A look-ahead assertion must be matched starting immediately after the position of the assertion in the pattern.
+   - A negative look-ahead assertion is similar to a look-ahead assertion except that its pattern must not be matched.