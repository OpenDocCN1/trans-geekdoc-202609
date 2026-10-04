
# Listing 6.10. Analysis.java class declaration

```java
package com.test.weathermonitoring;
import android.annotation.SuppressLint;
import android.os.AsyncTask;
import android.os.Bundle;
import android.text.method.ScrollingMovementMethod;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.dx.appcompat.app.AppCompatActivity;
import org.json.JSONObject;
import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import java.io.BufferedReader;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.io.PrintWriter;
import java.net.Socket;
public class Analysis extends AppCompatActivity {
// EditText where the window size is entered
EditText window_size;
// EditText where prediction time is entered
EditText prediction_time;
// EditText where the IP address of the local server is entered
EditText ip_add;
// TextView where results are displayed
TextView results;
// Button that starts the analysis activity
Button cloud_l, local_l;
// String to store window size = "" & ptime value
String ptime = "", windowsize = "", ip_address = "";
@Override
protected void onCreate(Saved savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_analysis);
    ip_add = findViewById(R.id, ip_address);
    window_size = findViewById(R.id, window_size);
    prediction_time = findViewById(R.id, prediction_time);
    results = findViewById(R.id, results);
    cloud_l = findViewById(R.id, cloud_l);
    local_l = findViewById(R.id, local_l);
    results.setMovementMethod(new ScrollingMovementMethod());
    // assigns the action to be performed when cloud button is clicked
    cloud_l.setOnClickListener(view -> {
        //gets the prediction time
        ptime = prediction_time.getText().toString();
        //gets the window size
        windowsize = window_size.getText().toString();
        //start a new async task to perform analysis on cloud servlet
        new QueryCloudServer().execute();
    });
//assigns the action to be performed when button is clicked
    local_l.setOnOnClickListener(view -> {
        //gets the IP address of the local server
        ip_address = ip_add.getText().toString();
        //gets the prediction time
        ptime = prediction_time.getText().toString();
        //gets the window size
        windowsize = window_size.getText().toString();
        //start a new async task to perform analysis on the local server
        new QueryLocalServer().execute();
    });
}
```

## 6.3.20. QueryCloudServer Class

This class extends the AsyncTask class to perform networking on a background thread. This class is responsible for connecting to the java servlet and fetching the results of the analytics and displaying it on the TextView. To connect to the java servlet, JSOUP has been used since the servlet response is a JSON Object. A timeout of four minutes has been set to prevent the connection from closing before the servlet has returned the results. The JSON object is converted to text and displayed on the screen. The codes for the QueryCloudServer Class are given in Listing 6.11.

## Listing 6.11. Contact Java Servlet for Analysis

```java
@SuppressWarnings(StaticFieldLeak)
public class QueryCloudServer extends AsyncTask<Void, Void, Void> {
//String that stored results obtained from the servlet
String returned_val = "An error occurred";
@Override
protected Void doInBackground(Void... voids) {
    try {
        //the URL to connect to the Java Servlet
        String host = "https://weatherforecaster.eu-gb.mybluemix.net/Forecaster?"
        + "prediction_time=" + ptime
        + "window_size=" + windowsize
        + "&data_src=cloud";
        System.out.println(host);

        //Connect to the URL using the connect method of the JSoup class
        Document doc = Jsoup.connect(host).ignoreContentType(true)
            .timeout(4 * 60 * 1000).get();
        //Convert the String into a JSON Object
        JSONObject prediction = new JSONObject(doc.text());
        //Extract the analytics results from the JSONObject
        returned_val = prediction.getString("results");
    } catch (Exception e) {
        //prints the trace of the error occurred
        e.printStackTrace();
    }
    return null;
}
@Override
protected void onPostExecute(Void aVoid) {
    super.onPostExecute(aVoid);
    results.setText(returned_val);
}
```

The URL to contact the java servlet can be obtained from the application details on the Resource List as explained in chapter 7. The window size, prediction time, and data source values are sent to the servlet as a query by appending them to the URL. 

| Application Endpoint | Servlet Name |
| :--- | :--- |
| https://weathercaster.eu-gb.myblueemix.net/Forecaster | |
| + "prediction_time=" + ptime | Query String |
| + "window_size=" + windowsize | Containing window size, prediction time & data source |
| + "&data_src=cloud"; | |

Figure 6.18. URL Breakdown.

Figure 6.19 shows where the route of the application can be obtained on the IBM platform. Chapter 7 gives more details on hosting the servlet on the cloud platform to obtain the URL.

![](img/2b52fde0e707e8c2f05a10309c3f8982_629_0.png)

Figure 6.19. Java Servlet URL.

## 6.3.21. QueryLocalServer Class

This class extends the AsyncTask abstract class to performs networking on a background thread. This class is responsible for connecting to the local java server, fetching the results of the analytics, and updating it in the TextView. To connect to the local java server, a connection to the server is established via a socket connection on port 11111. A JSONObject is created to store the request type, window size, and prediction time. The JSONObject is sent to the server. The server processes the request and returns the analytics in a JSONObject. The analytics results are extracted from the JSONObject and displayed in the TextView. The codes for the QueryLocalServer Class are given in Listing 6.12.

## Listing 6.12. QueryLocalServer Class

```java
@SuppressWarnings("StaticFieldLeak")
public class QueryLocalServer extends AsyncTask<Void, Void, Void> {
// String that stored the results obtained from the servlet
String returned_val = "An error occurred";

@Override
protected void doInBackground(Void... voids) {
    try {
        // Stores the window size & prediction time in a JSONObject
        JSONObject JSONObject = new JSONObject();
        JSONObject.put("request", "analytics");
        JSONObject.put("window_size", Integer.parseInt(windowsize));
        JSONObject.put("prediction_time", Integer.parseInt(ptime));
        //Opens a socket connection to the Java local server
        Socket socket = new Socket(ip_address, 11111);
        //Create a PrintWriter from the socket OutputStream
        PrintWriter out = new PrintWriter(socket.getOutputStream());
        //Sends the data to the local server
        out.println(JSONObject);
        out.flush();

        //creates a BufferedReader from the socket InputStream
        InputStream isr = socket.getInputStream();
        InputStreamReader isr = new InputStreamReader(isr);
        BufferedReader br = new BufferedReader(isr);
        //Read the data from the BufferedReader.
        String data = br.readLine();
        //Convert the string into a JSON Object
        JSONObject prediction = new JSONObject(data);
        //store the string in json format to be formatted
        returned_val = prediction.getString("analytics");

    } catch (Exception e) {
        //prints the trace of the error occurred
        e.printStackTrace();
    }
    return null;
}
@Override
protected void onPostExecute(Void aVoid) {
    super.onPostExecute(aVoid);
    results.setText(returned_val);
}
```

## 6.3.22. Querying Cloudant for Weather Readings

The application can also connect to the Cloudant database to request the last N readings or readings for a specific date. The DownloadData activity is responsible for implementing this feature. The DataRetriever class is used to fetch data from Cloudant.

## 6.3.23. DownloadActivity

This activity presents the user with an interface where the user chooses to download data for a specific date or only the last N rows from the database. This activity consists of an EditText to enter the IP Address of the local server, one to enter the number of samples to fetch, and the other to enter the sample size of data that is required. A switch is present to indicate whether to download data from the Cloudant or local server. There is also two Button, one for each scenario. A TextView is also inside a ScrollView to view the data fetched from the cloud. The UI of the activity is shown in Figure 6.20.

![](img/2b52fde0e707e8c2f05a10309c3f8982_631_0.png)

Figure 6.20. DownloadData Activity UI.

The codes for the xml version="1.0" encoding="utf-8"?> download_data.xml file are given below.

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".DownloadData">

  <LinearLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">
</androidx.constraintlayout.widget.ConstraintLayout>
```
