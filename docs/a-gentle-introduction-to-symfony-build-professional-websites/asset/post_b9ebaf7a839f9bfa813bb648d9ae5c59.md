
actions.class.php
config/
security.yml
lib/
BasesfSampleModuleActions.class.php
templates/
indexSuccess.php
web/
css/
sfSampleStyle.css
images/
sfSampleImage.png

For authoring, the location of the plug-in directory (sfSamplePlugin/ in Listing 17-22) is not important. It can be anywhere on the disk.

> Take examples of the existing plug-ins and, for your first attempts at creating a plug-in, try to reproduce their naming conventions and file structure.

## Creating the package.xml File

The next step of plug-in authoring is to add a package.xml file at the root of the plug-in directory. The package.xml follows the PEAR syntax. Have a look at a typical symfony plug-in package.xml in Listing 17-23.

## Listing 17-23 - Example package.xml for a Symfony Plug-In

```
<?xml version="1.0" encoding="UTF-8"?>
<package packagerversion="1.4.6" version="2.0" xmlns="http://pear.php.net/dtd/package-2.0" xmlns:tasks="http://pear.php.net/dtd/tasks-1.0"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://pear.php.net/dtd/tasks-1.0 http://pear.php.net/dtd/tasks-1.0.xsd http://pear.php.net/dtd/package-2.0.xsd">
<name>sfSamplePlugin</name>
<channel>plugins.symfony-project.org</channel>
<summary>symfony sample plugin</summary>
<description>Just a sample plugin to illustrate PEAR packaging</description>
<lead>
<name>Fabien POTENCIER</name>
<user>fabpot</user>
<email>fabien.potencier@symfony-project.com</email>
<active>yes</active>
</lead>
<date>2006-01-18</date>
<time>15:54:35</time>
<version>
<release>1.0.0</release>
<api>1.0.0</api>
</version>
<stability>
<release>stable</release>
<api>stable</api>
</stability>
<license uri="http://www.symfony-project.org/license">MIT license</license>
<notes>-</notes>
<contents>
<dir name="/" />
<file role="data" name="README" />
<file role="data" name="LICENSE" />
<dir name="config">
<!-- model -->
<file role="data" name="schema.yml" />
<file role="data" name="ProjectConfiguration.class.php" />
</dir>
<dir name="data">
<dir name="fixtures">
<!-- fixtures -->
<file role="data" name="fixtures.yml" />
</dir>
</dir>
<dir name="lib">
<dir name="model">
<!-- model classes -->
<file role="data" name="sfSampleFooBar.php" />
<file role="data" name="sfSampleFooBarPeer.php" />
</dir>
<dir name="task">
<!-- tasks -->
<file role="data" name="sfSampleTask.class.php" />
</dir>
<dir name="validator">
<!-- validators -->
<file role="data" name="sfSampleValidator.class.php" />
</dir>
</dir>
<dir name="modules">
<dir name="sfSampleModule">
<file role="data" name="actions/actions.class.php" />
<file role="data" name="config/security.yml" />
<file role="data" name="lib/BasesfSampleModuleActions.class.php" />
<file role="data" name="templates/indexSuccess.php" />
</dir>
</dir>
<dir name="web">
<dir name="css">
<!-- stylesheets -->
<file role="data" name="sfSampleStyle.css" />
</dir>
<dir name="images">
<!-- images -->
<file role="data" name="sfSampleImage.png" />
</dir>
</dir>
</dir>
</contents>
<dependencies>
<required>
<php>
<min>5.2.4</min>
</php>
<pearinstaller>
<min>1.4.1</min>
</pearinstaller>
<package>
<name>symfony</name>
<channel>pear.symfony-project.com</channel>
<min>1.3.0</min>
<max>1.5.0</max>
<exclude>1.5.0</exclude>
</package>
</required>
</dependencies>
<phprelease />
<changelog />
</package>
```

The interesting parts here are the `<contents>` and the `<dependencies>` tags, described next. For the rest of the tags, there is nothing specific to symfony, so you can refer to the PEAR online manual for more details about the package.xml format.

## Contents

The `<contents>` tag is the place where you must describe the plug-in file structure. This will tell PEAR which files to copy and where. Describe the file structure with `<dir>` and `<file>` tags. All `<file>` tags must have a role="data" attribute. The `<contents>` part of Listing 17-23 describes the exact directory structure of Listing 17-22.

> The use of `<dir>` tags is not compulsory, since you can use relative paths as name values in the `<file>` tags. However, it is recommended so that the package.xml file remains readable.

## Plug-In Dependencies

Plug-ins are designed to work with a given set of versions of PHP, PEAR, symfony, PEAR packages, or other plug-ins. Declaring these dependencies in the `<dependencies>` tag tells PEAR to check that the required packages are already installed, and to raise an exception if not.

You should always declare dependencies on PHP, PEAR, and symfony, at least the ones corresponding to your own installation, as a minimum requirement. If you don't know what to put, add a requirement for PHP 5.2.4, PEAR 1.4, and symfony 1.3.

It is also recommended to add a maximum version number of symfony for each plug-in. This will cause an error message when trying to use a plug-in with a more advanced version of the framework, and this will oblige the plug-in author to make sure that the plug-in works correctly with this version before releasing it again. It is better to have an alert and to download an upgrade rather than have a plug-in fail silently.

If you specify plugins as dependencies, users will be able to install your plugin and all its dependencies with a single command:

```
$ php symfony plugin:install --install-deps sfSamplePlugin
```

## Building the Plug-In

The PEAR component has a command (pear package) that creates the .tgz archive of the package, provided you call the command shown in Listing 17-24 from a directory containing a package.xml.

## Listing 17-24 - Packaging a Plug-In As a PEAR Package

```
$ cd sfSamplePlugin
$ pear package

Package sfSamplePlugin-1.0.0.tgz done
```

Once your plug-in is built, check that it works by installing it yourself, as shown in Listing 17-25.

## Listing 17-25 - Installing the Plug-In

```
$ cp sfSamplePlugin-1.0.0.tgz /home/production/myproject/
$ cd /home/production/myproject/
$ php symfony plugin:install sfSamplePlugin-1.0.0.tgz
```

According to their description in the <contents> tag, the packaged files will end up in different directories of your project. Listing 17-26 shows where the files of the sfSamplePlugin should end up after installation.

## Listing 17-26 - The Plug-In Files Are Installed on the plugins/ and web/ Directories

```
plugins/
sfSamplePlugin/
README
LICENSE
config/
schema.yml
sfSamplePluginConfiguration.class.php
data/
fixtures/
fixtures.yml
lib/
model/
sfSampleFooBar.php
sfSampleFooBarPeer.php
task/
sfSampleTask.class.php
validator/
sfSampleValidator.class.php
modules/
sfSampleModule/
actions/
actions.class.php
config/
security.yml
lib/
BasesfSampleModuleActions.class.php
templates/
indexSuccess.php
web/
sfSamplePlugin/    ## Copy or symlink, depending on system
css/
sfSampleStyle.css
images/
sfSampleImage.png
```

Test the way the plug-in behaves in your application. If it works well, you are ready to distribute it across projects—or to contribute it to the symfony community.

## Hosting Your Plug-In in the Symfony Project Website

A symfony plug-in gets the broadest audience when distributed by the symfony-project.org website. Even your own plug-ins can be distributed this way, provided that you follow these steps:

- 1. Make sure the README file describes the way to install and use your plug-in, and that the LICENSE file gives the license details. Format your README with the Markdown Formatting syntax.
- 2. Create a symfony account (http://www.symfony-project.org/user/new) and create the plugin (http://www.symfony-project.org/plugins/new).
- 3. Create a PEAR package for your plug-in by calling the pear package command, and test it. The PEAR package must be named sfSamplePlugin-1.0.0.tgz (1.0.0 is the plug-in version).
- 4. Upload your PEAR package (sfSamplePlugin-1.0.0.tgz).
- 5. Your plugin must now appear in the list of plugins.

If you follow this procedure, users will be able to install your plug-in by simply typing the following command in a project directory:

```
$ php symfony plugin:install sfSamplePlugin
```

## Naming Conventions

To keep the plugins/ directory clean, ensure all the plug-in names are in camelCase and end with Plugin (for example, shoppingCartPlugin, feedPlugin, and so on). Before naming your plug-in, check that there is no existing plug-in with the same name.

> > Plug-ins relying on Propel should contain Propel in the name (the same goes for if you use Doctrine). For instance, an authentication plug-in using the Propel data access objects should be called sfPropelAuth.

Plug-ins should always include a LICENSE file describing the conditions of use and the chosen license. You are also advised to add a README file to explain the version changes, purpose of the plug-in, its effect, installation and configuration instructions, etc.

## Summary

The symfony classes notify events that give them the ability to be modified at the application level. The event mechanism allows multiple inheritance and class overriding at runtime even if the PHP limitations forbid it. So you can easily extend the symfony features, even if you have to modify the core classes for that—the factories configuration is here for that.

Many such extensions already exist; they are packaged as plug-ins, to be easily installed, upgraded, and uninstalled through the symfony command line. Creating a plug-in is as easy as creating a PEAR package, and provides reusability across applications.

The symfony plugin section contains many plug-ins, and you can even add your own. So now that you know how to do it, we hope that you will enhance the symfony core with a lot of useful extensions!
