```
import java.util.*;
import org.json.JSONException;
import org.json.JSONObject;
import java.io.IOException;
import com.cloudant.client.api.ClientBuilder;
import com.cloudant.client.api.CloudantClient;
import com.cloudant.client.api.Database;
import static com.cloudant.client.api.query.Expression.eq;
import com.cloudant.client.api.query.QueryBuilder;
import com.cloudant.client.api.query.QueryResult;
import com.cloudant.client.api.query.Selector;
import com.google.gson.Gson;
import java.net.URL;
import java.util.List;
import java.util.Map;
import java.util.HashMap;
import java.util.stream.Collectors;
```

public class MainActivity extends AppCompatActivity {

```
static CloudantClient client;
Database db;
```

> // Declare the TextView, EditText and Button variables that will be required:
TextView TV3;
EditText ED1,ED2,ED3,ED4;
Button B1,B2,B3, B4;

> // Declare the variables pertaining to the Student records:
String id,id1,name,course,grade;

```
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
```

> // Link the GUI variables in the MainActivity to their counterparts in the
//activity_main file

```
TV3 = (TextView)findViewById(R.id.TV3);
ED1 = (EditText)findViewById(R.id.ED1);
ED2 = (EditText)findViewById(R.id.ED2);
ED3 = (EditText)findViewById(R.id.ED3);
```