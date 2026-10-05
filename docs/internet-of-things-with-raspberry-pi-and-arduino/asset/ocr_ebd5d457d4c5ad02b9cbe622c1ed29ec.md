# # 11
Blynk Application with Raspberry Pi

# ## 11.1 Introduction to Blynk

There are three major components in the platform:

+   - **Blynk App**—Allow to create an interface by using various widgets.
- **Blynk Server**—It is responsible for the communication between the smartphone and hardware. It is an open-source platform.
- **Blynk Library**—Blynk can work with Arduino, Raspberry Pi, or on similar boards.

Blynk works with any model of Raspberry Pi through Wi-Fi/Ethernet.

# ### 11.1.1 Installing Blynk on Raspberry Pi

To install Blynk on Raspberry Pi, first install the Blynk libraries. It is required to have the latest version of Raspian to install Blynk on Pi.

```
sudo apt-get update
sudo apt-get install git-core // If Git is not installed, install it
git clone git://git.drogeon.net/weiringPi // Install WiringPi using GIT
cd wiringPi // go to wiringPi and run the build.
./build
```

To install Blynk globally, run the commands:

```
git clone https://github.com/blynkkk/blynk-library.git
cd blynk-library/linux
make clean all target=raspberry
sudo./blynk --token=token <num> // authentication token
```

Figure 11.1 shows the window after the execution of the commands.