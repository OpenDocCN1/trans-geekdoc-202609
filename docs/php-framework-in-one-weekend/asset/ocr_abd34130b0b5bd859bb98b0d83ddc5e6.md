```
12
13 <div class="collapse navbar-collapse" id="main-nav"> 14 <ul class="nav navbar-nav">
15
16 {% for item in nav %}
17 <li><a href="{{ item.url }}">{{ item.title }}</a></li> 18 {% endfor %}
19
20 </ul>
21 </div> <!-- /.navbar-collapse --> 22 </div> <!-- /.container -->
23 </nav>
```

# **Listing 9.9: templates/includes/nav.html**

```
17 {% include 'includes/nav.html' %}
```

# **Listing 9.10: templates/index.html**

The value of the nav variable is set by our new TemplateService class. Listing 9.11 shows what this might look like. We then update the controllers to use our template service, instead of directly accessing Twig. Listings 9.12 and 9.13 show the updates to the controller classes. We then need to update our dependency injection configuration with details of our new template service. This is configured with the twigand config_service services as dependencies. We also change the configuration of the controllers to provide the new template service instead of twig. Listing 9.14 shows the new services.yml configuration file.

```
2
3 namespace Weekend\Service;
4
5
6 use Twig_Environment;
7
8 class TemplateService
9 {
10     protected $twig; 11     protected $menu; 12
13     public function __construct(Twig_Environment $twig, ConfigService $config) 14 {
15 $this->twig = $twig;
16
17     $this->menu = $config->getConfig();
18 }

19     public function render($templateName, $variables) 20 {
21 foreach ($this->menu as $path => $menuItem) 22 {
23 $variables['nav'][] = [
24 'title' => $menuItem['title'],
25 'url' => '/' . $path,
26 ];
27 }

28 return $this->twig->render($templateName, $variables); 29 }

30
31 }
```

# **Listing 9.11: src/Service/TemplateService.php**

```
3 use Symfony\Component\HttpFoundation\Response;

4 use Weekend\Service\ConfigService;

5 use Weekend\Service\TemplateService;

6

7 class BasicPageController

8 {
9 {
```