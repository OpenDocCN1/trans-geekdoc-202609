while True:

```
RAJ_dist = distance()
print("DISTANCE = %.1f cm" % RAJ_dist)
RAJ_lcd.clear()#the contents of LCD
RAJ_lcd.message('DIST = %.1f cm' % RAJ_dist)
wait.sleep(1)
```

exceptKeyboardInterrupt:
print("stop measurement")
ANITA.cleanup()

# 5.23 Interfacing of Camera with Raspberry Pi

A camera is used to take still pictures or videos. The interfacing of Raspberry Pi with a camera module can be done with Python and Picamera. Switch off the Raspberry Pi then connect the camera to the camera port and switch on the Raspberry Pi.

# 5.23.1 Configuring the Camera with Raspberry Pi

+   1. Connect the camera and start up the Raspberry Pi.
2. Open the configuration tool from the main menu (Figure 5.37).
3. Enable the camera software and reboot the Raspberry Pi (Figure 5.38).

# 5.23.2 Capturing the Image with Pi Camera

+   1. Make a new editable file using the command sudano image_RAJ.py on Pi terminal

```
frompicamera import PiCamera
import time as wait
RAJ_camera = PiCamera()
RAJ_camera.start_preview()
wait.sleep(10)
RAJ_camera.stop_preview()
```