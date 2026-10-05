# #7

# ## Python and Arduino with Pyfirmata

# ### 7.1 Python with Arduino

Arduino is an open-source platform to build hardware and software environments. Arduino provides limitless possibilities for tinkerers and electronics enthusiasts.

Raspberry Pi is a full-fledged computer that can do tasks like a desktop PC. It provides a platform for coding and designing electronic circuits, from creating a web server to a gaming console for retro gaming.

Arduino does not understand Python, so Firmata and Pyfirmata protocols are used to communicate through Raspberry Pi using Python. Pyfirmata is a protocol for Raspberry Pi to access Arduino. The program will be written on interface with Raspberry Pi with Python. Firmata is protocol for Arduino to interface with Raspberry Pi in Python to access sensors connected to Arduino.

To install Firmata to Arduino, connect it to a USB socket of Raspberry Pi to communicate and power up Arduino. Next, install Firmata sketch to the Arduino in order for this open an Arduino IDE. Find the Firmata sketch in File→Examples→Firmata→StandardFirmata and upload it to the Arduino board. Once Firmata is installed, Arduino waits for communication from Raspberry Pi.

The next step is to install Pyfirmata to Raspberry Pi. For this, just run the following terminal commands on Raspberry Pi:

```
$ sudo apt-get install git
$ sudo git clone https://github.com/tino/pyfirmata.git
$ cdpyFirmata
$ sudo python setup.py install'
```