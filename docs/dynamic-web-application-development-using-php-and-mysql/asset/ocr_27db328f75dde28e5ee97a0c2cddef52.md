```
<TR>
    <TD>
        <INPUT TYPE="radio" name="status" id="guest" value="guest">
    </TD>
    <TD><LABEL for="guest">Access the site as a guest</LABEL></TD>
</TR>
<TR>
    <TD><INPUT TYPE="radio" name="status" id="new"
value="new"></TD>
    <TD><LABEL for="new">Set up a new user account</LABEL></TD>
</TR>
<TR>
    <TD>
        <INPUT TYPE="radio" name="status" id="login" value="login"
checked="checked">
    </TD>
    <TD>
        <LABEL for="login">Login using an existing account</LABEL>
    </TD>
</TR>
<TR>
    <TD colspan="2">
        <LABEL for="mailinglist">Please check this box if you would
like to be added to our mailing list</LABEL>
    </TD>
    <TD>
        <INPUT type="checkbox" name="mailinglist"
id="mailinglist" checked="checked">
    </TD>
</TR>
<TR>
    <TD></TD>
    <TD>
        <INPUT type="submit" value="Continue">
        <INPUT type="reset">
    </TD>
</TR>
</TABLE>
</FORM>
</BODY>
</HTML>
```

Figure 3.14 shows the page with radio buttons and a checkbox displayed in Opera 9.

# Text areas

Text areas, which allow the input of multiple lines of text, do not use the INPUT element but are defined by a TEXTAREA element. This element includes optional attributes to set the number of rows and columns of text (the ‘rows’ and ‘cols’ attributes). The text typed into a TEXTAREA automatically wraps at the end of a line. If any text is added to the body of the element, then it appears inside the text area, as in this example