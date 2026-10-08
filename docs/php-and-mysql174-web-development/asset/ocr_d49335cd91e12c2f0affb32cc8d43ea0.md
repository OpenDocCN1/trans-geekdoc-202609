# Making Decisions with Conditionals

This HTML code adds a new form variable (called find) whose value will be 'a', 'b', 'c', or
'd'. You could handle this variable with a series of if and elseif statements like this:

```
if ($find == "a") {
    echo "<p>Regular customer.</p>";
} elseif ($find == "b") {
    echo "<p>Customer referred by TV advert.</p>";
} elseif ($find == "c") {
    echo "<p>Customer referred by phone directory.</p>";
} elseif ($find == "d") {
    echo "<p>Customer referred by word of mouth.</p>";
} else {
    echo "<p>We do not know how this customer found us.</p>";
}
```

Alternatively, you could write a switch statement:

```
switch($find) {
    case "a":
        echo "<p>Regular customer.</p>";
        break;
    case "b":
        echo "<p>Customer referred by TV advert.</p>";
        break;
    case "c":
        echo "<p>Customer referred by phone directory.</p>";
        break;
    case "d":
        echo "<p>Customer referred by word of mouth.</p>";
        break;
    default:
        echo "<p>We do not know how this customer found us.</p>";
        break;
}
```

(Note that both of these examples assume you have extracted $find from the $_POST array).

The switch statement behaves somewhat differently from an if or elseif statement. An if statement affects only one statement unless you use curly braces to create a block of statements. A switch statement behaves in the opposite way. When a case in a switch is activated, PHP executes statements until it reaches a break statement. Without a break statement, a switch would execute all the code following the case that was true. When a break statement is reached, the next line of code after the switch statement is executed.

# Comparing the Different Conditionals

If you are not familiar with the statements described in the preceding sections, you might be asking, “Which one is the best?”