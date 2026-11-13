# # Chapter 16
# Maintaining a Scalable and
# More Efficient Server

+   - Keeping the server updated
+   - Caching and optimizing
+   - Handling backups

This chapter focuses on the best practices for maintaining your server while also introducing more advanced application improvement techniques such as caching, efficient databases, backups, and scalable code.

After you learn and apply this information to your applications, you will quickly notice that they run more efficiently. If you keep these steps in mind at the beginning of the application development process, you will not have to rework the application later.

# ## Running an Updated Server

One of the simplest but most ignored methods for maintaining a more efficient server is keeping your libraries and core server-side code updated. Oftentimes these programs that are responsible for running your applications are updated as the developers continue to find ways to speed them up or make them more efficient. This updating process is not referring to your personal code, but the libraries and services your code depends on.

Updating your server not only provides performance enhancements, but also can ensure your Web server is more secure. PHP, for example, is updated frequently as more enhancements and coding changes are introduced. This is due to new security concerns being discovered, which results in a stronger application overall.

Before updating your system, ensure your applications will be compatible. For example, applications developed in PHP 4 are not always compatible with PHP 5. You will find some instances where another piece of software on your server may require a specific version. A good example of this is mail