# Automatically Generating WSDL with PHP 5's SOAP Extension

The greatest shortcoming of PHP5-SOAP is that there is no way to automatically generate WSDL with it. This is not often mentioned; however, it does create problems in real life. WSDL is so complicated that errors in the WSDL are hard to see and even harder to find.

However, you can create such a WSDL description for a Web Service in several ways, most of which have been used in real-world projects:

+   - Use NuSOAP or PEAR::SOAP to create a similar service, just to get the WSDL—just change the `<soap:address>` element
+   - Use the class Ctrx_SOAP_AutoDiscover (available at http://crtx.org/index.php?area=Main&page=CrtxSoapAutoDiscover)
+   - Use the Webservice Helper tool (available at http://www.jool.nl/new/index.php?file_id=1)
+   - Use the WSDL_Gen class (available at http://www.schlossnagle.org/~george/php/WSDL_Gen.tgz)

So as you can see, WSDL support is being worked on, not as part of the SOAP extension itself, but in the form of external projects. But hopes are that this will change some day.

If you finally have a WSDL description of your service (in the download archive, you will find a file AddService.wsdl that originated from the PEAR::SOAP-generated WSDL), the code for the server must only be slightly updated. The first parameter for the SoapServer instantiation receives the WSDL URL; also, the method(s) of the Web Service must be