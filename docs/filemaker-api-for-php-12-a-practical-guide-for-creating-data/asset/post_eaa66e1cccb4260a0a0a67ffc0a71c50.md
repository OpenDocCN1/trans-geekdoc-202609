
# FileMaker

# PHP

# PHP Difference

| Filter() | PHP | Result |
|---|---|---||
| Filter("(858)-794-1530") | preg_replace("[0-9]+",","", "(858)-794-1530") | 858794153 |
| GetDate("12/14/2010") | date("m/d/Y") | 12/14/2010 |
| GetNumber("ABC123") | preg_replace("[0-9]+",","", "ABC123") | 123 |
| GetText("ABC123") | preg_replace("[a-zA-Z]+",","", "ABC123") | ABC |
| GetTime("08:00") | date("h:i:s") | 08:00 |
| GetTimeStamp("12/14/2010 08:00") | date("m/d/Y H:i:s") | 12/14/2010 08:00 |
| GetURLencode("tduell@formulations.com") | urlencode("tduell@formulations.com") | tduell%40formulations.com |
| Hour("9.5") | int(9) | 9 |
| Int(Random(10)) | rand(10) | 5 |
| IsValid("22/09/2010") | strpos("22/09/2010",1) | 0 |
| Left Text("Duell") | substr("Duell",0,4) | Todd |
| LeftWords("Todd Duel") | implode(",",array_str_word_count("Todd Duel",1),0,1) | Todd |
| Length("Duell") | strlen("Duell") | 5 |
| Lower Text("Duell") | strtolower("Duell") | duell |
| Log(2) | log(2) | 1 |
| Log(100) | log(100) | 2 |
| MiddleText("Duell",2,3) | substr("Duell",1,3) | odd |
| MiddleWords("Todd Duel San Diego;3") | implode(",",array_str_word_count("Todd Duel San Diego",1,2),1) | San |
| Minute("08:00") | date("i") | 0 |
| Mod(5,3) | 5%3 | 2 |
| Month("12/14/2010") | date("m") | 5 |
| MonthName | date("F") | December |
| PatternCount("Todd;d") | substr(strtolower("Todd"),"d") | |
| Pi | pi | 3.14 |
| Position("Duell";1,1) | strpos("Duell",1,1) | 1 |
| Proper("Duell") | ucwords("Duell") | Todd |
| Random | rand(1000) | 0.15 |
| Replace("Todd Duel:",("Todd Duel":1)) | str_replace("Todd Duel:","Tim","Tim Duel",0) | Tim |
| Length("Tim") | | |
| Right("Todd Duel",5) | substr("Todd Duel",-5) | Duel |
| RightWords("Todd Duel",1) | implode(",",array_str_word_count("Todd Duel",1),1) | Duel |
| Round(10,12.5) | round(10,12.5) | 10.1 |
| Seconds(08:00:25) | date("s") | 25 |
| Sign(-10) | gmp_sign("-10") | -1 |
| Sqrt(10) | sqrt(10) | 3.16 |
| StDev("2;4;6") | $values = array("2","4","6"); $result = stdev_standard_deviation($values); | |
| Substitute("Todd Duel";"B":"B") | str_replace("B","B","Todd Duel") | Buell |

| FileMakerName | PHP | Result | PHP Reference |
|---|---|---|---|
| Sum(FieldName) | $values = array(2,4,6); echo $result = array_sum($values); | 12 | http://us.php.net/manual/en/function.array-sum.php |
| Tan(13) | tan(13); | 0.13 | http://us.php.net/manual/en/function.tan.php |
| Time(8;00,00) | date("H:i:s"); | 8:00:00 | http://us.php.net/manual/en/function.date.php |
| Timestamp(Date(12/14/2010); | date("m/d/Y H:i A"); | 12/14/2010 6:30 AM | http://us.php.net/manual/en/function.date.php |
| Trim("Todd Duel") | trim("Todd Duel"); | Todd Duel | http://us.php.net/manual/en/function.trim.php |
| Truncate(1.2345; 1) | floor(1.2345*pow(10,1))/10 | 1.2 | http://www.php.net/manual/en/function.intval.php |
| Upper("Todd Duel") | strupper("Todd Duel"); | TODEL | http://us.php.net/manual/en/function.strtoupper.php |
| ValueCount("Todd Duel") | $values = array("Todd", "Duel"); echo $result = count($values); | 2 | http://us.php.net/manual/en/function.count.php |
| WeekOfYear("12/14/2010") | date("W"); | 51 | http://us.php.net/manual/en/function.date.php |
| WordCount("Todd Duel") | str_word_count("Todd Duel", 0); | 2 | http://us.php.net/manual/en/function.str_count.php |
| Year("12/14/2010") | date("Y"); | 2010 | http://us.php.net/manual/en/function.date.php |

# Other Methods — PHP/ODBC, ASP, JSP

There are quite few options available for publishing data to the web with FileMaker. FileMaker API for PHP is not the only option. ODBC (from Claris/FileMaker) and JSP (from Lasso) came years ago, but were proprietary technologies that didn't keep up with the standards. PHP is not necessarily the best option depending on your requirements. Before you embark down the road of building your website you need to know the pros and cons of each technology. Therefore I will not be providing examples of installing, configuring, or utilizing these technologies. They are outside the scope of this book. If you would like more information regarding the use of these you can visit our web site at www.formulations.com.

# PHP/ODBC

PHP can utilize an ODBC driver to access FileMaker Server. This is similar to MySQL. Therefore, if you are comfortable with MySQL you may find that using the standard driver will get you up and running without modifying your code (with the exception of specific functions).

Server Operating System: Windows or OS X

Application Server: IIS or Apache

Driver: ODBC

Pros:
- Allows you to use standard SQL commands to access the database. This is a very traditional approach that many people are comfortable using.
- Dreamweaver has built-in support for ODBC, and SQL. You would be using the settings since there is no built-in configuration for FileMaker Pro.
- FileMaker provides the ODBC drivers for free.
- You can utilize a lot of the PHP materials and third party products without having to do much work to convert the code to the FileMaker API for PHP.
- You can display images from a container using PHP.
- Apache is free and can be installed on either Windows or OS X.
- IIS Server comes with Windows Server and has a nice user interface to configure the server.

Cons:
- Installing the ODBC driver can be a hassle.
- The ODBC driver can be a major issue in the long run when you upgrade the OS or FileMaker Server. FileMaker has switched ODBC manufacturers since is not capable of providing technical support if there is a problem. If anything is broken you may have to wait a long, long time before it gets fixed.
- Using an ODBC driver is just one more layer of technology to develop.
- The ODBC driver is not as fast as the FileMaker API for PHP.
- The Windows software and CALS are not free. Using Windows will be a more expensive approach.
- Apache requires manual configuration.

# ASP

Application Server Pages are a Windows technology that runs IIS Server. ASP and ASP.NET have been available for a long time and have a strong following on the Internet.

Server Operating System: Windows

Web Server: IIS

Application Server: IIS

Driver: ODBC

Pros:
- Allows you to use standard SQL commands to access the database. This is a very traditional approach that many people are comfortable using.
- Dreamweaver has built-in support for ODBC, and SQL. You would be using the ASP settings.
- FileMaker provides the ODBC drivers for free.
- You can utilize a lot of the ASP materials and third party products.
- IIS Server comes with Windows Server and a nice user interface to configure the server.
- We have complete instructions to use ASP on our web site at www.formulations.com.

Cons:
- You cannot run scripts with the ODBC driver.
- You cannot display images from a container field using the ODBC driver.
- Installing the ODBC driver can be a hassle.
- The ODBC driver can be a major technical issue in the long run when you upgrade the OS or FileMaker Server. FileMaker has switched ODBC driver manufacturers several times and is not capable of providing OEM technical support if there is a problem. If is broken you may have to wait a long, long time before it feels fixed.
- Using an ODBC driver is just one more layer of technology to deal with.
- The ODBC driver is not as fast as the FileMaker API for PHP.
- I have not been successful at using ASP.NET to work with FileMaker Server or the supplied ODBC drivers.
- The Windows software and CALS are not free. Using Windows will be a more expensive approach.

# JSP

Java Pages is a Sun technology, recently taken by ORACLE, that runs using the Tomcat server. In many cases users have their html pages processed by Apache and their jsp pages processed by Tomcat to optimize performance. JSP technology has been available for a long time and has a strong following on the Internet.

Server Operating System: Windows or OS X

Web Server: Apache or Tomcat

Application Server: Tomcat

Driver: JDBC

Pros:
- Allows you to use standard SQL commands to access the database.
- Dreamweaver has built-in support for ODBC, and SQL.
- You would be using the ASP settings.
- FileMaker provides the ODBC drivers for free.
- You can utilize a lot of the ASP materials and third party products.
- IIS Server comes with Windows Server and a nice user interface to configure the server.
- We have complete instructions to use ASP on our web site at www.formulations.com.
