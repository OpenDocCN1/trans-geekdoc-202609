# Setting Up The Testing Environment

```
'bootstraps' = array(
    // /path/to/bootstrap.php',
    // /var/www/sites/my.awesome.site.com/laravel/bootstrap/autoload.php',
    // /Users/kenji/code/CodeIgniter/application/tests/Bootstrap.php'
);
```

> The listing above in a format unified diff. It shows the difference between two files. In short, remove the line starting with - from the original file and add the green line with +, to get the new file. Conventions Used in This Book for details.

# Configuring PHPUnit XML Configuration File

To use the PHPUnit XML configuration file to define which tests to run, modify the PHPUnit configuration file in CodeIgniter directory to include the following listeners element:

```
a/CodeIgniter/application/tests/phpunit.xml
+++ b/CodeIgniter/application/tests/phpunit.xml
@@ -27,4 +27,8 @@

<log type="coverage-clover" target="Build/logs/clover.xml">
<log type="phpunit" target="build/logs/phpunit.xml" logIncompleteSkipped="false" />
<logging>
    <!-- This is required for VPU to work correctly -->
    <listeners>
        <listener class="PHPUnit_Util_Log_JSON"></listener>
    </listeners>
</logging>
</phpunit>
```

Okay, that's all. For the next chapter, Test Jargon.

> If you use PHPUnit, you can't use PySH which is introduced in (Optional) Installing PHPUnit.

# 2. Installing PHPUnit

Download https://phpunit.de/phpunit-4.8.10.phar and rename it to phpunit.phar, then put it into your application/tests folder. For most environments, that's, but if you run into issues installing PHPUnit, the installation section of the PHPUnit Manual should help you figure out what's wrong.