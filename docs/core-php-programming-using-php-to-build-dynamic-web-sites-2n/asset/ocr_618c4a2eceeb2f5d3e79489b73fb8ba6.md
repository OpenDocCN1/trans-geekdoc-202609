# Core PHP Programming

at all with others. COM seeks to solve this problem. COM objects are accessible by C++, Visual Basic, Java, and PHP.

A tutorial on COM is beyond the scope of this text, course. Microsoft's list of "noteworthy" books about COM is relatively long http://www.microsoft.com/tech/com.asp. However, you could keep busy just reading the articles online. You might read Dr. Guli's Guide to COM first http://www.microsoft.com/news/drgui.asp.

To use a COM object in PHP, you first load it with com_load and invoke methods with com_invoke, and you get and set properties with com_propget and com_propset.

Zeev Suraski added COM support for PHP.

# com_get

Use com_get as an alias for com_propget.

value com_invoke(integer object, string method, argument, argument, ...)

The com_invoke function invokes a method on a COM object. You must specify a valid object resource identifier and the name of the method. If the method takes arguments, you list them by their method name.

# integer com_load(string module, string server)

The com_load function loads the named COM object and returns a resource identifier to be used by the other COM functions. The optional server argument allows you to specify a remote server. FALSE is returned when the load fails. The module is named by its ProgID.

```
// load object
if(!$beeper = com_load("BeepCntMod.BeepCnt"))
{
    print("Could not load object!<BR>\n");
    exit();
}

//print current value of count
print(com_propget($beeper, "Count") . "<BR>\n");

//change count
```