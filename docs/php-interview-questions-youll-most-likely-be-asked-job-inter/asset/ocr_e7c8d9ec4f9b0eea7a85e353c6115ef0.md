It's also used to reduce the server load.

# 169: What is the use of “die”? Why use “die” for errors when script anyway terminates?

Answer:
We use die in order to prevent abnormal termination of script. The use of die() helps to prevent displaying the physical path of the script in case a fatal error is caught and we terminate the script using die.

# 170: Can you profile your PHP code?

Answer:
One can use the PEAR benchmark module to profile the PHP code.

# 171: How can one use LDAP authentication in PHP?

Answer:
One can use PEAR’s Auth class which supports LDAP authentication.

# 172: Can you add watermark to an image using PHP?

Answer:
The imagestring() function can be used to add a watermark to an image using PHP.

# 173: How do you search for a node or content in XML using PHP?

Answer:
One can use XML path language (XPath) to search for a node or content in XML.

# 174: Is it alright to enable display_errors in PHP.ini file?

Answer:
It should not be enabled as the user will be able to see the complete physical path to the script if some error occurs.