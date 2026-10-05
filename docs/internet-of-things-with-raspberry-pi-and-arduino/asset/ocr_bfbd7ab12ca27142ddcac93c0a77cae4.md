# 10.1.3 Recipe

```
import sys # import sys library
importRPi.GPIO as RA # import GPIO library
import time as wait # add time library
importAdafruit_DHT as RAJ_DHT
import urllib2 #import urllib library
my_API = 'F1MAEF943TLMVTCI'
defensor_data():
    HUM, TEMP = RAJ_DHT.read_retry(RAJ_DHT.DHT11, 21)
    return str(HUM,TEMP)
defmain_function():
    base_URL = 'https://api.thingspeak.com/update?api_key=%s ' % my_API
    while True: # infinite loop
    try:
        HUM, TEMP = sensor_data(base) # read value of Temperature and Humidity
        f = urllib2.urlopen(base_URL + '&field1=%s&field2=%s ' % (HUM, TEMP))
        print(f.read()) # print function value
        f.close() # close function
        wait.sleep(15) # delay of 15 Sec
    except:
        print 'exit from program ' # print string on terminal
        break

# calling main function
if __name__ == '__main_function_':
    main_function()
```

# 10.2 Ultrasonic Sensor Data Logger with ThingSpeak Server

The ultrasonic sensor is designed to measure distance between the source and target using ultrasonic waves. HC-SR04 is a commonly module for distance measurement for distances from 2 to 400 cm. The time taken by sound waves between transmission and reception is calculated. To measure distance, the system is comprised of a Raspberry Pi, a power supply, and an ultrasonic sensor. Connect pin (Vcc) and pin (GND) of the