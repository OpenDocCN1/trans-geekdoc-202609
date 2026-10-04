# Server and Servlet Architectures for a Cloud-Based Real-Time .

```
// Create a JSONObject to hold the data
JSONObject result = new JSONObject();
// Putting the String into the JSONObject
result.put("csv", values);
// Sending the JSONObject to the client (Webpage)
out.print(result);
out.flush();
out.close();
System.out.println("Data sent");

}
```

# 5.3.6.3. downloader.java

With the webpage displaying the functionality to download values by a particular date, this class sends a JSONObject bearing the values as a String object when queried with a URL appended with the required date, as well as the data source. The same global variables in Listing 5.14 are inserted in this class, as well as the modified fetchRegressionValuesPC() method from networkCloudServlet.java. The doGet() method is shown in Listing 5.52.

# Listing 5.52. doGet() for downloader.java

```
// doGet(HttpServletRequest request, HttpServletResponse response)
throws ServletException, IOException {
// Getting the date for which fetch values
String date = request.getParameter("date");
// Getting the source from which to fetch values
String source = request.getParameter("source");
// Setting the source of data from the HTTP request
if (source.equals("1")) {
    dataSource = "cloudant";
}
 (source.equals("2")) {
    dataSource = "localhost";
}
// Printing the values obtained from the URL
System.out.println("Date is: " + date);
System.out.println("Source is: " + dataSource);
```

String type1 = date; // e.g., Dec 17, 2020
String[] splits = date.split("*");
String[] splits2 = splits[0].split("*");
String type2 = splits2[1] + " * " + splits2[0] + splits[1]; // Dec 2020
System.out.println("Date formats are: " + type1 + " * " + type2);
// Conversion of date fetched to yymm-mm-dd to format of MySQL
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("MMM d, yyyy",