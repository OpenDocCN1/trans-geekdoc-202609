# Chapter 12 Caching

One of the ways to speed up an application is to store chunks of generated HTML code, or even full pages, for future requests. This technique is known as caching, and it can be managed on the server side and on the client side.

Symfony offers a flexible server-caching system. It allows saving the full response, the result of an action, a partial, or a template fragment into a file, through a very intuitive setup based on YAML files. When the underlying data changes, you can easily clear selective parts of the cache with the command line or special action methods. Symfony also provides an easy way to control the client-side cache through HTTP 1.1 headers. This chapter deals with all these subjects, and gives you a few tips on monitoring the improvements that caching can bring to your applications.

# Caching the Response

The principle of HTML caching is simple: Part or all of the HTML code that is sent to a user upon a request can be reused for a similar request. This HTML code is stored in a special place (the cache/ folder in symfony), where the front controller will look for it before executing an action. If a cached version is found, it is sent without executing the action, thus greatly speeding up the process. If no cached version is found, the action is executed, and its result (the view) is stored in the cache folder for future requests.

As all the pages may contain dynamic information, the HTML cache is disabled by default. It is up to the site administrator to enable it in order to improve performance.

Symfony handles three different types of HTML caching:

+   - Cache of an action (with or without the layout)
+   - Cache of a partial or a component
+   - Cache of a template fragment

The first two types are handled with YAML configuration files. Template fragment caching is managed by calls to helper functions in the template.

# Global Cache Settings

For each application of a project, the HTML cache mechanism can be enabled or disabled (the default), per environment, in the cache setting of the settings.yml file. Listing 12-1 demonstrates enabling the ability to cache. Note this will not cause anything to be cached; to do so you must enable caching in each module/action (see below).

Listing 12-1 - Activating the Cache, in frontend/config/settings.yml