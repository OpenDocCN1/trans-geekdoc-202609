```
<INPUT TYPE="radio" NAME="gender" VALUE="m"> Male
<INPUT TYPE="radio" NAME="gender" VALUE="f" CHECKED> Female
```

The final input type that you will learn about is the `SUBMIT` button. This is the button you click to send the contents of a form to the script specified in the form's `METHOD` attribute. The label on the button is specified in the `VALUE` attribute, so the following HTML would create a submit button labeled Send comments:

```
<INPUT TYPE=SUBMIT VALUE="Send comments">
```

A submit button can also have a `NAME` attribute, although this is rarely used. You will see later in this lesson how this affects the values sent to PHP.

# The `<TEXTAREA>` Tag

The `<TEXTAREA>` tag is used to create a multiple-line text input item. In many respects, it behaves just like a `TEXT` type input tag, but the way it is formed in HTML is slightly different.

Because the initial value in a text area could span many lines, it is not given in a `VALUE` attribute. Instead, the starting value appears between a pair of tags, as follows:

```
<TEXTAREA ROWS=4 COLS=50 NAME="comments">
Enter your comments here
</TEXTAREA>
```

PHP is not concerned with what type of input a value comes from; the difference between a text area and text input is an HTML issue only.

# The `<SELECT>` Tag

The final form item we will look at is the `<SELECT>` item, correctly known as a *menu* but more commonly called a *drop-down list* .

The most common use of a menu is to prompt for a single selection from a predefined list of values. The following example builds a drop-down list of possible places that visitors may have heard about your website:

```
<SELECT NAME="referrer">
<OPTION VALUE="search">Internet Search Engine</OPTION>
<OPTION VALUE="tv">TV Advertisement</OPTION>
<OPTION VALUE="billboard">Billboard</OPTION>
<OPTION SELECTED VALUE="other">Other</OPTION>
</SELECT>
```