```
}
return String();
}
void setup(){ pinMode(ProxSensor,INPUT); Serial.begin(115200);
WiFi.begin(ssid, password); //begin WiFi connection Serial.
Serial.println("");
// Wait for connection
while (WiFi.status() != WL_CONNECTED) { delay(5000);
Serial.print("");
}
Serial.println("");\ Serial.print("Connected to ");\ Serial.
println(ssid); Serial.print("IP address: ");\ Serial.
println(WiFi.localIP());\ server.on("/", HTTP _GET, []())
{
  server.send(200, "text/html", index _html);
});
server.on("/values", HTTP _GET, []())
{
  server.send(200, "text/plain", readcurrent());
});
server.on("/values1", HTTP _GET, []())
{
  server.send(200, "text/plain", readcurrent1());
});
server.on("/values2", HTTP _GET, []())
{
  server.send(200, "text/plain", readcurrent2());
});
server.on("/values3", HTTP _GET, []())
{
  server.send(200, "text/plain", readcurrent3());
});
server.begin();
Serial.println("Web server started!");
}
void loop(){ server.handleClient();n
```

# CONCLUSION AND FUTURE ENHANCEMENTS

This research has implemented an IoT-based parking system that checks the status of a parking slot online and through it created web server for checking the status of the parking slots. Users can add additional features to the server. As a future enhancement, the researchers would like to improve the efficiency of the server and add features reserving parking slots, navigating the user from the entrance to the slot, and payment options. This will be helpful for the users to search for parking spaces and it will be user-friendly.