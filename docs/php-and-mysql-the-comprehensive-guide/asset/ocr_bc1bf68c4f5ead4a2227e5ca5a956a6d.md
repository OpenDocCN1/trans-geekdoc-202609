```
error += "Salutation\n";
}
```

It is easier with the checkbox. Here, only the checkbox itself needs to be considered— again, in the checked property:

```
if (!f.elements["erms"].checked) {
 error += "Terms & conditions\n";
}
```

With the selection lists, the result depends very much on what exactly "Nothing is selected" means. In the example form, the single selection list contains a dummy entry (Please Select) at the top, which is of course considered "not filled in." The field is only considered correctly completed from the second list entry on. The internal counting of the list fields in JavaScript starts at 0; that is, everything is OK from field number 1. The selected field number is in the selectedIndex property, which results in the following check code:

```
if (!f.elements["Number"] || f.elements["Number"].selectedIndex < 1) {
 error += "Number of tickets\n";
}
```

In a multiple list, selectedIndex is rarely used because when querying the form entries, not only the first selected element (which is in selectedIndex) is of interest, but all selected elements. When checking fields, on the other hand, it is only relevant whether anything has been selected at all. If not, selectedIndex has the value -1, which we check as follows:

```
if (!f.elements["Section[]"] ||
 f.elements["Section[]"].selectedIndex == -1) {
 error += "Section\n";
}
```

**Note**
You must enter the complete name of the field in JavaScript, including the square brackets in the name for multiple selection lists!

The error variable is checked at the end. If there is something in it, an error has occurred, so you should inform the user of this (see Figure 13.13) and prevent the form from being sent with return false:

```
if (error != "") {
 alert("** Error in the following fields:\n" + error);
 return false;
} else {
```