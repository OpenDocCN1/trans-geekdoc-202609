# 100 T. P. Fowdar, L. Baboor, M. N-U-Ibn Nazir Rosun and M. Indoondonon

```
ED4 = (EditText)findViewById(R.id.ED4);
B1 = (Button)findViewById(R.id.B1);
B2 = (Button)findViewById(R.id.B2);
B3 = (Button)findViewById(R.id.B3);
B4 = (Button)findViewById(R.id.B4);
```

/ This method defines the action to be performed when the 'SEND TO CLOUD WITH DEFAULT INDEX 'button is pressed ' /

```
B1.setOnOnClickListener(new View.OnClickListener() {
  @Override
  public void onClick(View v) {
```

/ The operations in this method include extracting the input of the user, wrapping it as a JSON object, use Map Function to map its values, create a client agent, a database object, and send the data to the cloudant database. The details are similar to the Desktop app./ /

```
id = String.valueOf(ED1.getText());
name = String.valueOf(ED2.getText());
course = String.valueOf(ED3.getText());

JSONObject jsonString = new JSONObject();
```

```
try {
  jsonString.put("Name", name);
  jsonString.put("id", id);
  jsonString.put("Course", course);
} catch (JSONException e) {
  e.printStackTrace();
}
```

/ Create a runnable interface with the corresponding run method that will run on a separate thread to handle the communication between the client and the cloudant database. / /

```
Runnable runnable = new Runnable() {
  @Override
  public void run() {
  try {
```

```
client = ClientBuilder.url(new URL("https://913fa458-c60e-496a-b6b0-1cd35d57936a-bluemix.cloudant.com"))));
```