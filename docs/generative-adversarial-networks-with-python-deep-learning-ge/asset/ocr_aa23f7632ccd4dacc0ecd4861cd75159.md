![](bbox=[0.18, 0.1, 0.81, 0.48])

# Figure C.8: Review Your Running Instance

Your server is now running and ready for you to log in.

# C.4 Login, Configure and Run

Now that you have launched your server instance, it is time to log in and start using it.

+   1. Click View Instances in your Amazon EC2 console if you have not done so already.
+   
+   2. Copy the Public IP (down the bottom of the screen in Description) to your clipboard. In this example my IP address is 54.186.97.77. **Do not use this IP address, it will not work as your server IP address will be different.**
+   
+   3. Open a Terminal and change directory to where you downloaded your key pair. Login to your server using SSH, for example:
+   
+   4. If prompted, type yes and press enter.

```
ssh -i keras-aws-keypair.pem ec2-user@54.186.97.77
```

# Listing C.2: Log-in To Your AWS Instance.