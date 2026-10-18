![PHP Data Persistence with Doctrine 2 ORM](images/title_page.jpg)

## PHP Data Persistence with Doctrine 2 ORM

### Concepts, Techniques and Practical Solutions

 

#### Michael Romer

 

This book is for sale at [http://leanpub.com/doctrine2-en](http://leanpub.com/doctrine2-en)

This version was published on 2013-08-23

![publisher's logo](images/leanpub-logo.png)

\*   \*   \*   \*   \*

This is a [Leanpub](http://leanpub.com) book. Leanpub empowers authors and publishers with the Lean Publishing process. [Lean Publishing](http://leanpub.com/manifesto) is the act of publishing an in-progress ebook using lightweight tools and many iterations to get reader feedback, pivot until you have the right book and build traction once you do.

\*   \*   \*   \*   \*

© 2013 by Michael Romer, Grevingstrasse 35, 48151 Münster, Germany, mail@michael-romer.de - All rights reserved. 

# Table of Contents

*   [1 About this book](#chap00.xhtml#leanpub-auto-about-this-book) 
    *   [1.1 Software version](#chap00.xhtml#leanpub-auto-software-version)
    *   [1.2 Database system](#chap00.xhtml#leanpub-auto-database-system)
    *   [1.3 Code downloads](#chap00.xhtml#leanpub-auto-code-downloads)
    *   [1.4 Conventions used in this book](#chap00.xhtml#leanpub-auto-conventions-used-in-this-book)
    *   [1.5 An important notice for Amazon customers](#chap00.xhtml#leanpub-auto-an-important-notice-for-amazon-customers)
*   [2 Introduction](#chap01.xhtml#leanpub-auto-introduction) 
    *   [2.1 Object oriented programming (OOP) & the Domain Model](#chap01.xhtml#leanpub-auto-object-oriented-programming-oop--the-domain-model)
    *   [2.2 Demo application](#chap01.xhtml#leanpub-auto-demo-application)
*   [3 A self-made ORM](#chap02.xhtml#leanpub-auto-a-self-made-orm) 
    *   [3.1 Loading an Entity](#chap02.xhtml#leanpub-auto-loading-an-entity)
    *   [3.2 Saving an entity](#chap02.xhtml#leanpub-auto-saving-an-entity)
    *   [3.3 Associations](#chap02.xhtml#leanpub-auto-associations)
    *   [3.4 Next steps](#chap02.xhtml#leanpub-auto-next-steps)
*   [4 Hello, Doctrine 2!](#chap03.xhtml#leanpub-auto-hello-doctrine-2) 
    *   [4.1 Installation](#chap03.xhtml#leanpub-auto-installation)
    *   [4.2 A first Entity](#chap03.xhtml#leanpub-auto-a-first-entity)
    *   [4.3 A first Association](#chap03.xhtml#leanpub-auto-a-first-association)
    *   [4.4 Core concepts at a glance](#chap03.xhtml#leanpub-auto-core-concepts-at-a-glance)
*   [5 Defining entities](#chap04.xhtml#leanpub-auto-defining-entities) 
    *   [5.1 Mapping formats](#chap04.xhtml#leanpub-auto-mapping-formats)
    *   [5.2 Mapping objects to tables](#chap04.xhtml#leanpub-auto-mapping-objects-to-tables)
    *   [5.3 Mapping scalar member variables to fields](#chap04.xhtml#leanpub-auto-mapping-scalar-member-variables-to-fields)
    *   [5.4 Inheritance](#chap04.xhtml#leanpub-auto-inheritance)
*   [6 References between Entities](#chap05.xhtml#leanpub-auto-references-between-entities) 
    *   [6.1 One to one relationship, unidirectional](#chap05.xhtml#leanpub-auto-one-to-one-relationship-unidirectional)
    *   [6.2 One to one relationship, bidirectional](#chap05.xhtml#leanpub-auto-one-to-one-relationship-bidirectional)
    *   [6.3 One to many relationship, bidirectional](#chap05.xhtml#leanpub-auto-one-to-many-relationship-bidirectional)
    *   [6.4 Many to many relationship, unidirectional](#chap05.xhtml#leanpub-auto-many-to-many-relationship-unidirectional)
    *   [6.5 Many to many relationship, bidirectional](#chap05.xhtml#leanpub-auto-many-to-many-relationship-bidirectional)
    *   [6.6 One to many relationship, unidirectional](#chap05.xhtml#leanpub-auto-one-to-many-relationship-unidirectional)
    *   [6.7 Many to one relationship, unidirectional](#chap05.xhtml#leanpub-auto-many-to-one-relationship-unidirectional)
    *   [6.8 One to one relationship, self-referencing](#chap05.xhtml#leanpub-auto-one-to-one-relationship-self-referencing)
    *   [6.9 One to many relationship, self-referencing](#chap05.xhtml#leanpub-auto-one-to-many-relationship-self-referencing)
    *   [6.10 Many to many relationship, self-referencing](#chap05.xhtml#leanpub-auto-many-to-many-relationship-self-referencing)
*   [7 Managing Entities](#chap06.xhtml#leanpub-auto-managing-entities) 
    *   [7.1 Creating a new Entity](#chap06.xhtml#leanpub-auto-creating-a-new-entity)
    *   [7.2 Loading an existing Entity](#chap06.xhtml#leanpub-auto-loading-an-existing-entity)
    *   [7.3 Changing an existing Entity](#chap06.xhtml#leanpub-auto-changing-an-existing-entity)
    *   [7.4 Removing an Entity](#chap06.xhtml#leanpub-auto-removing-an-entity)
    *   [7.5 Sorting an association](#chap06.xhtml#leanpub-auto-sorting-an-association)
    *   [7.6 Removing an association](#chap06.xhtml#leanpub-auto-removing-an-association)
    *   [7.7 Life Cycle events](#chap06.xhtml#leanpub-auto-life-cycle-events)
    *   [7.8 Cascading operations](#chap06.xhtml#leanpub-auto-cascading-operations)
    *   [7.9 Transactions](#chap06.xhtml#leanpub-auto-transactions)
*   [8 Doctrine Query Language](#chap07.xhtml#leanpub-auto-doctrine-query-language) 
    *   [8.1 Introduction](#chap07.xhtml#leanpub-auto-introduction-1)
    *   [8.2 Retrieving results](#chap07.xhtml#leanpub-auto-retrieving-results)
    *   [8.3 Constructing basic queries](#chap07.xhtml#leanpub-auto-constructing-basic-queries)
    *   [8.4 Constructing join queries](#chap07.xhtml#leanpub-auto-constructing-join-queries)
*   [9 Command line tools](#chap08.xhtml#leanpub-auto-command-line-tools) 
    *   [9.1 Setting up the command line tools](#chap08.xhtml#leanpub-auto-setting-up-the-command-line-tools)
    *   [9.2 DBAL commands](#chap08.xhtml#leanpub-auto-dbal-commands)
    *   [9.3 ORM commands](#chap08.xhtml#leanpub-auto-orm-commands)
*   [10 Caching](#chap09.xhtml#leanpub-auto-caching) 
    *   [10.1 Introduction to ORM cache types](#chap09.xhtml#leanpub-auto-introduction-to-orm-cache-types)
    *   [10.2 Caching backends](#chap09.xhtml#leanpub-auto-caching-backends)
*   [11 Advanced Topics](#chap10.xhtml#leanpub-auto-advanced-topics) 
    *   [11.1 Zend Framework 2 integration](#chap10.xhtml#leanpub-auto-zend-framework-2-integration)
    *   [11.2 Native SQL statements](#chap10.xhtml#leanpub-auto-native-sql-statements)
    *   [11.3 Doctrine 2 Extensions](#chap10.xhtml#leanpub-auto-doctrine-2-extensions)

## 1 About this book

> “I would have written a shorter book, but I did not have the time.” freely adapted from Blaise Pascal (French mathematician, logician, physicist and theologian.)

### 1.1 Software version

This book is based on Doctrine 2.3, however, most of its content will still be valid for later versions.

### 1.2 Database system

All examples in this book are based on [MySQL](http://www.mysql.com). However, Doctrine 2 supports other DBMS such as [PostgreSQL](http://www.postgresql.org/) or [SQLite](http://www.sqlite.org/). Most examples will work with other DBMS right away, some may need to be adopted.

### 1.3 Code downloads

Most of the code shown in this book can be found in a [public repository GitHub](https://github.com/michael-romer/doctrine2buch). While the code of chapter 3 (“A self-made ORM”) can be found on the [master branch](https://github.com/michael-romer/doctrine2buch), there is [another branch available called “doctrine”](https://github.com/michael-romer/doctrine2buch/tree/doctrine), which holds the modifications made in chapter 4 (“Hello, Doctrine 2!”). There is a third [branch called “application”](https://github.com/michael-romer/doctrine2buch/tree/application) holding the modifications made in the later chapters. As the demo application grows throughout the book, the “application branch” also includes a basic MVC-framework called [Slim](http://www.slimframework.com/) to better structure the application’s code as well as [Twitter’s Bootstrap](http://getbootstrap.com) for some basic UI styling.

### 1.4 Conventions used in this book

Code listings are highlighted and have line numbering. Listings that start with a $ symbol represent the command line, lines stating with a > symbol represent command output. New terms are written in *italic* on first usage.

### 1.5 An important notice for Amazon customers

If you bought this book at Amazon, it is currently somewhat more difficult to ensure that you automatically receive all of its updates as they are published. To avoid problems, please send a short email with “Updates Doctrine 2 book” in the subject line to mail@michael-romer.de. In this manner, you can be certain that you will really always have the latest version of the book. As thanks for your efforts you will also additionally receive the PDF and EPUB versions of the book.

## 2 Introduction

### 2.1 Object oriented programming (OOP) & the Domain Model

PHP developers nowadays mostly think and code in an object oriented way. Application functionality is built using classes, objects, methods, inheritance and other techniques of object orientation. In the beginning, OOP has mostly been used for the general technical aspects of application, such as MVC frameworks or logging and mailing libraries. All these components more or less can be used “as is” in all applications, no matter what domain the application is in: e-commerce, portal or community site. For complex systems and also if aspects such as maintainability and extensibility are important, OOP in the domain specific code also is an advantage. Mainly, every application consists of two different types of code: general technical code and domain specific code. General technical code often is re-usable when built as a library or framework, domain specific code often is too custom to be re-used.

Object oriented domain specific code is characterized by the existence of a so-called *domain model*. A domain model mainly means:

*   Classes and objects represent the main concepts of a domain, the so-called *entities* (these elements can also be *value objects* to be precise, but compared to entities, value objects don’t have a persistent identity). In an online shop, the main elements would be “Customer”, “Order”, “Product”, “Cart” and so forth.
*   Domain specific classes and objects may have associations between them. Again, in an online shop, an “Order” usually has at least one “Customer” that it references as well as one or more references to the “Product(s)” ordered.
*   Domain specific functions are implemented as a part of an entity. In an online shop, a “Cart” often has a `calculateTotalPrice()` method to calculate the final price based on the items in cart considering their quantity.
*   Functions that span multiple entities usually are implemented in so-called *services*, simply because they cannot clearly be assigned to one single entity. Again, in an online shop, the “Checkout” service may take care of lowering the inventory, invoicing, updating the order history, etc. The service deals with several different entities at once.
*   Whenever possible, domain specific objects are used instead of generic data containers such as PHP arrays (exceptions prove the rule here).
*   Business logic (such as business rules) is implemented within the domain objects of an application, not in e.g. controllers, whenever possible (controllers are used in MVC based frameworks to handle user input).

The main advantage of the domain model lies in having the domain specific code centrally in defined classes and objects supporting maintenance and changes. The possibility of incidentally breaking a function, when changing or extending code, drops. By isolating domain specific code from general technical code, portability is supported. That’s helpful, e.g. when migrating from one application framework to another.

Besides the advantages mentioned above, the domain model also supports teamwork. Often, when building and launching a new software product, besides programmers also business and marketing folks are involved. A domain model can bridge the mental gap between business and IT by unifying the terminology used. This alone makes a Domain model invaluable.

### 2.2 Demo application

Concrete examples make things easier to understand. Throughout this book, a demo application called “Talking” will help to put theory into practice. Talking is a (simple) web application allowing users to publish content online. The application’s domain model looks like this:

![Demo application "Talking" - Domain Model](images/domain-model-talking.jpeg)

Demo application “Talking” - Domain Model

A `User` can write `Post`s. A **Post** always only has one author and both entities reference each other. A User can act in one or more `Role`s. A `User` references its `Role`s, but from a given `Role`, one cannot access the `User`s in this Role. A `User` references `UserInfo` holding the date of registration and the date of de-registration if available. `UserInfo` references back to a `User`. A `User` references `ContactData` where email and phone number is saved. `ContactData` does not reference back to its `User`. A `User` may reference another `User` as its life partner. The `USER`’s life partner references back if known. A `User` may have an unlimited number of friends. Given a `User`, one can identify its friends, but there is no reference back. The `Post` of a `User` can have an unlimited number of `Tag`s. A `Tag` can be re-used in several `Post`s. There is a bi-directional association between a `Post` and its `Tag`s. A `Post` references its `Category`, however, there is no reference from a `Category` to its `Post`s. A `Category` can have subcategories which it references, as well as a parent `Category`, if given. Categories are user specific. A `User` references its categories, but there is no reference back.

The domain model is designed to use as many different association types as possible, so that we can see most of the features of Doctrine 2 in action in the scope of the demo application. In a real application, the domain model would probably look a bit different. As you can see, not every association between entities is bi-directional. As we will see later in this book, this essentially is a feature of an ORM system like Doctrine 2 living in the object oriented world. In relational databases, there are no uni-directional associations. They are always bi-directional by design.

## 3 A self-made ORM

 
| ![information](images/leanpub_information.png) || 

#### Jump straight into Doctrine 2?

This section describes why Doctrine 2 is such a big help for the application developer. Step by step, we will implement certain ORM features on our own, that Doctrine 2 already ships with. This chapter is not needed to learn Doctrine 2-but it helps understanding why one should learn it. |
| --- | --- |

### 3.1 Loading an Entity

A domain model is a good thing. As long as the application developer acts in his familiar object oriented world, there are no obstacles when designing and implementing a domain model. It gets harder, if it’s about persisting objects of the domain model in relational databases or loading and reconstructing previously stored objects. There is, for instance, the fact that objects are more than just dumb data structures. With their methods, they have behavior as well. Let’s consider the `User` entity definition of the demo application Talking:

```
 1 <?php
 2 namespace Entity;
 3 
 4 class User
 5 {
 6     private $id;
 7     private $firstName;
 8     private $lastName;
 9     private $gender;
10     private $namePrefix;
11 
12     const GENDER_MALE = 0;
13     const GENDER_FEMALE = 1;
14 
15     const GENDER_MALE_DISPLAY_VALUE = "Mr.";
16     const GENDER_FEMALE_DISPLAY_VALUE = "Mrs.";
17 
18     public function assembleDisplayName()
19     {
20         $displayName = '';
21 
22         if ($this->gender == self::GENDER_MALE) {
23             $displayName .= self::GENDER_MALE_DISPLAY_VALUE;
24         } else if ($this->gender == self::GENDER_FEMALE) {
25             $displayName .= self::GENDER_FEMALE_DISPLAY_VALUE;
26         }
27 
28         if ($this->namePrefix) {
29             $displayName .= ' ' . $this->namePrefix;
30         }
31 
32         $displayName .= ' ' . $this->firstName . ' ' . $this->lastName;
33 
34         return $displayName;
35     }
36 
37     public function setFirstName($firstName)
38     {
39         $this->firstName = $firstName;
40     }
41 
42     public function getFirstName()
43     {
44         return $this->firstName;
45     }
46 
47     public function setGender($gender)
48     {
49         $this->gender = $gender;
50     }
51 
52     public function getGender()
53     {
54         return $this->gender;
55     }
56 
57     public function setId($id)
58     {
59         $this->id = $id;
60     }
61 
62     public function getId()
63     {
64         return $this->id;
65     }
66 
67     public function setLastName($lastName)
68     {
69         $this->lastName = $lastName;
70     }
71 
72     public function getLastName()
73     {
74         return $this->lastName;
75     }
76 
77     public function setNamePrefix($namePrefix)
78     {
79         $this->namePrefix = $namePrefix;
80     }
81 
82     public function getNamePrefix()
83     {
84         return $this->namePrefix;
85     }
86 }
```

**Listing 1.1**

Interesting here is method `assembleDisplayName()`. It creates the “display name” for a user based on a user’s data. The display name is used to print a post’s author. The code

```
 1 <?php
 2 include('../entity/User.php');
 3 
 4 $user = new Entity\User();
 5 $user->setFirstName('Max');
 6 $user->setLastName('Mustermann');
 7 $user->setGender(0);
 8 $user->setNamePrefix('Prof. Dr');
 9 
10 echo $user->assembleDisplayName();
```

**Listing 1.2**

results in

```
1 Mr. Prof. Dr. Max Mustermann
```

The method `assembleDisplayName()` therefore defines a specific behavior of a `User` object.

If a user’s master data is retrieved from the database, it must be transformed in a way, that the behavior described above is attached to it. Or in other words: The user’s master data, retrieved from the database, must be transformed into a `User` object, since within the application, we mainly always want to deal with objects of our domain and easily create a user’s display name by simply calling its `assembleDisplayName()` method. Let’s build that into our ORM tool.

First, we set up the database structure:

```
1 CREATE TABLE users(
2 	id int(10) NOT NULL auto_increment, 
3 	first_name varchar(50) NOT NULL,
4 	last_name varchar(50) NOT NULL, 
5 	gender ENUM('0','1') NOT NULL,
6 	name_prefix varchar(50) NOT NULL,
7 	PRIMARY KEY (id)
8 );
```

Then, let’s add dummy data for “Max Mastermann” (the German “John Doe”, by the way):

```
1 INSERT INTO users (first_name, last_name, gender, name_prefix)
2 VALUES('Max', 'Mustermann', '0', 'Prof. Dr.');
```

Now, if we want to reconstruct the `User` object from the database, we can do it like this:

```
 1 <?php
 2 include('../entity/User.php');
 3 
 4 $db = new \PDO('mysql:host=localhost;dbname=app', 'root', '');
 5 $userData = $db->query('SELECT * FROM users WHERE id = 1')->fetch();
 6 
 7 $user = new Entity\User();
 8 $user->setId($userData['id']);
 9 $user->setFirstName($userData['first_name']);
10 $user->setLastName($userData['last_name']);
11 $user->setGender($userData['gender']);
12 $user->setNamePrefix($userData['name_prefix']);
13 
14 echo $user->assembleDisplayName();
```

 
| ![information](images/leanpub_information.png) || 

#### Database credentials in live systems

In a live system, you use strong keywords and don’t work with user “root”, right? The code shown above is just an example … |
| --- | --- |

With these lines of code, we started implementing our own ORM system, that allows reconstructing domain objects by fetching data from a database. Let’s further improve it.

To encapsulate the “data mapping” shown above, we move the code into its own class:

```
 1 <?php
 2 namespace Mapper;
 3 
 4 class User
 5 {
 6 	private $mapping = array(
 7 		'id' => 'id',
 8 		'firstName' => 'first_name',
 9 		'lastName' => 'last_name',
10 		'gender' => 'gender',
11 		'namePrefix' => 'name_prefix'
12 	);
13 
14 	public function populate($data, $user)
15 	{
16 		$mappingsFlipped = array_flip($this->mapping);
17 
18 		foreach($data as $key => $value) {
19 			if(isset($mappingsFlipped[$key])) {
20 				call_user_func_array(
21 					array($user, 'set'. ucfirst($mappingsFlipped[$key])),
22 					array($value)
23 				);
24 			}
25 		}
26 
27 		return $user;
28 	}
29 }
```

It’s not perfect, but it does the job. Now, our invoking code looks like this:

```
 1 <?php
 2 include_once('../entity/User.php');
 3 include_once('../mapper/User.php');
 4 
 5 $db = new \PDO('mysql:host=localhost;dbname=app', 'root', '');
 6 $userData = $db->query('SELECT * FROM users WHERE id = 1')->fetch();
 7 
 8 $user = new Entity\User();
 9 $userMapper = new Mapper\User();
10 $user = $userMapper->populate($userData, $user);
11 
12 echo $user->assembleDisplayName();
```

However, we can make it even easier by moving the SQL statement into its own object, a so-called *repository*:

```
 1 <?php
 2 namespace Repository;
 3 
 4 include_once('../entity/User.php');
 5 include_once('../mapper/User.php');
 6 
 7 use Mapper\User as UserMapper;
 8 use Entity\User as UserEntity;
 9 
10 class User
11 {
12 	private $em;
13 	private $mapper;
14 
15 	public function __construct($em)
16 	{
17 		$this->mapper = new UserMapper;
18 		$this->em = $em;
19 	}
20 
21 	public function findOneById($id)
22 	{
23 		$userData = $this->em
24 			->query('SELECT * FROM users WHERE id = ' . $id)
25 			->fetch();
26     
27 		return $this->mapper->populate($userData, new UserEntity());
28 	}
29 }
```

Lastly, we move the code to connect to the database into a class called `EntityManager` and make the new `User` repository available through it:

```
 1 <?php
 2 
 3 include_once('../repository/User.php');
 4 
 5 use Repository\User as UserRepository;
 6 
 7 class EntityManager
 8 {
 9 	private $host;
10 	private $db;
11 	private $user;
12 	private $pwd;
13 	private $connection;
14 	private $userRepository;
15 
16 	public function __construct($host, $db, $user, $pwd)
17 	{
18 		$this->host = $host;
19 		$this->user = $user;
20 		$this->pwd = $pwd;
21 
22 		$this->connection = new \PDO(
23 			"mysql:host=$host;dbname=$db", 
24 			$user, 
25 			$pwd);
26 
27 		$this->userRepository = null;
28 	}
29 
30 	public function query($stmt)
31 	{
32 		return $this->connection->query($stmt);
33 	}
34 
35 	public function getUserRepository()
36 	{
37 		if (!is_null($this->userRepository)) {
38 			return $this->userRepository;
39 		} else {
40 			$this->userRepository = new UserRepository($this);
41 			return $this->userRepository;
42 		}
43 	}
44 }
```

The Entity Manager now acts as the main entry point-it opens the database connection as well makes database queries available to client code. After the refactoring, the result still remains the same:

```
1 Mr. Prof. Dr. Max Mustermann
```

We wrote a whole bunch of code-and yet can’t do anything more than reading data from a database and making an object out of it. We didn’t even push our own application forward. Looks like building an ORM system is hard work and time-consuming. And we just started. Let’s spend some more time enhancing our ORM, so that later, we even more appreciate Doctrine 2 existing.

### 3.2 Saving an entity

So far, we implemented a really trivial use case: Loading a single object from the database based on an ID given. But what about writing operations? Actually, there are two types of write operations: inserts and updates. Let’s first deal with the insert operation by adding an `extract()` method to the `User` mapper:

```
 1 <?php
 2 namespace Mapper;
 3 
 4 class User
 5 {
 6 	private $mapping = array(
 7 		'id' => 'id',
 8 		'firstName' => 'first_name',
 9 		'lastName' => 'last_name',
10 		'gender' => 'gender',
11 		'namePrefix' => 'name_prefix'
12 	);
13 
14 	public function extract($user)
15 	{
16 		$data = array();
17 
18 		foreach($this->mapping as $keyObject => $keyColumn) {
19 
20         	if ($keyColumn != 'id') {
21             	$data[$keyColumn] = call_user_func(
22                 	array($user, 'get'. ucfirst($keyObject))
23             	);
24         	}
25     	}
26 
27     	return $data;
28 	}
29 
30 	public function populate($data, $user)
31 	{
32 		$mappingsFlipped = array_flip($this->mapping);
33 
34 		foreach($data as $key => $value) {
35 			if(isset($mappingsFlipped[$key])) {
36 				call_user_func_array(
37 					array($user, 'set'. ucfirst($mappingsFlipped[$key])),
38 					array($value)
39 				);
40 			}
41 		}
42 
43 		return $user;
44 	}
45 }
```

This is how we extract the data from the object. The entity manager, extended by a `saveUser()` method, now can insert a new record into the database:

```
 1 <?php
 2 
 3 include_once('../repository/User.php');
 4 include_once('../mapper/User.php');
 5 
 6 use Repository\User as UserRepository;
 7 use Mapper\User as UserMapper;
 8 
 9 class EntityManager
10 {
11 	private $host;
12 	private $db;
13 	private $user;
14 	private $pwd;
15 	private $connection;
16 	private $userRepository;
17 
18 	public function __construct($host, $db, $user, $pwd)
19 	{
20 		$this->host = $host;
21 		$this->user = $user;
22 		$this->pwd = $pwd;
23 		
24 		$this->connection = 
25 			new \PDO("mysql:host=$host;dbname=$db", $user, $pwd);
26 		
27 		$this->userRepository = null;
28 	}
29 
30 	public function query($stmt)
31 	{
32 		return $this->connection->query($stmt);
33 	}
34 
35 	public function saveUser($user)
36 	{
37 		$userMapper = new UserMapper();
38 		$data = $userMapper->extract($user);
39 		$columnsString = implode(", ", array_keys($data));
40 
41 		$valuesString = implode(
42 			"', 
43 			'", 
44 			array_map("mysql_real_escape_string", $data)
45 		);
46 
47 		return $this->query(
48 			"INSERT INTO users ($columnsString) VALUES('$valuesString')"
49 		);
50 	}
51 
52 	public function getUserRepository()
53 	{
54 		if (!is_null($this->userRepository)) {
55         	return $this->userRepository;
56 		} else {
57 			$this->userRepository = new UserRepository($this);
58 			return $this->userRepository;
59 		}
60 	}
61 }
```

Adding a new record now works like this:

```
 1 <?php
 2 include_once('../EntityManager.php');
 3 $em = new EntityManager('localhost', 'app', 'root', '');
 4 $user = $em->getUserRepository()->findOneById(1);
 5 echo $user->assembleDisplayName() . '<br />';
 6 
 7 $newUser = new Entity\User();
 8 $newUser->setFirstName('Ute');
 9 $newUser->setLastName('Musermann');
10 $newUser->setGender(1);
11 $em->saveUser($newUser);
12 
13 echo $newUser->assembleDisplayName();
```

So far, so good! But what if we want to update an existing record? How to identify, if we deal with a new or an existing record? In our case, we might simply check, if the object already has a value given for the `id` field. It’s an “auto_increment” field and MySQL will populate it automatically for any new record. For sure, this is not the most elegant way one may come up with. We might use a so-called *identity map* that brings some more advantages: Re-reading an already loaded database without querying the database again. An identity map mainly is nothing else but an associative array holding references to already loaded entities based on IDs. A good place for an identity map is the entity manager and its `saveUser()` method:

```
 1 <?php
 2 
 3 include_once('../repository/User.php');
 4 include_once('../mapper/User.php');
 5 
 6 use Repository\User as UserRepository;
 7 use Mapper\User as UserMapper;
 8 
 9 class EntityManager
10 {
11 	private $host;
12 	private $db;
13 	private $user;
14 	private $pwd;
15 	private $connection;
16 	private $userRepository;
17 	private $identityMap;
18 
19 	public function __construct($host, $db, $user, $pwd)
20 	{
21 		$this->host = $host;
22 		$this->user = $user;
23 		$this->pwd = $pwd;
24 		
25 		$this->connection = 
26 			new \PDO("mysql:host=$host;dbname=$db", $user, $pwd);
27 		
28 		$this->userRepository = null;
29 		$this->identityMap = array('users' => array());
30 	}
31 
32 	public function query($stmt)
33 	{
34 		return $this->connection->query($stmt);
35 	}
36 
37 	public function saveUser($user)
38 	{
39 		$userMapper = new UserMapper();
40 		$data = $userMapper->extract($user);
41 
42 		$userId = call_user_func(
43 			array($user, 'get'. ucfirst($userMapper->getIdColumn()))
44 		);
45 
46 		if (array_key_exists($userId, $this->identityMap['users'])) {
47         	$setString = '';
48 
49 			foreach ($data as $key => $value) {
50 				$setString .= $key."='$value',";
51 			}
52 
53 			return $this->query(
54 				"UPDATE users SET " . substr($setString, 0, -1) .
55 				" WHERE " . $userMapper->getIdColumn() . "=" . $userId
56 			);
57 
58 		} else {
59 			$columnsString = implode(", ", array_keys($data));
60 			$valuesString = implode(
61 				"', 
62 				'", 
63 				array_map("mysql_real_escape_string", $data)
64 			);
65 
66 			return $this->query(
67 				"INSERT INTO users ($columnsString) VALUES('$valuesString')"
68 			);
69 		}
70 	}
71 
72 	public function getUserRepository()
73 	{
74 		if (!is_null($this->userRepository)) {
75 			return $this->userRepository;
76 		} else {
77 			$this->userRepository = new UserRepository($this);
78 			return $this->userRepository;
79 		}
80 	}
81 
82 	public function registerUserEntity($id, $user)
83 	{
84 		$this->identityMap['users'][$id] = $user;
85 		return $user;
86 	}
87 }
```

As one can see, we added a method `getIdColumn()` as well. It returns “id”. Now the following code works nicely:

```
1 <?php
2 include_once('../EntityManager.php');
3 $em = new EntityManager('localhost', 'app', 'root', '');
4 $user = $em->getUserRepository()->findOneById(1);
5 echo $user->assembleDisplayName() . '<br />';
6 
7 $user->setFirstname('Moritz');
8 $em->saveUser($user); 
```

The entity is updated in the database and no additional record is added.

### 3.3 Associations

Now we finally want to list all posts from a specific `User`. Therefore, we want to simply iterate over a `Post`s collection of a `User` and print each `Post`’s title:

```
 1 <?php
 2 include_once('../EntityManager.php');
 3 $em = new EntityManager('localhost', 'app', 'root', '');
 4 $user = $em->getUserRepository()->findOneById(1);
 5 ?>
 6 <h1><?echo $user->assembleDisplayName(); ?></h1>
 7 <ul>
 8 <?php foreach($user->getPosts() as $post) { ?>
 9 <li><?php echo $post->getTitle(); ?></li>
10 <?php } ?>
11 </ul>
```

What do we have to do to make this happen?

First, we create the data structure:

```
1 CREATE TABLE posts(
2 	id int(10) NOT NULL auto_increment, 
3 	user_id int(10) NOT NULL,
4 	title varchar(255) NOT NULL, 
5 	content text NOT NULL,
6 	PRIMARY KEY (id)
7 );
```

We add a test `User` and some test `Post`s, so that we can actually test the implementation. Next, we need to extend a whole bunch of classes. The `User` entity gets a `getPosts()` method, which loads the `User`’s `Post`s on first invocation via the corresponding repository:

```
 1 <?php
 2 namespace Entity;
 3 
 4 class User
 5 {
 6 	// [..]
 7 
 8     private $postRepository;
 9 
10 	public function getPosts()
11 	{
12     	if (is_null($this->posts)) {
13         	$this->posts = $this->postRepository->findByUser($this);
14     	}
15    
16     	return $this->posts;
17 	}
18 
19 	// [..]
20 }
```

This will only work if the `User` entity has access to the `Post` repository. To make it available, the `User` repository method `findOneById()` needs to be extended:

```
 1 <?php
 2 namespace Repository;
 3 
 4 include_once('../entity/User.php');
 5 include_once('../mapper/User.php');
 6 
 7 use Mapper\User as UserMapper;
 8 use Entity\User as UserEntity;
 9 
10 class User
11 {
12 	private $em;
13 	private $mapper;
14 
15 	public function __construct($em)
16 	{
17 		$this->mapper = new UserMapper;
18 		$this->em = $em;
19 	}
20 
21 	public function findOneById($id)
22 	{
23 		$userData = $this->em
24 			->query('SELECT * FROM users WHERE id = ' . $id)
25 			->fetchAll();
26 
27 		$newUser = new UserEntity();
28 		$newUser->setPostRepository($this->em->getPostRepository());
29 
30 		return $this->em->registerUserEntity(
31 			$id,
32 			$this->mapper->populate($userData, $newUser)
33 		);
34 	}
35 }
```

The entity manager needs to be extended by the method `getPostRepository()` as well:

```
 1 <?php
 2 
 3 // [..]
 4 
 5 class EntityManager
 6 {
 7 	// [..]
 8     
 9 	private $postRepository;
10 	
11 	public function getPostRepository()
12 	{
13 		if (!is_null($this->postRepository)) {
14 			return $this->postRepository;
15 		} else {
16 			$this->postRepository = new PostRepository($this);
17 			return $this->postRepository;
18 		}
19 	}
20 }
```

Now, the Post entity and the `Post` mapper must be implemented:

```
 1 <?php
 2 namespace Entity;
 3 
 4 class Post
 5 {
 6 	private $id;
 7 	private $title;
 8 	private $content;
 9 
10 	public function setContent($content)
11 	{
12 		$this->content = $content;
13 	}
14 
15 	public function getContent()
16 	{
17 		return $this->content;
18 	}
19 
20 	public function setId($id)
21 	{
22 		$this->id = $id;
23 	}
24 
25 	public function getId()
26 	{
27 		return $this->id;
28 	}
29 
30 	public function setTitle($title)
31 	{
32 		$this->title = $title;
33 	}
34 
35 	public function getTitle()
36 	{
37 		return $this->title;
38 	}
39 }
```

And here the mapper:

```
 1 <?php
 2 namespace Mapper;
 3 
 4 class Post
 5 {
 6 	private $mapping = array(
 7 		'id' => 'id',
 8 		'title' => 'title',
 9 		'content' => 'content',
10 	);
11 
12 	public function getIdColumn()
13 	{
14 		return 'id';
15 	}
16 
17 	public function extract($user)
18 	{
19 		$data = array();
20 
21 		foreach ($this->mapping as $keyObject => $keyColumn) {
22 			if ($keyColumn != $this->getIdColumn()) {
23 				$data[$keyColumn] = call_user_func(
24 					array($user, 'get'. ucfirst($keyObject))
25 				);
26 			}
27 		}
28 
29 		return $data;
30 	}
31 
32 	public function populate($data, $user)
33 	{
34 		$mappingsFlipped = array_flip($this->mapping);
35 
36 		foreach ($data as $key => $value) {
37 			if (isset($mappingsFlipped[$key])) {
38 				call_user_func_array(
39 					array($user, 'set'. ucfirst($mappingsFlipped[$key])),
40 					array($value)
41 				);
42 			}
43 		}
44 
45 		return $user;
46 	}
47 }
```

And last but not least, the `Post` repository:

```
 1 <?php
 2 namespace Repository;
 3 
 4 include_once('../entity/Post.php');
 5 include_once('../mapper/Post.php');
 6 
 7 use Mapper\Post as PostMapper;
 8 use Entity\Post as PostEntity;
 9 
10 class Post
11 {
12 	private $em;
13 	private $mapper;
14 
15 	public function __construct($em)
16 	{
17 		$this->mapper = new PostMapper;
18 		$this->em = $em;
19 	}
20 
21 	public function findByUser($user)
22 	{
23 		$postsData = $this->em
24 			->query('SELECT * FROM posts WHERE user_id = ' . $user->getId())
25 			->fetchAll();
26 
27 		$posts = array();
28 
29 		foreach($postsData as $postData) {
30 			$newPost = new PostEntity();
31 			$posts[] = $this->mapper->populate($postData, $newPost);
32 		}
33 
34 		return $posts;
35 	}
36 }
```

That’s it! Up to this point, the application’s files and folder structure looks like this:

```
 1 EntityManager.php
 2 entity/
 3 	Post.php
 4 	User.php
 5 mapper/
 6 	Post.php
 7 	User.php
 8 repository/
 9 	Post.php
10 	User.php
11 public/
12 	index.php
```

### 3.4 Next steps

Great! We built our own little ORM tool. However, our code already doesn’t look that good anymore. The fact that technical code is mixed-up with domain specific code is an issue. Our solutions to the problems faced are more or less only valid to our concrete use case. Also, it smells like “copy & paste” in here! In fact, some refactoring already needs to be done.

And what about composite primary keys? Adding and deleting associations? Many-to-many associations? Inheritance, performance, caching and entities, mappers and repositories for the tons of yet missing core elements of the application? Also, what happens if the data structures change? This would mean refactoring of multiple classes already! Looks like it is time for Doctrine 2 to enter the stage.

## 4 Hello, Doctrine 2!

 
| ![information](images/leanpub_information.png) || 

#### Don’t worry!

We run through Doctrine 2 quickly in this chapter but we will look into each single aspect of it in depth later in the book again. |
| --- | --- |

### 4.1 Installation

The easiest way to install Doctrine 2 is by using “Composer” which can be downloaded from its [Website](http://getcomposer.org/download/). The phar file must be stored in the root directory of the application. Then, a file `composer.json` needs to be created with the following contents (one may need to adjust the version number given):

```
1 {
2 	"require": {
3 		"doctrine/orm": "2.3.1"
4 	}
5 }
```

Executing the command

```
1 $ php composer.phar install
```

in the root directory of the application downloads Doctrine 2 to the subfolder `vendor` and makes it available to the application by configuring autoloading for its classes. One then does only need to add

```
1 <?php
2 // [..]
3 if (file_exists('vendor/autoload.php')) {
4     $loader = include 'vendor/autoload.php';
5 }
```

to the `index.php` file. Once down, all Doctrine 2 classes are loaded automatically on demand. Nice!

### 4.2 A first Entity

Based on the first section of this book, in which we developed our own little ORM system, we now can radically simplify the code needed by adding Doctrine 2 annotations to the `User` entity:

```
  1 <?php
  2 namespace Entity;
  3 
  4 /**
  5  * @Entity
  6  * @Table(name="users")
  7  */
  8 class User
  9 {
 10 	/**
 11 	* @Id @Column(type="integer")
 12 	* @GeneratedValue
 13 	*/
 14 	private $id;
 15 
 16 	/** @Column(type="string", name="first_name", nullable=true) */
 17 	private $firstName;
 18 
 19 	/** @Column(type="string", name="last_name", nullable=true) */
 20 	private $lastName;
 21 
 22 	/** @Column(type="string", nullable=true) */
 23 	private $gender;
 24 
 25 	/** @Column(type="string", name="name_prefix", nullable=true) */
 26 	private $namePrefix;
 27 
 28 	const GENDER_MALE = 0;
 29 	const GENDER_FEMALE = 1;
 30 
 31 	const GENDER_MALE_DISPLAY_VALUE = "Mr.";
 32 	const GENDER_FEMALE_DISPLAY_VALUE = "Mrs.";
 33 
 34 	public function assembleDisplayName()
 35 	{
 36 		$displayName = '';
 37 
 38 		if ($this->gender == self::GENDER_MALE) {
 39 			$displayName .= self::GENDER_MALE_DISPLAY_VALUE;
 40 		} elseif ($this->gender == self::GENDER_FEMALE) {
 41 			$displayName .= self::GENDER_FEMALE_DISPLAY_VALUE;
 42 		}
 43 
 44 		if ($this->namePrefix) {
 45 			$displayName .= ' ' . $this->namePrefix;
 46 		}
 47 
 48 		$displayName .= ' ' . $this->firstName . ' ' . $this->lastName;
 49 
 50 		return $displayName;
 51 	}
 52 
 53 	public function setFirstName($firstName)
 54 	{
 55 		$this->firstName = $firstName;
 56 	}
 57 
 58 	public function getFirstName()
 59 	{
 60 		return $this->firstName;
 61 	}
 62 
 63 	public function setGender($gender)
 64 	{
 65 		$this->gender = $gender;
 66 	}
 67 
 68 	public function getGender()
 69 	{
 70 		return $this->gender;
 71 	}
 72 
 73 	public function setId($id)
 74 	{
 75 		$this->id = $id;
 76 	}
 77 
 78 	public function getId()
 79 	{
 80 		return $this->id;
 81 	}
 82 
 83 	public function setLastName($lastName)
 84 	{
 85 		$this->lastName = $lastName;
 86 	}
 87 
 88 	public function getLastName()
 89 	{
 90 		return $this->lastName;
 91 	}
 92 
 93 	public function setNamePrefix($namePrefix)
 94 	{
 95 		$this->namePrefix = $namePrefix;
 96 	}
 97 
 98 	public function getNamePrefix()
 99 	{
100 		return $this->namePrefix;
101 	}
102 }
```

The code in `index.php` now can be changed to the following lines of code to read and modify entities using Doctrine 2:

```
 1 <?php
 2 include '../entity/User.php';
 3 include '../vendor/autoload.php';
 4 
 5 use Doctrine\ORM\Tools\Setup;
 6 use Doctrine\ORM\EntityManager;
 7 
 8 $paths = array(__DIR__ . "/../entity/");
 9 $isDevMode = true;
10 
11 $dbParams = array(
12 	'driver'   => 'pdo_mysql',
13 	'user'     => 'root',
14 	'password' => '',
15 	'dbname'   => 'app',
16 );
17 
18 $config = Setup::createAnnotationMetadataConfiguration($paths, $isDevMode);
19 $em = EntityManager::create($dbParams, $config);
20 $user = $em->getRepository('Entity\User')->findOneById(1);
21 echo $user->assembleDisplayName() . '<br />';
22 $user->setFirstname('Moritz');
23 $em->persist($user);
24 $em->flush();
```

That’s it! Easy!

### 4.3 A first Association

Dealing with the association is easy as well. The `User` entity has to be changed to:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5  * @Entity
 6  * @Table(name="users")
 7  */
 8 class User
 9 {
10 	// [..]
11 
12 	/**
13 	* @OneToMany(targetEntity="Entity\Post", mappedBy="user")
14 	*/
15 	private $posts;
16 
17 	// [..]
18 	
19 	public function __construct()
20 	{
21 		$this->posts = new \Doctrine\Common\Collections\ArrayCollection();
22 	}
23 	
24 	// [..]
25 }
```

Now some more annotations to the `Post` entity:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="posts")
 7 */
 8 class Post
 9 {
10 	/**
11 	* @Id @Column(type="integer")
12 	* @GeneratedValue
13 	*/
14 	private $id;
15 
16 	/**
17 	* @ManyToOne(targetEntity="Entity\User", inversedBy="posts")
18 	* @JoinColumn(name="user_id", referencedColumnName="id")
19 	*/
20 	private $user;
21 
22 	/** @Column(type="string") */
23 	private $title;
24 
25 	/** @Column(type="string") */
26 	private $content;
27 
28 	public function setUserId($user_id)
29 	{
30 		$this->user_id = $user_id;
31 	}
32 
33 	public function getUserId()
34 	{
35 		return $this->user_id;
36 	}
37 
38 	public function setContent($content)
39 	{
40 		$this->content = $content;
41 	}
42 
43 	public function getContent()
44 	{
45 		return $this->content;
46 	}
47 
48 	public function setId($id)
49 	{
50 		$this->id = $id;
51 	}
52 
53 	public function getId()
54 	{
55 		return $this->id;
56 	}
57 
58 	public function setTitle($title)
59 	{
60 		$this->title = $title;
61 	}
62 
63 	public function getTitle()
64 	{
65 		return $this->title;
66 	}
67 }
```

Once the User is loaded, one may iterate over the user’s posts as always:

```
 1 <?php
 2 // [..]
 3 $user = $em->getRepository('Entity\User')->findOneById(1);
 4 ?>
 5 <h1><?echo $user->assembleDisplayName(); ?></h1>
 6 <ul>
 7 	<?php foreach($user->getPosts() as $post) {?>
 8 		<li><?php echo $post->getTitle(); ?></li>
 9 	<?php } ?>
10 </ul>
```

In fact, now with Doctrine 2 included, we don’t need most of the code anymore which was needed to implement the exact same functionality by hand:

```
1 entity/
2 	Post.php
3 	User.php
4 public/
5 	index.php
```

It couldn’t be much easier - thank you, Doctrine 2! Before we add more features to our demo app, we will now look at some basics concepts of Doctrine 2.

### 4.4 Core concepts at a glance

Before we deep-dive into the details of Doctrine 2, let’s step back and look at its core concepts.

We already defined an entity as an object with identity that is managed by Doctrine 2 and persisted in a database. Entities are the domain objects of an application. Saving entities and retrieving them from the database is essential to an application. The term “entity” is used with two different meanings throughout this book: On one hand, its used for single, persistent objects, on the other hand, its used for PHP classes that act as a template for persistent objects. A persistent object with Doctrine 2, an entity, always is in a specific state. This state can be “NEW”, “MANAGED”, “DETACHED” or “REMOVED”. We will learn about this later in the book.

The entity manager is Doctrine’s core object. As an application developer, one does interact a lot with the entity manager. The entity manager is responsible for persisting new entities, but also takes care of updating and deleting them. Repositories are retrieved via the entity manager.

Simply speaking, a repository is a container for all entities of a specific type. It allows to look-up entities via so-called *finder methods* or *finders*. Some finders are available by default, others may be added manually if needed.

*Doctrine’s database access layer (DBAL)* is the foundation for the Doctrine 2 ORM library. It’s a stand-alone component that might be used even without using Doctrine’s ORM capabilities. Technically, DBAL is a wrapper for PHP’s PDO extension that makes dealing with databases even easier compared to PDO alone. However, again, Doctrine 2 ORM makes dealing with databases even more easy compared to DBAL alone.

## 5 Defining entities

We already learned how easy it is to map member variables to fields in a database table. Let’s take a look at how this works exactly.

### 5.1 Mapping formats

In general, mappings can be defined using annotation within the entities itself, or with external XML or YAML files. In terms of performance, there is no difference between the different ways for implementing the mapping when using a cache. Therefore, using annotations often is preferred, simply because it make coding easier-all the persistence metadata is located in the same file. In the following examples, annotations are used exclusively.

### 5.2 Mapping objects to tables

First of all, a class that acts as a template for persistent objects needs to get the `Entity` annotation:

```
1 <?php
2 /**
3 * @Entity
4 */
5 class User
6 {
7 	// [..]
8 }
```

Simply adding `@Entity` without additional configuration means that Doctrine 2 looks for a database table named `user` in this case. If the table has another name, this can be configured like this:

```
1 <?php
2 /**
3 * @Entity
4 * @Table(name="users")
5 */
6 class User
7 {
8 	// [..]
9 }
```

The optional attribute `indexes` of the `@Table` annotation can be used to create indexes automatically using Doctrine’s schema tool that we will discuss later in the book. For now, one should remember that this attribute has no meaning during runtime. Some persistence metadata is important only in conjunction with “offline” tools like the schema tool, while other metadata is evaluated during runtime. An index definition to the users table goes like this:

```
 1 <?php
 2 /**
 3 * @Entity
 4 * @Table(name="users",
 5 *	indexes={@Index(name="search_idx", columns={"name", "email"})}
 6 * )
 7 */
 8 class User
 9 {
10 	// [..]
11 }
```

The `indexes` attribute of annotation `@Table` itself has an annotation with attributes as its value. The annotation `@Index` needs the attribute `name` (name of the index) and the list of columns to be considered. Multiple values may be given using curly braces.

The same applies to another optional attribute called `uniqueConstraints` which defines special unique values indexes:

```
 1 <?php
 2 /**
 3 * @Entity
 4 * @Table(name="users",
 5 * 	uniqueConstraints={@UniqueConstraint(name="user_unique",
 6 * 		columns={"username"})}, 
 7 *	indexes={@Index(name="user_idx", columns={"email"})}
 8 * )
 9 */
10 class User 
11 {
12 	// [..] 
13 } 
```

### 5.3 Mapping scalar member variables to fields

Mapping scalar-valued member variables (e.g. numbers or strings) to a database table is super simple:

```
1 <?php
2 
3 // [..]
4 
5 /** @Column(type="string") */
6 private $lastName;
```

First, it’s important that all member variables mapped to database fields are declared as `private` or `protected`. Doctrine 2 often applies a technique called “lazy loading” which means that data is loaded just in the moment its needed, but not earlier. To make this happen, Doctrine 2 implements so-called *proxy objects* which rely on the entities’ getter methods. Therefore, one will want to make sure they are set-up.

The main annotation here is `@Column`. Its attribute `type` is the only mandatory attribute and is important to make persistence work correctly. If a wrong type is defined, one may lose information on saving to or while reading from the database. In addition, there is a bunch of other optional attributes like `name`, which allows to configure the table column name. It defaults to the name of the member variable. The attribute `length` only is needed for “strings” and it defines the max length of a string value. It defaults to 255 if not defined differently. If one encounters truncated values in the database, a wrong `length` configuration often is the root cause.

The attributes `precision` and `scale` are only valid for values of type “decimal”, while `unique` ensures uniqueness and `nullable` tells Doctrine 2, if value `NULL` is allowed (`true`) or not (`false`):

```
1 <?php
2 
3 // [..]
4 
5 /**
6 * @Column(type="string", 
7 * 	name="last_name", length=32, unique=true, nullable=false)
8 */
9 protected $lastName;
```

#### 5.3.1 Data types

Doctrine 2 ships with a set of data types. They map the PHP data types to the SQL data types. All Doctrine 2 data types are compatible to the most common database systems:

*   string: Type that maps an SQL VARCHAR to a PHP string.
*   integer: Type that maps an SQL INT to a PHP integer.
*   smallint: Type that maps a database SMALLINT to a PHP integer.
*   bigint: Type that maps a database BIGINT to a PHP string.
*   boolean: Type that maps an SQL boolean to a PHP boolean.
*   decimal: Type that maps an SQL DECIMAL to a PHP double.
*   date: Type that maps an SQL DATETIME to a PHP DateTime object.
*   time: Type that maps an SQL TIME to a PHP DateTime object.
*   datetime: Type that maps an SQL DATETIME/TIMESTAMP to a PHP DateTime object.
*   text: Type that maps an SQL CLOB to a PHP string.
*   object: Type that maps a SQL CLOB to a PHP object using serialize() and unserialize()
*   array: Type that maps a SQL CLOB to a PHP object using serialize() and unserialize()
*   float: Type that maps a SQL Float (Double Precision) to a PHP double. IMPORTANT: Works only with locale settings that use decimal points as separator.

 
| ![information](images/leanpub_information.png) || 

#### Custom data types

If needed, one may define custom data types, mappings between PHP data types and SQL data types. The [official documentation covers this topic in depth.](http://docs.doctrine-project.org/en/latest/reference/basic-mapping.html#custom-mapping-types) |
| --- | --- |

#### 5.3.2 Entity identifier

An entity class must define a unique identifier. The `@Id` annotation is used for this:

```
1 <?php
2 
3 // [..]
4 
5 /**
6 * @Id @Column(type="integer")
7 */
8 private $id;
```

If the `@GeneratedValue` annotation is used as well, the unique identifier doesn’t need to be given by the application developer but is assigned automatically be the database system. The way this value is generated depends on the “strategy” defined. By default, Doctrine 2 identifies the best approach on its own. When using MySQL for instance, Doctrine 2 uses the `auto_increment` function. There are additional strategies that can be used, however, mainly they don’t work cross-platform and therefore should be avoided.

By the way: The `@Id` annotation can be used with multiple member variables to define composite keys. Clearly, the `@GeneratedValue` annotation can then not be used anymore. In this case, the application developer needs to take care of assigning unique keys.

### 5.4 Inheritance

Doctrine 2 supports persistence of hereditary structures with three different strategies:

*   Single Table Inheritance
*   Class Table Inheritance
*   Mapped Superclass

#### 5.4.1 Single Table Inheritance

The *single table inheritance* strategy uses a single database table with a so-called “discriminator column” to differentiate between the different types. All classes of a hierarchy go into the same table. Let’s say our demo application differentiates between different types of posts. The supported types are:

*   `Post`: A simple, text based post.
*   `ImagePost`: A post with text and image.
*   `VideoPost`: A post with text and video.

Both, `ImagePost` and `VideoPost`, extend `Post` and add an image or video URL. To set up this hierarchy, the topmost `Post` class holds the configuration needed as well as all member variables and associations that are shared between the three types:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity(repositoryClass="Repository\Post")
 6 * @Table(name="posts")
 7 * @InheritanceType("SINGLE_TABLE")
 8 * @DiscriminatorColumn(name="discr", type="string")
 9 * @DiscriminatorMap({"text"="Post","video"="VideoPost","image"= "ImagePost"})
10 */
11 class Post
12 {
13 	// member variables and associations shared between all types
14 }
```

Since the `Post` itself can be an entity, it has the typical entity-related annotations. In addition, via the `@InheritanceType` annotation, it configures single table inheritance. The `@DiscriminatorColumn` annotation is used to label the column which indicates the type persisted. Lastly, via the `@DiscriminatorMap`, the values are defined which can be present in the discriminator column. In our case, Doctrine 2 writes “text” into the discriminator column, if the entity is a `Post`. If the entity is a `VideoPost`, Doctrine 2 writes “video” and if the entity is a `ImagePost` the value used is “image”.

The `ImagePost` itself is straight-forward:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 */
 7 class ImagePost extends Post
 8 {
 9 	/** @Column(type="string") */
10 	protected $imageUrl;
11 
12 	/**
13 	* @param mixed $imageUrl
14 	*/
15 	public function setImageUrl($imageUrl)
16 	{
17 		$this->imageUrl = $imageUrl;
18 	}
19 
20 	/**
21 	* @return mixed
22 	*/
23 	public function getImageUrl()
24 	{
25 		return $this->imageUrl;
26 	}
27 }
```

The same is true for the `VideoPost`:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 */
 7 class VideoPost extends Post
 8 {
 9 	/** @Column(type="string") */
10 	protected $videoUrl;
11 
12 	/**
13 	* @param mixed $videoUrl
14 	*/
15 	public function setVideoUrl($videoUrl)
16 	{
17 		$this->videoUrl = $videoUrl;
18 	}
19 
20 	/**
21 	* @return mixed
22 	*/
23 	public function getVideoUrl()
24 	{
25 		return $this->videoUrl;
26 	}
27 }
```

The data structure used by Doctrine 2 looks like this:

| Col || Type || Length || NULL? || KEY || Extras |
| --- | --- | --- | --- | --- | --- |
| id || INT || 11 ||   || PRI || auto\_increment |
| --- | --- | --- | --- | --- | --- |
| user\_id || INT || 11 || YES || MUL ||   |
| category\_id || INT || 11 || YES || MUL ||   |
| title || VARCHAR || 255 ||   ||   ||   |
| content || LONGTEXT ||   ||   ||   ||   |
| discr || VARCHAR || 255 ||   ||   ||   |
| videoUrl || VARCHAR || 255 || YES ||   ||   |
| imageUrl || VARCHAR || 255 || YES ||   ||   |

Now all three types of entities can easily be persisted. The downside of this approach is that-depending on how complex the hierarchy is and how different the types involved are-the table grows and grows with many fields never used by certain types. In our case, the `videoUrl` won’t ever be used by entities of type `ImagePost`. The `imageUrl` won’t be used by `VideoPost` entities and for `Post` entities even both fields will remain blank.

The upside is-due to its nature-that this strategy allows for very efficient queueing across all types in the hierarchy without any joins.

#### 5.4.2 Class Table Inheritance

While single table inheritance uses only one table for all types, *class table inheritance* is a different approach where each class in the hierarchy is mapped to several tables. While this gives the best flexibility for sure, this also means that reconstructing entities will require joins in the database. Since joins are expensive operations, usually, the performance with class table inheritance is not as good as with single table inheritance.

The main difference in configuration is in `Post`:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity(repositoryClass="Repository\Post")
 6 * @Table(name="posts")
 7 * @InheritanceType("JOINED")
 8 * @DiscriminatorColumn(name="discr", type="string")
 9 * @DiscriminatorMap({"text"="Post","video"="VideoPost","image"= "ImagePost"})
10 */
11 class Post
12 {
13 	// member variables and associations shared between all types
14 }
```

Instead of inheritance type “SINGLE\_TABLE”, now “JOINED” is used. This tells Doctrine 2 to apply the class table inheritance strategy. Since tables will be used for each type, configuring the tables names may be useful for subclasses:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="posts_image")
 7 */
 8 class ImagePost extends Post
 9 {
10 	/** @Column(type="string") */
11 	protected $imageUrl;
12 
13 	/**
14 	* @param mixed $imageUrl
15 	*/
16 	public function setImageUrl($imageUrl)
17 	{
18 		$this->imageUrl = $imageUrl;
19 	}
20 
21 	/**
22 	* @return mixed
23 	*/
24 	public function getImageUrl()
25 	{
26 		return $this->imageUrl;
27 	}
28 }
```

The table name `posts_image` is handy for `ImagesPost` entities. We add the same style of configuration to `VideoPost` entities as well:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="posts_video")	
 7 */
 8 class VideoPost extends Post
 9 {
10 	/** @Column(type="string") */
11 	protected $videoUrl;
12 
13 	/**
14 	* @param mixed $videoUrl
15 	*/
16 	public function setVideoUrl($videoUrl)
17 	{
18 		$this->videoUrl = $videoUrl;
19 	}
20 
21 	/**
22 	* @return mixed
23 	*/
24 	public function getVideoUrl()
25 	{
26 		return $this->videoUrl;
27 	}
28 }
```

When letting Doctrine 2 create the database schema, we will end up with three tables for this hierarchy, while the `posts` table holds the main information:

| Col || Type || Length || NULL? || KEY || Extras |
| --- | --- | --- | --- | --- | --- |
| id || INT || 11 ||   || PRI || auto\_increment |
| --- | --- | --- | --- | --- | --- |
| user\_id || INT || 11 || YES || MUL ||   |
| category\_id || INT || 11 || YES || MUL ||   |
| title || VARCHAR || 255 ||   ||   ||   |
| content || LONGTEXT ||   ||   ||   ||   |
| discr || VARCHAR || 255 ||   ||   ||   |

The `posts_video` table only holds the specifics of this type:

| Col || Type || Length || NULL? || KEY || Extras |
| --- | --- | --- | --- | --- | --- |
| id || INT || 11 ||   || PRI ||   |
| --- | --- | --- | --- | --- | --- |
| videoUrl || VARCHAR || 255 || YES ||   ||   |

The same is true for `posts_image`:

| Col || Type || Length || NULL? || KEY || Extras |
| --- | --- | --- | --- | --- | --- |
| id || INT || 11 ||   || PRI ||   |
| --- | --- | --- | --- | --- | --- |
| imageUrl || VARCHAR || 255 || YES ||   ||   |

By evaluating the foreign key reference, entities of type `ImagePost` and `VideoPost` can be re-constructed by table joins.

#### 5.4.3 Mapped Superclass

Lastly, a *mapped superclass* strategy can be used. The main difference to the other two strategies we already discussed, is that the superclass itself cannot be an entity. Taken the example above, this means that class `Post` cannot be an entity itself. It simply inherits member variables and associations to its subclasses.

To configure the mapped superclass strategy means adding the `@MappedSuperclass` annotation to the `Post` class:

```
1 <?php
2 namespace Entity;
3 
4 /** @MappedSuperclass */
5 class Post
6 {
7 	// member variables and associations shared between all types
8 }
```

Both subclasses, `ImagePost` and `VideoPost` do not need to be changed. However, with the Mapped Superclass strategy applied, we cannot persist objects of type `Post` anymore, which mainly consist of text. We could fix this by adding another new type called `TextPost`:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="posts_text")	
 7 */
 8 class TextPost extends Post
 9 {
10 	/**
11 	* @Id @Column(type="integer")
12 	* @GeneratedValue
13 	*/
14 	protected $id;
15 
16 } 
```

Now we have three concrete entity types and one superclass not being an entity. This results in three tables in the database: `posts_text`, `posts_images` and `posts_video`.

As shown above, it’s important that each entity has its ID column specified, while the mapped superclass does not. It only inherits member variables and associations, but not the ID column definition.

When inheriting attributes or associations like shown above, one may want to overwrite certain definitions.

Let assume we don’t want to talk about `content` in a `VideoPost`, but call it `closed_caption`. This requires the following configuration:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="posts_video")
 7 * @AttributeOverrides({
 8 *     @AttributeOverride(name="content",
 9 *         column=@Column(
10 *             name = "closed_caption",
11 *             type = "text"
12 *         )
13 *     )
14 * })
15 */
16 class VideoPost extends Post
17 {
18 	// [..]
19 }
```

While Doctrine 2 requires member variables being either `private` or `protected`, it’s important to remember that member variables need to be `protected` here. Otherwise they won’t be available in the subclass. When overwriting property `content` with `closed_caption` like shown above, this leads to a `closed_caption` column in the database for this type of entity.

Also, entities of type `VideoPost` aren’t organized in categories called channels. We can overwrite the association like shown below:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="posts_video")
 7 * @AssociationOverrides({
 8 *     @AssociationOverride(name="category",
 9 *         joinColumns=@JoinColumn(
10 *              name="channel_id", referencedColumnName="id"
11 *         )
12 *     )
13 * })
14 */
15 class VideoPost extends Post
16 {
17 	// [..]
18 }
```

## 6 References between Entities

Entities usually are part of a bigger, interconnected object graph. They have references to other entities. A `User` holds references to its `Post`s, while a `Post` references a `Category` which reference back to the `User` who set the `Category` up and so forth. As we will see in the following, there are a lot of different ways to establish connections between entities. Connections are characterized by the number of items they connect and the association’s direction. Let’s take a look!

 
| ![information](images/leanpub_information.png) || 

#### Domain model of the demo app Talking

The following code samples are related to the domain model of the demo app introduced earlier in the book. The drawing of the domain model might be helpful as a reference throughout this chapter. |
| --- | --- |

### 6.1 One to one relationship, unidirectional

In contrast to foreign key relationships in a database, joining two tables in both directions always, this is not true for objects. Therefore, Doctrine 2 differentiates between unidirectional and bidirectional associations between objects. Unidirectional means that one objects points to the other, but the latter does not have a pointer back.

To set up this type of a relationship between two entities, one simply needs to pick a member variable acting as the pointer:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="users")
 7 */
 8 class User
 9 {
10 	// [..]
11 
12 	/**
13 	* @OneToOne(targetEntity="Entity\ContactData")
14 	*/
15 	private $contactData;
16 	
17 	// [..]
18 }
```

The `@OneToOne` annotation defines the type of the relationship-a one to one relationship. The `targetEntity` attribute defines the entity class the pointer references to. The class given with the `targetEntity` attribute needs to be fully qualified including a namespace if applicable. In any case, one must not add a leading backslash.

It’s now already possible to reach a referenced entity (`ContactData`) through a loaded `User`, if a getter method has been added as well beforehand:

```
1 <?php
2 var_dump($user->getContactData());
```

However, the simple persistence configuration shown above only works because `ContactData` has a member variable called `id`:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="contact_data")
 7 */
 8 class ContactData
 9 {
10 	/**
11 	* @Id @Column(type="integer")
12 	* @GeneratedValue
13 	*/
14 	private $id;
15 	
16 	// [..]
17 }
```

If the member variable has a different name, like `contactDataId` or something similar, one needs to tell Doctrine 2 about it:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="users")
 7 */
 8 class User
 9 {
10 	// [..]
11 
12 	/**
13 	* @OneToOne(targetEntity="Entity\ContactData")
14 	* @JoinColumn(name="id", referencedColumnName="contactDataId")
15 	*/
16 	private $contactData;
17 	
18 	// [..]
19 }
```

Later in this book, we will learn more about the details of the `@JoinColumn` annotation.

Loading a `User` and its `ContactData`-like shown above-only works, if the data structure in the database has also been set up beforehand, in addition to the PHP class and the persistence configuration. If not, all this won’t work and errors are reported by Doctrine 2. Based on the situation, one of the following will be true:

*   We have an existing data structure given in the database and we adapt the persistence configuration to it.
*   We don’t have an existing data structure given and the persistence configuration has no external restrictions. In this case, the Doctrine 2 *schema tool* can even create the data structure in the database simply based on the persistence configuration. More about how to auto-create a data structure in a database can be found in chapter “Doctrine 2 on the command line” later in this book.

In any case, its important that the data structure and the Doctrine 2 persistence mappings match. If not, one will be in trouble for sure. The schema tool can also be used to verify that data structure and persistence mappings match.

In the following, let’s assume, we always create the data structure for the demo application using the schema tool. In this case, the table `users` will be created after invoking the proper schema tool commands:

| Col || Type || Length || NULL? || KEY || Extras |
| --- | --- | --- | --- | --- | --- |
| id || INT || 11 ||   || PRI || auto\_increment |
| --- | --- | --- | --- | --- | --- |
| first\_name || VARCHAR || 255 || Y ||   ||   |
| last\_name || VARCHAR || 255 || Y ||   ||   |
| gender || INT || 11 || Y ||   ||   |
| name\_prefix || VARCHAR || 255 || Y ||   ||   |
| contactData\_id || INT || 11 || Y || UNI ||   |

The table `contact_data` created looks like this:

| Col || Type || Length || NULL? || KEY || Extras |
| --- | --- | --- | --- | --- | --- |
| id || INT || 11 ||   || PRI ||   |
| --- | --- | --- | --- | --- | --- |
| email || VARCHAR || 255 || Y ||   ||   |
| phone || VARCHAR || 255 || Y ||   ||   |

### 6.2 One to one relationship, bidirectional

In contrast to the unidirectional one to one relationship two pointers exist: One pointing from object A to object B and another pointing from object B to object A. Its important that we talk about two separate pointers here, as we will see in a minute. Let’s take the a `User` entity again with a reference to a `UserInfo` entity:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="users")
 7 */
 8 class User
 9 {
10 	// [..]
11 
12 	/**
13 	* @OneToOne(targetEntity="Entity\UserInfo")
14 	*/
15 	private $userInfo;
16 
17 	// [..]
18 }
```

If we now want the `UserInfo` entity to point back to the `User` entity, we need to extend the configuration of the `User` entity by adding `inversedBy="user"`:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="users")
 7 */
 8 class User
 9 {
10 	// [..]
11 
12 	/**
13 	* @OneToOne(targetEntity="Entity\UserInfo", inversedBy="user")
14 	*/
15 	private $userInfo;
16 
17 	// [..]
18 }
```

We configured, that the `UserInfo` entity has a pointer called `$user` to a `UserInfo` entity. The `UserInfo` entity itself looks like this:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="user_info")
 7 */
 8 class UserInfo
 9 {
10 	/**
11 	* @Id @Column(type="integer")
12 	* @GeneratedValue
13 	*/
14 	private $id;
15 
16 	/** @Column(type="datetime", nullable=true) */
17 	private $signUpDate;
18 
19 	/** @Column(type="datetime", nullable=true) */
20 	private $signOffDate = null;
21 
22 	/**
23 	* @OneToOne(targetEntity="Entity\User", mappedBy="userInfo")
24 	*/
25 	private $user;
26 
27 	public function setId($id)
28 	{
29 		$this->id = $id;
30 	}
31 
32 	public function getId()
33 	{
34 		return $this->id;
35 	}
36 
37 	public function setSignOffDate($signOffDate)
38 	{
39 		$this->signOffDate = $signOffDate;
40 	}
41 
42 	public function getSignOffDate()
43 	{
44 		return $this->signOffDate;
45 	}
46 
47 	public function setSignUpDate($signUpDate)
48 	{
49 		$this->signUpDate = $signUpDate;
50 	}
51 
52 	public function getSignUpDate()
53 	{
54 		return $this->signUpDate;
55 	}
56 
57 	public function setUser($user)
58 	{
59 		$this->user = $user;
60 	}
61 
62 	public function getUser()
63 	{
64 		return $this->user;
65 	}
66 }
```

In the `UserInfo` entity we define the target entity class via `targetEntity="Entity\User"` and let Doctrine 2 know by adding `mappedBy="contactData"`, that the `User` entity references back via `contactData`.

So far, so good! We just established a bidirectional connection between two entities. Let’s now talk about the `inversedBy` and `mappedBy` configuration.

For a moment, let’s image there exists a `User` entity and a `UserInfo` entity, both belonging together and pointing to each other in a bidirectional manner: `$userInfo` points to a `UserInfo` instance and `$user` points to a `User` instance. We if now want to disconnect the two, we remove both pointers:

```
1 <?php
2 // [..]
3 $user = $em->getRepository('Entity\User')->findOneById($id);
4 $user->getUserInfo()->setUser(null);
5 $user->setUserInfo(null);
6 $em->flush();
```

But what if we only remove one of the two pointers existing? Actually, we would create an inconsistency. Which reference tells Doctrine 2 the truth about the two objects and their association? One entity says “yes, we are connected”, the other says “no, we aren’t connected at all”. Remember that this problem only exists in the object oriented world, not in the relational database universe. In a relational database, references are always bidirectional. There is no concept of a unidirectional relationship. Back to the inconsistency issue: Which entity should Doctrine 2 listen two when taking care of persistence? The solutions looks like this: In doubt, Doctrine 2 listens to the entity, which carries the `inversedBy` attribute. This means that the following code would not remove the association between the two entities:

```
1 <?php
2 // [..]
3 $user = $em->getRepository('Entity\User')->findOneById($id);
4 $user->getUserInfo()->setUser(null);
5 $em->flush();
```

In contract, the following code would remove the association:

```
1 <?php
2 // [..]
3 $user = $em->getRepository('Entity\User')->findOneById($id);
4 $user->setUserInfo(null);
5 $em->flush();
```

The reason is that the `User` entity has the `inversedBy` attribute and acts as the so-called *owning side* of the connection. The owning side is the side Doctrine 2 listens to while determining if a connection exists or not. The other side, the so-called *inverse side* doesn’t matter here. Doctrine 2 doesn’t care about what the inverse side says.

However, even if we correctly cut the connection between the two from the owning side, this change is durable only after flushing:

```
1 <?php
2 use Doctrine\ORM\EntityManager;
3 // [..]
4 $em = EntityManager::create($dbParams, $config);
5 $em->flush();
```

As long as no flushing happend, we have still have an inconsistency in the running program:

```
1 <?php
2 $user = $em->getRepository('Entity\User')->findOneById($id);
3 $userInfo = $user->getUserInfo();
4 $user->setUserInfo(null);
5 var_dump($user->getUserInfo()); // NULL
6 var_dump($userInfo->getUser()); // object(Entity\User)
7 $em->flush();
8 var_dump($user->getUserInfo()); // NULL
9 var_dump($userInfo->getUser()); // NULL
```

Only once `$em->flush()` has been executed will `var_dump($userInfo->getUser())` finally return `NULL`. Before that, it still returns the referenced object. In some cases, this situation may lead to difficult-to-debug issues. A good advice here is to always make sure that both references are removed simultaneously so that even the running program stays intact:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="users")
 7 */
 8 class User
 9 {
10 	// [..]
11 
12 	public function removeUserInfo()
13 	{
14 		$this->userInfo->setUser(null);
15 		$this->userInfo = null;
16 	}	
17 }
```

The following code now always deals with a consistent state:

```
1 <?php
2 $user = $em->getRepository('Entity\User')->findOneById($id);
3 $userInfo = $user->getUserInfo();
4 $user->removeUserInfo();
5 var_dump($user->getUserInfo()); // NULL
6 var_dump($userInfo->getUser()); // NULL
7 $em->flush();
8 var_dump($user->getUserInfo()); // NULL
9 var_dump($userInfo->getUser()); // NULL
```

As a good practice, one should always add a persistence supporting method on the owning side.

Let’s recap: A bidirectional relationship always has an owning side and an inverse side. Unidirectional relationships only have an owning side, which also does not need to be declared explicitly. Regarding associations, only chances to the owning side are relevant for persistence. Doctrine 2 doesn’t care about the inverse side in this concern. The data base table of the entity declared as the owning side holds the foreign key. Which side of the connection is defined as the owning side is decidable by the application developer.

Given a bidirectional association, the owning side can be identified by spotting the `inversedBy` attribute, while the inverse side carries the `mappedBy` attribute.

### 6.3 One to many relationship, bidirectional

In chapter “Hello, Doctrine 2!”, we added a bidirectional one to many relationship to the demo app between a `User` and its `Post`s. Again, let’s take a close look at how we got that working. The `User` entity has a member variable called `$posts`:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="users")
 7 */
 8 class User
 9 {
10 	/**
11 	* @OneToMany(targetEntity="Entity\Post", mappedBy="user")
12 	*/
13 	private $posts;
14 	
15 	// [..]
16 }
```

The `@OneToMany` annotation defines the one to many relationship to the `Post` entity (`targetEntity`). As the `mappedBy` attribute is given, it’s a bidirectional relationship. The `Post` entity looks like this:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="posts")
 7 */
 8 class Post
 9 {
10 	/**
11 	* @ManyToOne(targetEntity="Entity\User", inversedBy="posts")
12 	*/
13 	private $user;
14 	
15 	// [..]
16 }
```

Here we find the counterpart annotation `@ManyToOne`. In a one to one relationship, the application developer can decide freely which side to declare as the owning side. This isn’t the case here. The entity carrying the `@ManyToOne` annotation must become the owning side and get the `inversedBy` attribute.

If again the schema tool is used to create the data structure based on the persistence configuration, the following tables are set up:

| Col || Type || Length || NULL? || KEY || Extras |
| --- | --- | --- | --- | --- | --- |
| id || INT || 11 ||   || PRI || auto\_increment |
| --- | --- | --- | --- | --- | --- |
| first\_name || VARCHAR || 255 || Y ||   ||   |
| last\_name || VARCHAR || 255 || Y ||   ||   |
| gender || INT || 11 || Y ||   ||   |
| name\_prefix || VARCHAR || 255 || Y ||   ||   |
| contactData\_id || INT || 11 || Y || UNI ||   |
| userInfo\_id || INT || 11 || Y || UNI ||   |

The table `user_info` looks like this:

| Col || Type || Length || NULL? || KEY || Extras |
| --- | --- | --- | --- | --- | --- |
| id || INT || 11 ||   || PRI ||   |
| --- | --- | --- | --- | --- | --- |
| user\_id || INT || 11 ||   || MUL ||   |
| title || VARCHAR || 255 ||   ||   ||   |
| content || VARCHAR || 255 ||   ||   ||   |

As we can see, table `user_info` holds the foreign key, which may occur more than once. When accessing a `User`’s `Post`s from a given `User` entity, Doctrine uses a `Doctrine\ORM\PersistentCollection` to provide the referenced `Post` entities. It extends other classes such as `\Countable`, `\IteratorAggregate` and `\ArrayAccess`, which makes a `Doctrine\ORM\PersistentCollection` very similar to a regular PHP array, meaning it can easily be used e.g. in PHP foreach loops.

As long as the referenced `Post`s haven’t been accessed at least once, the member variable `$user` has value `null` and not yet an object of class `Doctrine\ORM\PersistentCollection` assigned. If once wants to work with the collection, before it has been set up by Doctrine 2, this could be an issue. Therefore, as a good practice, a member variable holding a persistent association should always be initialized:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="users")
 7 */
 8 class User
 9 {
10 	// [..]
11 	
12 	public function __construct()
13 	{
14 		$this->posts = new \Doctrine\Common\Collections\ArrayCollection();
15 	}
16 
17 	// [..]
18 }
```

### 6.4 Many to many relationship, unidirectional

In our demo app, one `User` may act in different `Role`s with different access rights. Let’s distinguish between base- and pro-users and administrators. `User` with the base `Role` can read `Post`s, but can’t write `Post`s. Pro-users can also write `Post`s. Administrators can manage the overall application and various settings. We design the relationship in a way, that from given a `User` entity, we can access the `User`’s `Role`s, but not the other way round. To do so, we simply need to add the following persistence configuration:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="users")
 7 */
 8 class User
 9 {
10 	// [..]
11 	
12 	/**
13 	* @ManyToMany(targetEntity="Entity\Role")
14 	**/
15 	private $roles;
16 	
17 	// [..]
18 }
```

The `Role` entity definitions are straight forward as well:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="role")
 7 */
 8 class Role
 9 {
10 	/**
11 	* @Id @Column(type="integer")
12 	* @GeneratedValue
13 	*/
14 	private $id;
15 
16 	/** @Column(type="string") */
17 	private $label;
18 
19 	public function setId($id)
20 	{
21 		$this->id = $id;
22 	}
23 
24 	public function getId()
25 	{
26 		return $this->id;
27 	}
28 
29 	public function setLabel($label)
30 	{
31 		$this->label = $label;
32 	}
33 
34 	public function getLabel()
35 	{
36 		return $this->label;
37 	}
38 }
```

Running the schema tool creating the data structure in the database, we now have a new table called `role`:

| Col || Type || Length || NULL? || KEY || Extras |
| --- | --- | --- | --- | --- | --- |
| id || INT || 11 ||   || PRI || auto\_increment |
| --- | --- | --- | --- | --- | --- |
| label || VARCHAR || 255 ||   ||   ||   |

Also, we find a table called `user_role` allowing to persist a many to many reference:

| Col || Type || Length || NULL? || KEY || Extras |
| --- | --- | --- | --- | --- | --- |
| user\_id || INT || 11 ||   || MUL ||   |
| --- | --- | --- | --- | --- | --- |
| role\_id || INT || 11 ||   || MUL ||   |

The reason for the fact that the join table shown above looks like it does, is that Doctrine 2 again has a default configuration applied for the `@JoinTable` annotation, which itself is not given with our code, but which implicitly is considered by Doctrine 2. If needed, our join table can be defined differently, e.g. if an existing data structure in a database needs to be used:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="users")
 7 */
 8 class User
 9 {
10 	// [..]
11 	
12 	/**
13 	* @ManyToMany(targetEntity="Entity\Role")
14 	* @JoinTable(name="users_roles",
15 	*      joinColumns={@JoinColumn(name="user", referencedColumnName="id")},
16 	*      inverseJoinColumns={@JoinColumn(name="role",
17 	*			referencedColumnName="id")
18 	*		}
19 	* )
20 	**/
21 	private $roles;
22 	
23 	// [..]
24 }
```

The persistence configuration now looks way more complex and tells Doctrine to deal with a join table that looks like this:

| Col || Type || Length || NULL? || KEY || Extras |
| --- | --- | --- | --- | --- | --- |
| user || INT || 11 ||   || MUL ||   |
| --- | --- | --- | --- | --- | --- |
| role || INT || 11 ||   || MUL ||   |

The `@JoinTable` annotation has an attribute called `name` to define the join table name as well as the attributes `joinColumns` and `inverseJoinColumns`, which both utilize another annotation called `@JoinColumn` to map the individual columns.

### 6.5 Many to many relationship, bidirectional

The author of a `Post` (a `User`) should be able to assign one or more `Tag`s. A `Tag` itself may be re-used in different `Post`s. In contrast to the relationship betweens a `User` and its `Role`s we design the association to be bidirectional. First, let’s set up the new `Tag` entity:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="tag")
 7 */
 8 class Tag
 9 {
10 	/**
11 	* @Id @Column(type="integer")
12 	* @GeneratedValue
13 	*/
14 	private $id;
15 
16 	/** @Column(type="string") */
17 	private $label;
18 	
19 	/**
20 	* @ManyToMany(targetEntity="Entity\Post", mappedBy="tags")
21 	*/
22 	private $posts;
23 
24 	public function __construct()
25 	{
26 		$this->posts = new \Doctrine\Common\Collections\ArrayCollection();
27 	}
28 
29 	public function setId($id)
30 	{
31 		$this->id = $id;
32 	}
33 
34 	public function getId()
35 	{
36 		return $this->id;
37 	}
38 
39 	public function setLabel($label)
40 	{
41 		$this->label = $label;
42 	}
43 
44 	public function getLabel()
45 	{
46 		return $this->label;
47 	}
48 	
49 	public function setPosts($posts)
50 	{
51 		$this->posts = $posts;
52 	}
53 
54 	public function getPosts()
55 	{
56 		return $this->posts;
57 	}
58 }
```

The `Post` entity needs to be extended as well by a new member variable:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="posts")
 7 */
 8 class Post
 9 {
10 	// [..]
11 
12 	/**
13 	* @ManyToMany(targetEntity="Entity\Tag", inversedBy="posts")
14 	*/
15 	private $tags;
16 
17 	public function __construct()
18 	{
19 		$this->tags = new \Doctrine\Common\Collections\ArrayCollection();
20 	}
21 
22 	// [..]
23 }
```

When setting up a many to many relationship, one can choose freely the owning side.

The schema tool once more creates the join table `post_tag` for us, if we run the proper commands:

| Col || Type || Length || NULL? || KEY || Extras |
| --- | --- | --- | --- | --- | --- |
| post\_id || INT || 11 ||   || MUL ||   |
| --- | --- | --- | --- | --- | --- |
| tag\_id || INT || 11 ||   || MUL ||   |

Again, defaults are applied here. If desired, the `@JoinTable` annotation can be used to alter the labels of the table and its columns.

### 6.6 One to many relationship, unidirectional

A `User` can set up multiple `Category`s for its `Post`s. We will use a unidirectional association for this domain model aspect, which requires-in contract to the bidirectional one to many relationship-a join table as well. Also, we need to use the `@ManyToMany` annotation, even though we don’t set up a many to many annotation (this might be somewhat confusing). With the help of a unique constraint, it finally results in a one to many relationship. The `User` entity is extended by the `$categories` member variable:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="users")
 7 */
 8 class User
 9 {
10 	// [..]
11 
12 	/**
13 	* @ManyToMany(targetEntity="Entity\Category")
14 	* @JoinTable(name="users_categories",
15 	*      joinColumns={@JoinColumn(name="user", referencedColumnName="id")},
16 	*      inverseJoinColumns={@JoinColumn(name="category",
17 	* 		referencedColumnName="id", unique=true)}
18 	* )
19 	*/
20 	private $categories;
21 
22 	public function __construct()
23 	{
24 		// [..]
25 		$this->categories = new \Doctrine\Common\Collections\ArrayCollection();
26 	}
27 
28 	public function setCategories($categories)
29 	{
30 		$this->categories = $categories;
31 	}
32 
33 	public function getCategories()
34 	{
35 		return $this->categories;
36 	}
37 
38 	// [..]
39 }
```

The annotations and attributes used are already known from the many to many relationship. New is just the `unique=true` configuration, which makes it a one to many relationship. The `Category` entity is simple:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="category")
 7 */
 8 class Category
 9 {
10 	/**
11 	* @Id @Column(type="integer")
12 	* @GeneratedValue
13 	*/
14 	private $id;
15 
16 	/** @Column(type="string") */
17 	private $label;
18 
19 	public function setId($id)
20 	{
21 		$this->id = $id;
22 	}
23 
24 	public function getId()
25 	{
26 		return $this->id;
27 	}
28 
29 	public function setLabel($label)
30 	{
31 		$this->label = $label;
32 	}
33 
34 	public function getLabel()
35 	{
36 		return $this->label;
37 	}
38 }
```

### 6.7 Many to one relationship, unidirectional

Multiple posts can be grouped in a `Category`, but every `Post` can only be in one `Category`. To allow access to a `Category` from a `Post`, the `Post` must be extended:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="posts")
 7 */
 8 class Post
 9 {
10 
11 	// [..]
12 
13 	/**
14 	* @ManyToOne(targetEntity="Entity\Category")
15 	* @JoinColumn(name="category_id", referencedColumnName="id")
16 	**/
17 	private $category;
18 
19 	// [..]
20 
21 	public function setCategory($category)
22 	{
23 		$this->category = $category;
24 	}
25 
26 	public function getCategory()
27 	{
28 		return $this->category;
29 	}
30 }
```

And that’s it-nothing more configuration is needed, as it’s a unidirectional association. The `Category` doesn’t need to be extended as well. In fact, even the `@JoinColumn` annotation is redundant, because its configuration is identical with Doctrine’s defaults.

### 6.8 One to one relationship, self-referencing

Doctrine 2 allows to define association between entities of the same type, so-called “self-referencing” relations. In our demo app a `User` can declare another `User` as its life partner. Both ends of the association allow to access the referenced life partner. The persistence configuration needed for a self-referencing association looks like this:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="users")
 7 */
 8 class User
 9 {
10 	/**
11 	* @OneToOne(targetEntity="Entity\User")
12 	**/
13 	private $lifePartner;
14 
15 	// [..]
16 
17 	public function setLifePartner($lifePartner)
18 	{
19 		$this->lifePartner = $lifePartner;
20 	}
21 
22 	public function getLifePartner()
23 	{
24     	return $this->lifePartner;
25 	}
26 }
```

If the database structure is created by the schema tool, Doctrine 2 automatically adds a column called `lifeParter_id` to the `users` table to maintain the reference. Again, Doctrine’s defaults are at play here. If needed, one may add the `@JoinColumn` annotation and overwrite the defaults:

```
 1 <?php
 2 // [..]
 3 
 4 /**	
 5 * @OneToOne(targetEntity="Entity\User")
 6 * @JoinColumn(name="partner", referencedColumnName="id")
 7 **/
 8 private $lifePartner;
 9 
10 // [..]
```

### 6.9 One to many relationship, self-referencing

With a self-referencing one to many relationship, e.g. a category tree can be built. A `Category` may have multiple child categories and one parent category (the root node won’t have a parent category). The persistence configuration for a self-referencing one to many relationship is similar to a regular bidirectional one to many relationship:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="category")
 7 */
 8 class Category
 9 {	
10 	/**
11 	* @OneToMany(targetEntity="Entity\Category", mappedBy="parent")
12 	**/
13 	private $children;
14 
15 	/**
16 	* @ManyToOne(targetEntity="Entity\Category", inversedBy="children")
17 	* @JoinColumn(name="parent_id", referencedColumnName="id")
18 	**/
19 	private $parent;
20 
21 	// [..]
22 
23 	public function __construct() {
24 		$this->children = new \Doctrine\Common\Collections\ArrayCollection();
25 	}
26 
27 	public function setParent($parent)
28 	{
29 		$this->parent = $parent;
30 	}
31 
32 	public function getParent()
33 	{
34 		return $this->parent;
35 	}
36 
37 	// [..]
38 }
```

The configuration shown above extends table `category` by column `parent_id`, if the already developed data structure again is extended using Doctrine’s schema tool. The relationship is designed in a way, that allows to reach a parent and children from a `Category` given.

### 6.10 Many to many relationship, self-referencing

Many to many self-referencing relationships can be defined as well. In our demo app, this type of a relationship is used to describe the social network of a `User`:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="users")
 7 */
 8 class User
 9 {
10 	// [..]
11 	
12 	/**
13 	* @ManyToMany(targetEntity="Entity\User")
14 	* @JoinTable(name="friends",
15 	*      joinColumns={@JoinColumn(name="user_id",
16 	* 			referencedColumnName="id")},
17 	*      inverseJoinColumns={@JoinColumn(name="friend_user_id",
18 	*			referencedColumnName="id")}
19 	* )
20 	**/
21 	private $myFriends;
22 
23 	public function __construct()
24 	{
25 		// [..]
26 		$this->myFriends = new \Doctrine\Common\Collections\ArrayCollection();
27 	}
28 
29 	// [..]
30 	
31 	public function setMyFriends($myFriends)
32 	{
33 		$this->myFriends = $myFriends;
34 	}
35 
36 	public function getMyFriends()
37 	{
38 		return $this->myFriends;
39 	}
40 }
```

If once more the schema tool is applied, it will report an error here, because Doctrine 2 wants to label both columns of the join table with “user\_id”, which is invalid. In this case, one will need to add the `@JoinTable` annotation to provide a different persistence configuration. Also, by default, the join table will be called `users_users`, if not defined otherwise. In our case, we tell Doctrine 2 to call it `friends`, a more meaningful table naming in our case. If one deals with an existing data structure, custom configuration would be necessary anyway.

## 7 Managing Entities

### 7.1 Creating a new Entity

Once the domain model is modeled, it is time for using it. A new entity can simply be created based on a new object of an entity class:

```
1 <?php
2 $newPost = new \Entity\Post();
3 $newPost->setTitle('A new post!');
4 $newPost->setContent('This is the body of the new post.');
5 $em->persist($newPost);
6 $em->flush();
```

The code shown above anticipates that `$em` references a ready-to-use entity manager. First, a new `Post` is created, then data is assigned and then the object is passed to the entity manager for persistence.

One must remember that the `persist()` method call does not yet cause an SQL INSERT statement to be issued. The entity only is scheduled for persistence with the next flushing. As long as no flushing took place, the entity is in a state called `MANAGED`-meaning that the entity manager recognizes the new entity and from now.

Only once the `flush()` method is invoked on the entity manager, a new record is written to the database. Otherwise, the entity will be lost after the script has finished.

### 7.2 Loading an existing Entity

Mainly, there are two different ways to load an existing entity: Either by querying and retrieving it from its corresponding repository or by accessing it through an association given by another, already loaded entity.

#### 7.2.1 Using a repository

We already learned that a repository is a container for all entity of a specific type. A repository is decorated by finder methods to search entities based on a query. While several finder methods are available out-of-the-box, custom finder methods can also be added later on. A custom finder method can be imagined as a “quick access” to a typical query. With the help of finder methods, once can look-up an entity, e.g. by its ID like this:

```
1 <?php
2 $post = $em->getRepository('Entity\Post')->findOneById($id);
```

First we request the repository from the entity manager and then execute a finder method on it. By default, four finder methods are available. To find a single entity based on its ID, the `find()` method is used:

```
1 <?php
2 public function find($id, $lockMode = LockMode::NONE, $lockVersion = null);
```

To find a single entity based on criteria, the `findOneBy()` method is used:

```
1 <?php
2 public function findOneBy(array $criteria, array $orderBy = null);
```

To find all entities of a specific type, the `findAll()` method is used:

```
1 <?php
2 public function findAll();
```

To find multiple entities based on criteria, the `findBy()` method is used:

```
1 <?php
2 public function findBy(
3 	array $criteria, 
4 	array $orderBy = null, 
5 	$limit = null, 
6 	$offset = null
7 );
```

One may define the order, limit and offset values when using `findBy()`.

Also helpful are the so-called *magic finders*. They allow to include search criteria directly in a finder method’s name. The next two statements produce the same result:

```
1 <?php
2 $tag = $em->getRepository('Entity\Tag')->findOneBy(array('label'=>$label));
3 $tag = $em->getRepository('Entity\Tag')->findOneByLabel($label);
```

Adding a custom repository with individual finder methods is a two step process. First, a new repository class needs to be set up:

```
 1 <?php
 2 namespace Repository;
 3 
 4 use Doctrine\ORM\EntityRepository;
 5 
 6 class Post extends EntityRepository
 7 {
 8 	public function findAllPostsWithTag($tag)
 9 	{
10 		// DQL statement goes here
11 	}
12 }
```

Next, Doctrine 2 needs to know about the new repository. This is done through the corresponding entity:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity(repositoryClass="Repository\Post")
 6 * @Table(name="posts")
 7 */
 8 class Post
 9 {
10 	// [..]
11 }
```

That’s all! The `findAllPostsWithTag()` finder method now can easily be invoked:

```
1 <?php
2 $posts = $em->getRepository('Entity\Post')->findAllPostsWithTag($tag);
```

We will learn more about DQL-the *Doctrine Query Language*\-later in the book. It is used to phrase a query.

#### 7.2.2 Using an association

Let’s assume we already have a loaded `User` entity available. Instead of loading the `User`’s contact data by utilizing its repository, we may also simply reach this entity from the given `User` entity:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="users")
 7 */
 8 class User
 9 {
10 	// [..]
11 
12 	/**
13 	* @OneToOne(targetEntity="Entity\ContactData")
14 	*/
15 	private $contactData;
16 
17 	// [..]
18 	
19 	public function getContactData()
20 	{
21 		return $this->contactData;
22 	}
23 }
```

In this case, when calling `getContactData()`, the referenced `ContactData` entity is loaded on demand by Doctrine’s proxy mechanism.

We could even make sure that the referenced `ContactData` entity is already loaded when loading the `User` itself-and save an additional database query:

```
1 <?php
2 // [..]
3 /**
4 * @OneToOne(targetEntity="Entity\ContactData", fetch="EAGER")
5 */
6 private $contactData;
```

By using `fetch="EAGER"`, we tell Doctrine 2 to always load the referenced `ContactData` entity when the `User` itself is loaded.

Loading eagerly sometimes has its advantages. Especially when it’s likely to access a referenced entity later in the process. If the `fetch` attribute is omitted, Doctrine 2 fetches `LAZY` by default. This means it loads the entity on first access. The third option is `EXTRA_LAZY`, which is helpful for huge datasets. Even if one decides to lazy load references, the referenced entities are still all loaded fully into RAM. Depending on the amount and size of the entities referenced, this could be a serious performance issue. When `EXTRA_LAZY` is used, several methods can be executed on the collection of referenced entities without fully loading them into the RAM right away. This is true for:

*   `contains()`
*   `count()`
*   `offsetSet()`
*   `add()`
*   `count()`
*   `slice()`

This way, e.g. a pagination feature can be built without performance issues.

### 7.3 Changing an existing Entity

Modifying an exiting, already loaded entity is easy. All changes made to such an entity are auto-detected by Doctrine 2 when flushing the entity manager:

```
1 <?php
2 // [..]
3 $post = $em->getRepository('Entity\Post')->find(1);
4 $post->setTitle("New title");
5 $em->flush();
```

There is no need for explicitly telling Doctrine 2 again about the fact that this entity has been changed. The method `persist($entity)` does not need to be called on the entity manager again.

### 7.4 Removing an Entity

Removing an existing entity can easily be done through the entity manager, if a handle to a loaded entity is available:

```
1 <?php
2 $em->remove($post);
3 $em->flush();
```

The SQL statement needed to physically delete the record in the database is not issued as long as `flush()` hasn’t been invoked.

### 7.5 Sorting an association

When accessing entities via an association, the order of the entities retrieved is not defined. As a part of the entity mapping definitions, one can define the order of entities using the `@OrderBy` annotation. If we get back to our demo application, we could define the order of a `User`’s `Post`s in a way, that the most recent `Post` is shown first in its list of `Post`s, simply by modifying the mapping configuration in the `User` entity:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @Table(name="users")
 7 */
 8 class User
 9 {
10 	// [..]
11 	
12 	/**
13 	* @OneToMany(targetEntity="Entity\Post", mappedBy="user")
14 	* @OrderBy({"id" = "DESC"})
15 	*/
16 	private $posts;
17 	
18 	// [..]
19 }
```

Alternatively, one may sort a collection with PHP after retrieving the entities from the database.

### 7.6 Removing an association

Removing an association is as straight-forward as removing of an entity is:

```
 1 <?php
 2 $newPost = new \Entity\Post();
 3 $newPost->setTitle('A new post!');
 4 $newPost->setContent('This is the body of the new post.');
 5 $user = $em->getRepository('Entity\User')->findOneById(1);
 6 $newPost->setUser($user);
 7 $em->flush();
 8 
 9 $newPost->setUser(null);
10 $em->flush();
```

First, a new `Post` entity is created in the example above. Then, an existing `User` entity is loaded and associated with the new post. After flushing, the reference has been persisted to the database. Next, we remove the association again by setting `User` to `null`. After the next flushing, the reference is gone in the database.

We need to keep in mind here that we have established a bidirectional relationship between the `User` and its `Post`s, while the `Post` entity is the owning side of the association. If, for example, we would take the `User` entity and remove the `Post` from its collection `$posts`, nothing would happen on flushing:

```
1 <?php
2 // [..]
3 $user->getPosts()->removeElement($newPost);
4 $em->flush();
```

The `removeElement()` method, which is used to remove an element from a given Doctrine 2 collection based on an entity loaded, is without the desired effect. However, there *is* an effect. While the change won’t be persisted, the element has been removed from the collection in RAM. One won’t find the element when looking it up in the collection anymore.

### 7.7 Life Cycle events

When working with entities, several events are triggered by Doctrine 2:

*   **preRemove**: Occurs for a given entity before the respective EntityManager remove operation for that entity is executed.
*   **postRemove**: Occurs for an entity after the entity has been deleted. It will be invoked after the database delete operations.
*   **prePersist**: Occurs for a given entity before the respective EntityManager persist operation for that entity is executed.
*   **postPersist**: Occurs for an entity after the entity has been made persistent. It will be invoked after the database insert operations.
*   **preUpdate**: Occurs before the database update operations to entity data.
*   **postUpdate**: Occurs after the database update operations to entity data.
*   **postLoad**: Occurs for an entity after the entity has been loaded from the database.

With `loadClassMetadata`, `onFlush` and `onClear`, additional events are triggered that are persistence related, but are not specific to a single entity.

With these events available, one may hook into persistence processing, with a so-called *lifecycle callback*, which are implemented as a method of an entity class.

Let’s assume we want to add login data for each `User` to our demo application. While the username can be picked be the user, the password is auto-generated on signup. This can be achieved by adding a lifecycle callback to the `User` class:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @HasLifecycleCallbacks
 7 * @Table(name="users")
 8 */
 9 class User
10 {
11 	// [..]
12 
13 	const GENERATED_PASSWORD_LENGTH = 6;
14 
15 	// [..]
16 
17 	/** @PrePersist */
18 	public function generatePassword()
19 	{
20 		for($i = 1; $i <= self::GENERATED_PASSWORD_LENGTH; $i++) {
21 			$this->password .= chr(rand(65, 90)); // 65 -> A, 90 -> Z
22 		}
23 	}
24 }
```

First, we need to declare that lifecycle callbacks are present by using the `@HasLifecycleCallbacks` annotation. Then we add the lifecycle annotation `@PrePersist` to the `generatePassword()` method. That’s it! Now, before persisting a new entity, this method is called automatically and the `User`’s password is auto-generated.

### 7.8 Cascading operations

When creating a new or modifying an existing entity, all operations by default only affect a single entity. A powerful, but somewhat dangerous feature, is the option to define “operation cascades”. Let’s consider the following example. If we delete a `User` in our demo application, we also want all of its `Post`s being deleted. This can be achieved by adding the `cascade` attribute to the association definition:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity
 6 * @HasLifecycleCallbacks
 7 * @Table(name="users")
 8 */
 9 class User
10 {
11 	// [..]
12  
13 	/**
14 	* @OneToMany(targetEntity="Entity\Post", mappedBy="user", cascade={"remove"})
15 	*/
16 	private $posts; 
17 
18 	// [..]
19 }
```

Now, when removing a user via

```
1 <?php
2 $user = $em->getRepository('Entity\User')->find($id);
3 $em->remove($user);
4 $em->flush();
```

the `User` is gone and also are all its `Post`s. When setting `cascade` to value `all`, the cascade will be applied on others operations, e.g. `persist`, as well.

When adding the `cascade` attribute, the side matters. In the code shown above, all referenced `Post` entities are removed, when a `User` is removed. When adding `cascade` to the `Post` entity like shown in the following code, the `User` entity will be removed, if one of its referenced `Post` entities is deleted:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity(repositoryClass="Repository\Post")
 6 * @Table(name="posts")
 7 */
 8 class Post
 9 {
10 	// [..]
11 
12 	/**
13 	* @ManyToOne(targetEntity="Entity\User", inversedBy="posts", cascade={"remove"})
14 	* @JoinColumn(name="user_id", referencedColumnName="id")
15 	*/
16 	protected $user;
17 	
18 	// [..]
19 }
```

Assuming that this is not the desired behavior, it is absolutely crucial to verify the cascade configuration to prevent data loss.

Another way to achieve automatic deletion of referenced entities like shown above is *orphan removal* for one-to-one and one-to-many associations. Orphan removal means Doctrine 2 will automatically remove referenced entities without a parent entity:

```
 1 /**
 2 * @Entity
 3 * @HasLifecycleCallbacks
 4 * @Table(name="users")
 5 */
 6 class User
 7 {
 8 	// [..]
 9  
10 	/**
11 	* @OneToMany(targetEntity="Entity\Post", mappedBy="user", orphanRemoval=true)
12 	private $posts; 
13 
14 	// [..]
15 }
```

Again, when the `User` is gone, also all of its `Post`s are gone.

While cascading operation are useful, they can be expensive. The reason for this is that all operations on the referenced entities happen in RAM. They will be loaded and reconstructed from the database first and then be modified. Depending on the size of the collection, this could be resource intensive.

Luckily, Doctrine 2 also offers “database level” cascading operations for updates and deleted via the \`@JoinColumn’ annotation:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity(repositoryClass="Repository\Post")
 6 * @Table(name="posts")
 7 */
 8 class Post
 9 {
10 	/**
11 	* @ManyToOne(targetEntity="Entity\User", inversedBy="posts")
12 	* @JoinColumn(name="user_id", referencedColumnName="id", onDelete="CASCADE")
13 	*/
14 	protected $user;  
15 	
16 	// [..]
17 }
```

### 7.9 Transactions

A transaction is an atomic unit of one or more database statements. All insert-, update- or delete-operations done through the entity manager are queued as long as the `flush()` method has been called on the entity manager. Technically speaking, the queue is an implementation of the so-called [*unit of work*](http://martinfowler.com/eaaCatalog/unitOfWork.html) pattern. When calling `flush()`, all queued operations in the unit of work are fired against the database as a single transaction. If one of these operations fail, Doctrine 2 automatically rolls back the entire transaction-this is all operations queued-and mainly quits itself to prevent data loss due to inconsistencies.

Doctrine 2 offers a convenient way to wrap several database operations into a single transaction. The following code demonstrates how to “reset” a `User` in the demo application. First, the existing `User` is deleted, then a new one is created by using its current first and last name:

```
 1 <?php
 2 // [..]
 3 $em->transactional(function($em) {
 4 	$oldUser = $em->getRepository('Entity\User')->find(1);
 5 	$newUser = new Entity\User();
 6 	$newUser->setFirstName($oldUser->getFirstname());
 7 	$newUser->setLastName($oldUser->getLastname());
 8 	$em->persist($newUser);
 9 	$em->remove($oldUser);
10 });
```

Both operations only take effect, if there was no exception thrown for one of them. Otherwise, both operations are rolled back.

Another issue may arise when two or more persons simultaneously work on the same sets of data, which is not unlikely, e.g. for web applications. Doctrine 2 fully supports a strategy called *optimistic locking*. The core idea behind optimistic locking is that multiple users can all read data sets, however, whenever changing data, only the first person writing is privileged to persist its changes. All other users now working with an outdated version of the entity will get an exception when trying to persist their individual changes. As this strategy allows for concurrent reading operations and only controls write operations, read-intensive application won’t be slowed down, compared to a pessimistic locking strategy.

To make optimistic locking happen, Doctrine 2 allows to add a special `integer` or `datetime` version field to an entity. The current value of this field is compared to the value loaded before and if it doesn’t match on write, an `OptimisticLockException` is thrown. If this happens, another user already modified the entity in the meantime. A version field can be set up by adding the `@Version` annotation:

```
 1 <?php
 2 namespace Entity;
 3 
 4 /**
 5 * @Entity(repositoryClass="Repository\Post")
 6 * @Table(name="posts")
 7 */
 8 class Post
 9 {
10 	// [..]
11 	
12 	/** @Version @Column(type="integer") */
13 	protected $version;
14 	
15 	// [..]
16 }
```

When creating the corresponding data schema via Doctrine 2, a column called `version` is added to the `posts` table. For every new `Post` entity, Doctrine 2 automatically assigns a value of `1`. The value is increased by one with each following modification:

```
1 $post = $em->getRepository('Entity\Post')->find(1);
2 $post->setTitle("New title");
3 $em->flush();
4 $em->clear();
5 $post = $em->getRepository('Entity\Post')->find(1);
6 $post->setTitle("Again, a new title");
7 $em->flush();  
```

The code shown above modifies the `Post` entity with an ID value of `1` two times. After both changes have been applied, the `value` column has a value of `3`. The `$em->clear()` statement is important here: If we omit it, we would produce an `OptimisticLockException` ourselves. The reason for this is that changing the title to “New title” and flushing the entity manager increments the version value for this entity by one in the database. However, the value stored in the `Post` entity object in RAM still has the old value of `1` and therefore now is outdated-it is not being updated to the latest version value automatically. Therefore, trying to modifying the title again will fail with an `OptimisticLockException`. The same will be true, if we would try to persist changes to an entity, which has been modified in the meantime by somebody else. How an `OptimisticLockException` situation is handled, is fully up to the application developer.

## 8 Doctrine Query Language

### 8.1 Introduction

Earlier in this book, we learned about repositories, containers for entities of a specific type. They are used to look up entities by specific criteria, do updates or deletes and so on. They do their work with the help of finder methods, which are implemented using Doctrine’s own entity query language DQL-the Doctrine Query Language. To be exact, DQL is not bound to finder methods or repositories, however, usually, one mainly will want to put all DQL statements there, just to keep things organized.

DQL itself is a language to query entities. It looks much like SQL-which makes learning DQL easier-but it isn’t SQL. While DQL statements can be written as a string like this

```
1 <?php
2 // [..]
3 $query = $em->createQuery(
4 	'SELECT u FROM Entity\User u WHERE u.lastName = "Mustermann"'
5 );
6 
7 $users = $query->getResult();  
```

it is much more convenient to use the *query builder*, especially when constructing dynamic queries:

```
 1 <?php
 2 // [..]
 3 $qb = $this->_em->createQueryBuilder();
 4 
 5 $qb->select('u')
 6 	->from('Entity\User', 'u')
 7 	->where($qb->expr()->eq('u.lastName', '?1'))
 8 	->setParameter(1, "Mustermann");
 9 
10 $users = $qb->getQuery()->getResult();
```

We assume that `$this->_em` holds a reference to the entity manager (which is true for every repository that extends `Doctrine\ORM\EntityRepository`). The entity manager is capable of providing a query builder, which in turn can be used to programmatically construct a query. Thanks to its fluent interface, the code looks pretty elegant. In contrast to the first example, we also utilize value parameters and the `Expr` class, which we will look at in detail in a minute.

### 8.2 Retrieving results

When executing a query, multiple options exist for retrieving results. When calling `getResult()` on a query object, a PHP array is returned containing all matching entity objects. Alternatively, `getArrayResult()` can be used to get all data in form of an array. No objects are returned, only all entities data as an array in a container array. This is pretty useful when dealing with bigger dataset or for simple display tasks, where no objects are needed in the processing. A similar result, but fully flat, not nested at all, creates `getScalarResult()`. When a single result is desired, calling `getSingleResult()` or `getSingleScalarResult()` will do. Method `getOneOrNullResult()` may be used if null is desired when no match was found.

If not only entities are selected by a query, the result set returned is so-called “mixed”-it includes objects as well as scalar values as well:

```
 1 <?php
 2 // [..]
 3 $qb = $this->_em->createQueryBuilder();
 4 
 5 $qb->select('u')
 6 	->addSelect($qb->expr()->concat('u.firstName', 'u.lastName'))
 7 	->from('Entity\User', 'u')
 8 	->where($qb->expr()->eq('u.lastName', '?1'))
 9 	->setParameter(1, "Mustermann");
10 
11 $users = $qb->getQuery()->getResult();
```

In this query, we not only retrieve entities, but also concatenate the user’s first and last name. The result of the query looks like this:

```
1 array 
2 	[0]
3 		[0] => Object
4 		[1] => "Max Mustermann"
5 	[1]
6 		// ..
```

Via `setFirstResult($offset)` and `setMaxResults($limit)` the result set can be limited, e.g. when building a pagination feature.

Another feature Doctrine 2 offers is retrieving partial objects, entities, which have been recreated from the database only partially. To retrieve a partial object, a special syntax is required:

```
 1 <?php
 2 // [..]
 3 $qb = $this->_em->createQueryBuilder();
 4 
 5 $qb->select('partial u.{id, firstName}')
 6 	->from('Entity\User', 'u')
 7 	->where($qb->expr()->eq('u.lastName', '?1'))
 8 	->setParameter(1, "Mustermann");
 9 
10 $users = $qb->getQuery()->getResult();
```

This way, we get back `User` objects, partly reconstituted from the database. When omitting the `partial` syntax and simply stating individual fields, the result otherwise is a plain array without objects:

```
1 array(1) { 
2 	[0]=> 
3 		array(2) { 
4 			["id"]=> int(1) 
5 			["firstName"]=> string(3) "Max" 
6 		} 
7 }
```

Its important to always include the identifier (`id` in this case) in a partial object definition. Otherwise an exception is thrown.

While Partial objects can be very helpful, e.g. while tweaking the performance of an app, they can be problematic as well. Code dealing with partial objects needs to be aware of the fact, that no “real” entities are returned and certain fields or associations might not be available. One will need to use partial objects with care.

### 8.3 Constructing basic queries

The query builder provides methods for the different parts of a query, such as the one shown above:

*   public function select($select = null);
*   public function delete($delete = null, $alias = null);
*   public function update($update = null, $alias = null);
*   public function set($key, $value);
*   public function from($from, $alias = null);
*   public function where($where);
*   public function andWhere($where);
*   public function orWhere($where);
*   public function groupBy($groupBy);
*   public function addGroupBy($groupBy);
*   public function having($having);
*   public function andHaving($having);
*   public function orHaving($having);
*   public function orderBy($sort, $order = null);
*   public function addOrderBy($sort, $order = null);

Expressions like the ones shown above are built using an `Expr` object, which is provided by the query builder when calling its `expr()` method. The `Expr` object provides several methods to construct an expression:

*   public function andX($x = null);
*   public function orX($x = null);
*   public function eq($x, $y);
*   public function neq($x, $y);
*   public function lt($x, $y);
*   public function lte($x, $y);
*   public function gt($x, $y);
*   public function gte($x, $y);
*   public function isNull($x);
*   public function isNotNull($x);
*   public function prod($x, $y);
*   public function diff($x, $y);
*   public function sum($x, $y);
*   public function quot($x, $y);
*   public function exists($subquery);
*   public function all($subquery);
*   public function some($subquery);
*   public function any($subquery);
*   public function not($restriction);
*   public function in($x, $y);
*   public function notIn($x, $y);
*   public function like($x, $y);
*   public function between($val, $x, $y);
*   public function trim($x);
*   public function concat($x, $y);
*   public function substr($x, $from, $len);
*   public function lower($x);
*   public function upper($x);
*   public function length($x);
*   public function avg($x);
*   public function max($x);
*   public function min($x);
*   public function abs($x);
*   public function sqrt($x);
*   public function count($x);
*   public function countDistinct($x);

Expressions are used in the SELECT, WHERE, HAVING or GROUP part of a query. However, the query shown above can also be created without using the `Expr` class:

```
 1 <?php
 2 $qb = $this->_em->createQueryBuilder();
 3 
 4 $qb->select('u')
 5 	->addSelect("CONCAT(u.firstName, u.lastName)")
 6 	->from('Entity\User', 'u')
 7 	->where('u.lastName = ?1')
 8 	->setParameter(1, "Mustermann");
 9 
10 $users = $qb->getQuery()->getResult();
```

This might be necessary sometimes, since not every function or arithmetic operator can be constructed via the `Expr` class. The following aggregate functions are allowed in SELECT and GROUP BY clauses:

*   AVG
*   COUNT
*   MIN
*   MAX
*   SUM

The following functions are supported in SELECT, WHERE and HAVING clauses:

*   IDENTITY
*   ABS(arithmetic\_expression)
*   CONCAT(str1, str2)
*   CURRENT\_DATE()
*   CURRENT\_TIME()
*   CURRENT\_TIMESTAMP()
*   LENGTH(str)
*   LOCATE(needle, haystack \[, offset\])
*   LOWER(str)
*   MOD(a, b)
*   SIZE(collection)
*   SQRT(q)
*   SUBSTRING(str, start \[, length\])
*   TRIM(\[LEADING | TRAILING | BOTH\] \[“trchar” FROM\] str)
*   UPPER(str)
*   DATE\_ADD(date, days, unit)
*   DATE\_SUB(date, days, unit)
*   DATE\_DIFF(date1, date2)

Via `setParameter()` or `setParameters($array)` values can be given for placeholders within queries. In the example shown above, number placeholders are used (starting with a “?” symbol). Alternatively, a string placeholder may be used (starting with a “:” symbol):

```
 1 <?php
 2 // [..]
 3 $qb = $this->_em->createQueryBuilder();
 4 
 5 $qb->select('u')
 6 	->addSelect($qb->expr()->concat('u.firstName', 'u.lastName'))
 7 	->from('Entity\User', 'u')
 8 	->where($qb->expr()->eq('u.lastName', ':lastName'))
 9 	->setParameter("lastName", "Mustermann");
10 
11 $users = $qb->getQuery()->getResult();
```

Whatever way is preferred, one needs to stick to it within a query. Mixing is not allowed.

### 8.4 Constructing join queries

Doctrine 2 supports two different types of joins. While regular joins are needed, e.g. to limit results via a WHERE clause, so-called *fetch joins* are used to fetch related entities for further usage:

```
 1 <?php
 2 // [..]
 3 $qb = $this->_em->createQueryBuilder();
 4 
 5 $qb->select('u', 'c')
 6 	->from('Entity\User', 'u')
 7 	->leftJoin('u.contactData', 'c')
 8 	->where($qb->expr()->eq('u.lastName', '?1'))
 9 	->setParameter(1, "Mustermann");
10 
11 $users = $qb->getQuery()->getResult(); 
```

The `select('u', 'c')` makes the join a fetch join. The referenced `ContactData` object is part of the result set. However, when omitting the `'c'` in the `select` clause, the `ContactData` object is not part of the result anymore, however, it can still be used e.g. within the `where` clause:

```
 1 <?php
 2 // [..]
 3    	 
 4 $qb = $this->_em->createQueryBuilder();
 5 
 6 $qb->select('u')
 7 	->from('Entity\User', 'u')
 8 	->leftJoin('u.contactData', 'c')
 9 	->where($qb->expr()->eq('u.lastName', '?1'))
10 	->andWhere($qb->expr()->eq('c.email', '?2'))
11 	->setParameter(1, "Mustermann")
12 	->setParameter(2, "max.mustermann@example.com");
13 
14 $users = $qb->getQuery()->getResult();
```

## 9 Command line tools

Doctrine 2 ships with powerful command line support. The command line tools can broadly be divided into DBAL-related and ORM-related operations. Via the `list` command, a list of all commands available can be printed:

```
1 $ ./doctrine list
```

The `help` command-or the command parameter `--help` in conjunction with other commands-prints the instructions for a command given. For example, if we need help dealing with the `orm:info` command, we can ask for help like that:

```
1 $ ./doctrine orm:info --help
```

Also will work:

```
1 $ ./doctrine help orm:info
```

Both commands print the identical output to the console.

### 9.1 Setting up the command line tools

Before Doctrine 2 can be used on the command line, some basic configuration code is needed. The command line tools require-like the application itself-a ready-to-go database connection and entity manager-if ORM-related commands are needed.

The configuration of the command line tools first looks somewhat strange-Doctrine 2 requires that a file called `cli-config.php` exists within the folder, in which the tools are executed on the command line. If Doctrine 2 was installed using Composer, the command line tools are located in `vendor/bin`. Therefore, this is the place where a file called `cli-config.php` needs to be set up with the following basic code:

```
 1 <?php
 2 include '../../vendor/autoload.php';
 3 
 4 use Doctrine\ORM\Tools\Setup;
 5 use Doctrine\ORM\EntityManager;
 6 
 7 $paths = array(__DIR__ . "/../../entity/");
 8 $isDevMode = true;
 9 
10 $dbParams = array(
11 	'driver'   => 'pdo_mysql',
12 	'user'     => 'root',
13 	'password' => '',
14 	'dbname'   => 'app',
15 );
16 
17 $config = Setup::createAnnotationMetadataConfiguration($paths,$isDevMode);
18 $em = EntityManager::create($dbParams, $config);
19 
20 $helperSet = new \Symfony\Component\Console\Helper\HelperSet(array(
21 'db' => new \Doctrine\DBAL\Tools\Console\Helper\ConnectionHelper(
22 	$em->getConnection()
23 ),
24 'em' => new \Doctrine\ORM\Tools\Console\Helper\EntityManagerHelper(
25 	$em
26 )
27 )); 
```

The code shown above is similar to the `index.php` file used in the demo app. First, autoloading is configured, then the entity manager is instantiated. If both clients-web application and command line tools-share the same credentials, externalizing this data may be helpful.

If now the command line tools are invoked, Doctrine 2 automatically includes the `cli-config.php` file and also looks for a so-called *helper set* defined in the global namespace. The *helper set* provides the command line tools with the database connection via key `db` (needed for the DBAL commands) as well as the entity manager via key `em` (needed for the ORM commands).

### 9.2 DBAL commands

#### 9.2.1 Execute an SQL statement

SQL commands can easily be executed via the command line with Doctrine’s command line tooling. The command `dbal:run-sql` requires a single parameter, a valid SQL statement:

```
1 $ ./doctrine dbal:run-sql "SELECT * FROM users;"
```

The result of the query is printed to the console.

#### 9.2.2 Import SQL files

If one needs to execute multiple statements, importing a SQL file might be a great option via the `./doctrine dbal:import` command. It takes one or more paths to SQL files, delimited by space:

```
1 $ ./doctrine dbal:import /tmp/import-data.sql
```

### 9.3 ORM commands

#### 9.3.1 Validate persistence configuration

One of the most helpful commands is `orm:validate-schema`. It validates the current persistence configuration and also makes sure it matches the existing data schema in the database. If all is good, the following command prints a positive message to the console:

```
1 $ ./doctrine orm:validate-schema
2 > [Mapping]  OK - The mapping files are correct.
3 > [Database] OK - The database schema is in sync with the mapping files.
```

The command `orm:info` prints an overview of the application entities known to Doctrine:

```
1 $ ./doctrine orm:info
2 > Found 2 mapped entities:
3 > [OK]   Entity\Post
4 > [OK]   Entity\User
```

#### 9.3.2 The Schema Tool

With the help of the commands

*   `orm:schema-tool:create`,
*   `orm:schema-tool:drop` and
*   `orm:schema-tool:update`

one can manipulate a database data schema based on the entity persistence configuration. However, when running these commands, nothing actually happens-it’s just a “dry run”. If the commands are executed with parameter `--dump-sql` again only a dry run occurs, however, this time, the schema tool prints all SQL statements, which would otherwise have been fired against the database, to the screen. Only if one uses the parameter `--force`, the schema tool finally executes the statements:

```
1 $ ./doctrine orm:schema-tool:drop --force
```

The command shown above makes all tables and data disappear:

```
1 > Dropping database schema...
2 > Database schema dropped successfully!
```

 
| ![information](images/leanpub_information.png) || 

#### Danger! Potential loss of data!

The schema tool can delete tables and/or data. Therefore, one will make sure these commands are used with caution. |
| --- | --- |

The execution of

```
1 $ ./doctrine orm:schema-tool:create
```

creates the data structure from scratch, while

```
1 $ ./doctrine orm:schema-tool:update
```

migrates an existing data schema from status quo to match the current persistence configuration, if the existing data schema is not yet up-to-date.

#### 9.3.3 Generate commands

With the help of the command `orm:generate-proxies`, the proxy classes for the entities defined can be created, which otherwise are created by Doctrine 2 automatically when needed. Via the command `orm:generate-entities`, the entity classes itself can be generated-this is especially helpful is the persistence configuration is given via XML or YAML. Executing the command

```
1 $ ./doctrine orm:generate-entities /tmp
```

creates the entity classes in `/tmp`, or to be precise, in `/tmp/Entity`. More options for the command `orm:generate-entities` can be identified running the following command:

```
1 $ ./doctrine orm:generate-entities --help
```

With the help of the command `orm:generate-repositories`, also repository classes can be auto-generated.

#### 9.3.4 Execute a DQL command

Similar to `dbal:run-sql`, also DQL statements can easily be executed using the command `orm:run-dql`.

#### 9.3.5 Cache related commands

With the commands

*   `orm:clear-cache:metadata`,
*   `orm:clear-cache:query` and
*   `orm:clear-cache:result`

the various Doctrine caches can be purged. These commands are especially helpful when deploying a new application version. They make sure that no outdated configuration or data is used in conjunction with a new application version-usually, this would lead to unrecoverable errors.

#### 9.3.6 Converting commands

Rarely used, but very helpful are the commands `orm:convert-d1-schema` and `orm:convert-mapping`. The command `orm:convert-d1-schema` is used to transform the old Doctrine 1 persistence configuration format to the one used by Doctrine 2-very handy when upgrading an existing application. The command `orm:convert-mapping` on the other hand allows to go from one Doctrine 2 mapping format to another, e.g. from XML to YAML.

#### 9.3.7 Production-ready configuration

The following command validates if Doctrine’s configuration is ready for production usage:

```
1 $ ./doctrine orm:ensure-production-settings
```

If this is the case, it prints a positive message on the console:

```
1 > Environment is correctly configured for production.
```

A lot of configuration aspects can cause a negative result. This could be missing proxy classes created by running the proper command or missing caches. Both is considered by Doctrine 2 to be a must for usage in productive systems.

 
| ![information](images/leanpub_information.png) || 

#### Custom commands

Doctrine 2 allows to develop custom commands that can be hooked into the command line tooling. More information about this topic can be found in the [official documentation](http://docs.doctrine-project.org/en/latest/reference/tools.html#adding-own-commands). |
| --- | --- |

## 10 Caching

### 10.1 Introduction to ORM cache types

Due to its nature and the way Doctrine 2 works, applications using Doctrine 2 naturally run a bit slower compared to others. However, with good caching strategies applied, this issue can nearly completely be removed. Doctrine 2 ORM brings native support for three different types of caches: The “meta cache”, the “query cache” and the “result cache”. When setting up the entity manager, the different caches can be added to the entity manager\`s configuration. In addition, the cache instance might be used for custom values as well.

### 10.2 Caching backends

Storing cached data can be done in different so-called “caching backends”. Doctrine 2 supports multiple technologies to be used as a caching backend:

*   APC
*   Array
*   Filesystem
*   Memcached
*   Redis
*   WinCache
*   Xcache
*   ZendDataCache

Based on the situation or technologies used, one can choose between the different technologies.

#### 10.2.1 Metadata Cache

The metadata cache holds the entity mapping data given as annotations or external XML or YAML files. Caching this data means that Doctrine 2 does not need to perform reflection or XML or YAML parsing for every single request, which saves a significant amount of processing time.

When setting up the entity manager, the cache can easily be configured:

```
 1 <?php
 2 // [..]
 3 $paths = array(__DIR__ . "/../src/Entity/");
 4 $isDevMode = false;
 5 
 6 $dbParams = array(
 7 	'driver'   => 'pdo_mysql',
 8 	'user'     => 'root',
 9 	'password' => '',
10 	'dbname'   => 'app',
11 );
12 
13 $config = Setup::createAnnotationMetadataConfiguration(
14 	$paths, $isDevMode
15 );
16 
17 $config->setMetadataCacheImpl(
18 	new \Doctrine\Common\Cache\FilesystemCache('/tmp/doctrine2')
19 );
20 
21 $em = EntityManager::create($dbParams, $config);
```

In the configuration shown above, we tell Doctrine 2 to cache meta data locally in the filesystem-we could use other caching backends here as well. The caching path needs to be given when using the `FilesystemCache`. Next time, when entities are processed, Doctrine 2 starts setting up a somewhat cryptic files & folders structure in the caching path given. Luckily, one doesn’t need to care about it-Doctrine 2 takes care of all things caching. We only need to make sure that the caching path given is writable to Doctrine 2. When caching via Memcached or Redis, these services need to be up and running and accessible to Doctrine 2 as well. If not, an exception will be raised.

#### 10.2.2 Query Cache

The query cache ensures that DQL statements need to be translated into SQL only once. This again speeds up a Doctrine 2 application significantly:

```
 1 <?php
 2 // [..]
 3 $paths = array(__DIR__ . "/../src/Entity/");
 4 $isDevMode = false;
 5 
 6 $dbParams = array(
 7 	'driver'   => 'pdo_mysql',
 8 	'user'     => 'root',
 9 	'password' => '',
10 	'dbname'   => 'app',
11 );
12 
13 $config = Setup::createAnnotationMetadataConfiguration($paths, $isDevMode);
14 $cachingBackend = new \Doctrine\Common\Cache\FilesystemCache('/tmp/doctrine2');
15 $config->setMetadataCacheImpl($cachingBackend);
16 $config->setQueryCacheImpl($cachingBackend);
17 $em = EntityManager::create($dbParams, $config);
```

In the configuration shown above, we first set up a general caching backend which now powers both, the metadata cache and the query cache.

#### 10.2.3 Result Cache

Last but not least, there is the result cache. Using a result caching prevents executing the same queries against the database again and again:

```
 1 <?php
 2 // [..]
 3 $paths = array(__DIR__ . "/../src/Entity/");
 4 $isDevMode = false;
 5 
 6 $dbParams = array(
 7 	'driver'   => 'pdo_mysql',
 8 	'user'     => 'root',
 9 	'password' => '',
10 	'dbname'   => 'app',
11 );
12 
13 $config = Setup::createAnnotationMetadataConfiguration($paths, $isDevMode);
14 $cachingBackend = new \Doctrine\Common\Cache\FilesystemCache('/tmp/doctrine2');
15 $config->setMetadataCacheImpl($cachingBackend);
16 $config->setQueryCacheImpl($cachingBackend);
17 $config->setResultCacheImpl($cachingBackend);
18 $em = EntityManager::create($dbParams, $config);
```

Via method `setResultCacheImpl()`, the result cache now is ready for action. In contrast to the two other caching types, one has to actively tell Doctrine 2 to cache results for a query given:

```
1 <?php
2 
3 // [..]
4 $query = $em->createQuery($dqlString);
5 $query->useResultCache(true);
```

Now, the result is cached.

## 11 Advanced Topics

### 11.1 Zend Framework 2 integration

The easiest way to use to Doctrine 2 with Zend Framework 2 (ZF2) is a Composer based installation. The ZF2 module [doctrine-orm-module](https://github.com/doctrine/DoctrineORMModule) not only ships the glue code to make both libraries work together, but also ensure that the Doctrine 2 library itself is downloaded and installed in an existing ZF2 application. One simply needs to add the following line to the `require` block of the projects’ `composer.json`:

```
1 "doctrine/doctrine-orm-module": "dev-master"
```

Above the `require` block the following line must also be added:

```
1 "minimum-stability": "alpha"
```

If this configuration is missing, Composer might refuse to install the module. In fact, with this configuration, we tell Composer to install even non-stable modules.

The following commands start the download and the installation process:

```
1 $ php composer.phar update
```

As one can see, a whole bunch of other ZF2 modules and additional libraries are downloaded.

Last but not least two ZF2 modules must be activated via the `application.config.php`:

```
 1 <?php
 2 return array(
 3 	'modules' => array(
 4 		'Application',
 5 		'DoctrineModule',
 6 		'DoctrineORMModule'
 7 	),
 8 	'module_listener_options' => array(
 9 		'config_glob_paths'    => array(
10 			'config/autoload/{,*.}{global,local}.php',
11 		),
12 		'module_paths' => array(
13 			'./module',
14 			'./vendor',
15 		),
16 	),
17 );
```

The modules register several services in Main Service Manager, all starting with the label “doctrine”, e.g. `doctrine.cache.apc` and `doctrine.sqlloggercollector.ormdefault`.

The entity manager can be obtained using a long-winded label:

```
1 <?php
2 // [..]
3 $this->getServiceLocator()->get('doctrine.entitymanager.orm_default');
```

But before this works, some additional configuration is need. Doctrine 2 needs to know where the entity classes are located and what the caching strategy looks like. The following example from the `module.php` tells Doctrine that the mappings are given as annotation, the entities are located in `__DIR__ . '/../src/Application/Entity'` and caching takes place via PHP arrays:

```
 1 <?php
 2 // [..]
 3 'doctrine' => array(
 4 	'driver' => array(
 5 		'my_annotation_driver' => array(
 6 			'class' => 'Doctrine\ORM\Mapping\Driver\AnnotationDriver',
 7 			'cache' => 'array',
 8 			'paths' => array(__DIR__ . '/../src/Application/Entity')
 9 		)
10 	)
11 )
12 // [..]
```

To allow other ZF2 modules to provide entities to the application, a so-called “Driver Chain” allow to combine multiple entity sources even with different mapping formats and caching strategies:

```
 1 <?php
 2 // [..]
 3 'doctrine' => array(
 4 	'driver' => array(
 5 		'my_annotation_driver' => array(
 6 			'class' => 'Doctrine\ORM\Mapping\Driver\AnnotationDriver',
 7 			'cache' => 'array',
 8 			'paths' => array(__DIR__ . '/../src/Application/Entity')
 9 		),
10 		'orm_default' => array(
11 			'drivers' => array(
12                 'Application\Entity' => 'my_annotation_driver'
13             )
14         )
15 	)
16 )
17 // [..]
```

Now the database connection must be configured. Usually, a dedicated config file in the `autoload` folder is used, e.g. `db.local.php`:

```
 1 <?php
 2 return array(
 3 	'doctrine' => array(
 4 		'connection' => array(
 5 			'orm_default' => array(
 6 				'driverClass' => 'Doctrine\DBAL\Driver\PDOMySql\Driver',
 7 				'params' => array(
 8 					'host'     => 'localhost',
 9 					'port'     => '3306',
10 					'user'     => 'username',
11 					'password' => 'password',
12 					'dbname'   => 'database',
13 				)
14 			)
15 		)
16 	),
17 );
```

Once done, we can start dealing with entities (e.g. a `Product` entity) through Doctrine 2:

```
 1 <?php
 2 namespace Application\Entity;
 3 
 4 use Doctrine\ORM\Mapping as ORM;
 5 
 6 /**
 7  * @ORM\Entity
 8  * @ORM\Table(name="product")
 9  */
10 class Product
11 {
12 	/**
13 	* @ORM\Id @ORM\Column(type="integer")
14 	* @ORM\GeneratedValue
15 	*/
16 	protected $productId;
17 
18 	/** @ORM\Column(type="string", nullable=true) */
19 	protected $name;
20 
21 	/** @ORM\Column(type="integer") */
22 	protected $stock;
23 
24 	/** @ORM\Column(type="string", nullable=true) */
25 	protected $description;
26 
27 	/** @ORM\Column(type="string", nullable=true) */
28 	protected $features;
29 
30 	public function setDescription($description)
31 	{
32 		$this->description = $description;
33 	}
34 
35 	public function getDescription()
36 	{
37 		return $this->description;
38 	}
39 
40 	public function setFeatures($features)
41 	{
42 		$this->features = $features;
43 	}
44 
45 	public function getFeatures()
46 	{
47 		return $this->features;
48 	}
49 
50 	public function setProductId($productId)
51 	{
52 		$this->productId = $productId;
53 	}
54 
55 	public function getProductId()
56 	{
57 		return $this->productId;
58 	}
59 
60 	public function setName($name)
61 	{
62 		$this->name = $name;
63 	}
64 
65 	public function getName()
66 	{
67 		return $this->name;
68 	}
69 
70 	public function setStock($stock)
71 	{
72 		$this->stock = $stock;
73 	}
74 
75 	public function getStock()
76 	{
77 		return $this->stock;
78 	}
79 }
```

From a controller, a finder method provided by a repository can be accessed like this:

```
1 <?php
2 // [..]
3 $this->getServiceLocator()->get('doctrine.entitymanager.orm_default')
4 	->getRepository('Application\Entity\Product')
5 	->findOneByProductId($id);
6 // [..]
```

The Doctrine 2 command line tools are available as well. One needs to bring up a command line and change to the project’s root folder:

```
1 $ php vendor/bin/doctrine-module orm:validate-schema
```

### 11.2 Native SQL statements

Doctrine 2 ships with a special class called `NativeQuery` that allows to execute native SQL select statements and to map the results returned to entity objects. What usually works out-of-the-box with Doctrine 2, can be implemented by hand in cases where native queries are needed or where they are the better solution to a problem. `NativeQuery` allows to retrieve “raw data” and then work with entity objects in the following. The [official documentation](http://docs.doctrine-project.org/en/latest/reference/native-sql.html) holds further information about how to properly implement native SQL statements.

Lastly, in general, one needs to remember that it’s always possible to execute arbitrary SQL statements via the underlying database connection:

```
1 <?php
2 // [..]
3 $em->getConnection()->exec('DELETE FROM posts');
```

While it is possible, it should always be the last option. It bypasses the Entity Manager and might produce hard-to-debug issues and data inconsistencies.

### 11.3 Doctrine 2 Extensions

While Doctrine 2 already ships with tons and tons of features, there is even more. In the [Doctrine 2 extension repository](https://github.com/l3pp4rd/DoctrineExtensions) on GitHub, one will find several extensions with solutions to typical problems, which otherwise must be solved individually by each application developer again and again:

*   Tree: Automates the tree handling process and adds some tree specific functions on repositories.
*   Translatable: Gives a very handy solution for translating records into different languages.
*   Sluggable: Takes a specified field from an entity and makes it compatible for URLs.
*   Timestampable: Updates date fields on create, update and even property change.
*   Blameable: Updates string or reference fields on create, update and even property change with a string or object (e.g. user).
*   Loggable: Helps tracking changes and history of objects, also supports version management.
*   Sortable: Makes any entity sortable.
*   Translator: Supports handling translations.
*   Softdeleteable: Allows to mark entities as deleted, without physically deleting them.
*   Uploadable: Provides file upload handling to entity fields.
*   References: Supports linking entities in Documents and visa versa.