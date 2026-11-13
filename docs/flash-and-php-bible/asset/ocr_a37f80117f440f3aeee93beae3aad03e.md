Even though you can clearly see numbers in the block of variables, all of the parameters are set as strings to be compatible with the HTML equivalent. The next piece is to establish the URL, which will be used to interface with PayPal. This is essentially the same variable as action, which is found in the original HTML.

```
var paypalURL:String = "https://www.paypal.com/cgi-bin/webscr";
```

When the PayPal variables and data are established, you can create the code that is called when the Buy Now button is clicked.

Here is the function that is used to call PayPal. This method doesn't require the custom variables to be passed in because they are defined outside of the function. Defining a variable outside a function is scoped so any function has access to them. If this variable is defined within the function it would only be visible to the function in which it is defined. The exception is, of course, if the function is global or the variable is returned from the created function.

```
function callPayPal(e:MouseEvent):void
{
    var urlVariables:URLVariables = new URLVariables();
    urlVariables.cmd = pp_cmd;
    urlVariables.business = pp_business;
    urlVariables.item_name = pp_item_name;
    urlVariables.item_number = pp_item_number;
    urlVariables.amount = pp_amount;
    urlVariables.currency_code = pp_currency;
    urlVariables.weight = pp_weight;
    urlVariables.weight_unit = pp_weight_unit;
    urlVariables.lc = pp_location;

    var urlRequest:URLRequest = new URLRequest(paypalURL);
    urlRequest.method = URLRequestMethod.POST;
    urlRequest.data = urlVariables;
    sendToURL(urlRequest);
}
```

# Using POST data

The method of the data sent to PayPal is in POST format. This means the variables are included in the call, but not on the URL as seen with GET. Using the POST format holds a few advantages, the first being the URL is clean and can't really be tampered with. The second is the added level of security when passing moderately sensitive data to the server.

If you need to send highly sensitive data, such as billing or credit card information, it is important that you use an HTTPS call. The reason for that is POST really only becomes a Security by Obscurity and isn't the safest result.