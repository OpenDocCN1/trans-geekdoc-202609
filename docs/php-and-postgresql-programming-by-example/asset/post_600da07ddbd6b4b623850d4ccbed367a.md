
## 1.3 PostgreSQL Server

You can download and install PostgreSQL server on [http://www.postgresql.org/download/](http://www.postgresql.org/download/). Don’t forget to install pgAdmin tool to manage our database. You can use commandline or any database tool.

![](img/c57c0fe41a78a4cec34dfc1c6ad7b9d6_21_0.png)

## 1.5 Development Tools

Basically you can use any editor to develop PHP. You can find a list of PHP editor on http://en.wikipedia.org/wiki/List_of_PHP_editors . I used PHP WebStorm, http://www.jetbrains.com/phpstorm/ , and IntelliJ IDEA, http://www.jetbrains.com/idea/ . They provide 30-days trial.

The following is a sample of PhpStorm.

![](img/c57c0fe41a78a4cec34dfc1c6ad7b9d6_23_0.png)

I also use DataGrip to manage, https://www.jetbrains.com/datagrip/ , PostgreSQL server.

## postgres.public.employee - DataGrip 1.0.3

PostgreSQL - postgres@localhost

+   - pg_catalog
+   - public
+     - sequences
+     - tables
+       - employee
+         - hrd_employee
+           - id INTEGER
+           - name CHAR(30)
+           - department CHAR(30)
+           - level CHAR(10)
+           - created TIMESTAMP
+     - routines

<Filter criteria>

0 rows

| id | name | department |
|---|---|---|

Data DDL

## 2.1 Connecting to PostgreSQL

After we setup PHP and PostgreSQL driver on IIS and Apache, now we can test to connect PostgreSQL Server. We can use **pg_connect()** to connect database PostgreSQL Server and **pg_close()** to close connection.

## 2.2 Creating PHP and Connecting to PostgreSQL

In this section, we create PHP file, called **hello.php**. The objective is to connect PostgreSQL via database authentication.

Firstly, we define server, username, password and database.

```php
<?php

$dbServer = "(local)";
$username = "dbtester";
$password = "dbtester";
$database = "postgres";
```

Please change $username and $password values.

Then we connect to PostgreSQL using **pg_connect()** by passing server information.

```php
// Connecting, selecting database
$dbconn = pg_connect("host=$dbServer dbname=$database user=$username password=$password")
or die('Could not connect: ' . pg_last_error());

$stat = pg_connection_status($dbconn);
    if ($stat === PGSQL_CONNECTION_OK) {
        echo 'Connection status ok';
    } else {
        echo 'Connection status bad';
    }

// Closing connection
pg_close($dbconn);
```

At the end of code, we close connection using **pg_close()**.

Save all code.

## 2.3 Testing

Deploy file hello.php into web server. I tested built-in web server from PhpStorm tool. Open browser and type URL of hello.php file.

Here is a sample of running PHP application.

![](img/c57c0fe41a78a4cec34dfc1c6ad7b9d6_28_0.png)

## 3. CRUD Operations

This chapter explains how to manipulate data PostgreSQL using PHP.

## 3.1 CRUD Operations

CRUD (Create, Read, Update, Delete) operations are basic data manipulation for database. In this chapter we will develop PHP application to execute CRUD operations. We use existing database, postgres. Then, create a table, called **hrd_employee**. The following is a query for creating the table.

```
CREATE TABLE public.hrd_employee
(
  id SERIAL PRIMARY KEY,
  name character(30),
  department character(30),
  level character(10),
  created timestamp without time zone
)
WITH (
  OIDS=FALSE
);
ALTER TABLE public.hrd_employee
  OWNER TO postgres;
```

You can run it using pgAdmin. You also can run it using other tool, for instance, DataGrip from Jetbrains, https://www.jetbrains.com/datagrip/ .

![](img/c57c0fe41a78a4cec34dfc1c6ad7b9d6_31_0.png)

A form of DataGrip.

![](img/c57c0fe41a78a4cec34dfc1c6ad7b9d6_32_0.png)

For database connection configuration, I created a PHP file, called **dbinfo.php**. The following is a content of dbinfo.php.

```php
<?php

$dbServer = "localhost";
$username = "user_db";
$password = "user_pass";
$database = "postgres";

$connString = "host=$dbServer dbname=$database user=$username password=$
```

Please change database parameter values based on your configuration.

You can modify this database configuration. The next step is to create a PHP class, called **CRUDDemo**. This class provides several functions to execute CRUD operations. Let’s start. Create PHP file, called **CRUDDemo.php**. Then write this script.

```php
<?php

include('dbinfo.php');

class CRUDDemo {
    private $msg = "";

    public function getMsg()
    {
```

```php
return $this->msg;
    }
}
```

Depending on your **dbinfo.php** location, you can change its path.

We will add some functions to execute CRUD operations on next section.

## 3.2 Creating Data

In this scenario, we create new employee and try to retrieve inserted ID. PostgreSQL driver provides function RETURNING to retrieve ID from inserted query SQL statement. We will use SQL statement to insert data but we use parameters to prevent SQL injection.

We use function pg_fetch_row() to obtain ID value from query RETURNING. At the end of code, don’t forget to release our usage resources and close connection using pg_close().

Now we add function createEmployee() to create new employee. Then, write this code.

```php
<?php
include('dbinfo.php');

class CRUDDemo {
    private $msg = "";

    public function getMsg()
    {
        return $this->msg;
    }
    public function createEmployee($name,$department,$level) {

        $id = -1;
        try {

            global $connString;

            $conn = pg_connect($connString);
            if( $conn === false )
            {
                $this->msg = "Unable to connect PostgreSQL Server.";
                return $id;
            }

            // insert data
            $query = "insert into hrd_employee(name,department,level,cre
            $params = array(&$name,&$department,&$level);

            $res = pg_query_params($conn,$query,$params);
            $row = pg_fetch_row($res);
            $id = $row[0];

            pg_close($conn);

        } catch (Exception $e) {
            $this->msg = $e->getMessage();
            $id = -1;
        }

        return $id;
    }
}
```

Save this code.

To test this class, we create PHP file, called **testcrud.php**. After that, we try to insert 10 data.

```php
<?php

include('CRUDDemo.php');

$obj = new CRUDDemo();

// insert 10 data
for($i=1;$i<=10;$i++) {
    $id = $obj->createEmployee("person " . $i,"depertment " . $i,"A".$i);
    echo "Inserted Id: " .$id . " \n";
    echo "Error message: " . $obj->getMsg() . " \n\n";
}
```

Save the code and try to run **testcrud.php**.

The following is sample running test on Intellij IDEA.

![](img/c57c0fe41a78a4cec34dfc1c6ad7b9d6_35_0.png)

To verify success or not, we can check database. If success, we can see 10 new data on table hrd_employee. Here is a sample of 10 data from table **hrd_employee** on PostgreSQL.

![](img/c57c0fe41a78a4cec34dfc1c6ad7b9d6_36_0.png)

```php
    return $data;
}
}
```

You can see that we define $data to hold data from database PostgreSQL.

Save this code.

Now we test function readEmployeeList(). Open file testcrud.php and add code as below.

```php
<?php

include('CRUDDemo.php');

$obj = new CRUDDemo();

// read data
$list = $obj->readEmployeeList();
if($list) {
    foreach($list as $item) {
        $content = "";
        foreach($item as $key => $value) {
            $content = $content . $key . ": " . $value . "\n";
        }
        echo $content . "\n";
    }
}
```

Save this code.

You can execute file testcrud.php. The following is a sample of output.

```
/usr/local/bin/php /Users/apusk/Documents/MyBooks/pearess/php_postgresql/codes/testcrud.php
id: 28
name: person 1
department: depertment 1
level: A1
created: 2016-03-25 14:15:16.876907

id: 29
name: person 2
department: depertment 2
level: A2
created: 2016-03-25 14:15:16.896776

id: 30
name: person 3
department: depertment 3
level: A3
created: 2016-03-25 14:15:16.913929

id: 31
name: person 4
department: depertment 4
level: A4
created: 2016-03-25 14:15:16.931068
```
