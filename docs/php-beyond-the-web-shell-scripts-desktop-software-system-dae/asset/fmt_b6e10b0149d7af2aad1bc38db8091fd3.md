
Once the commands above have been run, you should find that a `.so` file (`pcntl.so` in our example) has been compiled and placed in PHP’s extension directory. The final step is to tell PHP about it, by adding the following line somewhere in your `php.ini` file:

```
extension=pcntl.so
```

If you’re not sure where your `php.ini` file is, you can run `php -i | grep "Loaded Configuration File"` on the command line to find out. You can also use `php -i` to check that your extension is now correctly installed and available for use.

### Installing multiple versions of PHP

Sometimes (particularly on development machines) you may want to install multiple versions of PHP at the same time, for instance if you are deploying to end users with PHP already installed but who may have different versions. One straight forward way to achieve this is to create a set of virtual machines (I use VirtualBox for this) with a different version of PHP installed in each. In this scenario you can always be sure which version you are running and that the installation and configuration of one version isn’t interfering with that of another. The downside is that it can be slow to start up and shut down different VMs (or a hit on resources to run them all at once), and if you are using proprietary OSes like Windows you can incur additional licensing costs. As I noted in a previous section, it is possible to have multiple versions installed and running directly on the same machine. However if you are not careful it can become a nightmare trying to keep the versions and their dependencies separate and making sure you know which version you are using at all times. As such I am not going to delve into it in this book. However below are two articles from respected PHP community members who have done just that, which may give you some pointers on what to do and the pitfalls involved. I would suggest that before you try this, you become intimately familiar with compiling and installing PHP, the file and directory structures and locations that PHP uses, and how to check which versions of PHP and extensions are running.

There are also a couple of relevant tools listed below. The first is `php-build`, which automatically builds multiple versions of PHP from source, although you still need to exercise care installing and using them simultaneously. The second is `3v4l.org`, a web service which allows you to test chunks of code in 90+ versions of PHP at the same time. This may avoid the need for installing multiple versions at all. And the final tool is a library which simulates many functions from newer versions for use with older versions.

| ![information](Images/image00248.jpeg) || Further Reading |
| --- | --- |
| | Installing multiple versions, using SVN |
| | [http://derickrethans.nl/multiple-php-version-setup.html](http://derickrethans.nl/multiple-php-version-setup.html) |
| | Installing multiple versions, using GIT |
| | [http://mark-story.com/posts/view/installing-multiple-versions-of-php-from-source](http://mark-story.com/posts/view/installing-multiple-versions-of-php-from-source) |

| ![](Images/image00249.gif) || `php-build` |
| --- | --- |
| | |
| | `php-build` automatically builds multiple PHP versions from source |
| | |
| | Main website & documentation : [http://www.christophh.net/php-build/](http://www.christophh.net/php-build/) |

| ![](Images/image00249.gif) || `3v4l.org` |
| --- | --- |
| | |
| | Web service which allows you test chunks of code in 90+ versions of PHP with the click of 1 button. |
| | |
| | Main website : [http://3v4l.org/](http://3v4l.org/) |

| ![](Images/image00249.gif) || `upgrade.php` |
| --- | --- |
| | |
| | Library to emulate newer functions for older versions of PHP. |
| | |
| | Main website : [http://include-once.org/p/upgradephp/](http://include-once.org/p/upgradephp/) |

### PEAR and PECL

PEAR (PHP Extension and Application Repository) is a library of code and extensions written in PHP, with an easy to use packaging and distribution system. PECL (PHP Extension Community Library) is essentially the same, but for extensions written in C.

Both PECL and PEAR work in a similar way to package managers such as Debians `apt-get`. For example to install the Cairo graphics extension from PECL, simply do `sudo pecl install cairo` at the command line. This will download, compile and install Cairo for you and you can then start using it from within your PHP scripts. Similarly, to install the RDF extension from PEAR, use `pear install rdf`.

The `pear` and `pecl` commands are included as standard with PHP, however some package managers put them in the optional `php-dev` or `php-pear` package. On Ubuntu, for instance, use `sudo apt-get install php-pear` to install it.

More information on both as well as the hundreds of extensions and libraries available, can be found at [http://pear.php.net](http://pear.php.net) and [http://pecl.php.net](http://pecl.php.net) respectively.

### Composer

Composer is a dependency manager. While it deals with packages, it is not a package manager like PEAR. Rather than installing packages centrally, it deals with them on a per-project basis, ensuring that the appropriate versions of the relevant packages, and their dependencies, are installed automatically for that project.

The basic Composer workflow happens as follows :

*   You install Composer.
*   In the base directory of your project, you create a json-formatted file called `composer.json` that specifies which packages (and versions) your project needs
*   In that directory, you run Composer. It will fetch and install of the specified packages, and will automatically also install any of the other packages that those you have specified depend on (and so on until all dependencies are satisfied)
*   In your PHP code, simply add the function `require 'vendor/autoload.php';` and your libraries will be automatically available when you use them.

Fully comprehensive documentation, aimed at beginners as well as advanced users, is available on the composer website. Composer itself doesn’t host any packages, that is the job of package repositories. Packagist is the main, and currently the only, comprehensive public repository, and is the default used by Composer. You can browse the thousands of available packages on the Packagist website. You can of course specify a different repository and indeed create and use your own packages privately if you need to.

| ![](Images/image00249.gif) || Composer Dependency Manager |
| --- | --- |
| | |
| | The easy way to keep libraries consistent and up-to-date on a per-project basis. |
| | |
| | Main website : [http://getcomposer.org/](http://getcomposer.org/) |
| | |
| | Package Repository : [https://packagist.org/](https://packagist.org/) |
| | |
| | Installation info : [http://getcomposer.org/doc/00-intro.md#installation-nix](http://getcomposer.org/doc/00-intro.md#installation-nix) |
| | |
| | Main documentation : [http://getcomposer.org/doc/](http://getcomposer.org/doc/) |
| | |
| | Tutorial : [http://code.tutsplus.com/tutorials/easy-package-management-with-composer--net-25530](http://code.tutsplus.com/tutorials/easy-package-management-with-composer--net-25530) |

### Symfony2 bundles

If you’re using the Symfony2 framework, you can choose from and download over a thousand useful code bundles from knpbundles. These can be installed manually, or often using the Composer dependency system (see the section above). Visit [http://knpbundles.com/](http://knpbundles.com/) for more information and to browse the available code.

## Appendix B : File & data format libraries for PHP
