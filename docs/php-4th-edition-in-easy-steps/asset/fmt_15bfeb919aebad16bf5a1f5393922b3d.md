
## Sticky Form Example

```
// Statements to be inserted here (Steps 3-5).
}
?>
```

![image](images/3r.jpg)
Next, insert into the PHP script block a statement to create an array for error messages

`$errors \= array() ;`

![image](images/hot.jpg)

`$_SERVER['PHP_SELF']` is used by this example to ensure the script will still work if renamed.

![image](images/forget.jpg)

The `if` statement tests that the form has been submitted by checking the request method is `POST`, not the `GET` method that is used to display the empty form.

![image](images/4r.jpg)
Then, insert statements to initialize variables with submitted values, or add to the errors array for omissions

```
if ( empty( $_POST['name'] ) ) { $errors[] \= 'name' ; }
else { $name \= trim( $_POST['name'] ) ; }
```

```
if ( empty( $_POST['email'] ) ) { $errors[] \= 'email' ; }
```

```
else { $email \= trim( $_POST['email'] ) ; }
```

![image](images/5r.jpg)
Now, insert statements to write error messages or confirm successful form submission

```
if( !empty( $errors ) )
{ echo 'Error! Please enter your ' ;
foreach ( $errors as $msg ) { echo " - $msg " ; } }
else { echo "Success! Thanks $name " ; }
```

![image](images/6r.jpg)
Save the document in your web server's `/htdocs` directory as `sticky.php` then open it via HTTP and submit the form to see the retained values and response messages

![image](images/pg151_1.jpg)

![image](images/pg151_2.jpg)

![image](images/hot.jpg)

It is good practice to use the `trim()` function, as seen here, to remove any leading and trailing spaces from the submitted field value.

## Uploading Files

![image](images/pg152_1.jpg)

The PHP `$_FILES` superglobal variable makes it simple to POST file uploads from an HTML form if the `<form>` tag includes an enctype attribute set to "multipart/formdata". When submitted, a `$_FILES` associative array is created with keys that include the file name, a generated temporary name (`tmp_name`), and the file size. The filename and size can be used for validation. The temporary filename can then be specified to the `move_uploaded_file()` function along with the original filename to upload the file:

![image](images/1r.jpg)
Create an HTML document containing a sticky form with a file type input named "image"

```
<form action="<?php $_SERVER['PHP_SELF'] ?>" method="POST" enctype = "multipart/formdata" >
Select an image to upload :
<input type="file" name="image" >
<input type="submit" value="Upload Image"> </form>
```

![image](images/commonr.jpg)

`upload.php`

![image](images/2r.jpg)
Now, add a PHP script to handle the form submission

```
<?php
if ( $_SERVER['REQUEST_METHOD'] == 'POST' )
{
// Statements to be inserted here (Steps 3-7).
}
?>
```

![image](images/3r.jpg)
Next, insert statements to initialize three variables with information about the file selected by the user

`$name \= $_FILES['image']['name'] ;`

`$temp \= $_FILES['image']['tmp_name'] ;`

`$size \= $_FILES['image']['size'] ;`

![image](images/4r.jpg)
Now, insert statements to ensure the selected file is of a desired file type by testing the file extension, or quit

`$ext \= pathinfo( $name , PATHINFO_EXTENSION ) ;`

`$ext \= strtolower( $ext ) ;`

```
if( $ext != 'png' && $ext != 'jpg' && $ext != 'gif' )
{ echo 'Format must be PNG, JPG, or GIF' ; exit() ; }
```

![image](images/5r.jpg)
Insert a statement to ensure the selected file is of a desired file size, or quit

```
if( $size > 512000 )
{ echo 'File size must not exceed 500Kb' ; exit() ; }
```

![image](images/snake.jpg)

The PHP configuration must permit file uploads for this example to work. The configuration file `php.ini`, within the PHP directory, must contain a line `file_uploads = On`.

![image](images/hot.jpg)

Notice how the `pathinfo()` function provides the file extension part of the filename here.

![image](images/6r.jpg)
Insert a statement to ensure the selected file does not have the same name as one already on the server, or quit

```
if( file_exists( $name ) )
{ echo 'File '.$name.' already uploaded' ; exit() ; }
```

![image](images/7r.jpg)
Finally, attempt to upload the file, naming it by its original filename and displaying it below the form

```
try
{
move_uploaded_file( $temp , $name ) ;
echo 'File uploaded : '.$name ;
echo '<br><img src="'.$name.'">' ;
}
catch( Exception $e )
{
echo 'File upload failed!' ;
}
```

![image](images/8r.jpg)
Save the document in your web server's `/htdocs` directory as `upload.php` then open it via HTTP and select a suitable image file for upload to the `/htdocs` directory

![image](images/pg153_1.jpg)

![image](images/pg153_3.jpg)

![image](images/pg153_2.jpg)

`coke.png`

![image](images/hot.jpg)

The arguments to the `move_uploaded_file()` function specify the (temporary) filename and destination. It could usefully specify a dedicated directory path destination, such as `'uploads/'.$name`.

## Surrounding Forms

PHP usefully allows multiple files to be incorporated together to create a single web page. This means that dynamic forms can be surrounded by static header and footer content that can be easily reused to create other pages within a website.

![image](images/pg154_1.jpg)

The PHP `include()` function takes the URL of another file to be incorporated within a web page as its argument. Typically, included static content files are HTML and are located in an "includes" folder within the `/htdocs` directory of your web server.

PHP also provides a `require()` function that works just like the `include()` function to incorporate other files within a web page, but is subtly different. When the `include()` function fails, as the specified file cannot be found, for example, a warning gets sent to the browser but the script continues to run. When the `require()` function fails, an error is printed but the script gets halted. Usually, the `include()` function incorporates static HTML files, whereas the `require()` function incorporates dynamic PHP scripts.

Importantly, the title of a web page incorporating multiple files can be dynamically written by PHP to allow maximum flexibility of otherwise static HTML header content:

![image](images/1r.jpg)
Create an HTML document containing static header content and a PHP snippet to write the page title

```
<!DOCTYPE HTML>
<html lang="en">
<head>
<meta charset="UTF-8">
<title> <?php echo $page_title ; ?> </title>
<link rel="stylesheet" href="includes/style.css">
</head>
<body>
<header><h1>Page Header</h1></header>
```

![image](images/pg154_2.jpg)

`header.html`

![image](images/2r.jpg)
Now, create an HTML document containing footer content

```
<footer><p>Page Footer</p></footer>
</body>
</html>
```

![image](images/pg154_2.jpg)

`footer.html`

![image](images/3r.jpg)
Next, create a folder named "includes" in the `/htdocs` directory of your web server and save the above documents inside it as `header.html` and `footer.html` respectively

![image](images/4r.jpg)
Create a CSS style sheet to present the header and footer content (and rules to present aspects of later examples)

```
header > h1 { border-bottom : 1px dashed black ;
font-style : italic ; font-size : x-large ; }
footer > p { border-top : 1px dashed black ;
font-style : italic ; }
table { border-spacing : 5px ; width : 530px ; }
th { color : #FFF ; background : #000 ; text-align : left ; }
td { border-bottom : 1px solid black ;
padding : 3px ; background : #F0F0F0 ;
text-align : left ; vertical-align :top ; }
p#err_msg { color : #F00 ; font-weight : bold ; }
```

![image](images/pg155_1.jpg)

`style.css`

![image](images/5r.jpg)
Save the style sheet in the `/includes` folder you have created, alongside the HTML header and footer files
