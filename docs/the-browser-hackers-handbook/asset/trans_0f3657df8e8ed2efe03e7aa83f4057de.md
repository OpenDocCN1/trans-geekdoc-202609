
var result = "Not in use or not installed";

var lpdiv = document.getElementById('hiddenlpsubmitdiv');
// Check for the div first
if (typeof(lpdiv) != 'undefined' && lpdiv != null) {
  result = "Detected LastPass through presence of the <script> tag with id=hiddenlpsubmitdiv";

// Use JQuery to search inside script elements for the presence of lastpass_iter
} else if ($("script:contains(lastpass_iter)").length > 0) {
  result = "Detected LastPass through presence of the embedded <script> which includes references to lastpass_iter";
  
} else {
  if (document.getElementsByTagName("form").length == 0) {
      result = "The page doesn't seem to include any forms - we can't tell if LastPass is installed";
  }
}
```

First, the JavaScript checks for the script element discussed earlier. If that’s not found, it will then proceed to check for the embedded JavaScript. Finally, the script will update the result variable if there are no forms in the page.

Using the absence or presence of DOM properties gives you a reliable way to fingerprint the extensions in the browser. The DOM properties that are the telltales will depend entirely on the target.

### Firebug Example

Firebug can be installed as an extension or a script (Firebug Lite). Let’s use Firebug as an example to go over how to detect slight extension differences. Once you discover the extension is installed, you’ll want to confirm that it is actually the extension and not the Lite version. This can be tricky, because they create a lot of the same properties in the DOM. However, you come armed with the knowledge of a property that is unique to the Lite version.

To detect the Firebug extensions, use the following DOM properties: `!!window.console.clear`, `!!window.console.exception`, and `!!window.console.table`. If they all return true, the browser has Firebug installed and active.

A test that is unique to Firebug Lite is `!!window.console.provider`. If you want to confirm that the extension is not the Lite version, you’ll need that last test to return false.

## Fingerprinting using the Manifest

In the past, the extensions really helped you out when trying to fingerprint them. Google Chrome extensions based on manifest version 1 permitted access to all files of the extension and could easily be reached by their URL: `chrome-extension://<guid>/path/to/file.txt`. Because all extensions need to have a `manifest.json` file, knowing the GUID would allow you to simply request the following URL:

```
chrome-extension://abcdefghijklmnopqrstuvwxyz012345/manifest.json
```

But that was then; this is now. Now you need to do a little more work to fingerprint the extension using the files in the manifest. In manifest version 2, Google made no extension resources accessible by default.

Of course, some extension developers rely on their resource to be accessible for correct functionality. Google created a new array called `web_accessible_resources` in the `manifest.json` file. This array lists resources that can be accessed via a URL. The following snippet from the manifest file shows an example array being declared, making `logo.png`, `menu.html`, and `style.css` accessible:

```
{
  {
    "name": "extensionName",
    "version": "versionString",
    "manifest_version": 2
  },
  "web_accessible_resources": [ "logo.png", "menu.html", "style.css" ]
}
```

With this fictitious extension, the following URL can access the `logo.png` resource:

```
chrome-extension://abcdefghijklmnopqrstuvwxyz012345/logo.png
```

Hence, you need just two pieces of information to fingerprint your target extension. The first is GUID, which is covered in a moment. The other piece of information is which resources (if any) are defined in the `web_accessible_resources` array.

Luckily for you, most extensions have at least one file declared in `web_accessible_resources`. Knowing the resource, next you need to discover the extension’s GUIDs (32-character strings). You can achieve all this information trivially by scraping content from the Chrome Web Store.

You can do this manually or by using publicly available tools such as XSS ChEF26 from Kotowicz. It will download and unpack extensions from the Chrome Web Store, so you can use it to scan the `manifest.json` files and build your Chrome extension fingerprinting database from there.

Now that you have your Chrome extension resource database, you’ll need to run some code in the hooked browser to probe for that resource. Use the earlier `logo.png` resource to create the following code:27

```
var testScript = document.createElement("script");
testURL = "chrome-extension://abcdefghijklmnopqrstuvwxyz012345/logo.png";
testScript.setAttribute("onload", "alert('Extension Installed!')");
testScript.setAttribute("src", testURL);
document.body.appendChild(testScript);
```

You can extend this code to iterate through your database of extensions and very quickly fingerprint target extensions.

The methods examined in the previous sections will give you insight into what extensions are available for you to target. Research into attacking extensions is still expanding so be sure to keep up-to-date with new techniques.

# Attacking Extensions

There will be many avenues to attack a target and these will depend intimately on the functionality of the extension. An understanding of what is accessible from the attacker’s position is important.

Vulnerabilities can result due to the developers creating interfaces that can easily be replicated in the web page origin, lack of encryption, improper validation, and more. Let’s jump straight in and explore some real-world examples.

## Impersonating Extensions

By this stage you might be wondering why you would want to steal someone’s password. Why steal a password when, instead, you can just inject a hook, piggyback on a victim’s session, and impersonate them without ever having to type in a password?

We touched briefly on stealing passwords using social engineering techniques in Chapter 2 and Chapter 5, but what wasn’t covered was just how serious the password reuse issue is. In 2011 Joseph Bonneau28 researched the issue of password reuse by analyzing password hashes disclosed from hacks against Gawker and rootkit.com. His research, while only comparing a relatively small subset of users present in both systems, conservatively estimated that password reuse occurred in about 30 percent of instances.

Even if this figure is an overestimation, you would be fooling yourself if you thought a lot of users didn’t reuse their passwords for certain systems. One of the common approaches to addressing the issue of password reuse is by using unique and potentially random passwords for every site you visit. This, of course, then introduces a whole other set of problems.

### Impersonating the LastPass Extension

How does the average Joe maintain all these unique passwords? Writing all the passwords down on a piece of paper that is kept secure is one option; and potentially a sound option depending on how well the piece of paper is protected. Password management software is another approach, one that has slowly been gaining traction as more and more offerings have made their way online. Of course, another factor that has likely been driving the popularity of these applications is the issue of password breaches and impacts of password reuse coming under the media spotlight. The LinkedIn breach of 2012 highlighted the issue of password security for millions of users.29 Perhaps the initial question for an attacker shouldn’t be why would you want to steal a password, but instead, why steal one password when you can steal access to all passwords used by a victim?

But what does this have to do with extensions? Well, a common feature of many password management software suites includes integration with web browsers. In fact, some products use browser extensions as their primary method of access.

