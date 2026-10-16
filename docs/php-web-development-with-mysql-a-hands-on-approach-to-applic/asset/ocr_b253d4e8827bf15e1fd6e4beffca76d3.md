# 19. WORKING WITH FILES AND FEATURE ADDITIONS TO EXISTING CODE

# Complete Movie Image File Script

Our completed movieimagefileutil.php script including our validateMovieImageFile() and addMovieImageFileReturnPathLocation() functions looks like Listing 19.8.

# Listing 19.8.

```
```php
1. <?php
2. require_once 'movielistingfileconstants.php';
3. 
4. /**
5.  * Purpose:    Validates an uploaded movie image file
6.  *
7.  * Description: Validates an uploaded movie image file is not greater than
8.  *              ML_MAX_FILE_SIZE (1/2 MB), and is either a jpg or png image type, and
9.  *              has no errors. If the image file validates to these constraints,
10. *              an error message containing an empty string is returned. If
11. *              there is an error, a string containing constraints the file failed
12. *              to validate to are returned.
13. *
14. * @return string  Empty if validation is successful, otherwise error string containing
15. *                 constraints the image file failed to validate to.
16. */
17. function validateMovieImageFile()
18. {
19.     $error_message = "";
20. 
21.     // Check for $_FILES being set and no errors.
22.     if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
23.     {
24.         // Check for uploaded file < Max file size AND an acceptable image type
25.         if ($_FILES['movie_image_file']['size'] > ML_MAX_FILE_SIZE)
26.         {
27.             $error_message = "The movie file image must be less than "
28.                         . ML_MAX_FILE_SIZE . " Bytes";
29.         }
30. 
31.         $image_type = $_FILES['movie_image_file']['type'];
32. 
33.         if ($image_type != 'image/jpg' && $image_type != 'image/jpeg'
34.             && $image_type != 'image/pjpeg' && $image_type != 'image/png'
35.             && $image_type != 'image/gif')
36.         {
37.             if (empty($error_message))
38.             {
39.                 $error_message = "The movie file image must be of type jpg, png, or gif.";
40.             }
41.             else
42.             {
43.                 $error_message .= ", and be an image of type jpg, png, or gif.";
```
```