
## How to execute INSERT, UPDATE, and DELETE statements

Figure 4-6 shows how to prepare and execute INSERT, UPDATE, and DELETE statements. The examples in this figure use the prepare, bindValue, execute, and closeCursor methods presented in the last few figures. As a result, you shouldn’t have much trouble understanding how these examples work.

The first example inserts a row into the database. Here, the INSERT statement specifies four parameters: one value for each column.

The second example updates a row in the database. Here, the UPDATE statement specifies two parameters: the first specifies the new price for the product and the second uniquely identifies the product to update.

The third example deletes a row from the database. Here, the DELETE statement specifies a single parameter that uniquely identifies the product to delete.

### How to execute an INSERT statement

```php
$category_id = 1;
$code = 'strat';
$name = 'Fender Stratocaster';
$price = 699.99;

$query = "INSERT INTO products
            (categoryID, productCode, productName, listPrice)
        VALUES
            (:category_id, :code, :name, :price)";

$statement = $db->prepare($query);
$statement->bindValue(':category_id', $category_id);
$statement->bindValue(':code', $code);
$statement->bindValue(':name', $name);
$statement->bindValue(':price', $price);
$statement->execute();
$statement->closeCursor();
```

### How to execute an UPDATE statement

```php
$product_id = 4;
$price = 599.99;

$query = "UPDATE products
        SET listPrice = :price
        WHERE productID = :product_id";

$statement = $db->prepare($query);
$statement->bindValue(':price', $price);
$statement->bindValue(':product_id', $product_id);
$statement->execute();
$statement->closeCursor();
```

### How to execute a DELETE statement

```php
$product_id = 4;

$query = "DELETE FROM products
        WHERE productID = :product_id";

$statement = $db->prepare($query);
$statement->bindValue(':product_id', $product_id);
$statement->execute();
$statement->closeCursor();
```

Figure 4-6: How to execute INSERT, UPDATE, and DELETE statements

## The Product Viewer application

Now that you know how to use PHP to work with MySQL, you’re ready to see how database-driven PHP applications work. To start, Figure 4-7 presents a simple Product Viewer application that lets you view product data by category. After you review this application, you’ll study a more complicated application.

### The user interface

The primary page of the Product Viewer application is divided into two parts. The sidebar on the left displays a list of category links that let the user select a category. The main portion of the page lists the products for that category in an HTML table.

When the application starts, this application displays the products in the category named Guitars. Then, if the user wants to view the products in another category, the user can click on the link for that category. If, for example, the user clicks on the Basses link, this application displays the products in that category. To facilitate that, the category_id field is sent with the HTTP request for the same page. This is illustrated by the URL for the second screen in this figure, which requests the default page in the ch04_product_viewer directory.

To make it easy to identify columns and rows for the product data, this application uses CSS to format the HTML table. This formatting adds a solid border around the outside of the table and a dashed border between the columns and rows.

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_162_0.png)

### The user interface after the user selects a new category

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_162_1.png)

### The code

The database.php file contains the code that creates the PDO object and stores it in the variable named $db. This file is executed by the index.php file that’s shown on the next page.

However, if an error occurs when this file is executed, the catch block stores the error message in a variable named $error_message. Then, the catch block uses the include function to include the database_error.php file, which displays a page that contains the error message. Last, the catch block exits the script.

Note that in the database.php file, the username for the connection is “mgs_user” and the password is “pa55word”. For this connection to work, then, a user with this username and password must be stored with the MySQL database. In fact, as you learned in chapter 3, this user is created by the SQL script that creates the databases for this book. Also, this user is given the privileges that are needed for running SELECT, INSERT, UPDATE, and DELETE statements against any table in the my_guitar_shop1 database. As a result, this connection will work for this application.

### The database.php file

```php
<?php
    $dsn = 'mysql:host=localhost;dbname=my_guitar_shop1';
    $username = 'mgs_user';
    $password = 'pa55word';

    try {
        $db = new PDO($dsn, $username, $password);
    } catch (PDOException $e) {
        $error_message = $e->getMessage();
        include('database_error.php');
        exit();
    }
?>
```

### The database_error.php file

```php
<!DOCTYPE html>
<html>
    <!-- the head section -->
    <head>
        <title>My Guitar Shop</title>
        <link rel="stylesheet" type="text/css" href="main.css">
    </head>

    <!-- the body section -->
    <body>
    <main>
        <h1>Database Error</h1>
        <p>There was an error connecting to the database.</p>
        <p>The database must be installed as described in appendix A.</p>
        <p>The database must be running as described in chapter 1.</p>
        <p>Error message: <?php echo $error_message; ?></p>
    </main>
    </body>
</html>
```

## Automated Container Terminals – A Literature Review on the Operational Research Contributions

Nils Kemper, Asir Asad, Jürgen W. Böning

Received: 24 March 2021 / Revised: 10 November 2021 / Accepted: 15 November 2021 © The Author(s) 2021

**Abstract** Due to constantly increasing container volumes and the continuously increasing size of container vessels, the optimization and automation of container terminals has become more and more important. Especially in the operational area, terminal capacities can be increased through an optimized design and utilization of the existing resources. The focus of this literature review is the evaluation of past and current research contributions towards the automatic or semi-automatic control of a container terminal. Hereby, it is possible to assist the future planning and decisions related to the standardization of the terminal automation regarding logistics processes, equipment, and control systems. A special focus is put on the (semi-)automated control of logistic processes such as the stowage planning, the allocation of resources, and their scheduling. We also detail the operational research methods used to solve the often complex optimization problems. The searched literature consists of research articles published in the leading scholarly journals as well as in the relevant conference proceedings of the last decade. We can show that most of the state-of-the-art approaches are characterized by sophisticated mathematical models and tested against terminal environments, whereas the entire process chain of a modern automated container terminal is rarely represented in the literature. In most cases, only the optimization of individual processes is considered. Additionally, the applied models are rarely reused or even compared to alternative models of the same context. To this end, we propose a standardization of the definition of the overall as well as of sub-processes in the context of an automated container terminal to facilitate the comparability of different approaches.

**Keywords:** Automated container terminal · Container terminal · Operations research · Logistics · Automation

## 1 Introduction

The constant growth in global container shipping traffic and the increasing size of container vessels exert pressure on seaport container terminals to increase their productivity, throughput, and efficiency. Especially since the era of containerization, ports constitute one of the most important nodes in the global supply chain. In fact, around 90% of the global trade volume is handled by maritime transportation. The operation of a container terminal is a highly complex process, which requires the interplay of several different subsystems. This is especially true for automated container terminals. As the complexity of the processes is high, sophisticated methods are required for planning and controlling the processes in the terminal. However, the available approaches often target specific sub-processes or optimization issues.

## 2 State of the Art of Automated Container Terminals

### 2.1 Functional Areas, Material Handling Equipment, and Processes

In general, a container terminal can be separated into six different areas. These areas are the berth, the quay, the yard, the gate, the railway, and the depot. The berth is the area where vessels are moored and where loading and unloading of the containers takes place. The quay is the area where the containers are stored temporarily before they are transported to the yard. The yard is the area where containers are stored for a longer period. The gate is the area where containers enter and leave the terminal by truck. The railway is the area where containers are transferred between the terminal and the railway. The depot is the area where empty containers are stored. The material handling equipment (MHE) used in a container terminal can be classified into three categories: quay cranes, yard cranes, and internal transport vehicles. These are used to move containers between the different areas of the terminal. The processes that are executed in a container terminal can be classified into four groups: the vessel process, the quay process, the yard process, and the gate process. The vessel process includes all activities that are related to the vessel, such as the berthing and the departure of the vessel. The quay process includes the loading and unloading of the vessel. The yard process includes the stacking and retrieval of containers in the yard. The gate process includes all activities that are related to the gate, such as the check-in and check-out of the trucks.

| | Type | Short Description |
|---|---|---|
| ACC | Automated Container Terminal | Container terminal with automated processes |
| AGV | Automated Guided Vehicle | Automated transport vehicle |
| ALV | Automated Lifting Vehicle | Automated vehicle with lifting capability |
| ASC | Automated Stacking Crane | Automated crane for stacking operations |
| ARMG | Automated Rail-Mounted Gantry | Automated gantry crane on rails |
| ARTG | Automated Rubber-Tired Gantry | Automated gantry crane on rubber tires |
| ATLS | Automated Transport and Lifting System | Automated transport with lifting capability |
| AV | Automated Vehicle | Generic automated vehicle |
| BCO | Beneficial Cargo Owner | Owner of the cargo |
| BAP | Berth Allocation Problem | Problem of allocating berths |
| BEO | Box Exchange Point | Point of box exchange |
| BLAP | Berth Layout Problem | Problem of berth layout |
| BMH | Box Handling Machine | Machine for box handling |
| BPM | Business Process Model | Model of business processes |
