```
<?php
// Login to the connection
// ... (code block content)
?>
```

# # Building FTP Clients

The FTP functions were designed to be low level. This approach gives developers the control they need to build advanced FTP applications. The trade-off for this extra control is that extra effort is required to build the applications. Every step in the process must be explicitly called, thus making the extension inconvenient to use.

Now let's build two simple applications:

+   - A wrapper that makes the FTP functions more convenient to use. This wrapper will be optimized for scripts that need to transfer files between FTP servers and local file systems.

+   - A basic web-based FTP client. This application will be designed for users who need to transfer files to and from public FTP sites.