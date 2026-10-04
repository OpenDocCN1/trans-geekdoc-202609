# Server and Servlet Architectures for a Cloud-Based Real-Time . 545

```
PrintWriter out = response.getWriter();
response.setContentType("application/json");
response.setCharacterEncoding("UTF-8");
// Writing values to the page
out.print(json.toString());
out.flush();n
```

# 5.3.6. Building the Downloading Servlets

The servlets cater for the download of .csv files both by a particular of samples 'N' or are implemented through the fetching of certain parameters from URL that accesses the servlet. These URL calls are performed in the web pages created, in Section 5.3.7. The classes are previously summarized in Table 5.17 as well as in Figure 5.42.

5.3.6.1. downloadValues.java
This class focuses on firstly fetching PC network parameters from either the Cloudant database or localhost as globally declared object, as used by the local server, before using a PrintWriter to send out the obtained values as a JSONObject, of type String. This thins the webpage with the ability to make a .csv file with the obtained values, at the client-side. A loop dictates how many values are sent, depending on the "number" parameter appended to URL. Also appended is the "source" variable. The following steps depict this process.

+   1. Listing 5.49 shows the globally declared variables for this class. An object of type double denoted "length" is also defined that it identifies the number of samples to send download, after the fetching process.

> Listing 5.49. Global variables in downloadValues.java

```
public class downloadValues extends HttpServlet {
    private static final long serialVersionUID = 1L;

    // Object to send the output onto the browser
    private PrintWriter out;

    // Declaring variables for connection to cloud database
    CloudClient client = null;
    Database db;

    double numItems = 0.0; // For predict button and download functions
    // Variables for Regression analytics
```