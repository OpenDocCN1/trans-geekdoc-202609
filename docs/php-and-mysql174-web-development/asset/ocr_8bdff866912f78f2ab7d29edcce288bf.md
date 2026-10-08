To provide some functionality, the class also needs operations. You can start by providing accessor functions to set and get the values of the attributes defined:

```
public function __set($name, $value)
{
    $this->$name = $value;
}
```

The __set() function does not contain error checking (for brevity), but this capability can be easily added later, as required. Since it is unlikely that you will be requesting any of these values from outside the class, you can elect not to provide a __get() function, as done here.

The main purpose of this class is to display a page of HTML, so you need a function. We called ours Display(), and here it is as follows:

```
public function Display()
{
    echo "<html>\<head>\n";n    $this->DisplayTitle();
    $this->DisplayKeywords();
    $this->DisplayStyles();
    echo "</head><body>\n";n    $this->DisplayHeader();
    $this->DisplayMenu($this->buttons);
    echo $this->content;
    $this->DisplayFooter();
    echo "</body>\n</html>\n";
}
```

The function includes a few echo statements to display HTML but mainly consists of calls to other functions in the class. As you have probably guessed by their names, these other functions display parts of the page.

Breaking up functions like this is not compulsory. All these separate functions might have been combined into one big function. We separated them out for a number of reasons.

Each function should have a defined task to perform. The simpler this task, the easier writing and testing the function will be. Don't go too far; if you break your program into too many small units, it will be hard to read.

Using inheritance, you can override operations. When you replace one large Display() function, it is unlikely that you will want to change the entire page is displayed. It will be much better to break up the display into a few self-contained tasks and be able to override only the parts that you want to change.

This Display() calls DisplayTitle(), DisplayKeywords(), DisplayStyles(), DisplayHeader(), DisplayMenu(), and DisplayFooter(). This means that you need to define these operations. You can write operations or functions in any logical order, unlike many other languages, you need to write the function or operation before the actual code for it can be called. Most of the operations are fairly simple and need to display some HTML and perhaps the contents of the attributes.