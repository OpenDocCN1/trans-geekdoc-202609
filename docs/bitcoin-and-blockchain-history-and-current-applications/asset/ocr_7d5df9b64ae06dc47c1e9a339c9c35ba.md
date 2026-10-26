The below command in Linux OS is used to clone the source code.

```
```sh
$ git clone https://github.com/bitcoin/Bitcoin.git
```
```

After execution of the above command, a local copy of the complete database of source code will be available in Bitcoin directory. Documentation will also be offered along with the source code and is available in numerous files. The main documentation will be available in README.md file in Bitcoin directory. Get into the Bitcoin directory by executing the below command.

```
```sh
$ cd bitcoin
```
```

In order to ensure that the system in which the source code is downloaded has all libraries to compile, the following script has to be executed to find the correct setting.

```
```sh
$ ./autogen.sh
```
```

The above autogen.sh script generates a set of automatic configuration scripts. These configuration scripts will examine your system to find the correct settings, and will ensure that the system has all the needed libraries to compile the code.

The most important script is the “Configure” script. It facilitates various options to customize the build process. The command ./configure --help will list the options available to create a customized build for your system.

```
```sh
$ ./configure
```
```

This script will find all the necessary files automatically, and thus a customized build will be created. If everything is well, the configure script will finish its execution without any error and create customized build scripts which will help in compiling Bitcoin. Otherwise, it will terminate with errors. The error possibly could be a missing or incompatible library. In that case, analyze the build document again and be assured that necessary prerequisites are installed, and then rerun the configure code.

The next step is to compile the source code, which will take hours to complete. The compilation process has to be monitored often to check whether any error message is shown.

```
```sh
$ make
```
```

Once the source code is compiled without any errors, installing the Bitcoin executable into the system path is the final step. This can be done by executing the make command.

```
```sh
$ sudo make install
```
```

To confirm the successful installation of Bitcoin, the following commands can be executed. The sudo make install command asks for the path of the two executables.