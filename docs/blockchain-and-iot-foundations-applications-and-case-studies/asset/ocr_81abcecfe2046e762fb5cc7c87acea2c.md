# TABLE 6.2 (CONTINUED)
Testing for Arduino Implementation

| Test Case ID | Test Description | Test Procedure | Test Input | Expected Result | Actual Result |
|---|---|---|---|---|--|
| T-8 | To check whether the IR sensors sense the object correctly | The object is placed near the sensor | The sensor will sense the object. | The sensor must sense object and sends signal to Arduino board. | The sensor must sense object and sends signal to Arduino board. |
| T-9 | To check whether the LCD displays the slot status correctly | Give power supply and test the input. | The object must be placed in the slot to check the LCD | The LCD must display the slot status correctly. | The LCD displayed the status correctly. |
| T-10 | To check whether the ESP256 NodeMCU integrates with the web server. | | Compile the web server code. | The web server display the status in the Arduino board correctly. | The web server displayed the status in the Arduino board correctly.|