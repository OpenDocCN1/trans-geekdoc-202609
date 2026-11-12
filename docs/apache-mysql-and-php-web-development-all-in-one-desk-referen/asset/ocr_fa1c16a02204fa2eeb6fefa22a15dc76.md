# # Chapter 4: Apache Modules

# ## In This Chapter

+   - Understanding Apache modules
+   - Installing Apache modules
+   - Finding out about useful Apache modules

Modules provide many of Apache's features. The following types of modules are available:

+   - **Base modules:** These modules are included with the Apache distribution and are enabled by default, meaning they're always available unless you disable them when installing Apache.
+   - **Extension modules:** These modules are also included in the Apache distribution, but they're not compiled by default. You must specifically enable these modules when installing Apache.
+   - **External modules:** These are third-party modules created for Apache.

# ## Installing Modules

You can compile modules in one of two ways:

+   - **Statically:** The module is compiled with Apache as part of the Apache binary. To add or remove the module, you must recompile Apache.
+   - **Dynamically:** You compile the module separately from Apache, as a Dynamically Shared Object (DSO). You use the `LoadModule` directive to include the module features as part of Apache at start up.

# ## Compiling modules

You can compile modules when Apache is installed. You enable modules during the configuration step in the installation procedure (see Book II, Chapter 2). To include a module, use the installation option, as follows:

```
./configure --enable-modulename
```