
Press `CTRL-C` in the terminal window to stop `cansniffer` when you’ve experimented enough. Don’t worry if the packets were going by too quickly for you to pick out specific IDs. The next step will be to record some packets so you can study them in your own time.

## Capturing Packets

The can-utils tool `candump` records messages from a CAN bus so that we can analyze them further or even replay them.

1. To start recording packets from `vcan0`, enter this command:

```
kali@kali:~/ICSim$ candump -l vcan0
```

The `-l` option (that’s a hyphen and a lowercase `l`) is short for `log`, because we’re asking `candump` to log its output by saving the data into a file.

2. Switch back to the CANBus Control Panel window and drive for a few seconds. Speed up and slow down, use your left and right turn signals, and unlock and lock the doors.

3. Press `CTRL-C` to stop recording.

4. In the terminal window, enter `ls` (short for `list`) to show the contents of the `ICSim` directory. You should see a new file in the format `candump-YYYY-MM-DD_time.log` (time is defined in hours, minutes, and seconds—`HHMMSS`), such as in this example:

```
candump-2021-05-18_113713.log
```

The `candump` logfile is a simple text file. You can view the file in a text editor and use `CTRL-F` to find specific CAN ID values, like `188` for the turn signals, as shown in [Figure 10-4](#c10.xhtml#figure10-4).

![Figure 10-4: Searching for specific CAN ID values in the Mousepad text editor](image_fi/502000c10/f10004.png)

Figure 10-4: Searching for specific CAN ID values in the Mousepad text editor

## Replaying Packets

By resending the packets we captured in the logfile on the `vcan0` network, we can make the dashboard “relive” the recorded driving session. This kind of hack is called a `replay attack`.

1. First, close the CANBus Control Panel. The controller window sends signals constantly even when idle, and we want to use only the packets we’ve captured to control the dashboard.

2. Enter the following command into the terminal window to replay the logfile with the `canplayer` tool, replacing `candump-YYYY-MM-DD_time.log` with your logfile name:

```
kali@kali:~/ICSim$ canplayer -I candump-YYYY-MM-DD_time.log
```

3. Your ICSim dashboard should begin moving exactly the same way it did when you captured the packets originally. In [Figure 10-5](#c10.xhtml#figure10-5), for example, I’m turning right and unlocking all four doors while driving over 90 miles per hour! (I don’t recommend doing this in your real car.)

![Figure 10-5: The replayed packets are controlling the dashboard.](image_fi/502000c10/f10005.png)

Figure 10-5: The replayed packets are controlling the dashboard.

Many IoT devices are vulnerable to replay attacks like this one. For example, when they first came out, many Bluetooth door locks were subject to such attacks. With a laptop running a Bluetooth wireless sniffer (like `Kismet`, which is included with Kali) and a physical Bluetooth antenna (like the `Ubertooth One` for around $100), you could capture packets while someone was opening the door with their smartphone and replay those packets to unlock the door anytime you wanted. Nowadays, to prevent replay attacks, a special value is added to each message so the system can tell whether it’s receiving a new message or one it’s seen before.

## Sending New Commands

Car hackers can analyze `candump` logfiles to decipher CAN ID numbers and figure out what the data values in each message mean. Armed with that knowledge, hackers can send specific commands to the system to make the car do what they want. For example, sending the message `02000000` to ID# `188` turns on the right turn signal. Let’s try it out!

Enter the following command into the terminal with ICSim open and the controller window closed:

```
kali@kali:~/ICSim$ cansend vcan0 188#02000000
```

We use `cansend` to send a CAN message to `vcan0`. The message contains the ID number of the turn signals (`188`), then the hash mark (`#`) as a separator, and finally the data value that represents the right turn signal (`02000000`). The right turn signal on your dashboard should light up green.

If you want to turn on the left signal instead, send this message:

```
kali@kali:~/ICSim$ cansend vcan0 188#01000000
```

To turn off the signals, send the message `188#00000000`. Or use this command to turn `on` both signals at the same time:

```
kali@kali:~/ICSim$ cansend vcan0 188#03000000
```

Now take a look at the data values in CAN packets related to the speedometer (ID# `244`) in your `candump` logfile. It looks like the last four hexadecimal digits go up as the speed increases. The data value `0000000000` is 0 miles per hour, and `0000003894` corresponds to about 90 miles per hour. Let’s see what the value `0000009999` would do:

```
kali@kali:~/ICSim$ cansend vcan0 244#0000009999
```

As you can see in [Figure 10-6](#c10.xhtml#figure10-6), the speedometer jumps to 240 miles per hour! You can go even higher using hexadecimal—try changing the last four digits to `A000`, `B000`, or even `FFFF`.

![Figure 10-6: We can control the dashboard by sending signals directly to the CAN bus using `cansend`.](image_fi/502000c10/f10006.png)

Figure 10-6: We can control the dashboard by sending signals directly to the CAN bus using `cansend`.

Similarly, we can lock all the doors by sending the message `19B#00000F000000` and unlock all the doors with the message `19B#000000000000` (that’s 12 zeros after the hash mark):

```
kali@kali:~/ICSim$ cansend vcan0 19B#00000F000000
kali@kali:~/ICSim$ cansend vcan0 19B#000000000000
```

Our virtual car thinks it’s turning both left and right and unlocking all four doors while zipping around at 240 miles per hour!

## How Attackers Hack Real Cars

To use the same `can-utils` tools and skills you just learned about to hack a real car, all an attacker needs is a laptop running Kali Linux and a cable to connect the laptop to the `on-board diagnostic, version two (OBD-II)` port, located under the steering wheel in most cars. Many such cables are available for under $100. However, real-world car hacking is a serious matter that can lead to significant property damage or injury. Researchers practice car hacking in controlled conditions to look for security vulnerabilities. If you practice car hacking, be sure to do it safely in your garage or driveway or on a closed course; never hack a car on the road or anywhere someone could get hurt.

Car hackers don’t always have to maintain a wired connection with a vehicle to send commands. After finding useful CAN ID numbers and messages by connecting directly to a particular make and model of car, an attacker or security researcher could attempt to connect to the car wirelessly via Bluetooth, Wi-Fi, or 4G/5G to try to send CAN messages remotely. One high-profile hack used the driver’s hands-free smartphone connection to take remote control of the car through the car’s dashboard entertainment system. Another used Tesla’s 4G wireless over-the-air update system to install malicious software and tamper with the car from far away.

One piece of good news is that every car is slightly different, and the CAN ID numbers in one car usually aren’t the same as the CAN IDs in another car. Every manufacturer uses different codes, and sometimes every model from the same manufacturer uses a different set of codes, and those codes can change from one model year to the next! Plus, there are several different types of controller networks on modern cars; the `CAN` is just the most common one. In short, it takes a lot of patience to crack the codes on a real car.

## The Takeaway
