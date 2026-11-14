function that we specify. In our case, the success function just runs a function called hacked that’s in the remotely loaded file. When the hacked function runs, it just creates a new alert box, but it can do anything that you can do with JavaScript, such as spoofing a login box or keylogging a victim.

# Framework Vulnerabilities

Using frameworks is an amazing way to develop code more quickly and to gain functionality without having to write a ton of code. In 2017, a number of these frameworks were being used, but two of the higher-profile vulnerabilities occurred in a framework called Struts that is part of the Apache projects. Struts is a framework that aids in web application development by providing interfaces such as REST, AJAX, and JSON through the Model-View-Controller (MVC) architecture. Struts was the source of one of the biggest breaches of the decade—the Equifax1 breach that impacted 143 million individuals.

# Setting Up the Environment

For the labs in this section, we’re going to use a web server with a vulnerable version of Struts. To do that, we need to build a different Docker image from the GitHub repository for this chapter. To begin with, we need to make sure our previous Docker image is stopped:

```
# docker container list -f "ancestor=xss"
CONTAINER ID        IMAGE               COMMAND                 CREATED
STATUS              PORTS               NAMES
caea75279d86        xss                 "/my_init"            39 hours ago
Up 39 hours         0.0.0.0:80->80/tcp  vigilant_goldwasser
# docker container stop caea75279d86
caea75279d86
```

If the first command returns a container, then issue the stop for that container ID. That should ensure our previous image is stopped. Next, we need to create our Tomcat image that has the vulnerable Struts libraries installed. The following commands assume that you are in the Ch16 directory of the GitHub repository for this book:

```
root@kali:~/Ch16# cd Vuln_Tomcat/
root@kali:~/Ch16/Vuln_Tomcat# docker build -t vuln_tomcat .
Sending build context to Docker daemon  566.9MB
Step 1/7 : FROM tomcat:9
<trimmed for brevity>
Successfully built f800d8acfe1e
Successfully tagged vuln_tomcat:latest
root@kali:~/Ch16/Vuln_Tomcat# docker run -p 8080:8080 -dti vuln_tomcat
f04e7d549f6a9758079c59319bf06134fff7f065e039624c8a88e851921fa502
```

Now our Tomcat instance should be up on port 8080. You can verify it is working by visiting http://localhost:8080 on the Kali 64-bit image.