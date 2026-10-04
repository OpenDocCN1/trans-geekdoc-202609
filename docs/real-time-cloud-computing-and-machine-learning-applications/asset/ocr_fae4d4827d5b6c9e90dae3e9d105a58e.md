# 766 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoonondun

```
databaseArray = dataRetriever.getDatabaseArray(", 1);
el {
databaseArray = sqlConn.fetchLastN(1);
// Extract the array containing the readings
double[][] readings = (double[][]) databaseArray[0];
// initialize an array to return
```

```
double value = 0;
// A switch-case to determine the parameter needed
witch (parameter) {
    case "Temperature":
        value = readings[0][0];
        break;
    case "wind speed":
        value = readings[0][1];
        break;
    case "Wind Direction":
        value = readings[0][2];
        break;
    case "Pressure":
        value = readings[0][3];
        break;
    case "Visibility":
        value = readings[0][4];
        break;
    case "Humidity":
        value = readings[0][5];
        break;
    case "Cloudiness":
        value = readings[0][6];
```

```
}
// creates a new JSON Object and store the value to be returned
JSONObject res = new JSONObject();
res.put("value", value);
// Get a PrintWriter and set content type to JSON
PrintWriter out = new PrintWriter(response);
response.setContentType("application/JSON");
response.setCharacterEncoding("UTF-8");
// Write the JSON to the user and close the connection
out.print(res.toString());
out.flush();
out.close();
}
}
```