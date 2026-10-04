# 596 T. P. Fowdur, L. Babooram, M. N-U-Dbn Naz Rosun and M. Indoonondan

```
import com.github.mikephil.charting.data.Entry;
import com.github.mikephil.charting.data.LineData;
import com.github.mikephil.charting.data.LineDataSet;
import com.github.mikephil.charting.interfaces.ILineDataSet;
import com.google.gson.JsonParser;
import com.google.gson.internal.LinkedTreeMap;

//import from the JSON library to manipulate JSON
import org.json.JSONException;
import org.json.JSONObject;
import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;

import java.io.IOException;
import java.io.PrintWriter;
import java.net.Socket;
import java.net.URL;
import java.sql.Timestamp;
import java.util.HashMap;
import java.util.List;
import java.util.Map;
```

# 6.3. Global Variables

The class has eight global private variables defined at the top. The name and function of each variable are given in Table 6.3. The declarations for the global variables are given in Listing 6.2.

# Table 6.3. MainActivity Global Variables

| No. | Object Name | Object Type | Function |
|---|---|---|---|
| 1 | m | LineChart | A chart that draws a line to represent a list of values. |
| 2 | spinner | Spinner | Used to change the current variable displayed on the graph. |
| 3 | IP_address | EditText | The user enters the IP address of the local server. |
| 4 | monitor | Button | When pressed, the program start monitoring or stop the monitoring process depending on the value of the boolean monitoring. |
| 5 | cloud_save | Switch | Used to determine whether to send the data directly to the cloud database or local server.
On-state – send to the cloud database.\ Off-state – send to the local server. |
| 6 | Monitoring | boolean | Used to determine whether the monitoring process is running or not. True – monitoring process has started. False – monitoring process not running. |
| 7 | mHandler | Handler | Used to schedule in action to be performed every N milliseconds. |
| 8 | mRunnable | Runnable | Defines a set of instructions to be performed. |
| 9 | download_data | Button | Used to launch the DownloadDataActivity. |