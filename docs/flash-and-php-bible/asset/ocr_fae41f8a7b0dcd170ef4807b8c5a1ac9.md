# FIGURE 5.1 Sample form built using the default components that ship with Flash

![](bbox=[0.102, 0.183, 0.408, 0.365])

> NOTE If the component doesn’t appear on the Stage, ensure the layer is not displaying a locked icon in the Layer list.

If you run this Flash movie, you would see some cool components on the Stage but they would be nonfunctional. The process of using them is very straightforward. You assign an instance name to the component and reference the name in your ActionScript.

For example, if you had a TextInput and wanted to prefill it, you would add the following code:

```
textInstance.text = "please enter your name";
```

As useful as that code is, you should also capture user input. This is achieved by adding a Submit button component to the stage.

```
userName.text = "please enter your name";
submitBtn.addEventListener(MouseEvent.CLICK, submitHandler);
function submitHandler(e:MouseEvent):void
{
    trace("User input: " + userName.text);
}
```

You can expand this example to add error checking and enforcing required fields:

```
function submitHandler(e:MouseEvent):void
{
    if(userName.text.length == 0)
    {
        trace("Please enter a name!");
    }
}
```

Very often you will want to get feedback from a viewer of your site. This is accomplished by adding a contact form, which generally consists of a Flash form that talks to a PHP file.