
}

If the upload fails, the error messages are added to the `$errors` array instead of the `$messages` array. To prevent the details of a problem file from being inserted into the database, it’s identified by using `$no_spaces` as the array key.

The other change is that if the upload succeeds, the file’s name, caption, and associated `place_id` are added as an array to a new array called `$images`. Each element of the top-level array contains the details of a single image. For example, the first array element contains the following subarray: `$images[0]['filename']`, `$images[0]['caption']`, and `$images[0]['place_id']`.

**12** Save upload_images.php, and include it in db_insert_place.php after the conditional statement for `checkDuplicatePlacename()`. The include command should similarly be wrapped in a conditional statement like this:

if (!$errors) {  

  checkDuplicatePlacename($dbRead, $_POST['name'], $errors);  

}  

**if (!$errors) {**  

  require_once('upload_images.php');  

**}**

You can compare your code with upload_images.php, db_definitions_02.php, and db_insert_place_02.php in lesson10/completed/scripts.

#### Inserting the place and photo data

Once the data has been validated and the photos uploaded successfully, you’re ready to insert the data into the `places`, `photos`, and `place2photo` tables. A SQL `INSERT` query cannot deal with multiple tables, so you need to handle each table separately. You also need to query the database to obtain the primary key for each place and photo so that you can insert them as foreign keys in the `place2photo` table. This is done with the `Zend_Db lastInsertId()` method, although you must remember to use it immediately after inserting a record.

The rest of the script is relatively short and easy to understand.

**1.** In db_insert_place.php, add another conditional statement to make sure there were no errors when the photos were uploaded:

if (!$errors) {  

  require_once('upload_images.php');  

}  

**if (!$errors) {**  

**}**

All remaining code goes inside this conditional statement.

**2.** Create an array of values to be inserted in the `places` table:

$data = array('name'        => $_POST['name'],  

              'state_id'    => $_POST['state_id'],  

              'description' => $_POST['description'],  

              'link_name'   => str_replace(' ', '', $_POST['name']),  

              'created'     => new Zend_Db_Expr('NOW()'));

The values for the `name`, `state_id`, and `description` columns come directly from the form. The `link_name` column takes its value from the `name` field in the form after it has been passed to the `str_replace()` function. The first argument passed to the function is a pair of quotation marks with a space between them; the second argument is also a pair of quotation marks but without a space. This closes up any spaces—San Francisco becomes SanFrancisco. Spaces should never be used in a URL.

The `updated` column doesn’t need a value, because it’s automatically initialized to the current timestamp. However, the timestamp needs to be set explicitly in the `created` column by using the MySQL `NOW()` function, which inserts the current date and time. As explained in “Using SQL functions with Zend_Db” in [Lesson 8](#ch08.html#ch08), functions need to be wrapped in a `Zend_Db_Expr` object.

**3.** Insert the data with the `insert()` method like this:

$inserted = $dbWrite->insert('places', $data);

**4.** If any photos have been uploaded, you need to get the primary key of the new record and insert the details in the `photos` and `place2photo` tables. However, if nothing has been uploaded, there’s nothing more to do apart from display a message reporting the result.

The result of the `insert()` method is captured in `$inserted`. If the `$images` array created by upload_images.php contains any values, you know images have been uploaded. Use both values to determine whether to retrieve the new record’s primary key. Add the following code on the next line:

if ($inserted && isset($images)) {  

  $place_id = $dbWrite->lastInsertId();  

}

This gets the primary key from the `places` table and stores it in `$place_id`.

**5.** You can now loop through the `$images` array to insert the filename and caption for each image in the `photos` table. Immediately after inserting the data, capture the primary key using the `lastInsertId()` method, and insert the primary keys from the `places` and `photos` tables in `place2photo`. The loop that does all that looks like this:

if ($inserted && isset($images)) {  

  $place_id = $dbWrite->lastInsertId();  

  foreach($images as $image) {  

   $data = array('filename' => $image['filename'],  

                  'caption' => $image['caption']);  

   $dbWrite->insert('photos', $data);  

   $photo_id = $dbWrite->lastInsertId();  

   $data = array('place_id' => $place_id,  

                  'photo_id' => $photo_id);  

   $dbWrite->insert('place2photo', $data);  

  }  

}

There’s no need to check for errors in the image uploads, because the conditional statement you added in step 1 prevents the script from getting this far if there are any problems.

**6.** All that remains is to do is to prepare the messages to report what has happened. The next section of code needs to go after the conditional statement that handles the images. It looks like this:

$dbWrite->insert('place2photo', $data);  

}  

}  

if ($inserted) {  

      $messages[] = $_POST['name'] . ' is now listed in the database';  

} else {  

      $errors[] = $_POST['name'] . ' could not be inserted';  

}  

}  

}  

catch (Exception $e) {  

7.** Save db_insert_place.php, and test insert_place.php by typing values in the “Place name” and Description fields, and selecting a state. Browse to the images folder to select a couple of images and add captions. Then click Insert Place. If all your code and the database structure are correct, you should see a series of success messages at the top of the form.

![image](graphics/fig10_18.jpg)

**8.** Check the image_upload folder in the Files panel. Copies of the photos you selected should have been added to the folder. Also check in phpMyAdmin. The `places`, `photos`, and `place2photo` tables should have the first set of data.

![image](graphics/fig10_19.jpg)

![image](graphics/fig10_20.jpg)

![image](graphics/fig10_21.jpg)

If it didn’t work, compare all your files carefully with insert_place_02.php in lesson10/completed and with db_definitions_02.php, db_insert_place_03.php, and upload_images.php in lesson10/completed/scripts. Also check your database structure, and load it from lesson10/start/scripts/cms_structure.sql. This is a complex script, so there are many places where you might have made a mistake.

Before moving on to the next section, add two or three more places to the database. The images folder contains photos of ten locations in Arizona, California, Nevada, and Utah, but you don’t need to confine yourself to them. Not every place needs to be accompanied by a photo, and captions are optional. The CMS is designed to allow you to add photos and edit their details later.

#### Inserting photos separately

All the hard work for this administration page has already been done. The script in upload_images.php validates the images and uploads them. The main task is to create the script that inserts the image details into the database.

**1.** Open insert_photos.php. The `<select>` menu needs to be populated with a list of the places already registered in the database. This will be used in the same way as the State `<select>` menu in insert_place.php, storing the primary key of each place so it can be inserted as a foreign key in the `place2photo` table.
