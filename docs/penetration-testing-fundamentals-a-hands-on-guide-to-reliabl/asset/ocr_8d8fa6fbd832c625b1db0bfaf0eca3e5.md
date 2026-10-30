4. You have been asked to perform a penetration test of a small university. Which of the following would be the best time to attempt a DoS test?

+   - A. Monday morning very early
+   - B. Friday evening before a long weekend
+   - C. Finals week
+   - D. Registration week

# PROJECTS

# PROJECT 1: Denial of service

Select an isolated Windows machine, preferably one in a lab. Turn on IIS (Windows web server) so you have a web server target. This is easy to do:

If you do not have IIS installed, accessing **Control Panel > Programs > Programs & Features** will allow you to add it.

Then open a browser, and direct it to the IP address of this machine (both computers should be on the same network). You will then see the default IIS website.

Then use any of the DoS tools mentioned in this chapter to attack that website. Every few seconds, while the attack is ongoing, refresh the browser and see what happens to website response time.

# PROJECT 2: Wi-Fi

Set up your computer as a hotspot, and have a partner access it. If you are using a Windows computer, you can follow the instructions in this chapter. If you are using Linux, then use Wifi-Honey. You may wish to also run a packet sniffer while your partner surfs the web through your fake hotspot.