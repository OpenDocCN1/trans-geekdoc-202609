Before discussing the particulars of this code, I’d like to point out that there is no visual way to write a cookie using Dreamweaver, so you have to write the code yourself. While Dreamweaver can help you develop dynamic Web sites, you have to be willing to do some hand-coding if you really want to build dynamic sites. If you’ve been studying the code, you can probably already understand how the code works.

Though the syntax varies markedly when you compare ASP, ColdFusion, and PHP, all three sets of code work the same way. They create two new cookie variables, one named firstName and the other named lastName. As before, we are naming two completely different variables with the same names (QueryString.firstName and Cookies.firstName, with a comparable pair for the last name), but their different scopes prevent any possible confusion. Both specify expiration dates (30 days from today in ASP, never in ColdFusion, and one day for PHP). Finally, all three specify the new cookie variable’s value as the current value of QueryString.firstName and QueryString.lastName.

In other words, the values of the new cookie variables are dynamically set. Not only can you set variables to static, hard values, such as Cat or Dog, but you can also create variables to hold contents drawn from other variables. Here, the cookie variables are dynamically set with the contents of the querystring/URL variables.

+   4) Back in design view, create a new paragraph below the existing one, and type Check cookie. Link the word cookie to a page named test_form_processor_cookies.asp. Save and upload this page.

```
<%@LANGUAGE="VBScript" CODEPAGE="1252"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-t...
<html>
<%
Response.Cookies("firstName") = Request.QueryString("firstName")
Response.Cookies("firstName").Expires = Date+30
Response.Cookies("lastName") = Request.QueryString("lastName")
Response.Cookies("lastName").Expires = Date+30
%>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Untitled Document</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
</head>
```