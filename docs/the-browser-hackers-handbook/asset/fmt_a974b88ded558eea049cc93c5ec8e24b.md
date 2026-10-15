
Another common behavior is replying with a `302` HTTP Redirect status code when requesting a nonexistent resource that is under a path protected by authentication. For example, let’s say you request `http://browserhacker.com/admin/non_existent`, where all resources under the `/admin/` path require the user to be authenticated. The web application replies with a `302` status code if you request `/admin/non_existent` as an unauthenticated user, redirecting back to the login page at `/admin/login`. Instead, if you are an authenticated user and you request `/admin/non_existent`, you get a `404` Not found error.

Mike Cardwell analyzed multiple social networking sites, checking whether they use HTTP status codes in a similar way. His analysis revealed interesting results. `8` Twitter, for example, behaves like the second example, returning a `302` or `404` on non-existent resources depending on whether or not the user session is authenticated.

Consider that the script HTML tag fires the `onerror` event if the resource you want to load returns a `403`, `404`, or `500` status code, and fires the `onload` event if the resource returns with a `200` or `302` status code. Also consider that Twitter requires authentication to access resources under the `/account/*` path. Armed with these two details, you can reliably determine if the hooked browser is logged in to Twitter on one of its open tabs (or windows), and you can do it cross-origin without violating the SOP. The following code snippet will do the trick:

```
var script = document.createElement("script");
script.onload = function(){
  alert('not logged in')
};
script.onerror = function(){
  alert('logged in')
};
script.src = "https://twitter.com/account/non_existent";
var head = document.getElementsByTagName("head")[0];
head.appendChild(script);
```

As you can see from `[Figure 9-6](#c09.html#figure9-6)`, if the hooked browser is not logged in to Twitter, a `302` response code is returned if a nonexistent resource such as `/account` is requested. This results in the script firing the `onload` event.

 start figure 

[**Figure 9-6:**](#c09.html#figureanchor9-6) Detecting that the victim is not logged in to Twitter

![c09f006.tif](image_fi/662090c09/c09f006.png)

 end figure 

If the hooked browser is logged in to Twitter, as you can see in `[Figure 9-7](#c09.html#figure9-7)`, requesting the same non-existent resource returns a `404` status code instead, resulting in the `onerror` event being executed.

 start figure 

[**Figure 9-7:**](#c09.html#figureanchor9-7) Detecting that the victim is logged in to Twitter

![c09f007.eps](image_fi/662090c09/c09f007.png)

 end figure 

Monitoring resource load times is another technique that works cross-origin. You can extrapolate important details if there is a load time delta on a resource when a session is authenticated versus when it is not. Using this information you can ascertain if the browser is logged in to an application.

Haroon Meer and Marco Slaviero presented this technique at DEF CON 15 in 2007`9` using `IFrames` with a custom `onload` event handler that monitors how long it takes for the framed resource to load. The results are more accurate the greater the load time delta. Many interactions in a web application may cause a delay.

A good example is a default installation of Drupal 6. If you’re logged in and you request `http://browserhacker.com/drupal/?q=admin`, the content length will be `3,264` bytes. On the other hand, if you are not logged in and you request the same resource, you receive a `403` HTTP status code and the content length will be `1,374` bytes.

A bigger content length often results in a longer load time, even if we are only talking milliseconds. The following code snippet can perform this query, but bear in mind it must be modified to suit your needs and the application you are testing:

```
var add_iframe;
var counter = 5;
var sum = 0;
/* Average time to match. In this case for
the http://browserhacker.com/drupal/?q=admin
resource:
logged in takes > 210ms
not logged in takes < 210ms
*/
var avg_to_match = 210;
function append(){
  if(counter > 0){
   var i = document.createElement("iframe");
   i.src = "http://browserhacker.com/drupal/?q=admin";
   var start = new Date().getTime();
   console.log('start:' + start);
   
   /* Custom onload handler to monitor load time*/
   i.onload = function(){
    var end = new Date().getTime();
    console.log('end:' + end);
    var total = end - start;
    console.log('total:' + total);
    sum += total;
    counter--;
   }
   document.body.appendChild(i);
  }else{
   clearInterval(add_iframe);
   var avg = sum / 5;
   var logged_in = true;
   console.log("sum: " + sum + ", avg:" + avg);
   if(avg < 210){
    logged_in = false;
   }
   console.log("logged in Drupal 6: " + logged_in);
  }
}
add_iframe = setInterval(function(){append()},500);
```

Continuing with the Drupal example, `[Figure 9-8](#c09.html#figure9-8)` and `[Figure 9-9](#c09.html#figure9-9)` highlight the results of running the previous script. Note the different sum and average times.

 start figure 

[**Figure 9-8:**](#c09.html#figureanchor9-8) Detecting that the victim is NOT logged in to Drupal

![c09f008.tif](image_fi/662090c09/c09f008.png)

 end figure start figure 

[**Figure 9-9:**](#c09.html#figureanchor9-9) Detecting that the victim is logged in to Drupal

![c09f009.tif](image_fi/662090c09/c09f009.png)

 end figure 

The fact you can accurately identify if the hooked browser is logged in to a web application helps launch attacks more reliably. Combine this knowledge with resources that are not protected with XSRF tokens, and you can potentially perform all sorts of actions on behalf of the hooked user.

# Exploiting Cross-site Request Forgery

Cross-site Request Forgery vulnerabilities are often referred to as either CSRF or XSRF vulnerabilities. XSRF attacks were first discussed in 2001 when Peter Watkins started a thread`10` on the Full Disclosure mailing list to discuss the issue. Since this time, XSRF vulnerabilities have become well known and understood throughout the security community.

## Understanding Cross-site Request Forgery

XSRF attacks exploit the trust a web application places on its users’ HTTP requests. This attack class is particularly useful when you know a user has authenticated with an application. Remember, techniques discussed in the previous section will help determine if a user has logged in.

Let’s take an application that requires an admin user to be logged in before being able to access the `[http://browservictim.com/admin/users](http://browservictim.com/admin/users)` resource. If an attacker controls a different origin on the browser with the authenticated origin, the attacker can potentially exploit an XSRF vulnerability within the web application. This means the attacker can perform actions on behalf of the authenticated user by including properly formatted requests to the vulnerable resource.

The attacker can forge cross-origin AJAX requests for the vulnerable resource. When processed by the browser, the requests will automatically include the cookies of the user, and therefore appear to be legitimate, authenticated requests. Using JavaScript to dynamically create and submit HTML forms with the same parameters will result in the same forged request. These requests will often be trusted by the web application, exploiting the fact that the user is logged in, and the cookies are sent with each request to the origin. Such vulnerabilities can be exploited because HTTP requests can be replayed, and the HTTP protocol doesn’t dictate how to handle unique requests.

Consider another scenario. A user is logged in to the admin interface of a Cisco c24e000 router. If the web admin UI is vulnerable to XSRF attacks, every request can be replayed by simply knowing the required parameters. An attacker can therefore trick the user into executing the following code from another origin:
