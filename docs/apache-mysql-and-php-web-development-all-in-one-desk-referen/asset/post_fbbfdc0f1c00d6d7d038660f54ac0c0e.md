
For example, to compile and include mod_info when installing Apache, use the following installation option:

```
./configure --enable-info
```

This option compiles mod_info statically and includes it as part of the Apache binary.

To compile a module dynamically, use the following format:

```
./configure --enable-modulename=shared
```

A dynamically compiled module usually has the extension .so. For Apache to use the module, you must include a LoadModule directive in the main configuration file that loads the module, as follows:

```
LoadModule moduleIdentifier pathtoDSOfile
```

The moduleIdentifier is listed in the documentation for the module. For example, the following directive loads mod_status:

```
LoadModule status_module modules/mod_status.so
```

## Using base and extension modules

Many modules are included in the Apache distribution. When you unpack the tarball, the module source files are unpacked into the modules subdirectory in the source directory. Some of these modules are base modules; some are extension modules. The base modules are compiled and included by default when you install Apache. The extension modules are not included by default.

The base modules are compiled statically and are included in Apache during installation by default. You can use the following command to see which modules are compiled into Apache:

```
httpd -l
```

If you don't want one of the base modules installed, you need to disable it during installation by using an option similar to the following:

```
./configure --disable-info
```

The extension modules are not included in Apache by default. If you want to add one of the extension modules, use one of the following options:

```
./configure --enable-headers
```

```
./configure --enable-headers=shared
```

If you enable the module as a DSO, using shared, the compiled module is stored in the modules subdirectory in the Apache main directory. A LoadModule directive is needed in the main configuration file to tell Apache to load the module and provide the location of the module. During the build process, the LoadModule directive is automatically added to the configuration file for you, along with the correct location for the module.

If you install the module as a DSO, you have more flexibility. You can remove or add the module whenever you need to with the LoadModule directive, without needing to recompile Apache.

## Using external modules

Many third-party modules are available for use with Apache. If you want to use an external module, check the third party's Web site for information about the module. Use the installation instructions provided with the module. Some modules need to be installed statically; some work better as a DSO.

## Some Useful Modules

The following sections describe some modules with useful features.

### PHP

PHP is a scripting language used to make Web sites dynamic. PHP is the most popular Apache module, according to a survey of Apache module use conducted by SecuritySpace (www.securityspace.com/s_survey). Over 13 million domains use PHP, according to Netcraft (www.php.net/usage.php).

PHP is open-source software that runs on most operating systems and works with most Web servers, not just on Linux with Apache. The PHP project is supported by the Apache Software Foundation, the same group that supports the development of Apache. Consequently, PHP runs particularly well with Apache. PHP can be statically compiled and run as part of Apache or can run as a DSO module.

PHP was designed specifically for use on Web sites and is particularly well suited for that purpose. Book V discusses PHP in detail.

### Secure Sockets Layer (SSL) module

If you plan to send any important information between Apache and Web site visitors' browsers, you need to use the Secure Sockets Layer (SSL) protocol. With SSL, information sent between Apache and the browser is encrypted, preventing anyone who intercepts the information from being able to understand it. In addition, the SSL server holds a digital certificate, issued by certificate authorities that verify the server's identity.

When a server is communicating using SSL, the protocol is HTTPS, not HTTP. The server listens for HTTPS requests on port 443 rather than port 80. Apache can support both HTTP and HTTPS at the same time. Any files on the Web site can be sent using HTTP or HTTPS, whichever is specified in the URL.

The Apache distribution includes mod_ssl as an extension, which means you must enable mod_ssl at installation with the option:

```
./configure --enable-ssl
```

However, mod_ssl uses a library called OpenSSL, so you also need to download and install OpenSSL. The following steps provide a quick overview of installing OpenSSL; the OpenSSL download includes more complete installation instructions:

- 1. Download the latest version of OpenSSL from www.openssl.org/source/ and save it in an appropriate directory, such as /usr/local/src.
- 2. Unpack the tarball.
- You must be using an account that has permission to write in the directory where the tarball is being unpacked, such as root.
- 3. CD (change directory) to the OpenSSL directory created when the tarball was unpacked.
- 4. Type ./configure.
- 5. Type make.
- 6. Type make test.
- This step tests the libraries built in Step 5. If the test fails, informative error messages are displayed. Solve the problems and repeat the steps starting from Step 5. If the test is successful, continue to Step 7.
- 7. Type: make install.

Installing OpenSSL creates a directory containing the OpenSSL libraries, libcrypto and libssl. The default location for the directory is /usr/local/ssl. After the OpenSSL libraries are installed, you can use the OpenSSL command-line tool to install your certificate, either a fake certificate for testing purposes or a real certificate obtained from an organization that issues certificates, such as VeriSign. In addition, the directives provided by mod_ssl to configure SSL for your server are available for use. See the Apache documentation for descriptions of the directives available.

The installation process creates a configuration file called conf/ssl.conf that contains the configuration directives for your SSL server. For example, the file contains a Listen directive for port 443. You may need to edit this configuration file. When you install SSL with Apache, you need to start Apache with the following command:

```
/usr/local/apache2/bin/apachectl startssl
```

### Perl

You can use the module mod_perl to execute Perl CGI scripts. Scripts executed with mod_perl run much faster than Perl scripts executed as CGI scripts.

The mod_perl project is supported by the Apache Software Foundation. A Web page for mod_perl provides the software and documentation at perl.apache.org. Two versions of mod_perl are provided: mod_perl 1 for Apache 1.3 and mod_perl 2 for Apache 2. The mod_perl module is installed statically, as part of Apache. The documentation on the Web site provides detailed installation instructions.

### Python

You can use the mod_python module to execute Python programs with Apache. These programs execute much faster than traditional CGI scripts. You can also use the more advanced features provided by Python. Python is an open-source, object-oriented computer language, comparable to Perl or Java.

The mod_python project is supported by the Apache Software Foundation. You can download the source at httpd.apache.org/modules/python-download.cgi. Version 3.0 is available for Apache 2, and version 2.7 is available for Apache 1.3. Documentation and other information are available at www.modpython.org. You can subscribe to a Python mailing list by sending an e-mail with the word subscribe in the subject line to mod_python-request@modpython.org.

The mod_python module is installed dynamically as a DSO. The Python source must also be available, as well as Python libraries. If you installed Python from source on your system, you have everything you need. If you installed Python from an RPM, installing just binaries, you need to download the source.
