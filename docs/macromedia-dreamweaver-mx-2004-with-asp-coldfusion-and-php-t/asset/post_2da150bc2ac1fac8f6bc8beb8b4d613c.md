
If you are running ColdFusion locally as a standalone server without IIS, enter http://localhost:8500/newland/.

If you are running Apache locally in Windows or on a Macintosh, enter http://localhost/newland/.

![](img/43fd0127a958864ab2d93e28efe683e7_142_0.png)

NOTE As indicated earlier, the word localhost is a shortcut that activates the Web server on your computer, and tells it to look in the server's root folder (the wwwroot folder for IIS and the standalone ColdFusion Web server, or htdocs on Apache), in which you created a newland folder in a previous step.

If you are using a remote server, whether through a network or through FTP, enter the server's URL, which the site administrator should have given you. It probably looks something like http://www.bigcompany.com/newland/.

Either way, the URL prefix must begin with http:// and should not have any drive letters (such as h:) anywhere in it. Also note that the slashes in the URL are forward slashes, not backslashes.

TIP If the site doesn't display properly later in the lesson, the URL prefix is the first place you should look when troubleshooting. If this information is wrong, you will not be able to browse your site and see it in action, even if all your code is correct and your server and server models are correctly configured and running.

- 5) Click OK to save and close the dialog, and then click Done to close the Edit Sites dialog.

The site is now redefined and should be ready for dynamic development.

- 6) One at a time, right-click (Windows) or Control-click (Macintosh) each of the HTML files in the Site panel, choose Edit > Rename, and change the extension from .htm to .asp, .cfm, or .php as appropriate. Whenever the Update Files dialog appears, click Update.

Changing the extension is required when you upgrade to dynamic sites, because the server uses the extension to determine whether to process any special code on the page.

![](img/43fd0127a958864ab2d93e28efe683e7_143_0.png)

When you change the extension, all of the links that point to that page are broken. Dreamweaver's site manager catches this and fixes the problem when you choose Update.

![](img/43fd0127a958864ab2d93e28efe683e7_143_1.png)

- 7) Click once on the top-level folder, and click the Put File(s) button.

This uploads the entire site to the remote folder and testing server.

NOTE If a dialog appears asking whether you want to Put the entire site, click OK.

![](img/43fd0127a958864ab2d93e28efe683e7_144_0.png)

PUT FILE(S) BUTTON

- 8) Click once to select index.asp, index.cfm, or index.php in the Site panel, and press F12.

Pressing F12 tests the site as it runs through the server. This test results in either good news or bad news. If you can see the Newland Tours index page, then you have correctly configured the site, and you are ready to start developing. If you get an error message or the site doesn't display properly, then something has gone amiss. To troubleshoot, take a second look at the URL prefix. Also, use Windows Explorer or Macintosh Finder to make sure that the files really were uploaded to the remote site. If you are still hung up, talk to your site administrator, who should be able to help you resolve this problem.

## SITE URL DISPLAYS IN ADDRESS BAR

![](img/43fd0127a958864ab2d93e28efe683e7_144_1.png)

## BUILDING A SIMPLE, DYNAMIC APPLICATION

You have now tested the site going through the remote server, and—assuming you saw index.asp, index.cfm, or index.php in your browser—you have everything correctly configured. But nothing in the Newland site is actually dynamic yet. At this point, you’ve done all the work and haven’t seen any of the benefits. In this task, you will create a very simple dynamic application, which will reward you with a taste of what’s to come, both conceptually (how dynamic sites work) and behaviorally (the sequence of steps needed to create the functionality).

### CREATING THE INPUT PAGE

You’re going to build a page containing a form that asks users their names. Then they will click Submit, at which point they will be redirected to a second page, which will display the name they entered. No, this application doesn’t exactly push the limits of ASP, ColdFusion, or PHP. It does, however, introduce you to building forms, dealing with dynamic data, and distinguishing between server-side and client-side code.

- 1) With the Newland site open, choose File > New. In the New Document dialog, choose Dynamic Page in the Category list on the left side, and then choose ASP VBScript, ColdFusion, or PHP on the right. Make sure Make Document XHTML Compliant is checked. Click Create.

![](img/43fd0127a958864ab2d93e28efe683e7_145_0.png)

In this step, you are creating a new dynamic page. By specifying the type of dynamic page, you tell Dreamweaver what code to use when you use Dreamweaver’s ready-made server behaviors, which extension to use when you save the file, and in some cases, which additional code to add to the document header.

ASP users will see <%@LANGUAGE="VBSCRIPT" CODEPAGE="1252"%>; this line specifies whether you are using VBScript and JScript, either of which you can use with ASP. For the exercises in this book, though, you must work with VBScript. ColdFusion and PHP don't have multiple scripting languages, so a new ColdFusion or PHP page has no equivalent for this line.

- 2) Click anywhere in the design window, select the Forms category in the Insert panel, and click the Form button to insert a form. Click the Text Field button, and then click the Button button.

You have just added a basic form to your page.

![](img/43fd0127a958864ab2d93e28efe683e7_146_0.png)

The red dashed line indicates the form's boundaries. This will not appear in the browser; it is there just to help you know where the form begins and ends on the page.

The form at this stage is not yet customized and does not do anything. Lacking even a text label beside the text field, it doesn't tell you anything about itself.

- 3) Click the text field, and then press the left keyboard arrow once to position the insertion point before the text field. Type *First Name*.

If you don't label your text fields, no one will know what to type in them.

- 4) Click the text field, and in the Property inspector, name it *firstName* and press Tab or Enter/Return.

![](img/43fd0127a958864ab2d93e28efe683e7_147_0.png)

You will use this name to retrieve the value in ASP, ColdFusion, or PHP in a few minutes. Always give your form fields meaningful names. Code is hard enough to write as it is—don't make it worse by sticking with "Textfield1, Textfield2, and Textfield3, which Dreamweaver inserts by default.

You press Tab or Enter/Return to apply a setting entered in the Property inspector.

- 5) Click <form#form1> in the tag selector, to activate the Property inspector for the form. Name the form *frm_name*, and type *test_form_processor.asp* (or *.cfm* or *.php*) in the Action field.

The Action field points to the page (or other resource) that contains the script that can process the form data. It is always a URL. In this case, it points to a URL that doesn't exist, because you haven't created test_form_processor.asp (or .cfm or .php) yet. The method should be set to POST. I'll explain what POST means in a later lesson.

NOTE Henceforth, I will assume you can figure out your own extensions. It wastes space and insults your intelligence for me to specify "(or .cfm or .php)" every time I refer to a file. I will always use .asp, so if you are using ColdFusion, just use the .cfm extension instead, and if you are using PHP, use the .php extension instead.

![](img/43fd0127a958864ab2d93e28efe683e7_147_1.png)

- 6) Choose File > Save As and name the file *test_form.asp*.

This is a throwaway file that you are creating just to test a simple dynamic site feature. I often prefix such files used for testing purposes with "test_"; that way, when I am finished, I can easily find and remove them.
