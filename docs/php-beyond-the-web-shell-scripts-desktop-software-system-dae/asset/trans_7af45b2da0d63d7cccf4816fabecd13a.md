

# 进阶 PHP 静态分析工具

## 基础工具

| ![information](Images/image00248.jpeg) || **进一步阅读** 如何（PHP 创始人 Rasmus Lerdorf 的雇主）Etsy.com 为其 PHP 栈实现静态分析  

[http://codeascraft.etsy.com/2012/08/10/static-analysis-for-php/](http://codeascraft.etsy.com/2012/08/10/static-analysis-for-php/) “PHP Static Analysis in Sublime Text” by Phil Sturgeon  

[http://philsturgeon.co.uk/blog/2013/08/php-static-analysis-in-sublime-text](http://philsturgeon.co.uk/blog/2013/08/php-static-analysis-in-sublime-text) “Analyzing PHP statically”，由 Julien Verlaguet，Facebook 制作的视频  

[http://www.youtube.com/watch?v=gKWNjFagR9k](http://www.youtube.com/watch?v=gKWNjFagR9k) |

| --- | --- |

| ![](Images/image00249.gif) || `PHPLint` |

| --- | --- |

|   ||   |

|   || 一个全面的 PHP 代码检查工具，可供下载或在线使用 |

|   ||   |

|   || **主网站、文档和安装信息** : [http://www.icosaedro.it/phplint/](http://www.icosaedro.it/phplint/) |

|   ||   |

|   || **在线工具** : [http://www.icosaedro.it/phplint/phplint-on-line.html](http://www.icosaedro.it/phplint/phplint-on-line.html) |

| ![](Images/image00249.gif) || `PHPHint` |

| --- | --- |

|   ||   |

|   || 一个 PHP 代码检查工具，可供下载或在线使用，还可以尝试将代码清理为符合 PSR 标准。它是其他项目的前端，目前为 Alpha 版本。 |

|   ||   |

|   || **主网站和在线工具** : 原为 http://phphint.org，现已不可用 |

|   ||   |

|   || **主文档和安装信息** : [https://github.com/klaussilveira/PHPHint/](https://github.com/klaussilveira/PHPHint/) |

| ![](Images/image00249.gif) || `PHP_Codesniffer` |

| --- | --- |

|   ||   |

|   || 用于检测违反定义的一组编码标准的 Pear 包 |

|   ||   |

|   || **主网站** : [http://www.squizlabs.com/php-codesniffer](http://www.squizlabs.com/php-codesniffer) |

|   ||   |

|   || **安装信息** : [https://github.com/squizlabs/PHP_CodeSniffer/#about](https://github.com/squizlabs/PHP_CodeSniffer/#about) |

|   ||   |

|   || **主文档** : [http://pear.php.net/manual/en/package.php.php-codesniffer.php](http://pear.php.net/manual/en/package.php.php-codesniffer.php) |

| ![](Images/image00249.gif) || `PHP Depend` |

| --- | --- |

|   ||   |

|   || 一个静态分析和指标生成工具。建议与 PHP Mess Detector（下文）配合使用。 |

|   ||   |

|   || **主网站** : [http://pdepend.org/](http://pdepend.org/) |

|   ||   |

|   || **安装信息** : [http://pdepend.org/documentation/getting-started.html#installation](http://pdepend.org/documentation/getting-started.html#installation) |

|   ||   |

|   || **主文档** : [http://pdepend.org/documentation/getting-started.html](http://pdepend.org/documentation/getting-started.html) |

| ![](Images/image00249.gif) || `PHPMD (PHP Mess Detector)` |

| --- | --- |

|   ||   |

|   || 一个衍生工具，使用 PHP Depend 查找错误、次优代码等。 |

|   ||   |

|   || **主网站** : [http://phpmd.org/](http://phpmd.org/) |

|   ||   |

|   || **安装信息** : [http://phpmd.org/download/index.html](http://phpmd.org/download/index.html) |

|   ||   |

|   || **主文档** : [http://phpmd.org/documentation/index.html](http://phpmd.org/documentation/index.html) |

| ![](Images/image00249.gif) || `PHPLOC` |

| --- | --- |

|   ||   |

|   || 一个简单工具，用于输出关于代码的各种统计信息。 |

|   ||   |

|   || **主网站** : [https://github.com/sebastianbergmann/phploc](https://github.com/sebastianbergmann/phploc) |

|   ||   |

|   || **主文档和安装信息** : [https://github.com/sebastianbergmann/phploc/blob/master/README.md](https://github.com/sebastianbergmann/phploc/blob/master/README.md) |

| ![](Images/image00249.gif) || `PHP Analyzer` |

| --- | --- |

|   ||   |

|   || 一个高级静态分析工具。设计用于作为 CI 工作流的一部分，也可作为独立工具使用。 |

|   ||   |

|   || **主网站** : [https://github.com/scrutinizer-ci/php-analyzer](https://github.com/scrutinizer-ci/php-analyzer) |

|   ||   |

|   || **安装信息** : [https://github.com/scrutinizer-ci/php-analyzer#installation](https://github.com/scrutinizer-ci/php-analyzer#installation) |

|   ||   |

|   || **主文档** : [https://scrutinizer-ci.com/docs/tools/php/php-analyzer/](https://scrutinizer-ci.com/docs/tools/php/php-analyzer/) |

| ![](Images/image00249.gif) || `RIPS` |

| --- | --- |

|   ||   |

|   || 一个主要面向安全漏洞检测的分析工具。面向网站，但也可以分析 CLI 代码。 |

|   ||   |

|   || **主网站** : [http://rips-scanner.sourceforge.net/](http://rips-scanner.sourceforge.net/) |

|   ||   |

|   || **安装信息** : [http://rips-scanner.sourceforge.net/#download](http://rips-scanner.sourceforge.net/#download) |

|   ||   |

|   || **主文档** : 无 |

| ![](Images/image00249.gif) || `PHP_CodeCoverage` |

| --- | --- |

|   ||   |

|   || 一个用于测试代码覆盖率（实际运行时会执行的代码）的高级工具。 |

|   ||   |

|   || **主网站** : [https://github.com/sebastianbergmann/php-code-coverage](https://github.com/sebastianbergmann/php-code-coverage) |

|   ||   |

|   || **主文档和安装信息** : [https://github.com/sebastianbergmann/php-code-coverage/#php_codecoverage](https://github.com/sebastianbergmann/php-code-coverage/#php_codecoverage) |

| ![](Images/image00249.gif) || `PHP_sat` |

| --- | --- |

|   ||   |

|   || 一个用于 PHP 的通用静态分析工具。仅提供不稳定版本。 |

|   ||   |

|   || **主网站** : [http://www.program-transformation.org/PHP/PhpSat](http://www.program-transformation.org/PHP/PhpSat) |

|   ||   |

|   || **安装信息** : [http://www.program-transformation.org/PHP/PhpSatDocumentation#Installation](http://www.program-transformation.org/PHP/PhpSatDocumentation#Installation) |

|   ||   |

|   || **主文档** : [http://www.program-transformation.org/PHP/PhpSatGettingStarted](http://www.program-transformation.org/PHP/PhpSatGettingStarted) |

超越基本的 Lint 类型功能和单一用途扫描，PHP 还有许多高级开源和商业分析平台可用，它们提供更广泛的分析和报告功能，包括各种代码质量指标、代码重复分析、安全模式分析等，并可与其他工具（如单元测试软件和 IDE）集成。这些工具通常有不容忽视的学习曲线和部署/使用“成本”（在时间和资源方面），更适合大型项目、关键任务项目以及多开发者项目。但是，即使是从单个开发者的小型项目开始，如果你诚实地认为你的项目将来会扩展，那么从一开始就考虑使用此类工具可能值得，以帮助尽量减少“技术债务”在项目后期被“追讨”。此类工具包括：

| ![](Images/image00249.gif) || `Sonarqube` |

| --- | --- |

|   ||   |

|   || 一个用于通过代码分析管理代码质量的广泛开放平台。 |

|   ||   |

|   || **主网站** : [http://www.sonarqube.org/](http://www.sonarqube.org/) |

|   ||   |

|   || **安装信息** : [http://docs.sonarqube.org/display/SONAR/Setup+and+Upgrade](http://docs.sonarqube.org/display/SONAR/Setup+and+Upgrade) |

|   ||   |

|   || **主文档** : [http://docs.sonarqube.org/display/SONAR/User+Guide](http://docs.sonarqube.org/display/SONAR/User+Guide) |

|   ||   |

