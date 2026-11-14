Again, the reference to the CSS file assumes it will be found in the **Web root directory/css** folder.

+   8. After including the jQuery library, include the hoverIntent and Superfish JavaScript files:

```
<script src="//js/hoverIntent.js" type="text/javascript"
charset="utf-8"></script>
<script src="//js/superfish.js" type="text/javascript"
charset="utf-8"></script>
```

Make sure you include the scripts in this order.

+   9. In a separate script block, apply Superfish:

```
<script type="text/javascript">
$(function() {
$("ul.sf-menu").superfish({
autoArrows: false,
speed: 'fast'
});
});
</script>
```

> ### tip
> 
> The **us.sf-menu** code actually selects every unordered list with a class of `sf-menu`, but the template has only one.

This code enables the Superfish menu. The very basic JavaScript being executed is just `$( );`. This is magic jQuery speak for “when the document is ready, do the following.” The code to be executed when the document is ready is defined in an **anonymous function** (a function without a name). Within the function, the unordered list with a class of `sf-menu` is selected. To that selection, the **superfish()** method is applied. Two attribute-value pairs are passed to the **superfish()** method: one disabling arrows that indicate submenus exist; the other sets the Superfish speed to **fast**.

> ### tip
> 
> If the Superfish menu doesn’t work for you, use a JavaScript debugging tool, such as Firebug for the Firefox browser, to see what might be wrong.

+   10. Save the file and test it in your Web browser.

# # Updating create_form_input()

The **create_form_input()** function, first defined in Part Two, “Selling Virtual Products,” then redefined in Chapter 10, “Checking Out,” will be used in the administrative pages, too. As currently defined, the function works well for the public side, creating the text inputs and different select menus used by the checkout process. The administrative pages will have some forms that also require textareas, so that functionality needs to be added to the function.