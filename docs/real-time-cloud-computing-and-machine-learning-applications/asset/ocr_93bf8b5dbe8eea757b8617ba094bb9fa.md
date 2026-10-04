118 T. P. Fowder, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoonendam

# 2.8.1. Creating a Desktop Application to Send a Request to the CalculateArea servlet

This application is developed in the Netbeans IDE by creating a project CalculateArea to which a JFrame frame called Calculate_Area.java has been added. The completed application with a typical output is shown in Figure 2.127. When the SEND PARAMETERS TO CLOUD button is pressed, the values entered in the length and width fields are sent as URL query to the CalculateArea servlet which responds with the value of the calculated area.

![](bbox=[0.277, 0.296, 0.722, 0.545])

Figure 2.127. JFrame of Calculate_Area.java.

The project will need the jsoup-1.13.1.jar file which is available from [37]. This jar file will allow the following two libraries to be imported in the project:

+   1. org.jsoup.Jsoup : It is a Java library that supports operations on standard HTML files. It provides a very convenient API for extraction and manipulation of data, using several methods as Document Object Methods (DOM), CSS, and jquery-like methods. Jsoup analyzes HTML files in a similar way as state of the art browsers, using the same DOM [38]. It also implements the WHATWG HTML5 standard.

+   2. org.jsoup.nodes.Document: The Document class provides the connect() method to connect to the URL host or the get() method to get the response from the host [39].

After creating the GUI frame and adding the jar file to the project, the main JFrame i.e. Calculate_Area.java is coded as shown in Listing 2.10. It is to be noted that only the codes for the JButtonActionPerformed() method need to be added as the other codes are auto-generated when the GUI is assembled.