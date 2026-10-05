# Chapter I.5: Sessions and Cookies 47

```
<td>Name:</td>
<td><input type=text name=name></td>
</tr>
<tr>
<td>Password:</td>
<td><input type=password name=pass></td>
</tr>
<tr>
<td>&nbsp;</td>
<td><input type=submit value='Enter'></td>
</tr>
</form>
</table>
```

As you can see from Listing I.5.1, the HTML form passes the data to the handler for processing. The handler is located in the handler.php file. For simplicity, the system will check whether the password and the login name match the admin string. If they do, the system will mail a notification using the mail() function (Listing I.5.2).

# Listing I.5.2. The handler.php file

```
<?php
if ($_POST['name'] == 'admin' && $_POST['pass'] == 'admin')
{
    echo "<br><br>The message has been sent<br><br>";
    mail("admin@somewhere.ru","Statistics", "Message body");
}
?>
```

The intruder places the HTML form shown in Listing I.5.1 on his or her local host, then he or she would be able to repeat access attempts infinitely, either guessing the password, using the service, or providing visitors of his or her site with services located on the other site. In addition, using sockets, it is possible to automate the process of accessing the handler of the HTML form. Thus, it is necessary to use a session to protect HTML forms so that it is possible to use the service only on the site where it is located.