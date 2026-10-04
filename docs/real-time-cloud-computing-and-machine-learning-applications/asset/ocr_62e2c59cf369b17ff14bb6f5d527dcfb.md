# 604 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoonondon

# Listing 6.7. dolInBackground method

```
protected String dolInBackground(Void... v) {
try {
    String URL = "https://api.openweathermap.org/data/2.5/weather?\nq=port%20louis
&appid=d9ef3c5a1c7aad855a430f86eabe867
&mode=JSON
&units=metric";
    // Document doc from JSON Library
    Document doc = Jsoup.connect(URL).ignoreContentType(true).get();
    return doc.text();
} catch (IOException e) {
    e.printStackTrace();
    return null;
}
```

# 6.3.16. onPostExecute ()

This method is invoked after the previous method has finished its execution. responsible for:

+   - Converting the String from the dolInBackground() method into a JSONObject.
- Extracting the necessary information from the JSONObject using the getDouble () & getJSONObject() methods.
- Displaying the current weather variable being monitored. Sending the data to either a local server or directly to the cloud.
- Sending the data to either a local server or directly to the cloud.

The codes are given in Listing 6.8.

# Listing 6.8. Convert String to JSONObject and gets the values

```
protected void onPostExecute(String result) {
    //Create a JSON Object from a String using the JSON library
    JSONObject json = new JSONObject(result);
    JSONObject main = json.getJSONObject("main");
    JSONObject wind = json.getJSONObject("wind");
    JSONObject cloud = json.getJSONObject("clouds");

    double visibility = json.getDouble("visibility");
}
```