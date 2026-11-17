# # Hosting Your Plug-In in the Symfony Project Website

A symfony plug-in gets the broadest audience when distributed by the symfony-project.org website. Even your own plug-ins can be distributed this way, provided that you follow these steps:

+   1. Make sure the README file describes the way to install and use your plug-in, and that the LICENSE file gives the license details. Format your README with the Markdown⁶⁰ Formatting syntax.
+   2. Create a symfony account (http://www.symfony-project.org/user/new) and create the plugin (http://www.symfony-project.org/plugins/new).
+   3. Create a PEAR package for your plug-in by calling the pear package command, and test it. The PEAR package must be named sfSamplePlugin-1.0.0.tgz (1.0.0 is the plug-in version).
+   4. Upload your PEAR package (sfSamplePlugin-1.0.0.tgz).
+   5. Your plugin must now appear in the list of plugins⁶¹.

If you follow this procedure, users will be able to install your plug-in by simply typing the following command in a project directory:

```
$ php symfony plugin:install sfSamplePlugin
```

# # Naming Conventions

To keep the plugins/ directory clean, ensure all the plug-in names are in camelCase and end with Plugin (for example, shoppingCartPlugin, feedPlugin, and so on). Before naming your plug-in, check that there is no existing plug-in with the same name.

> > Plug-ins relying on Propel should contain Propel in the name (the same goes for if you use Doctrine). For instance, an authentication plug-in using the Propel data access objects should be called sfPropelAuth.

Plug-ins should always include a LICENSE file describing the conditions of use and the chosen license. You are also advised to add a README file to explain the version changes, purpose of the plug-in, its effect, installation and configuration instructions, etc.

# # Summary

The symfony classes notify events that give them the ability to be modified at the application level. The event mechanism allows multiple inheritance and class overriding at runtime even if the PHP limitations forbid it. So you can easily extend the symfony features, even if you have to modify the core classes for that—the factories configuration is here for that.

Many such extensions already exist; they are packaged as plug-ins, to be easily installed, upgraded, and uninstalled through the symfony command line. Creating a plug-in is as easy as creating a PEAR package, and provides reusability across applications.

The symfony plugin section contains many plug-ins, and you can even add your own. So now that you know how to do it, we hope that you will enhance the symfony core with a lot of useful extensions!