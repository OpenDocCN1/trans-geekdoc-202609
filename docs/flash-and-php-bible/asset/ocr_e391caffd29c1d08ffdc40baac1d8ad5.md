In some cases, you will want to use the current value of the sandboxType property in programming to determine how an application should interact. Using a simple switch statement, you can construct a custom function that will trace out the current sandbox type, as shown in Figure 7.4.

# FIGURE 7.4

Output window displaying an example result from the whichSandbox function

![](bbox=[0.105, 0.26, 0.735, 0.642])

```
function whichSandbox():String
{
    var str:String = "";
    switch(Security.sandboxType)
    {
        case Security.REMOTE:
            str = "This SWF is from an Internet URL. "
            + "It cannot access local files";
            break;
        case Security.LOCAL_WITH_FILE:
            str = "This SWF is local, but not trusted by "
            + "the user. It does not have access to "
            + "remote files.";
            break;
        case Security.LOCAL_WITH_NETWORK:
            str = "This SWF can communicate with remote "
```