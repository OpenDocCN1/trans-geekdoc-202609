```
c:\> mkdir c:\dev\sfproject
c:\> cd c:\dev\sfproject
```

Windows users are advised to run symfony and to setup their new project in a path which contains no spaces. Avoid using the Documents and Settings directory, including anywhere under My Documents.

If you create the symfony project directory under the web root directory, you won't need to configure your web server. Of course, for production environments, we strongly advise you to configure your web server as explained in the web server configuration section.

# Choosing the Symfony Version

Now, you need to install symfony. As the symfony framework has several stable versions, you need to choose the one you want to install by reading the installation page20 on the symfony website.

# Choosing the Symfony Installation Location

You can install symfony globally on your machine, or embe d it into each of your projects. The latter is the recommended approach as projects will then be totally independent from each other and upgrading your locally installed symfony won't break some of your projects unexpectedly. It also means you will be able to have projects using different versions of symfony, and upgrade them one at a time as you see fit.

As a best practice, many people install the symfony framework files in the lib/vendor project directory. So, first, create this directory:

```
$ mkdir -p lib/vendor
```

# Installing Symfony

# Installing from an archive

The easiest way to install symfony is to download the archive for the version you choose from the symfony website. Go to the installation page for the version you have just chosen, symfony 1.421 for instance.

Under the "Source Download" section, you will find the archive in .tgz or in .zip format. Download the archive, put it under the freshly created lib/vendor/ directory, un-archive it, and rename the directory to symfony:

```
$ cd lib/vendor
$ tar zxpf symfony-1.4.0.tgz
$ mv symfony-1.4.0 symfony
$ rm symfony-1.4.0.tgz
```

Under Windows, unzipping the zip file can be achieved using Windows Explorer. After you rename the directory to symfony, there should be a directory structure similar to c:\dev\sfproject\lib\vendor\symfony.

20. http://www.symfony-project.org/installation
21. http://www.symfony-project.org/installation/1 4