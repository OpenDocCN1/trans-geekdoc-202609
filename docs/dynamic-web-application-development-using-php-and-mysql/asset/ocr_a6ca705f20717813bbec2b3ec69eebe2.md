```
<input type="text" name="strFirstname" id="strFirstname"/>
</p><p>
<label for="strSurname">Surname: </label>
<input type="text" name="strSurname" id="strSurname"/>
</p><p>
<label for="strUsername">Username: </label>
<input type="text" name="strUsername" id="strUsername"/>
</p><p>
<label for="strPassword">Password: </label>
<input type="password" name="strPassword" id="strPassword"/>
</p><p>
<input type="submit"/>
</p>
</form>
```

You should be familiar with XHTML forms but let us take a quick moment to examine the elements which make up the script.

| NOTE | Note that the example web form script is an XHTML document and should be saved with the extension .htm. |

The ‘form’ element consists of open and close tags and surround all other elements within the form:

```
< form action="filename" method="type">
...
</form>
```

The start form tag contains two attributes which specify the action to take when the form is submitted (this is normally the name of the script to invoke, in our case, a PHP script called ‘example10-1.php’) and the method by which the data should be sent to the script. PHP supports the post method and so the element looks like this:

```
<form action="example10-1.php" method="post">
...
</form>
```

Don’t worry about exactly what is meant by the post method; we shall explain how to access data sent by the post method shortly. The great thing is that you don’t need to understand the underlying mechanism to get some good results.

Within the ‘form’ element are a number of other elements. In this case, these are mostly pairs of ‘label’ elements denoting a text label and linking the label to a particular form input field:

```
<label for="inputFieldId">textLabel</label>
```

The labels are followed by ‘input’ elements and have the following syntax:

```
<input type="type" name="fieldname" id="inputFieldId"/>
```