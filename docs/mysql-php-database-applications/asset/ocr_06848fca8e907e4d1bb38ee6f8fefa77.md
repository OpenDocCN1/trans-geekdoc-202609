![](bbox=[0.102, 0.093, 0.187, 0.163])

The best place to begin the process of getting NuSOAP is on the Web site of Dietrich Ayala (http://dietrich.ganx4.com/nusoap/). His site includes links to the latest version of NuSOAP, as well as links to documentation, mailing lists, and other resources for developers and architects.

# The essence of NuSOAP

NuSOAP is a series of classes. You copy the downloaded files (most of them .php files) to your include directory and then make reference to them in your own PHP classes. The NuSOAP classes take care of such work as creating SOAP client and server objects and managing the transmission of SOAP messages among those objects. The NuSOAP classes even take care of something we discussed earlier in this chapter: the encoding of values into properly structured XML.

For the most part, you can think of the NuSOAP classes as black boxes. You just stick the PHP files in your include directory and then cease worrying about them. All you have to do is be aware, as you're writing PHP programs that you want to act as Web-service providers or consumers, that you have some new classes available to you.

Suppose you want to build a server. In other words, you want to make a PHP function available as a Web service. Once you've added the required include statement (as follows) you have a four-step process ahead of you.

```
require_once('nusoap.php');
```

+   1. Create a server object. All you need to do is set a variable equal to a soap_server object (soap_server being one of the classes made available by your inclusion of NuSOAP). It's easy:
+   
+   $server = new soap_server;

+   2. Register one of your local functions with that new soap_server object. Again, no problem. You simply invoke the register() function of the soap_server object, specifying one of your local functions as the sole argument. The complete syntax looks like this:
+   
+   $server->register('getInseam');

+   3. Define a function called getInseam(). This can contain whatever code you want. Presumably, in this case, it accesses a database to retrieve a named party's inseam measurement and then returns a value and unit. The skeleton of the function looks something like this:
+   
+   function getInseam($name) {
+   // Function code...
+   }