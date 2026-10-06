performing a function, not entering text, so make it one that you won't need for anything else. Dollar signs ($) and pound signs (#) are both good escape characters, but the only rule is that you can't use the character as text.

Once you've picked an escape code, customize the separator page with any of the variables shown in Table 16.3. Be sure to include the escape character before each function, as you've shown in this table with a dollar sign.

# Table 16.3: Separator Page Functions

| VARIABLE | FUNCTIONS |
| /B/S | Prints text in block characters created with pound signs (#) until you insert a $U. Been warned—printing text like this up a lot of room. |
| /D | Prints the date the job was printed, using the format defined on the Date tab of the Regional Options applet in Control Panel. |
| /E | Equivalent to a page break in Word; all further functions will be executed on a new page. If you use an extra blank separator page when you print, remove this function from the SEP file. |
| /Ffilename | Prints the contents of the specified file to the separator page, starting on a blank line. Because separator pages are strictly text, only the text will be printed—no formatting. |
| /Hnn | Sets a printer-specific control sequence, where nn is a hex ASCII code that goes directly to the printer. Look in your printer manual for any codes that you might set this way and for instructions on how to use them. |
| /I | Prints the job number. Each print job has a job number associated with it. |
| /Lxxx | Prints all the characters following (represented here with xxx) until it comes to another escape code. Use this function to print any customized text you like. |
| /N | Prints the login name of the person who submitted the job. |
| /n | Skips n lines (where n is a number from 0 to 9). Skipping  moves printing to the next line, so you could use that function to define where line breaks occur |
| /T | Prints the time the job was printed, using the format defined on the Time tab of the Regional Options applet in Control Panel. |
| /U | Turns off block printing. |
| /Wnn | Sets the line width, where nn is a number of characters. Any characters in excess of this line width are truncated. The default (which you don't have to define) is 80 characters. |