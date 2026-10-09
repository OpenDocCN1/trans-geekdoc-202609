# **Chapter 9**

This will create a folder /path/to/source/for/this/chapter/expressive. Change to this directory. Modify public/index.php as follows:

```
<?php
if (php_sapi_name() === 'cli-server'
    && is_file(__DIR__ . '/parse_url(
$_SERVER['REQUEST_URI'], PHP_URL_PATH))
) {
    return false;
}

chdir(dirname(__DIR__));
session_start();
$_SESSION['time'] = time();
$appDir = realpath(__DIR__ . '/../..');
$loader = require 'vendor/autoload.php';
$loader->add('Application', $appDir);
$container = require 'config/container.php';
$app = $container->get(\Zend\Expressive\Application::class);
$app->run();
```

You will then need to create a wrapper class that invokes our session validator middleware. Create a SessionValidateAction.php file that needs to go in the /path/to/source/for/this/chapter/expressive/src/App/Action folder. For the purposes of this illustration, set the stop time parameter to a short duration. In this case, time() + 10 gives you 10 seconds:

```
namespace App\Action;
use Application\MiddleWare\Session\Validator;
use Zend\Diactoros\ { Request, Response };
use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\ServerRequestInterface;
class SessionValidateAction
{
    public function __invoke(ServerRequestInterface $request,
    ResponseInterface $response, callable $next = null)
    {
        $inbound = new Response();
        $validator = new Validator($request, time()+10);
        $inbound = $validator($request, $response);
        if ($inbound->getStatusCode() != 200) {
            session_destroy();
            setcookie('PHPSESSID', 0, time()-300);
            $params = json_decode(
                $inbound->getBody()->getContents(), TRUE);
```