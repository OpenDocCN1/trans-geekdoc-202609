# Introduction

# xxxiii

scripts will live inside the folder designated to hold Web pages. For Apache, this will usually be /htdocs.

# BASIC SYNTAX

One thing about PHP is that it lets you move between straight HTML and commands that are part of the PHP programming language. It works like this: The sections of your script between the opening tag <?php and a closing tag ?> will be interpreted by the PHP engine, and portions not within these tags will be treated as plain HTML. Check out the following PHP page.

```
<php
echo "Hi.";
?>
```

When run through the Web server, this would create a Web page that prints, simply, "Hi, mom." PHP's echo command manages the first part of the line. But, of course, PHP can go quite bit more than that. Like any programming language, it can work with variables and make decisions.

```
?php
echo "hi, mom.";
```

```
$var = date("H");
if ($var < 11)
{
    echo "good morning";
}
elif ($var > 11 and $var < 18)
{
    echo "good afternoon";
}
else
{
    echo "good evening";
}
?
```

In this page, after printing the greeting, there is some real programming, I've used PHP's built-in date function to grab the time of the day in 24-hour format. That value is immediately assigned to a variable named $var. Then a decision is made, and the appropriate text is printed, depending on the time of day. Notice the syntax here. Each PHP command ends with a semicolon. In the if statement, curly braces hold the commands to be executed depending on the condition. And the condition itself is held within parentheses.