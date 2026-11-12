be used to uniquely identify a person. The extracted features are stored as templates in the database.

# 12.3.4 MATCHING

For a given test or a query image, the features are extracted and are compared with the reserved templates of the database to measure the level of closeness between the template and the extracted features of the clamming person. A decision is then made as to whether the individual or the user is a genuine (authorized or enrolled user) or an impostor(unauthorized user) depending on the observed closeness measure.

# 12.3.5 DATABASE

The feature set extracted from the raw biometric data (i.e., the template) is stored in the database along with some additional information (such as name, Personal Identification Number, address, etc.) representing the user.

# 12.4 HARDWARE IMPLEMENTATION AS IOT DEVICE

Raspberry Pi is a small card size computer that operates on Debian Linux. It is easy to use and learn. The operating system of Raspberry Pi can be installed easily by just adding a simple SDcard. The SD card will contain the OS, and it will be added into the Pi board and to power this board a simple USB mobile charger will be required, after this just connect the keyboard and mouse and a TV or computer will be connected by an HDMI cable and it is ready for use. If we need to work on a Windows platform, we might need Putty and VNC Viewer application toopen the Pi desktop on the Windows platform. Now, as the Pi desktop is opened it can do multiple things you can send emails or create spreadsheets. Raspberry Pi provides us with an opportunity to code with scratch or Python. As we are here working with an optical fingerprintsensor R307, we need to import multiple libraries like OpenCV or others. Raspberry Pi contains a command prompt from which we can import the libraries. It contains Ides so that we can code easily and run to see the function happening properly. So here we can start our work; the fingerprint sensor will capture the image of the fingerprint and store it in the PI and with the help of OpenCV which will