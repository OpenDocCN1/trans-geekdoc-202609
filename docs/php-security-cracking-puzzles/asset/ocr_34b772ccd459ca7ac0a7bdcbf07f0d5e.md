# I.3.11. Counting Lines in Project Files

Create a script to count lines in project files. The script must traverse all nested directories of the project and count lines in the files with the specified file extension, for example, *.php or *.h and *.cpp.

# I.3.12. Replacing a Substring in All Files in Subdirectories

Develop a script that would traverse all nested subdirectories of the current directory and replace the specified substring encountered in all files with another string.

# I.3.13. Uploading a File in Parts

Create a script to split a large file into fragments and then reassemble it after uploading it to the server. This script will allow you to use the script developed in Section II.3 for uploading large files if the remote server sets an overly restrictive limitation on the maximum size of the uploaded file.

# I.3.14. Deleting Directories

Directories are deleted using the standard rmdir() function. However, this function has limited functionality. It can only delete empty directories. Thus, if the directory to be deleted contains at least one file, the deletion operation will fail. Develop a custom function to bypass this limitation.

# I.3.15. Random Output from a File

The accompanying CD-ROM contains the text.txt file (/scripts/3/text.txt). The contents of this file are shown in Listing I.3.2.

> Listing I.3.2. The contents of the text.txt file

+   1 Programming
2 PHP programming
3 JavaScript programming