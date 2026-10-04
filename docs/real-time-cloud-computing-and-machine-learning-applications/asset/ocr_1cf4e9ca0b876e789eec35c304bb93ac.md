# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 651

```
//Map used to store values with a key
import org.google.gson.internal.LinkedTreeMap;
//Used to create some standard charts with JFreeChart
import org.jfree.chart.ChartFactory;
// A Swing component for displaying a JFreeChart object.
import org.jfree.chart.ChartPanel;
// A chart class implemented using the Java 2D APIs.
import org.jfree.chart.JFreeChart;
//Represents a sequence of zero or more data items in the form (x, y)
import org.jfree.data.xy.XY;
/* Represents a collection of (@link XYSeries) objects
that can be used as a dataset */
import org.jfree.data.xy.XYSeriesCollection;
//To create JSON Objects
import org.json.JSONObject;
//The core public access point to the JSoup functionality.
import org.jsoup.Jsoup;
//Represent a HTML Document.
import org.jsoup.nodes.Document;
import java.awt.Dimension;
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.io.PrintWriter;
import java.net.MalformedURLException;
import java.net.Socket;
import java.net.URL;
import java.sql.Timestamp;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.List;
import java.util.Timer;
import java.util.TimerTask;
import java.util.logging.Level;
import java.util.logging.Logger;
import javax.swing.JFileChooser;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.UIManager;
import org.json.JSONArray;
import org.json.JSONException;
```