6. WHAT’S NEXT?

# ## Editor/IDE Integration

As mentioned before, I tend to use PhpStorm when doing PHP coding work. Out-of-the-box, it comes with a lot of tooling that makes writing PHP code easier. But its real strength is a plugin system that allows third parties to extend functionality and integration points to allow the use of CLI tools from inside the IDE.

If an external tool can be easily used within the IDE, spend the time to configure it. I like the ability to click a button to run a PHPUnit test case instead of always changing focus back to a terminal shell.

Reducing friction in your tooling is critical. I am always looking at how other developers accomplish similar tasks. Video pairing sessions where I watch people really leverage their tools are a great way to re-examine and evaluate what I am doing.

# ## Containerized Development Environments

In my evaluation of Visual Studio Code\[^1] I was encouraged by long-time online friend Alvaro Videla\[^2] to take a look at the Remote Containers\[^3] extension, which provides the glue many other editors are missing to allow you to create and use containerized development environments using Docker\[^4]. It took me less than 30 minutes from reading the first bits of documentation to having a working development environment that works hand-in-hand with Visual Studio.

I also am aware you can do similar things with Docker and PhpStorm, but my own experiences were not as smooth as what Code provided. Making sure all developers on a project have a consistent, repeatable development environment can go a long way toward eliminating the “works for me” category of bugs.

+   \[1] https://code.visualstudio.com  
\[2] https://twitter.com/old\_sound  
\[3] https://code.visualstudio.com/docs/remote/create-dev-container  
\[4] https://docker.com