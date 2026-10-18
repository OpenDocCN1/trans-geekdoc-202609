An example of a form with a file upload field is shown below:

```
<!--example12-19.htm -->
<form enctype='multipart/form-data' action='example12-19.php' method='post'>
<p><input type='hidden' name='MAX_FILE_SIZE' value='100000' />
<label for='strFile'>Document File: </label>
<input name='strFile' type='file' id = 'strFile'/>
<input type='submit' name='SubmitQuery' /></p>
</form>
```

| NOTE | Note that the above script contains no PHP and thus is saved with the extension .htm. |

The output from the above script is illustrated in Figure 12.12.

You can enter the name and location of the file to upload in the form field, or you can click the Browse button to open a ‘choose a file window’ and locate and select the file to upload. This window is shown in Figure 12.13.

However, clicking on the submit button simply causes an error at this time as we haven’t written the PHP script to handle the receipt of the file.

# Creating the PHP upload script

There are many potential risks with scripts which access uploaded files. The potential for viruses and other malicious programs exists. In an attempt to overcome this, PHP file uploads have to undergo a number of steps to ensure their authenticity. Figure 12.14 illustrates these steps.

When a file is uploaded via a form, the file is stored in a temporary location. This location depends on your computer operating system. The file is stored using a temporary name created by PHP. A couple of environment variables are created to store the temporary

FIGURE 12.12 File upload form

![](bbox=[0.09, 0.75, 0.79, 0.95])