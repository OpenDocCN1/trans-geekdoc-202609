
- 13. If no matching order was found, indicate that:

```
} else { // No matching order!
$error = 'No matching order could be found.';
} // End of transaction ID IF-ELSE.
```

- 14. Report any messages or errors:

```
echo '<h3>Order Shipping Results</h3>';
if (isset($message)) echo "<p>$message</p>";
if (isset($error)) echo "<p class=\"error\">$error</p>";
```

Figures 11.15 and 11.16 show these lines in action.

![](img/4f47e47c67bd619ac73250f11c9fc7ce_369_0.png)

Figure 11.15

![](img/4f47e47c67bd619ac73250f11c9fc7ce_369_1.png)

Figure 11.16

- 15. Complete the form submission IF:

```
} // End of the submission IF.
```

- 16. Save the page and test it in your Web browser.

> **note**
> You'll need to use relatively recent orders to test this process, because the authorization for older orders may have since been revoked.

## INDEX

### NUMBERS
- 128-bit security, explained, 39
- 256-bit security, explained, 39
- 127.0.0.1, connecting to MySQL from, 36

### SYMBOLS
- ` (backticks), using with SQL commands, 51
- ^ (caret), using with mod_rewrite, 176
- , (comma), using between table names, 352
- {} (curly brackets), using with conditionals, 65
- $ (dollar sign)
  - omission from variables, 265
  - using with mod_rewrite, 177
- || (double pipe), using in PHP conditionals, 211
- () (parentheses)
  - using, 70
  - using with mod_rewrite, 176
  - using with stored procedures, 189
- + (plus) sign, using with mod_rewrite, 176
- ? (question mark), using with mod_rewrite, 176
- " (quotation marks), using in forms, 74
- ; (semicolon), ending stored procedure queries with, 198
- / (slash), using with mod_rewrite, 176
- [] (square brackets), using with mod_rewrite, 176

### A
- access control measures, implementing, 31
- access privileges system, using in MySQL, 36
- add_customer() stored procedure, 272
- add_inventory.php script, creating, 331
- add_order() procedure
  - failure of, 293
  - features of, 266
  - invoking for credit cards, 292
- add_other_products.php script, creating, 317
- add_pdf.php script, creating, 123
- add_specific_coffees.php script, creating, 326
- add_to_cart() stored procedure, creating, 231–232
- addresses, validating for shipping, 269
- administration directories. See also directories
  - naming, 53
  - password protecting, 173–174
- administration pages
  - creating footer for, 313
  - creating header for, 311–312
  - creating home page for, 313
  - creating template for, 310–313
  - placing in subdomain, 172
  - primary links, 310
  - removing background images from, 311
  - requiring authentication, 309
  - suckerfish approach, 310, 313
  - updating create_form_input(), 315–316
  - use of jQuery with, 309
- administrator scripts
  - adding coffee products, 325–330
  - adding non-coffee products, 316–325
- administrator user, creating, 37
- administrators
  - creating, 106–107
  - including in Knowledge is Power site, 50
- AIM (Advanced Integration Method), 296–298
- allow rules, checking, 174–175
- ALTER privileges, limiting in MySQL, 37
- ALTER ROUTINE syntax, using with stored procedures, 221–222
- American Express cards
  - number format for, 289
  - testing numbers for, 306
- anti-virus software, using, 31–33
- Apache
  - DocumentRoot directive, 34
  - using mod_rewrite feature, 175–177
  - Web site, xv
- ApacheBench Web site, 22
- APC (Alternative PHP Cache), 23
- APD (Advanced PHP Debugger), 24
- array of pages, creating for HTML template, 65
- attacks
  - blind, 45
  - brute force, 42–43
  - CSRF (Cross-Site Request Forgery), 44–46
  - DoS (Denial of Service), 42
  - LFI (Local File Inclusion), 44
  - Malicious File Execution, 44
  - RFI (Remote File Inclusion), 44
  - session fixation, 105
  - SQL Injection, 43
  - supplying problematic data, 35
  - XSS (Cross-Site Scripting), 41–42
- AUTH_ONLY status, using with orders, 350
- authentication, requiring, 309
- Authorize.net payment gateway. *See also* checkout process;
- PayPal accounts
  - Advanced Integration Method values, 296–297
  - defining merchant information, 296
- **explode()** function, 298
- features of, 15, 251–252
- response code, 299
- response fields, 299
- testing, 252–253
- testing accounts in, 296

### B
- background images, removing from admin pages, 311
- backticks (`), using with SQL commands, 51
- backtrack information, adding for config file, 59
- benchmarks, running on Web servers, 22–23
- billing address, verifying, 16
- billing information. *See also* checkout process
  - GET part of script for, 282
  - POST part of script for, 282
  - validating form data, 288–293
- **$billing_errors** array, creating, 288–289
- **billing.html** page
  - adding progress indicator to, 285
  - creating, 285–288
- **billing.php** script
  - creating, 283–284
  - creating view file for, 284–288
  - error-handling function, 293
  - failure of **add_order()** procedure, 293
  - reaching **trigger_error()** point, 293
  - updating, 300–302
- binding variables, 327, 332
- blind attack, example of, 45
- bound value types, using with prepared statements, 187
- **browse.php** script
  - creating, 204–206, 210–212
  - **list_coffees.html** file, 212
  - **list_products.html** file, 212
  - **noproducts.html** file, 212
  - versus **shop.php** script, 210
- browser
  - creating user interface in, 7
  - redirecting, 79–81
- brute force attacks, 42–43
- business goals
  - achieving, 3–4
  - listing, 4

### C
- caching, applying, 23
- CAPTCHA system, integrating, 45
- Card Security Code (CSC), 286
- Card Verification Value (CVV), 16
- cardholder data, protecting, 31–32
- caret (^) using with mod_rewrite, 176
- cart page versus wish list, 246
- **cart.html** file, creating, 240–243
- **cart.php** script, creating, 236–240
- carts
  - adding products to, 231–232, 237–238
  - beginning checkout process for, 243
  - calculating shipping, 247–249
  - clearing, 259
  - creating PHP script for, 236–240
  - creating views for, 240–243
  - displaying contents of, 274–278
  - **emptylist.html** view, 245–247
  - fetching contents of, 233–234
  - helper functions for, 234–236
  - making, 236
  - model aspect of, 230
  - moving products into, 238
  - MVC approach for, 230
  - removing products from, 232, 238
  - retrieving contents of, 273
  - stored procedures, 230–234
  - updating, 232–233
  - using **DELIMITER** with, 231–234
- catalog
  - creating “no products” view, 216–217
  - creating stored procedures, 201–204
  - highlighting sales, 224–229
  - indicating availability, 217–219
  - populating tables using SQL, 193–196
  - preparing database for, 192–193
  - showing sale prices, 219–224
  - using stored procedure queries, 196–201
- categories
  - creating view files for, 206–209
  - fetching information for, 213
  - shopping by, 204–209
- **category.php** script
  - creating, 115–118
  - **list()** function, 117
- CCV acronym, 286
- certificates
  - expense of, 40
  - multiple domain, 40
  - purchasing, 39
  - single domain, 40
- certificates (continued)
  - using with SSL, 38–39
  - warnings about, 40
  - warranties for failure of, 39–40
- change requests, handling, 5
- checkout process. See also Authorize.net payment gateway; billing information; payment gateways; shipping information
  - add_customer() stored procedure, 272
  - adding customers, 260–261
  - adding orders, 262–265
  - adding transactions, 259–261
  - Authorize.net payment gateway, 251–252
  - beginning for carts, 243
  - clearing shopping cart, 259
  - creating HTML template for, 253–255
  - creating test accounts, 252–253
  - fetching order total, 261
  - fetching shipping cost, 261
  - filter_var() function, 271
  - helper function for, 255–258
  - indicating errors in, 273
  - parts of, 250
  - retrieving order contents, 261–262
  - SSL connection required for, 254
  - stored procedures for, 259–265
  - validating cities, 270
  - validating email address, 271
  - validating phone numbers, 270
  - validating states, 270
  - validating street addresses, 269
  - validating zip codes, 270
- checkout_cart.html view file, 274–278
- checkout_header.html file, creating, 254
- checkout.html view file
  - adding progress indicator, 279
  - creating, 279–282
- checkout.php page
  - accessing over HTTPS, 267
  - adding shipping, 277
  - checkout_cart.html view file, 274–278
  - checkout.html view file, 279–282
  - creating PHP script for, 267–274
  - displaying totals, 278
  - features of, 266
  - reaching trigger_error() point, 273
  - view files for, 274
- cities, validating in shipping process, 270
- CKEditor WYSIWYG editor, 112
- classes, applying to pages dynamically, 65
- clients, signing contracts with, 4–5
- “closed-loop” confirmation process, 90
- cloud hosting, 11
- code
  - documenting, 21
  - organizing, 21
  - profiling, 24
  - security of, 21
- code blocks, defining, 188–191
- coffee products. See also non-coffee products; products
  - adding to administrative scripts, 325–330
  - selecting, 196–198, 220
- Coffee site
  - applying password protection, 173–174
  - carts table, 168
  - checking allow rules, 174–175
  - checking deny rules, 174–175
  - config file, 180–181
  - connecting to database, 179–180
  - customer tables, 167–169
  - customizing server behavior, 173–178
  - database design, 166–172
  - emailing customers, 168–169
  - enforcing SSL, 178
  - error handler, 181
  - error handler, 181
  - features of, 162
  - focus on purchases, 164
  - footer.html, 184–185
  - general_coffees table, 166
  - header.html, 182–184
  - heightened security, 165
  - helper files, 179–181
  - HTML template, 182–185
  - implementing MVC (Model-View-Controller), 164–165
  - improving security of, 185
  - versus Knowledge is Power site, 164–165, 172, 309
  - non_coffee_categories table, 166
  - orders table, 167–168
  - product tables, 166–167
  - products directory, 172–173
  - products sold on, 163
  - protecting directories, 174–175
  - protecting directory contents, 173
  - rewriting public URLs, 175
  - sales table, 167
  - server organization, 172–173
  - specific_coffee table, 167
  - specific_coffees table, 166–167
  - SQL commands for, 169–171
  - transactions table, 168
  - use of InnoDB storage engine, 172
  - use of stored procedures, 165
  - user_session_id, 168
  - using mod_rewrite feature, 175–177
  - using regular expressions on, 176
  - view files, 181
