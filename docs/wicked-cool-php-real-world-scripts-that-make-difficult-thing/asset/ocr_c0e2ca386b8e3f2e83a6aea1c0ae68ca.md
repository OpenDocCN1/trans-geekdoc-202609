It's best to start out experimenting with a local Apache server away from a production environment. You can really mess up a live server, so not only do you want to make sure you have some tech support handy in case something goes wrong, you also want to make sure that you've seen some of the things that can go wrong. If you feel completely unprepared for the task, you should get someone to help you.

Getting a library to work with PHP is a two-step process: First, you have to install the libraries for the extensions, and then you must make PHP recognize those extensions.

# Installing Libraries

The actual steps involved in installing an extension vary depending on what library you want to use. I can give you a rough overview as to how to do it, but make sure to look for any tutorials on the library’s download page and read all the README files before you do anything. If you want a detailed explanation of how it all fits together, you may want to look at the explanation of compiling software in *How Linux Works* by Brian Ward (No Starch Press, 2004).

The general steps are as follows:

+   1. Log in to your server as root or as a user with the rights to install new programs.

+   2. Download the library archive to the root directory of your server. A quick Google search for the library’s name and PHP (such as *mcrypt php*) will usually bring you to the library’s home page, where you’ll find the source files. They’ll usually be gzipped and tarred to save on storage space and will look something like *libraryfilename.tar.gz*.

+   3. Extract the contents of the archive. A *tar archive* is a bundle of files and directories. On top of this, the entire archive is compressed with the Gzip package, hence the .gz extension at the very end. Therefore, you can think of a .tar.gz file in the same way as a .zip file, except that .tar.gz is done in two separate stages, with two different programs. However, you don’t actually have to explicitly run both, because GNU tar knows how to run the decompressor. To extract the contents of your tar file, type *tar zxvf libraryfilename.tar.gz* at the command prompt. You’ll get a list of all the files and directories being extracted. Most archives create a tree under one top-level directory, so look for that.

+   4. Change to the library’s installed directory by typing *cd directoryname*. If you don’t remember or didn’t catch the name from the previous step, it’s usually the name of the library—*cd curl* for example. (The directory name is case-specific, by the way, so *cURL* is different from *CURL*.)

+   5. Run the *configure* command to see if all the *ingredients* are present to *complete the install on this machine*. Because of the many different types of Unix, installing a package on it takes some serious know-how. Fortunately, the *configure* command can do most of the dirty work for