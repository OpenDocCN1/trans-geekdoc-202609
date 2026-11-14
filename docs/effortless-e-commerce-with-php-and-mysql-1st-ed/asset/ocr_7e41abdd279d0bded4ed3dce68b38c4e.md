**tip**

Match the allowed tags in the `strip_tags()` function to the buttons in the editor.

+   8. Customize the editor's buttons:
+   
+   theme_advanced_buttons1 : "cut,copy,paste,pastetext,pasteword,l,
+   undo,redo,removeformat,l,search,replace,l,cleanup,help,code,
+   preview,visualaid,fullscreen",
+   theme_advanced_buttons2 : "bold,italic,underline,strikethrough,l,
+   justifyleft,justifycenter,justifyright,justifyfull,l,formatselect,l,bullist,
+   numlist,l,outdent,indent,blockquote,l,sub,sup,cite,abbr",
+   theme_advanced_buttons3 : "hr,l,link,unlink,anchor,image,l,charmap,
+   emotions,iespell,media",
+   
+   Each line indicates a row of buttons to create in the editor (Figure 5.7). TinyMCE uses specific names to create specific buttons, most of which are obvious. Using the pipe character (|) creates separators within a line so that you may group related buttons.

![](bbox=[0.365, 0.395, 0.785, 0.465])

Figure 5.7

+   9. Complete the customization:
+   
+   theme_advanced_toolbar_location : "top",
+   theme_advanced_toolbar_align : "left",
+   theme_advanced_statusbar_location : "bottom",
+   theme_advanced_resizing : true,
+   
+   The first three settings dictate where the toolbar and status bar are placed and aligned. The fourth says that the editor should be resized as the content grows, which is a nice touch.

+   10. Complete the script block:
+   
+   content_css : "/css/style.css",
+   });
+   </script>
+   
+   You can associate your site's CSS file with the editor so that content created within it will look the same as it will within a site page. That's what this line here does. The reference to the CSS file can be absolute, as in this case, or relative to the page that uses TinyMCE (not relative to the TinyMCE folder).

**tip**

If the editor doesn't show or doesn't reflect your customizations, make sure you refresh the browser. If there's still a problem, the cause is probably a syntax error in your JavaScript.

+   11. Save the file.

+   12. Reload the Web page in your browser to see the result (see Figure 5-3).