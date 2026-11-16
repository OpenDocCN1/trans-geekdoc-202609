# Coding FTP Clients

FTP is one of the oldest and best-known Internet protocols. It is familiar to most web developers as a standard way to transfer files from one system to another. This chapter provides a complete overview of PHP's FTP support by focusing on the practical aspects of using the FTP extension.

PHP's FTP extension focuses on the non-interactive use of FTP and is not a substitute for a complete FTP client. It is well suited for automated file transfer or for building web-based FTP clients (see below for a sample of this type of script).

This chapter is broken up into three major sections:

+   - The first section demonstrates how PHP's FTP extension works. It is intended to quickly familiarize the reader with the extension.
+   - The second section focuses on the development of two different applications based on PHP's FTP extension:
+     - A convenience wrapper to use FTP functions for moving files between servers
+     - A simple web-based FTP client
+   - The third section contains three different complementary function references:
+     - The first function reference groups the FTP functions by purpose. Each function listing in the group contains a function prototype, and a brief description.
+     - The second reference is an alphabetical list of commands. Each command has a function prototype, a technical description of its functionality, and a usage example.
+     - The third reference correlates common FTP client commands to the appropriate PHP FTP function.