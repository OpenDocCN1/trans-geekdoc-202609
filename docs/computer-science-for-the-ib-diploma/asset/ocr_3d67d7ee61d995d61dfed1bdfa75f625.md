3 Configure hostapd to use that configuration file by editing /etc/default/hostapd.
4 Prevent the wireless network card from being managed by the default network manager by changing /etc/
dhcpcd.conf and specifying denyinterfaces wlan0.

# **For the Raspberry Pi designated as DHCP server:**

+   1 Install isc-dhcp-server as a DHCP server.
+   2 The main configuration files will be /etc/dhcp/dhcpd.conf and /etc/default/isc-dhcp-server.
+   3 An example template for /etc/dhcp/dhcpd.conf is:

```
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.10 192.168.1.100;
  option domain-name-servers 192.168.1.1;
  option routers 192.168.1.1;
  default-lease-time 600;
  max-lease-time 7200;
}
```

+   4 Ensure the DHCP server is configured to start on boot.
+   5 Check the logs for errors by using cat /var/log/syslog | grep dhcp.

# **For the Raspberry Pi designated as web server:**

+   1 Ensure the Raspberry Pi is obtaining an IP address from the DHCP server. This Pi will need a static IP (so other Pi
+   computers can find it to request a webpage), so the DHCP server will need the MAC address of this Pi so as to
+   assign it the same IP address each time. To view the IP address from the console, use the command ip a.
+   2 Install nginx as the web server software, and set it to start automatically on boot.
+   3 Create a web page at /var/www/html.
+   4 The main configuration files for nginx can be found in /etc/nginx.
+   5 If nginx fails to start, you can check for configuration errors by using sudo nginx -t.
+   6 An example HTML file for /va/www/html/index.html might resemble:

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Welcome to Pi Web Server</title>
</head>
<body>
  <h1>Hello, Raspberry Pi Network!</h1>
  <p>This is a simple web page served from the Raspberry Pi web server.</p>
</body>
</html>
```

# **For the Raspberry Pi designated as proxy server:**

+   1 Ensure the Raspberry Pi is obtaining an IP address from the DHCP server. This Pi will need a static IP (so other Pi
+   computers can find it to request a webpage), so the DHCP server will need the MAC address of this Pi so as to
+   assign it the same IP address each time. To view the IP address from the console, use the command ip a.
+   2 Install squid proxy server software, and set it to start automatically on boot.
+   3 The main configuration file is at /etc/squid/squid.conf.