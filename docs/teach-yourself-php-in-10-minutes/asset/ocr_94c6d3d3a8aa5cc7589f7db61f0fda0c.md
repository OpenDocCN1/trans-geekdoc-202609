In this HTML, you supply an empty `VALUE` attribute because you do not want to supply a default value for the input; however, the `VALUE` attribute can be omitted.

**Field Lengths** The display size of a field does not affect how PHP handles the submitted values. This input has a display size of 30 characters but no `MAXLENGTH` attribute is set, so users with unusually long names can still type beyond the length of the field.

The `CHECKBOX` input type creates an input item that has only two possible values: on and off. Check boxes are useful for true/false values, and you could use the following HTML to create a check box with which the user could indicate whether he minds us contacting him by email:

```
<INPUT TYPE="CHECKBOX" NAME="may_contact" VALUE="Y" CHECKED>
```

In this case, the `CHECKED` attribute indicates that the check box should be checked automatically when the page loads.

The `RADIO` type is similar to a check box, but instead of a true/false value, a radio button group can contain several values, of which only one can be selected at a time.

To create a radio button group that can be used to gather the user's gender, you could use the following:

```
<INPUT TYPE="radio" NAME="gender" VALUE="m"> Male
<INPUT TYPE="radio" NAME="gender" VALUE="f"> Female
```

**Naming Radio Buttons** The `NAME` attribute determines the grouping of radio buttons. Only one selection can be made for each radio button group, although you can have several radio button groups on a page if you want. In this example, both buttons have the same name, `gender`.

To indicate that one of the buttons in a radio button group should be pre-selected, you can use the `CHECKED` attribute. For instance, if you are creating a website that will appeal primarily to women, you can pre-select the female option, as follows: