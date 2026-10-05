may seem like a lot, but when you are creating and modifying requests, 2048 characters can get used very quickly. The GET method is most useful for searches.

The other method is POST. POST is sent in the header of the URL. That can hide from the user and send much larger amounts of data. Because the user can't see the data doesn't mean it's secure. For real security, you still need to use an encrypted page (i.e. https). POST is useful for creating, updating, and deleting records.

Both GET and POST data will be sent using Name=Value pairs. That means you'll define the name of the value, such as the field name. Then type something like a text field for the user to enter data. For example, if you type T in Todd the Name=Value pair will be Search=Todd. To extend the logic of Name=Value pairs, the actual URL from the form will look like this:

```
http://localhost/TodduePHP/Form.php?id=123&search=Todd&Search=Submit
```

It starts with the name and word of of the file from the form attribute: http://localhost/TodduePHP/Form.php. Then it adds to all the Name=Value pairs defined in the form. In the example there are three Name=Value pairs. The first one is the value for the Record ID (id) and the value obtained from the exiting URL name of 'id'=123. The next is Search, the value you typed into the Search text box. Then the button that is pressed by the user is also set. In this case the Name=Value pair for the button is Search=Submit. In the example it is important to name your buttons in order to determine exactly which button was pressed. Especially when you have more than one button on your form:

Now let's back up for a moment and take a look at what you can put inside your form. In this example you've placed the hidden element of "id" in the specified type="hidden". Hidden values allow you to pass information to the web server and database without the user actually seeing any data on the browser screen. It is very useful for searches as Record ID's. In the example I'm passing some PHP code that retrieves the URL from 'id' with $_GET superglobal.

```
<input name="id" type="hidden" value="<?php echo $_GET['id']; ?>">
```

The other item I'm passing in the URL is the Search text from form field. I've given the name 'Search' and defined it as a text field that the user can enter. There are also other enterable fields for text area, check radio button, list/menu, etc. that will be demonstrated in the example files later in the book. For now, it's only important to know that the data in the form will be sent to the web server as Name=Value pair.

```
Search: <input name="Search" type="text">
```

Finally, you have to create a button to submit the form to the web server. The name in the Search and the value is defined as Submit. These values are also passed to the web server. It is very to create a FileMaker Pro script block where you have 3 buttons to choose from. When the user clicks a button the button they pressed by using the function Get(LastMessageChoice). In the case of a form, you'll be checking for Search==Submit, which is probably a lot more intuitive than checking for Get(LastMessageChoice)=1, 2, or 3. I always have to look at the Show Message dialog box to figure out which button is for which response, especially when the default button is something other "OK".

```
<input name="Search" type="submit" value="Submit">
```

# Create a Link

Links allow users to navigate from one page to another, within the same page, or pass information to the web server to perform processes as search for records. You probably recognize a link from 'Click Here' on a page. Rather than displaying absolute or relative link to the location web page shows a text or image-based link. Links with databases are useful for a variety of items. In the example files we will be creating links to navigate detail pages based on Record ID and links to change the order of the records by the URL.

All links start with the anchor tag <a href=""> where the value between the quotes for href is a relative or absolute path to a document. href stands for hypertext reference. Basically, it's saying what the path to the document you