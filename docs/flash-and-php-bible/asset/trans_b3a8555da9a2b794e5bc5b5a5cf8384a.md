

## 开发 Flash 点击计数器

With the PHP done, you can move onto the Flash development, which consists of an all ActionScript application.

The hit counter needs to first call the PHP file, which serves two purposes. The first is calling the PHP file to load and increment the count. The second purpose is to return the new value, which is passed in to a dynamic text field.

The first part is to assign the phpFile variable, which is a reference to the hit counter file located on the server.

```
var phpFile:String = " http://localhost/ch10/hitCounter/";
```

The first function to build is the loadHitCounter(), which is responsible for calling the server and assigning the response handler.

```
function loadHitCounter():void
{
    var urlRequest:URLRequest = new URLRequest(phpFile);
    var urlLoader:URLLoader = new URLLoader();
    urlLoader.addEventListener(Event.COMPLETE, handleServerResp);
    urlLoader.load(urlRequest);
}
```

After the response is loaded, the handleServerResp() is called passing along the loaded data. This data is then sent to the URLVariables class to pull out the resp property. This property is where the current count is located.

```
function handleServerResp(e:Event):void
{
    var loader:URLLoader = URLLoader(e.target);
    var variables:URLVariables = new URLVariables(loader.data);
    var count:uint = variables.resp;
    ...
}
```

The count is finally placed in the dynamic text field, which is not formatted in this example, but you can easily add this on your own.

```
var txt:TextField = new TextField();
txt.selectable = false;
txt.width = 200;
txt.text = count + " visitors";
}
```

The absolute last line of code in the ActionScript is the call to the loadHitCounter function, which kicks it all off.

```
loadHitCounter();
```

## 摘要

In this chapter you learned the elements of developing and designing an application. Then once you understood how the application should be constructed you built a chat client using PHP and Flash.

In the next section you learned how to develop a Flash-based photo gallery with dynamic category and image support using XML.

The last section was devoted to developing other applications using Flash, PHP, and MySQL to better understand the concepts.

You should now have a good idea how to build robust applications that take advantage of dynamic data for updating and functionality.

## 第 12 章
### 开发现实世界应用程序

- Using PayPal in Flash
- Developing a shopping cart
- Searching Amazon
- Developing a photo gallery

In this chapter, you learn about developing complete applications from the ground up. The focus is on class-based designs that you can easily update later on. The main aspect of this chapter will be how to use Flash and PHP to develop these applications.

This chapter is broken up into four applications: a PayPal cart, custom shopping cart, Amazon searcher, and a flickr photo gallery searcher. Each application section starts with the PHP code and continues with the ActionScript. Building an application like this makes it easier to test as you build and reduces the amount time in the development process.

The examples in this chapter are built using custom classes, which are covered in Chapter 9. If you haven't read that chapter yet, I strongly recommend you do so before continuing on in this chapter. Of course, if you have used classes in the past, then by all means continue on.

### 了解现实世界应用程序

A real-world application is one that has been designed, tested, and deployed with the intention that other users will be using it.

Just like in a real application there will be some sections that use a third-party Application Programming Interface (API) to load in and search data. When working with an API it is common to find a list of the methods and calls allowed as shown in Figure 12.1.

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_311_0.png)

An open API doesn't always mean anyone can gain access. For example, with flickr you are required to pass along a key that authorizes a request. This is not only to lock down certain aspects of an API, but also stops spamming and automated responses that could result in the API being disabled.

The Amazon and flickr examples in this chapter use those APIs, but the first thing to look at are the rules and requirements for the API that you are using.

### 在 Flash 中使用 PayPal

Working with PayPal in Flash is similar to HTML because PayPal offers a common set of connection and access abilities. However, one advantage to developing the solution in Flash is the ability to enhance the user experience as Flash offers more fluid communications with other services because it does not need to reload the entire page or open any additional windows.

### 注册 PayPal Premier

Before you begin to write the code for interfacing with PayPal, create a PayPal Premier account, which you can use to track your sales and authenticate your requests. It only takes a few minutes to set up an account, and it doesn’t cost anything.

To set up a PayPal Premier account, follow these steps:

- 1. In your Web browser, navigate to www.paypal.com. Choose Get Started → Account Types.
- 2. On the PayPal Account Types page, click Sign Up Now. The Choose Account Type page appears.
- 3. Under Premier Account, click Start Now. In the Create a PayPal Account form that appears (see Figure 12.2), type the requested information.
- 4. After you submit your form, you will received a confirmation e-mail. You must respond to the e-mail to activate your account.
- 5. Log in and test your new account.

> **注意** Remember, you must activate the account via e-mail before you can use it.

图 12.2
The PayPal account registration screen

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_312_0.png)

At this point, you should have a working PayPal login. Using the account you just registered for you can login to PayPal and begin setting up the account specifics.

> 注意 The system requires a login and password to generate content. However, in order to submit a data request you only need to provide your e-mail address. This is used to ensure the request is correct. At no time should you place your PayPal password in this form.

Click the Merchant link on the top of the page to visit the Buy Now generator page. The other options on the first screen are not important at this point. Finally, click Create Button, which will move to the next page where the HTML code is for the Buy Now button. Copy the HTML code that is generated by PayPal for the Buy Now buttons.

This code is used to build the Flash example. Following is the sample code copied from PayPal's merchant system generator that you just visited.

```
<form action="https://www.paypal.com/cgi-bin/webscr"
method="post">
<input type="hidden" name="cmd" value="_xclick">
<input type="hidden" name="business" value="{email_address}">
<input type="hidden" name="item_name" value="{item_name}">
<input type="hidden" name="item_number" value="{item_number}">
<input type="hidden" name="amount" value="{item_amount}">
<input type="hidden" name="currency_code" value="USD">
<input type="hidden" name="weight" value="1">
<input type="hidden" name="weight_unit" value="lbs">
<input type="hidden" name="lc" value="US">
</form>
```

> 注意 Ensure that you don't have Button Encryption enabled; doing so makes it impossible to grab the necessary information to build the Flash button.

As you can see, the code generated for the HTML form has all of the necessary variables that will be used to create a Flash button. The next step is to build the Flash code that will make the Buy Now button for the application.

Here is the ActionScript code needed to interface with PayPal, as you can see this code is very similar to the existing HTML code you generated on the PayPal page. The first part to focus on is the url variables that are responsible for building the POST data. This POST data is passed along to PayPal when the user clicks Buy Now.

```
// Paypal variables
var pp_cmd:String = "_xclick";
var pp_business:String = "store@example.com";
var pp_item_name:String = "sample product";
var pp_item_number:String = "0001";
var pp_amount:String = "24.99";
var pp_currency:String = "USD";
var pp_weight:String = "1";
var pp_weight_unit:String = "lbs";
var pp_location:String = "US";
```

