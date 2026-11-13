```
{
    userStyle = param.userstyle;
}
else
{
    validData = false;
}

if(!validData)
{
    trace("User data was not properly loaded");
}
else
{
    trace("User Information Loaded");
    trace("\tUser: " + param.username);
    trace("\tLevel: " + param. userlevel);
    trace("\tStyle: " + param.userstyle);
}
}
```

Basically, this code first initializes variables to store the user data and then checks each passed-in value for a valid entry. The validation variable is assigned to true from the start because if any of the if statements fail it will be changed to false. This process is considered reverse logic, but works quite well for validation routines.

# Using a more secure approach for returning data

In the previous example you learned how to securely work with returned data. The problem with this simplified approach is that other ways exist to intercept information passed between Flash and the server.

# Using unique responses

There are a few options to creating an even more secure application, which all depend on development time and cost. It is a common thought to ignore cost for the ultimate security, but this is simply not possible all of the time. Oftentimes you will work on a project that gets to a “good enough” point and the app will ship with issues; this is a downside to application development, but very common.

The best way to keep cost realistic is to look at all your options. One option is to use md5 to create unique response codes and ensure the data is valid, which will work, but nothing stops the “hacker” from decompiling your SWF and looking directly at the code.

# Securing your files

In previous versions of ActionScript you were able to create obfuscated SWFs, which meant that most applications couldn't decompile them. However, at the time of this writing no tool exists for AS3 applications.