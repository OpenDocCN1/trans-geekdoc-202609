# Providing Help-desk Support

Finally, Remote Desktop Services can make application support easier, not just in terms of installing new applications and fixing but in terms of helping people learn to use those applications. Remote Desktop Shadowing (previously called Remote Control) lets help-desk personnel or administrators connect to another person's remote session to watch what they're doing or to interact with them. This doesn't happen automatically and requires some sort of input from an administrator and a user. You can control some of their behavior using a GPU.

When you have remote control of another user's session, you can either watch what they're doing and coach them (perhaps over the telephone) or actually interact with the session so that you can demonstrate a process. This beats standing over someone's shoulder, "Click the File button at the top left. No, File. The FILE button," or trying to figure out what they're doing when your information comes from their description of the screen.

# Deploying RDS RemoteApp

RemoteApp programs are applications that are running on the RD Session Host server but appear to the end user to be running on their. This is often easier for an end user to conceptualize. They don't have to manage multiple desktops but instead can simply launch another application from their main desktop.

Windows Server 2008 introduced RemoteApp programs, and they've improved in every generation of Windows, including Windows 2012 R2. Here are some of the new enhancements into this release:

+   **RemoteApp Rotation** Faster resolution and rotation on client machines including changing the remote session's resolution.

+   **Monitor Hot-add/substract** If you add a monitor, it will allow you to move it to any and readjust if you need to.

+   **Click Once App Support** Users can now install apps directly from the browser, rather than having an administrator deploy and deploy them in previous versions.

+   **Hi-fi RemoteApp** This enables support for apps that use Desktop Window Manager. You can now get transparent notifications with fading effects.

Do take into account that it requires a bit of configuration to support RemoteApp programs. However, once you've configured all the pieces, users can access RemoteApp applications via the following methods:

+   **Through a Web Browser** If RD Web Access is configured, users can access the web page and click a link to launch the RemoteApp.

+   **Using a Remote Desktop Protocol File** Users can double-click-a properly configured .rdp file to launch the menu or RemoteApp application.

+   **Through the Start Menu or a Program Icon** RemoteApplications can be installed using traditional Windows (.msi) packages (also called Microsoft Installer packages). Once they're installed, users can launch the applications just like any other installed application. Or they can use the new Click Once deployment method.

You'll learn how to install all the components and deploy RemoteApp applications for each of the methods shown in the section "Adding Remote Desktop Services" later in this chapter.