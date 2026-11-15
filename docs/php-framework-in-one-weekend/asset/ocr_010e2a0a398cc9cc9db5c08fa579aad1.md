# Listing 9.13: src/Controller/ContactController.php

```
1 parameters:
2 template_dir: './templates'
3 data_dir: './data'
4
5 services:
6 loader:
7 class: Twig_Loader_Filesystem
8 arguments: ['%template_dir%']
9 twig:
10 class: Twig_Environment
11 arguments: ['@loader']
12 adapter:
13 class: League\\Flysystem\\Adapter\\Local 14 arguments: ['%data_dir%']
15 filesystem:
16 class: League\\Flysystem\\Filesystem 17 arguments: ['@adapter']
18
19 contact_controller:
20 class: Weekend\\Controller\\ContactController 21 arguments: ['@template_service']
22 basic_page_controller:
23 class: Weekend\\Controller\\BasicPageController 24 arguments: ['@template_service', '@config_service'] 25
26 config_service:
27 class: Weekend\\Service\\ConfigService 28 arguments: ['@filesystem']
29
30 template_service:
31 class: Weekend\\Service\\TemplateService 32 arguments: ['@twig', '@config_service']
```

# Listing 9.14: src/services.yml