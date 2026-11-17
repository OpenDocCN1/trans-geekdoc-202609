# Installing Plug-Ins from a Version Control Repository

Plug-ins sometimes have their own source code repository for version control. You can install them by doing a simple checkout in the plugins/ directory, but this can be problematic if your project itself is under version control.

Alternatively, you can declare the plug-in as an external dependency so that every update of your project source code also updates the plug-in source code. For instance, Subversion stores external dependencies in the svn:externals property. So you can add a plug-in by editing this property and updating your source code afterwards, as Listing 17-14 demonstrates.

# Listing 17-14 - Installing a Plug-In from a Source Version Repository

```
$ cd myproject
$ svn propedit svn:externals plugins
pluginName  http://svn.example.com/pluginName/trunk
$ svn up
$ php symfony plugin:publish-assets
$ php symfony cc
```

> If the plug-in contains a web/ directory, the symfony plugin:publish-assets command has to be run to generate the corresponding symlink under the main web/ folder of the project.

# Activating a Plug-In Module

Some plug-ins contain whole modules. The only difference between module plug-ins and classical modules is that module plug-ins don't appear in the myproject/apps/frontend/modules/ directory (to keep them easily upgradeable). They also need to be activated in the settings.yml file, as shown in Listing 17-15.

# Listing 17-15 - Activating a Plug-In Module, in frontend/config/settings.yml

```
all:
  .settings:
    enabled_modules: [default, sfMyPluginModule]
```

This is to avoid a situation where the plug-in module is mistakenly made available for an application that doesn't require it, which could open a security breach. Think about a plug-in that provides frontend and backend modules. You will need to enable the frontend modules only in your frontend application, and the backend ones only in the backend application. This is why plug-in modules are not activated by default.

> The default module is the only enabled module by default. That's not really a plug-in module, because it resides in the framework, in sfConfig::get('sf_symfony_lib_dir')/controller/default/. This is the module that provides the congratulations pages, and the default error pages for 404 and credentials required errors. If you don't want to use the symfony default pages, just remove this module from the enabled_modules setting.

# Listing the Installed Plug-Ins

If a glance at your project's plugins/ directory can tell you which plug-ins are installed, the plugin:list task tells you even more: the version number and the channel name of each installed plug-in (see Listing 17-16).

# Listing 17-16 - Listing Installed Plug-Ins