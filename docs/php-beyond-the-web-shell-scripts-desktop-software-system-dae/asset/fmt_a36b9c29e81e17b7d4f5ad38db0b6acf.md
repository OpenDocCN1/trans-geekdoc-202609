
# 进阶 PHP 静态分析工具

## 基础工具

| ![information](Images/image00248.jpeg) || **Further Reading** How (PHP founder Rasmus Lerdorf’s employer) Etsy.com implements static analysis for its PHP stack  

[http://codeascraft.etsy.com/2012/08/10/static-analysis-for-php/](http://codeascraft.etsy.com/2012/08/10/static-analysis-for-php/) “PHP Static Analysis in Sublime Text” by Phil Sturgeon  

[http://philsturgeon.co.uk/blog/2013/08/php-static-analysis-in-sublime-text](http://philsturgeon.co.uk/blog/2013/08/php-static-analysis-in-sublime-text) “Analyzing PHP statically”, video by Julien Verlaguet, Facebook  

[http://www.youtube.com/watch?v=gKWNjFagR9k](http://www.youtube.com/watch?v=gKWNjFagR9k) |

| --- | --- |

| ![](Images/image00249.gif) || `PHPLint` |

| --- | --- |

|   ||   |

|   || A comprehensive PHP lint tool, available to download or use online |

|   ||   |

|   || **Main website, documentation & installation info** : [http://www.icosaedro.it/phplint/](http://www.icosaedro.it/phplint/) |

|   ||   |

|   || **Online tool** : [http://www.icosaedro.it/phplint/phplint-on-line.html](http://www.icosaedro.it/phplint/phplint-on-line.html) |

| ![](Images/image00249.gif) || `PHPHint` |

| --- | --- |

|   ||   |

|   || A PHP lint tool, available to download or use online, which can also attempt to clean code to PSR standards. A front end to other projects, and an Alpha release. |

|   ||   |

|   || **Main website and online tool** : Was http://phphint.org, no longer available |

|   ||   |

|   || **Main documentation & installation info** : [https://github.com/klaussilveira/PHPHint/](https://github.com/klaussilveira/PHPHint/) |

| ![](Images/image00249.gif) || `PHP_Codesniffer` |

| --- | --- |

|   ||   |

|   || Pear package for detecting violations of a defined set of coding standards |

|   ||   |

|   || **Main website** : [http://www.squizlabs.com/php-codesniffer](http://www.squizlabs.com/php-codesniffer) |

|   ||   |

|   || **Installation info** : [https://github.com/squizlabs/PHP_CodeSniffer/#about](https://github.com/squizlabs/PHP_CodeSniffer/#about) |

|   ||   |

|   || **Main documentation** : [http://pear.php.net/manual/en/package.php.php-codesniffer.php](http://pear.php.net/manual/en/package.php.php-codesniffer.php) |

| ![](Images/image00249.gif) || `PHP Depend` |

| --- | --- |

|   ||   |

|   || A static analysis and metric generation tool. Recommended for use with PHP Mess Detector (below). |

|   ||   |

|   || **Main website** : [http://pdepend.org/](http://pdepend.org/) |

|   ||   |

|   || **Installation info** : [http://pdepend.org/documentation/getting-started.html#installation](http://pdepend.org/documentation/getting-started.html#installation) |

|   ||   |

|   || **Main documentation** : [http://pdepend.org/documentation/getting-started.html](http://pdepend.org/documentation/getting-started.html) |

| ![](Images/image00249.gif) || `PHPMD (PHP Mess Detector)` |

| --- | --- |

|   ||   |

|   || An spin-off tool that uses PHP Depend to look for bugs, suboptimal code and more. |

|   ||   |

|   || **Main website** : [http://phpmd.org/](http://phpmd.org/) |

|   ||   |

|   || **Installation info** : [http://phpmd.org/download/index.html](http://phpmd.org/download/index.html) |

|   ||   |

|   || **Main documentation** : [http://phpmd.org/documentation/index.html](http://phpmd.org/documentation/index.html) |

| ![](Images/image00249.gif) || `PHPLOC` |

| --- | --- |

|   ||   |

|   || A simple tool that outputs a range of statistics about your code. |

|   ||   |

|   || **Main website** : [https://github.com/sebastianbergmann/phploc](https://github.com/sebastianbergmann/phploc) |

|   ||   |

|   || **Main documentation & installation info** : [https://github.com/sebastianbergmann/phploc/blob/master/README.md](https://github.com/sebastianbergmann/phploc/blob/master/README.md) |

| ![](Images/image00249.gif) || `PHP Analyzer` |

| --- | --- |

|   ||   |

|   || An advanced static analysis tool. Designed for use as part of a CI workflow but can be used as a stand-alone tool as well. |

|   ||   |

|   || **Main website** : [https://github.com/scrutinizer-ci/php-analyzer](https://github.com/scrutinizer-ci/php-analyzer) |

|   ||   |

|   || **Installation info** : [https://github.com/scrutinizer-ci/php-analyzer#installation](https://github.com/scrutinizer-ci/php-analyzer#installation) |

|   ||   |

|   || **Main documentation** : [https://scrutinizer-ci.com/docs/tools/php/php-analyzer/](https://scrutinizer-ci.com/docs/tools/php/php-analyzer/) |

| ![](Images/image00249.gif) || `RIPS` |

| --- | --- |

|   ||   |

|   || An analysis tool primarily aimed at security vulnerability detection. Aimed at websites, but can analyse CLI code too. |

|   ||   |

|   || **Main website** : [http://rips-scanner.sourceforge.net/](http://rips-scanner.sourceforge.net/) |

|   ||   |

|   || **Installation info** : [http://rips-scanner.sourceforge.net/#download](http://rips-scanner.sourceforge.net/#download) |

|   ||   |

|   || **Main documentation** : None |

| ![](Images/image00249.gif) || `PHP_CodeCoverage` |

| --- | --- |

|   ||   |

|   || An advanced tool for testing code coverage (the code that would actually be executed in a run). |

|   ||   |

|   || **Main website** : [https://github.com/sebastianbergmann/php-code-coverage](https://github.com/sebastianbergmann/php-code-coverage) |

|   ||   |

|   || **Main documentation & installation info** : [https://github.com/sebastianbergmann/php-code-coverage/#php_codecoverage](https://github.com/sebastianbergmann/php-code-coverage/#php_codecoverage) |

| ![](Images/image00249.gif) || `PHP_sat` |

| --- | --- |

|   ||   |

|   || A general static analysis tool for PHP. Unstable release only. |

|   ||   |

|   || **Main website** : [http://www.program-transformation.org/PHP/PhpSat](http://www.program-transformation.org/PHP/PhpSat) |

|   ||   |

|   || **Installation info** : [http://www.program-transformation.org/PHP/PhpSatDocumentation#Installation](http://www.program-transformation.org/PHP/PhpSatDocumentation#Installation) |

|   ||   |

|   || **Main documentation** : [http://www.program-transformation.org/PHP/PhpSatGettingStarted](http://www.program-transformation.org/PHP/PhpSatGettingStarted) |

Going beyond basic Lint type capabilities and single purpose scanning, there are a number of advanced open source and commercial analysis platforms available for PHP that provide a much wider range of analysis and reporting capabilities, including various code quality metrics, code duplication analysis, security pattern analysis and more, as well as integration with other tools such as unit testing software and IDEs. These tools often have a non-negligible learning curve and deployment/use “cost” (in terms of time and resources), and are more suited to larger projects, mission critical projects and projects with multiple developers. However even when starting small with a single developer, if you honestly believe that your project will scale up it may be worth considering using such a tool from the start to help minimise “technical debt” building up to be “called in” later in the project. Such tools include :

| ![](Images/image00249.gif) || `Sonarqube` |

| --- | --- |

|   ||   |

|   || An extensive open platform for managing code quality through code analysis. |

|   ||   |

|   || **Main website** : [http://www.sonarqube.org/](http://www.sonarqube.org/) |

|   ||   |

|   || **Installation info** : [http://docs.sonarqube.org/display/SONAR/Setup+and+Upgrade](http://docs.sonarqube.org/display/SONAR/Setup+and+Upgrade) |

|   ||   |

|   || **Main documentation** : [http://docs.sonarqube.org/display/SONAR/User+Guide](http://docs.sonarqube.org/display/SONAR/User+Guide) |

|   ||   |
