
## 14. Change to Router A

Type `show run` and press Enter. Even if you don't enter the whole command, Cisco IOS can still execute it as long as it is unique. Press the spacebar to advance to the end of your results. Scroll back up to see your two Fast Ethernet ports and two serial ports verifying that this is a router.

## 15. Switch to Lab Instructions

Switch to Lab Instructions on the top screen and go through the four available free labs to familiarize yourself with configuration of a Cisco router and switches. Go through the Boson demo labs at least twice if this is new to you. You may want to first watch the second YouTube video from Boson that explains their first lab, which can be located with keyword searches on `Boson NetSim 9`.

## Lab A8: Shopping for Wi-Fi Antennas

The correct placement and antenna type are critical for getting the best performance and security for your Wi-Fi clients. Installing a better antenna on your access point can greatly increase range and speed. Access points come with fixed, removable, or internal antennas. If the antenna is removable, the installer can replace it with one that provides a different gain or transmission pattern. Wireless routers with internal antennas don't allow you to go to a different antenna to obtain a stronger signal. For these systems, a powered signal repeater can be installed to boost range. When making informed decisions about a wireless network, an administrator must be aware of the technologies available. Special wireless certifications are available, but a CASP must be familiar with antenna types and decibels. Your focus here is on replacing an access point's removable antenna with a better one based on the needs determined by a wireless site survey.

Omnidirectional antennas are common on small office, home office (SOHO) wireless routers or enterprise-grade access points. The radio signal radiates out in all directions (360°). The shape is smashed at the top and bottom with a stronger signal side to side. That is more like a donut than a ball. The antennas are considered to be like a stick, and they are sometimes called `rubber ducks` because they are somewhat flexible and rubber-coated. A factory-installed omnidirectional antenna typically boosts the signal around 3 decibels (dB). Range is considered to be about 100 meters with 2.4 GHz band. The same antenna is usually also used for transmissions in the 5 GHz band. You could compare this to the light from a table lamp with a shade. Omnidirectional antennas are typically used for point-to-multipoint connections.

Antenna gain (increase) is measured in decibels. The decibel scale is a logarithmic scale used to denote the ratio of one power value to another. The greater the decibels, the stronger the signal output.

Direction is the shape of the transmission pattern. A good analogy for an antenna is the reflector in a flashlight. The reflector concentrates and intensifies the light beam in a particular direction similar to what a Yagi or dish antenna would do to a Wi-Fi RF signal.

Directional antennas come in different styles and shapes. An antenna does not amplify or boost the signal; it simply redirects the energy received from the transmitter. A directional antenna can focus more energy in one direction and less energy in all other directions. As the signal gain of a directional antenna increases, the angle the signal is transmitted to decreases. Directional antennas provide greater range but with a reduced coverage angle. This is like the cone of light you would get from a desk lamp with a reflector.

Directional Wi-Fi antennas come in three basic types:

*   **Patch or panel antennas** broadcast in a single direction typically for multiple users.
*   **Yagi antennas** are long-range point-to-point connections typically between structures.
*   **Parabolic dishes** (like a satellite dish) or grid antennas have a very narrow RF energy path and must be carefully aimed at the receiving antenna. They focus a narrow beam almost like a laser and are used for long-range point-to-point connections between outdoor structures.

### Let's go shopping for antennas:

1.  Point your browser to `www.amazon.com` and search for `WiFi Antennas`.
2.  Narrow your search by choosing Computer Networking Antennas on the left.
3.  Continue to become more selective by choosing 2.4 GHz and three stars or better.
4.  Sort your antenna by choosing Low to High pricing from the drop-down at the right top.
5.  Under $10 you will see several rubber duck omnidirectional antennas. They do not normally use cables because of the high signal loss but connect directly to the wireless router or AP.
6.  Scroll down to view some higher-priced antennas. You will see some panel-type and parabolic directional antennas. You will also see some sets of three antennas for use on newer wireless routers that support Multi-input multi-output (MIMO) on IEEE 802.11n. With MIMO, a wireless router will have multiple transmitters and receivers to increase bandwidth and range. Gain will typically be listed as under 10 dB and will provide two to four times the signal strength of typically factory antennas in all directions.
7.  At around $20 you will start seeing patch or panel-style antennas, which look like a plastic book with a cable attached. Gain for these directional antennas will increase above 10 dBi. You can compare the panel antenna to an outdoor light mounted on a wall to light up the area by your front door. The signal only moves in one direction, commonly away from the wall to a fairly wide area. Panel antennas are typically used for point-to-multipoint connections.
8.  Yagi antennas will typically be a like a square pipe with a series of elements on it and a wire attached. Gain will be more like 18 dB, providing more than 10 times the range and power of a factory omnidirectional antenna. The Yagi is more like a spotlight mounted on the wall. It produces a strong signal but to a very limited area. Yagi antennas are normally used point to point between buildings. The Yagi used to receive is like a telescope for radio waves, gathering and enhancing even very weak incoming signals but only from a small area. Many Yagi and panel antennas are weatherproof and designed for outdoor use mounted on a pole or wall.

## Lab A9: Cloud Provisioning

Virtual servers running on rented hardware offer a great way to test or provide rapid deployment of resources on the Web using a cloud service provider. This is a rapidly changing field, so you may need to look for a different site than the one specified here.

Google Compute Engine is a service that provides virtual machines that run on Google infrastructure (pooled servers and storage). You'll find a video showing how to set up a functional web server here:

[https://developers.google.com/compute/docs/quickstart](https://developers.google.com/compute/docs/quickstart)

Some of the top cloud providers currently are Amazon, Google, HP, IBM, Microsoft, Red Hat, and VMware. It is a good idea to familiarize yourself with what they offer. Most of the systems will have a way for you to sign up for a “free” trial of their service. Valid email accounts and credit card information will probably be required. Shop and compare; who is offering the best self-service deal this week?

The National Institute of Standards and Technology (NIST) has developed many important IT standards. Do some research on current topics such as cloud computing at `http://csrc.nist.gov/publications/PubsSPs.html`.

NIST's current information about the cloud states, “Cloud computing is a model for enabling convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction.”

This cloud model promotes availability and consists of five essential characteristics:

*   On-demand self-service
