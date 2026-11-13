This example makes use of the constant POST variable that is found in the URLRequestMethod. Of course, you can simply use the literal string POST because this is what the constant actually has for a variable.

```
urlRequest.method = URLRequestMethod.POST;
```

# ## Using sendToURL

In previous examples, you may have noticed the use of navigateToURL, which calls a URL and offers the ability to send GET data across the URL. This example calls for POST data, so the use of sendToURL is a better option. It is important to understand that the sendToURL method sends the request to the server, but ignores any response that is returned.

```
sendToURL(urlRequest);
```

# ## Setting up PayPal communication

The final step is to assign the button action that is attached to the Buy Now MovieClip. Simply place a MovieClip on the Stage and give it the instance name buyNowBtn. If you choose to have more than one button, I recommend a Class structure that passes the PayPal data to minimize the amount of code needed.

The callPaypal function is attached to the button using an event listener. The CLICK event is used, which is called when the user clicks the button.

```
buyNowBtn.buttonMode = true;
byNowBtn.useHandCursor = true;
buyNowBtn.addEventListener(MouseEvent.CLICK, callPaypal);
```

The last step is to put all of the code together and test it.

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

var paypalURL:String = "https://www.paypal.com/cgi-bin/webscr";

function callPaypal(e:MouseEvent):void
{
    var urlVariables:URLVariables = new URLVariables();
    urlVariables.cmd = pp_cmd;
```