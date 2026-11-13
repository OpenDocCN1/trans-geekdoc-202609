# # 7

# # WORKING WITH FILES

![](bbox=[0.17, 0.47, 0.36, 0.63])

File manipulation is an important part of PHP programming. To accomplish your task, you may need to create text files on the fly, read tab-delimited files to import huge chunks of data, or perhaps even create cache files for speeding up your server and reducing processor overhead.

# ## File Permissions

In order to do any useful file operations, PHP needs permission to access files. On most webservers, PHP can read files easily enough, but it does not have the necessary permissions to create and alter files. This is a *good thing*, because universal file write access usually gives hackers carte blanche to do whatever they like with your server.

On Unix servers, there are three sets of permissions for owner, group, and world. The user ID that owns the file is the *owner*, and every user on the system is *world* (we won’t discuss *group* in this book; set the group permissions to the permissions of world).