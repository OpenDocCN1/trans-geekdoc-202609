# Online Selling: A Quick Way to E-Commerce

![](bbox=[0.137, 0.088, 0.863, 0.555])

Figure 14-6

# How It Works

In the code, we use the standard connection lines and our session lines. Then we check to see if the billing info is the same as the shipping info, and, if so, we populate the table with the billing information:

```
if ($_POST['name'] == 'on') {
    $_POST['shipfirst'] = $_POST['firstname'];
    $_POST['shiplast'] = $_POST['lastname'];
    $_POST['shipadd1'] = $_POST['add1'];
    $_POST['shipadd2'] = $_POST['add2'];
    $_POST['shipcity'] = $_POST['city'];
    $_POST['shipstate'] = $_POST['state'];
    $_POST['shipzip'] = $_POST['zip'];
    $_POST['shipphone'] = $_POST['phone'];
    $_POST['shipmail'] = $_POST['email'];
}
```

489