# # Checking a Check Box

The `CHECKED` attribute determines whether a check box is on or off by default when a page loads. Using PHP, you can embed a condition within the `<INPUT>` tag to determine whether to include the CHECKED attribute on a check box:

```
`<INPUT TYPE="CHECKBOX"
NAME="mybox" <?php if(condition) echo "CHECKED"; ?>>`
```

The way this looks can be confusing, particularly because two > symbols appear at the end of the tagone to close the PHP section and one to close the `<INPUT>` tag. In fact, the position of the CHECKED attribute is not important, so depending on your preference, you can move it around for readability:

```
`<INPUT <?php if(condition) echo "CHECKED"; ?>
TYPE="CHECKBOX" NAME="mybox">`
```

> **Closing PHP Tags** When embedding small chunks of PHP, you should always try to include the closing `?>` tag as soon as possible. If you miss this closing tag, PHP attempts to interpret the subsequent HTML as PHP and is likely to come up with some interesting error messages!

Spacing can be very important when you're using PHP within HTML. In the previous example, if there is not a space on either side of the PHP statement and the condition is true, the actual HTML produced is as follows:

```
`<INPUT CHECKEDTYPE="CHECKBOX" NAME="mybox">`
```

Because `CHECKEDTYPE` is not recognized as part of the `<INPUT>` tag, your browser is likely to display this as a text input box, not a check box! It's always better to have too much space around dynamic elements in HTML tags than to risk not having enough.

# # Selecting a Radio Button Group Item

The `CHECKED` attribute is also used to specify which item in a radio button group should be selected by default. For example, an online store may offer three shipping options, with each having a different cost. To make sure the customer always chooses a shipping option, one of the