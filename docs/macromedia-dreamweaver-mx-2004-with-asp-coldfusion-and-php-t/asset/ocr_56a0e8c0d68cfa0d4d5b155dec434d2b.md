When you are finished, close tourprice.asp.

![](bbox=[0.278, 0.078, 0.872, 0.428])

# COLLECTING, PROCESSING, AND DISPLAYING THE DATA

The stage is set, and now it is time to capture the data entered on the form and perform the price calculation based on the data the user entered. You are already familiar with collecting form data and displaying it on the page, so in this task you should focus on the calculation itself.

+   1) Open tourprice_processor.asp. If necessary, switch to split view or code view.

To perform the calculations, you need the data, which is available on the page specified in the form's action attribute.

The switch to code view is necessary for now, because you are about to do some hand-coding, and there is no way to do so in design view.

+   2) ASP only: Position the insertion point at the top of the document, before the opening <!DOCTYPE...> tag, press Enter/Return twice, return to line 1, and type <%@LANGUAGE="VBSCRIPT" CODEPAGE="1252" %>.

This line is necessary for two reasons. First, it tells the server that the scripting language used is VBScript. Remember, ASP can be coded using more than one language. The most common languages for ASP are VBScript and JScript, and with ASP.NET, you have even more options. ColdFusion users don't have to worry about