
## 3.4 Update Data

On this section, we will update data on particular ID. We use UPDATE statement and pass updated data.

Create a function called updateEmployee() and write this code.

```php
<?php
include('dbinfo.php');

class CRUDDemo {
    private $msg = "";

    public function getMsg()
    {
        return $this->msg;
    }
    public function updateEmployee($id,$name,$department,$level) {

        $success = -1;
        try {

            global $connString;

            $conn = pg_connect($connString);
            if( $conn === false )
            {
                $this->msg = "Unable to connect PostgreSQL Server.";
                return $success;
            }

            $query = "update hrd_employee set name=$1,department=$2,level=$3 where id=$4";
            $params = array(&$name,&$department,&$level,&$id);

            $res = pg_query_params($conn,$query,$params);
            if($res === FALSE) {
                $this->msg = "Error in executing query.";
                return $success;
            }
            $num_rows=pg_affected_rows($res);
            $success = $num_rows;
            $this->msg = "";

            pg_close($conn);

        } catch (Exception $e) {
            $this->msg = $e->getMessage();
            $success = -1;
        }

        return $success;
    }
}
```

Save this code.

Now we work on file testcrud.php to call updateEmployee(). In this testing, we update employee with ID 30. You may change employee ID.

```php
<?php

include( 'CRUDDemo.php' );

$obj = new CRUDDemo();

// update
// update data with id = 30. Change it with own id data
$success = $obj->updateEmployee(30, "update-employee","update-department","u-level");
echo "Success: " . $success . "\n";
echo "Error message: " . $obj->getMsg();
```

Save this code. Run file testcrud.php.

![](img/c57c0fe41a78a4cec34dfc1c6ad7b9d6_41_0.png)

If we open table hrd_employee, you can find updated data on data with ID = 30.

|  | id | name | department | level | created (yyyy-MM-dd HH:mm:ss.ffffff) |
|---|---|---|---|---|---|
| 1 | 28 | person 1 | department 1 | A1 | 2016-03-25 14:15:16.876907 |
| 2 | 29 | person 2 | department 2 | A2 | 2016-03-25 14:15:16.896776 |
| 3 | 31 | person 4 | department 4 | A4 | 2016-03-25 14:15:16.931068 |
| 4 | 32 | person 5 | department 5 | A5 | 2016-03-25 14:15:16.942084 |
| 5 | 33 | person 6 | department 6 | A6 | 2016-03-25 14:15:16.957744 |
| 6 | 34 | person 7 | department 7 | A7 | 2016-03-25 14:15:16.975317 |
| 7 | 35 | person 8 | department 8 | A8 | 2016-03-25 14:15:16.986468 |
| 8 | 36 | person 9 | department 9 | A9 | 2016-03-25 14:15:16.993604 |
| 9 | 37 | person 10 | department 10 | A10 | 2016-03-25 14:15:16.999911 |
| 10 | 30 | update-employee | update-department | u-level | 2016-03-25 14:15:16.913929 |

## 3.5 Deleting Data

To delete data, we use SQL statement using DELETE FROM and pass employee ID.

Create a function called deleteEmployee() and write this code.

```php
<?php
include('dbinfo.php');

class CRUDDemo {
    private $msg = "";

    public function getMsg()
    {
        return $this->msg;
    }
    public function deleteEmployee($id) {

        $success = -1;
        try {

            global $connString;

            $conn = pg_connect($connString);
            if( $conn === false )
            {
                $this->msg = "Unable to connect PostgreSQL Server.";
                return $success;
            }

            $query = "delete from hrd_employee where id=$1";
            $params = array(&$id);

            $res = pg_query_params($conn,$query,$params);
            if($res === FALSE) {
                $this->msg = "Error in executing query.";
                return $success;
            }
            $num_rows=pg_affected_rows($res);
            $success = $num_rows;
            $this->msg = "";

            pg_close($conn);

        } catch (Exception $e) {
            $this->msg = $e->getMessage();
            $success = -1;
        }

        return $success;
    }
}
```

Save this code.

Now we test this function on file **testcrud.php**. We delete data with ID = 30. You can change this ID.

```php
<?php

include('CRUDDemo.php');

$obj = new CRUDDemo();

// delete
// delete data with id = 30. Please change it
$success = $obj->deleteEmployee(30);
echo "Success: " . $success . "\n";
echo "Error message: " . $obj->getMsg();
```

Save this code and run **testcrud.php**.

![](img/c57c0fe41a78a4cec34dfc1c6ad7b9d6_44_0.png)

You can verify by opening table **hrd_employee**. Data with ID = 30 should not show.

| id | name | department | level | created (yyyy-MM-dd HH:mm:ss.ffffff) |
|----|------|------------|-------|--------------------------------------|
| 28 | person 1 | department 1 | A1 | 2016-03-25 14:15:16.876907 |
| 29 | person 2 | department 2 | A2 | 2016-03-25 14:15:16.896776 |
| 31 | person 4 | department 4 | A4 | 2016-03-25 14:15:16.931068 |
| 32 | person 5 | department 5 | A5 | 2016-03-25 14:15:16.942004 |
| 33 | person 6 | department 6 | A6 | 2016-03-25 14:15:16.957744 |
| 34 | person 7 | department 7 | A7 | 2016-03-25 14:15:16.975317 |
| 35 | person 8 | department 8 | A8 | 2016-03-25 14:15:16.986468 |
| 36 | person 9 | department 9 | A9 | 2016-03-25 14:15:16.993604 |
| 37 | person 10 | department 10 | A10 | 2016-03-25 14:15:16.999911 |

## 4. Working with Image and Blob Data

This chapter explains how to work with image and blob data on PostgreSQL and manipulate them using PHP.

### 4.1 Image and Blob Data

PostgreSQL provides data type for BYTEA which can store image file and binary type data.

In this chapter, we will work with image file on PostgreSQL. The following is table schema, called ImagesFiles.

![](img/c57c0fe41a78a4cec34dfc1c6ad7b9d6_47_0.png)

The following is a script for creating imagefiles table.

```
CREATE TABLE public.imagesfiles
(
  id SERIAL PRIMARY KEY,
  filename character(50),
  filetype character(10),
  imgfile BYTEA,
  created timestamp without time zone
)
WITH (
OIDS=FALSE
);
ALTER TABLE public.imagesfiles
OWNER TO postgres;
```

filetype is image type of uploading file. This is important while we want to display the image. See section 4.3 for further explanation.

The next action we create two PHP application, uploading image and listing image data.

### 4.2 Uploading Image

In this section, we upload image using traditional way: file html. After user choose image file and then click **Submit** button, PHP file will process uploading file and store it into database.

Firstly, we create **uploadimage.html** and write this script.

```html
<!DOCTYPE html>
<html>
<head>
    <title>PHP and PostgreSQL Programming by Example</title>
</head>
<body>
<h1>Uploading Image file</h1>

<p><br/></p>
<p>Upload image file (JPG/PNG/TIF/GIF) with file size maximum 500KB.</p>

<form action="upload_process.php" method="post"
      enctype="multipart/form-data">
    <label for="file">Image File (JPG/PNG/TIF/GIF):</label>
    <input type="file" name="file" id="file"><br/><br/>
    <input type="submit" name="submit" value="Submit">
</form>

</body>
</html>
```

You can see we use form multipart/form-data and input file to upload image file. The form action is POST and navigate to **upload_process.php**.

Now we create **upload_process.php** to process uploading file. We validate file input for gif, tif, jpg and png and restrict file size below 500 KB. Let’s write this code into **upload_process.php**.

```php
<?php

include('dbinfo.php');

$allowedExts = array("gif", "tif", "jpg", "png");
$filename = $_FILES["file"]["name"];
$temp = explode(".", $filename);
$fileExt = end($temp);
$imageType = $_FILES["file"]["type"];

if ((($imageType == "image/gif") || ($imageType == "image/jpg") || ($imageType == "image/jpeg")
    || ($imageType == "image/gif") || ($imageType == "image/tiff")
    || ($imageType == "image/x-png") || ($imageType == "image/png"))
    && ($_FILES["file"]["size"] < 500000)
    && in_array($fileExt, $allowedExts)) {
```
