
```
var timeout = 10000; 
var interval = new Date().getSeconds();
function timer(){
  var s_interval = new Date().getSeconds();
  var diff = s_interval - interval;

  if(diff == 10 && diff > 0) key = diff + "aaa"
  if(diff == -10 && diff < 0) key = diff + "bbb"

  decrypt(key); 
}
function decrypt(key){
  // decryption routine
  alert(key); 
}

setTimeout("timer()", timeout);
```

The `timer()` function is called after 10 seconds of delay. When the program flow enters that function, a check is made to see if 10 seconds have actually passed. If the expected time delay is verified, the key for the decryption routine is created, and the decryption routine is called. If the preceding code is obfuscated, including different time delays to multiple parts, it will become trickier to analyze. You might want to use different time delays in your code. This technique comes in handy, as most JavaScript sandboxes used for malware analysis have fixed timeouts, after which they give up analyzing the obfuscated code.

### Mixing Content from Another Context

Another method to obfuscate JavaScript is by mixing contexts. When a human is de-obfuscating JavaScript, the first thing they may look at is the JavaScript code itself—we would consider this a single context. Imagine if the code was broken up into multiple parts, or contexts, and they each need information from different contexts in order to function. The following code is calling the `decrypt()` function, passing as its parameter the concatenation of two String objects (from the DOM):

```
<body>
<div id="hidden_div">
<p>key</p>
</div>
</body>
```

The second string comes from the page URI: http://browserhacker.com/mixed-content/dom.html#YTJWNU1pMWpiMjUwWlc1MA== :

```
function decrypt(key){
 // decryption routine
 alert(key);
}

var key = document.getElementById('hidden_div').innerHTML;
var key2 = location.href.split("#")[1];

decrypt(key + key2);
```

If a human analyst de-obfuscates just the script itself their result won’t be overly effective. The results of using this technique can be seen in [Figure 3-16](#c03.html#figure3-16):

 start figure 

[**Figure 3-16:**](#c03.html#figureanchor3-16) Obfuscating code mixing two different contexts

![c03f016.tif](image_fi/662090c03/c03f016.png)

 end figure 

The same concept can be extended to different contexts, not only the DOM. PDF files, Flash content, and Java Applets are all callable from JavaScript, so pieces of information can be pulled in from multiple disparate contexts.

### Using the callee Property

In JavaScript, if `arguments.callee` is called inside a function, it returns the function itself. This is sometimes useful when using anonymous recursive functions. Unfortunately, the use of `arguments.callee` is being deprecated from JavaScript, and will not run if using ECMAScript version 5 in strict mode.

The fact the function itself is returned by `arguments.callee` can be exploited to make de-obfuscation trickier. Imagine the function is performing a check on the code length of itself. If this check fails, parts of the code will not be executed. If someone is manually evaluating the code, by changing it, this check will likely fail. This is common when manually reviewing obfuscated code. For example, nested `eval()` calls might be replaced with helper functions such as `console.log()` or custom printing functions, to better understand the code before it’s being evaluated.

If such an approach is used inside an obfuscated function that relies on `arguments.callee` to check for its own length, the part of the sample that contains the malicious code may never get executed. When such obfuscated code gets modified during manual analysis, and the check on the code length is not, the malicious code will simply not run. To better understand how this works, a Ruby implementation of this technique is shown here:

```
placeholder = "XXXXXX"
code = <<EOF
function boot(){
var key = arguments.callee.toString().replace(/\\W/g,"");
console.log(key.length);
if(key.length == #{placeholder}){ 
    console.log("verification OK");
    //... malicious code here
}else{
    console.log("verification FAIL");
    //... dead code here}
}
EOF

code_length = code.gsub(/\W/,"").length 
# XXXXXX -> 6 chars
digits = code_length.to_s.length # returns the number of integer digits
if(digits >= placeholder.length)
 to_add = digits - placeholder.length
 final_code = code.gsub(placeholder , (code_length + to_add).to_s)
else
 to_remove = placeholder.length - digits
 final_code = code.gsub(placeholder , (code_length - to_remove).to_s)
end

File.open("result.js", 'w'){|f|f.write(final_code)} 
```

The resulting JavaScript will be written to `result.js`, and looks like this:

```
function boot(){
var key = arguments.callee.toString().replace(/\W/g,"");
console.log(key.length);
if(key.length == 166){ 
  console.log("verification OK");
  //... malicious code here
}else{
  console.log("verification FAIL");
  //... dead code here
}
}
```

For the sake of the example, the code itself is not obfuscated, nor is the 166 Integer calculated through the Ruby script, but they can both easily be obfuscated with one of the many techniques described earlier. For example, after adapting the previous Ruby code, you might want to replace 166 with:

```
document.getElementById('hidden_div').innerHTML +
atob(location.href.split("#")[1])
```

The `document.getElementById()` function will retrieve an element from the current document with an ID of `hidden_div`, which may return 160. The second part will retrieve all the base64-encoded content after the fragment identifier from the current document, decode it, and return the value (that is, 6). Summing these together will result in 166. This is a very simple example of how you can combine different encoding and obfuscation techniques. Layering and chaining some of the techniques presented so far will assist you with hiding your JavaScript code from automated and manual analysis.

### Evasion using JavaScript Engines Quirks

If you know which rendering engine you want to target, you can refine your obfuscation techniques to make de-obfuscation trickier by using JavaScript quirks between different rendering engines. These quirks can be abused to allow your code to follow a different path, depending on which JavaScript engine you use while de-obfuscating it.

For instance, Trident (Internet Explorer’s engine) returns true if the following code is evaluated. Gecko and WebKit, on the other hand, return false.

```
'\v'=='v'
```

Another similar trick to identify Internet Explorer is by using conditional comments, which work only on IE. The following snippet is a very simple example of how the Boolean negation `!` is applied only if conditional comments are enabled with `@cc_on`:

```
is_ie=/*@cc_on!@*/false;
```

If the code is evaluated by IE, it will be effectively interpreted as `!false`, resulting in the `is_ie` variable being true. In every other browser, the variable will be false because the Boolean negation will be considered just a code comment.

Now imagine you are targeting Internet Explorer and the server-side HTTP filtering engine uses SpiderMonkey (the JavaScript engine used by Firefox). If the filtering engine (using SpiderMonkey) evaluates the following code the flow will always end up in the else block:

```
if('\v'=='v'){
 ... // Malicious code for IE browser

}else{
 ... // Dead and Not-Malicious code for non-IE browsers 
}
```

The filtering engine will parse the code in the else statement and diagnose it as not malicious. The whole JavaScript content will be allowed by the proxy, and will then be potentially executed by an Internet Explorer browser. This time though, the logic flow that gets followed leads to the malicious code.
