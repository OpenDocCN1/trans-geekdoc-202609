
- **Checkbox** — The name and value of the checkbox will only be passed if the checkbox is checked when the form is submitted. If the word “checked” appears in the tag, the checkbox will be checked by default. Remember to use name=box_name[] to pass multiple checkboxes as an array. See Chapter 4 for a discussion of passing arrays with PHP.
- **Radio** — Radio buttons allow the user to select only one of several choices. Radio buttons with the same name attribute belong to the same group. The “checked” command signifies the default choice.

The following form makes use of most of the form elements we just covered, except for the image type. Figure A-2 shows how it is rendered in the browser.

```
<h2>Please Enter Personal Information</h2>
<form>
    <input type="text" size="25" maxlength="15" name="name" value="Name Here"><br>
    <input type="password" size="25" maxlength="15" name="password" value=""><br>
    <input type="hidden" value="you can't see me">
    <input type="checkbox" name="telemarket" value="yes" checked>If checked, I have permission to clear out your bank account.
    <p>
    <b>What is your eye color?</b><br>
    <input type="radio" name="eye_color" value="blue" checked>blue<br>
    <input type="radio" name="eye_color" value="green">green<br>
    <input type="radio" name="eye_color" value="brown">brown<br>
    <input type="radio" name="eye_color" value="red">red<br>
    <input type="submit" name="submit" value="submit"> &nbsp &nbsp &nbsp
    <input type="Reset">
</form>
```

## Select, multiple select

The select form element creates drop-down boxes and (to use the Visual Basic term) list boxes. To create drop-down boxes, you must have an opening <select> tag with a name attribute. Within the select element, <option> tags will indicate possible choices. Each of these will have a value attribute.

![](img/de0823012275cf4ceebdb822a56e6b71_435_0.png)

Figure A-2: More form elements

The following HTML creates a drop-down box with 3 elements.

```
<form name="tester" action="script.php" method="get">
    <select name="dinner">
        <option value="1">chicken
        <option value="2">fish
        <option value="3">vegetarian
    </select>
</form>
```

By adding the word “multiple” to the select element you enable the user to pick more than one of the choices. The size attribute determines how many of the options are visible at one time.

The following code creates a list box with 3 visible elements. Figure A-3 shows how this HTML looks in the browser.

```
<form name="tester" action="script.php" method="get">
    <select name="side_dishes" multiple size=3>
        <option value="1">potato
        <option value="2">pasta
        <option value="3">carrot
        <option value="4">celery
        <option value="5">mango
    </select>
</form>
```

## Textarea

The textarea element creates a large block for text entry. Add a row and column attribute to specify the size of the box. Textarea is different from other form elements in that opening and closing tags surround the default text. For instance:

```
<textarea name="mytext" rows="5" columns="20">Here's the default text</textarea>
```

Keep in mind that if you have spaces or hard returns between your <textarea> tags, those characters will be carried to the form element.

Add the wrap attribute to change how text wraps when it reaches the end of a line in the box. If the value is wrap=physical, carriage returns are added at the end of line; if the value is wrap=virtual, the lines will appear to wrap but will be submitted as a single line. This is almost always the best choice.

These attributes came about from the folks at Netscape, and you still may need to use them. The official W3C HTML 4.0 attribute values for wrap are none, hard, and soft.

Figure A-3 adds the select, multiple select and textarea elements to a form with this code.

```
<h2>Please Enter Personal Information</h2>
<form>
<fieldset id="fieldset1"
style="position:absolute;
width:300;
height:100;
top:20;
left:10;"
>
<legend>Food Questions</legend>
<b>What did you eat for dinner?</b><br>
<select name="dinner">
<option value="1">chicken
<option value="2">fish
<option value="3">vegetarian
</select><br>
<b>Any Side dishes?</b><br>
    <select name="side_dishes" multiple size=3>
        <option value="1">potato
        <option value="2">pasta
        <option value="3">carrot
        <option value="4">celery
        <option value="5">mango
    </select>
<br>
<b>How are you feeling about dinner?</b><br>
<textarea name="mytext" rows="5" columns="20">
Here's the default text</textarea>
</fieldset>
<p>
<button>
    <img src="disk.gif" width="32" height="32" border="0"
alt="disk"><br>
Pretty Little Button
</button>
</form>
```

![](img/de0823012275cf4ceebdb822a56e6b71_437_0.png)

Figure A-3: Additional form elements

## Other attributes

With HTML 4.0 and the newest browsers some additional attributes have been introduced. Make sure to test these as part of your QA process because they will not work on all browsers.

### ACCESSKEY

An accesskey is the same as a hotkey. If this attribute appears in a form element, the user can hit (on a PC) Alt and the designated key to be brought directly to that form element. The hotkey is generally indicated by underlining of the hot letter.

```
<input type="text" name="mytext" accesskey="m"><u>M</u>y text box.
```

### TABINDEX

Users can use the Tab key to move through form elements. The tabindex attribute specifies the order in which focus will move through form elements.

## Other elements

Internet Explorer 5 and Mozilla support a couple of new and seldom-used form elements that you might want to consider using.

### BUTTON

The button is a fancier version of the submit button. It allows for both text and an image to be put on the same button. There are opening and closing <button> tags, and everything inside of them appears on the button. Figure A-3 shows an example of the button.

### FIELDSET AND LEGEND

These are nice for grouping elements in forms. All text and tags within the <fieldset> tags will be surrounded by a thin line. Text within the <legend> tags will serve as the caption for that grouping.

Figure A-3 shows all of the form types.

In the year 2001, it is still not a great idea to use most of the HTML 4.0 form elements and attributes. Generally speaking, they add very little, and they may look very strange on many browsers.

## Appendix B

### Brief Guide to PHP/MySQL Installation and Configuration

WHEN INSTALLING MYSQL AND PHP, you are faced with all kinds of options. The variety of operating systems and installation options creates more permutations than could possibly be handled in this book. Luckily, installation procedures for both packages are documented well in each package's respective documentation.

In this appendix we will cover the basic installation and configuration of MySQL and PHP on Windows 98 and Unix systems. I'm assuming that you will be using the Apache Web server on all platforms. For the Unix installation, this book will document only the method of compiling the source code. If you wish to use RPMs for your installation, you should consult the online manuals.

### Windows 98 Installation

Start by copying the MySQL binaries from the CD-ROM accompanying this book or the mysql.com site to your local drive. Do the same for Apache and PHP (the appropriate download sites here are http://www.apache.org/dist and http://www.php.net/download). The names of the files will be something like the following (they may be slightly different, depending on the version you are using):

- mysql-3.23.22-beta-win.zip
- apache_1_3_9_win32.exe
- php-4.0.1pl2-Win32.zip

Start by unzipping the mysql file and php files with your favorite unzip tool. (If you don't have one, we recommend Winzip, at http://www.winzip.com/.) Unzip them into a directory you find convenient. We prefer using a separate directory for each.

Start with MySQL. In the directory where you unzipped the file, you will have a file named setup.exe. Execute that file. Choose a directory (e.g. d:\mysqlinstall) where you want it installed, and then in the next screen select a Typical installation. (You may wish to examine the custom options, but with the Windows install there are very few real options.)
