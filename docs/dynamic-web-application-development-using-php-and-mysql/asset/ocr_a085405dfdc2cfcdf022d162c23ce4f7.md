```
<TD><INPUT type="text" name="loginid" id="loginid"></TD>
</TR>
<TR>
<TD><LABEL for="pword">Password:</LABEL></TD>
<TD><INPUT type="password" name="pword" id="pword"></TD>
</TR>
<TR>
<TD></TD>
<TD>
<INPUT type="submit" value="Login">
<INPUT type="reset" value="Clear form">
</TD>
</TR>
</TABLE>
</FORM>
</BODY>
</HTML>
```

Figure 3.13 shows how the form appears in Internet Explorer 7. Of course, pressing the 'Login' button simply gives an HTTP '404 not found' error, since we are not yet running anything on the server.

There are several other input types used in HTML forms. Two related types are checkboxes and radio buttons. The only difference between these is that checkboxes are always independent of any other component, whereas radio buttons can be grouped together so that only one radio button in a given group can be selected at any one time. A checkbox is defined by setting the INPUT element's 'type' attribute to 'checkbox'. Here we use a checkbox to indicate whether a user wishes to be added to a mailing list. A checkbox effectively represents a Boolean value; it is either checked (true) or not (false).

```
<INPUT type="checkbox" name="mailinglist">
```

A check box is unchecked by default. However we can change this by setting the value of the 'checked' attribute to 'checked'.

# FIGURE 3.13 A form displayed in Internet Explorer 7

![](bbox=[0.2, 0.7, 0.9, 0.94])