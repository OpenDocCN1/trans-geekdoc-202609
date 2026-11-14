We can use the date() function to carry out this one. It could be done as below - $sec = date("s");

# 67: What is the maximum size of file that can be uploaded using PHP and how can we change this?

Answer:
We need to set upload_max_filesize variable in PHP.ini file.

# 68: What does uksort() function do in PHP?

Answer:
This function sorts an array of keys using a user-defined comparison function.

# 69: How can you access global variables inside a function?

Answer:
One can bring the global variable into local scope with the global keyword or use it directly in $GLOBALS.

# 70: Does PHP support functions with variable number of arguments?

Answer:
Yes, this is doable in PHP, either by using an array or even without using arrays as arguments.

# 71: Should we use <? ?> tag mode or <?PHP ?> one?

Answer:
We should <?PHP ?> as the older one is getting depreciated now. Latest Zend engine recommends the later one to be used. We can enable this strict option in PHP.ini file as short_open_tag = off.

# 72: How can we create a database using PHP and MySQL?

Answer:
PHP: mysql_create_db()

# 73: How to run PHP in a command line?

Answer: