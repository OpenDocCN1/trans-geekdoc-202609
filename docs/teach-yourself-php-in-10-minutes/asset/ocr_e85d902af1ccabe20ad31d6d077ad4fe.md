In this case, the SELECTED attribute makes "Other" the default selection, even though it appears at the top of the list. If no item has the SELECTED attribute, the first option in the list is selected by default.

# Putting It All Together

By putting all these form elements together and adding some label text and a little formatting, you can create a simple comments submission form that you can then process in PHP, as shown in Listing 11.1 .

# Listing 11.1. A Web Form for Submitting User Comments

```
<FORM ACTION="send_comments.php" METHOD=POST>
<TABLE>
<TR>
<TD>Your name:</TD>
<TD><INPUT TYPE="TEXT" NAME="name" SIZE=30></TD>
</TR>
<TR>
<TD>Your email:</TD>
<TD><INPUT TYPE="TEXT" NAME="email" SIZE=30></TD>
</TR>
<TR>
<TD>Your gender:</TD>
<TD><INPUT TYPE="RADIO" NAME="gender" VALUE="m"> Male
     <INPUT TYPE="RADIO" NAME="gender" VALUE="f"> Female  </TD>
</TR>
<TR>
<TD>How you found us:</TD>
<TD>
     <SELECT NAME="referrer">
     <OPTION VALUE="search">Internet Search Engine</OPTION>
     <OPTION VALUE="tv">TV Advertisement</OPTION>
     <OPTION VALUE="billboard">Billboard</OPTION>
     <OPTION SELECTED VALUE="other">Other</OPTION>
     </SELECT>
</TD>
</TR>
<TR>
<TD>May we email you?</TD>
<TD><INPUT TYPE="CHECKBOX" NAME="may_contact"
     VALUE="Y" CHECKED></TD>
</TR>
<TR>
<TD>Comments</TD>
<TD><TEXTAREA ROWS=4 COLS=50
     NAME="comments">Enter your comments here
     </TEXTAREA></TD>
</TR>
```