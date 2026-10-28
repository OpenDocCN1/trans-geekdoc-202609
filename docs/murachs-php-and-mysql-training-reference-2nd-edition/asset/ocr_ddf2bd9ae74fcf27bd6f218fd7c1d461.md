# How to fix a possible problem
with the time zone

When you install XAMPP, it usually sets the time zone that’s used by PHP correctly. However, in some cases, XAMPP doesn’t set the time zone correctly. If that happens, you’ll get an error when you try to use PHP to get the current date and time.

To check whether the time zone is set correctly on your system, you can use the first procedure in figure B-7 to run the specified application. If you don’t see an error on the first page of this application, the time zone is set correctly. As a result, you don’t need to take any further action.

However, if the first page of this application displays an error, you need to set the time zone as shown in the second procedure. To do that, you need to open the php.ini file in a text editor such as TextWrangler and set the time zone. For a list of supported time zones, you can view the PHP documentation that’s available from the URL specified in this figure.