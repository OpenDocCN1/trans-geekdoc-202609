# Auto-Wiring Bootstrapping

In the phpunit.xml file, there is a section where you can set environment variables PHP can see. In the current version of OpenCFP, it looks like this:

```
<?php
<env name="COLUMNS" value="120"/>
<ini name="memory_limit" value="-1"/>
<server name="CFP_ENV" value="testing"/>
<env name="CFP_ENV" value="testing"/>
<env name="KERNEL_CLASS" value="OpenCFP\Kernel"/>
</php>
```

So, to take advantage of what I can only describe as “auto-wiring bootstrapping,” we set an environment variable that points to our custom Symfony kernel via KERNEL_CLASS. This is used by a base test case object provided by the symfony/framework-bundle package. If I create other test objects by extending from this base test case object, some magic behind the scenes runs all the code in my custom kernel, meaning I should have access to almost everything my code-under-test is expecting to be available.

This means my tests avoid having to explicitly do all the work that the older test bootstrapping did. This does means that maybe some dependencies get created that my particular test will not need, but I view not having to maintain multiple bootstrap-and-initialize sections (often with only minor differences between them) as a bonus.

One of the reasons to go with a web application framework is to take advantage of tools that have been created to solve common problems a programmer faces. If a framework gives you tools to make writing tests easier, use them! The kernel for Symfony allows you to reduce the amount of bootstrapping work you do and the ability to modify facades at run-time for testing Laravel-based applications spring to mind.