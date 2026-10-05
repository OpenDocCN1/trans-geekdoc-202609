# Lesson 33: PHP with AJAX

**Objective:** In this lesson you will learn how to use AJAX in conjunction with your PHP pages. This lesson will display hundreds of records and show detail button for each record. The detail button will update a single record at a time rather than updating all records. AJAX stands for Asynchronous JavaScript and XML. You don't have to use XML to make this work. This lesson will only use JavaScript and PHP. The power behind AJAX is the ability to retrieve data from your database and only update part of your web rather than reloading the entire page. The point behind AJAX is to reduce the load on your server. It is also cross-platform independent, which is always a nice bonus. I believe that with the use of any technology should be used appropriately. You won't need to reinvent the wheel with AJAX for your design. It does take a lot of extra code and an extra web page each time you need to call the JavaScript function. If you are displaying 1 record at a time AJAX probably isn't going to provide you with any noticeable improvement in performance. If, you are displaying a lot of records you could use AJAX to fetch the data from a single record when the user clicks a button to "show detail". I would also suggest that in a real-world design you need to display hundreds of records you want to re-think your design and implement a page system of say 10 records at a time to reduce the load on the server. If the user wants more information they can click the link and be to the single detail page. That will provide the same performance as AJAX, with less overhead and fewer technologies to support.

**Difficulty:** Difficult

**Sample Files:**
PHPFiles/Advanced/Lesson33/show_all.php
PHPFiles/Advanced/Lesson33/show_detail.php
PHPFiles/Advanced/Lesson33/ajax.f12

> This lesson uses a separate database file to demonstrate the lesson. Please upload the ajax.f12 database to your folder.

**Page Navigation:**

List | Detail | Database
|---|---|---|

**FileMaker API Methods:**
newFindAllCommand()
execute()
getRecords()
RecordID()
getField()
RecordByID()

**Code:**
The sample database has 152 records from pizza restaurants around the country. The whole point of AJAX is to improve performance. There the Demo layout only displays the Name field to match the show_all.php page. To maximize your layouts you should only have the fields that display on the web page. Adding additional fields slows down the response time. It may not be apparent for 152 records and four fields. However, under load with dozens of fields and thousands of records you could take an unnecessary performance hit, which is what AJAX can help solve. The second layout, Demo Detail, has the Address, City, and State fields. Notice that Name is not on the layout. That's because the show_detail.php page that AJAX uses to retrieve the record only needs these three fields. Again, it's all performance and using exactly what you need and nothing more.