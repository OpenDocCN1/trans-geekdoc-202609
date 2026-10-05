# # Appendix B

# ## How to Read ci-phpunit-test

If you want to customize or improve ci-phpunit-test, you need to read its source code. This is a guide to help you do so.

# ### Structure of ci-phpunit-test

ci-phpunit-test consists of the following major parts:

+   - Bootstrap ... Bootstrap for PHPUnit.
- Autoloader ... Autoloader for application and ci-phpunit-test class files.
- Replaced Classes and Functions ... Replacements for CodeIgniter code.
- New Functions ... Functions added for testing.
- TestCase classes ... TestCase classes provided by ci-phpunit-test.
- Request-related classes ... $this->request() and related functionality.
- Helper classes ... Helper or short-cut methods for test code.
- Monkey Patch ... Library to provide monkey patching capabilities.

```
tests/
├── Bootstrap.php ... Bootstrap
├── TestCase.php ... TestCase class for users
|├── _ci_phpunit-test/ ...
|   ├── CIPUnitTest.php ... Bootstrap
|   ├── CIPUnitTestAutoloader.php ... Autoloader class
|   ├── CIPUnitTestCase.php ... Base TestCase class
|   ├── CIPUnitTestDouble.php ... Helper class to create Mock objects
|   ├── CIPUnitTestCache.php ... Cache class for Autoloader
|   ├── CIPUnitTestReflection.php ... Helper class to access private methods
|   ├── CIPUnitTestRequest.php ... Request related class (main)
|   ├── CIPUnitTestRouter.php ... Request related class for routing
|   ├── CIPUnitTestSuperGlobal.php ... Request related class for super globals
|   ├── alias/ ... Class aliases
|   └── autoloader.php ... Autoloader
└── exceptions/ ... Exception classes
```