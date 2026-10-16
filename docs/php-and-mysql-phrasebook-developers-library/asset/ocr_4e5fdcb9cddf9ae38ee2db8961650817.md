```
}
?></select>
// ...
</form>
```

The code from the preceding phrase has one minor flaw: The number of days per month is always from 1 to 31, even in months that have fewer days. Using JavaScript, it is possible to write a fancy script that calculates how many days the current month has and then updates the selection list.

However, it is much more convenient to use a combination of JavaScript and PHP. Using JavaScript, you automatically submit the form. Using PHP, you prefill the form fields (see Chapter 5, “Interacting with Web Forms,” for more information about that) and, more important, find out how many days the related year has.

The JavaScript code is limited to a minimum: Selecting another month submits the HTML form (as does selecting another year because leap years make February longer):

```
<select name="month" onchange="this.form.submit();">
...
<select name="year" onchange="this.form.submit();">
```

The number of days per month can be found using date('t'). The listing at the beginning of this phrase contains the complete code for this, including some sanity checks for the information transmitted. In addition, the code automatically preselects the current date, unless the user chooses something else. Figure 3.5 contains the output of the complete code.