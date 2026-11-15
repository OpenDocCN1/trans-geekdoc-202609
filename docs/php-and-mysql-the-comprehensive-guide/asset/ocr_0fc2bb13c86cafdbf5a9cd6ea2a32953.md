If you have not installed Composer globally, but composer.phar is available, use the following command:

```
php /path/to/composer.phar require cboden/ratchet
```

Ratchet is then installed on the system. Even autoloading is supported; the vendor/autoload.php file has been created or adapted accordingly. A simple require "vendor/autoload.php" (with a customized path if necessary) loads all the classes required for Ratchet (see Figure 28.6).

![](bbox=[0.145, 0.265, 0.71, 0.625])

# Figure 28.6 Installation of Ratchet via Composer

Ratchet has a namespace of the same name and a number of classes underneath it. Let's first take a look at the MessageComponentInterface interface, which defines four methods:

+   - onOpen()
+     Called when the connection to the WebSocket server is established
+   - onClose()
+     Called when the connection to the WebSocket server is closed again
+   - onMessage()
+     Called when a message has been sent to the server
+   - onError()
+     Called when an error occurs