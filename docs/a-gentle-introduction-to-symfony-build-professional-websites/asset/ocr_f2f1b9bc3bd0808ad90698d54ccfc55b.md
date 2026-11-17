```
Listing 14-7
$ php symfony propel:generate-admin backend article --module=article
```

This call is enough to create an article module in the backend application based on the BlogArticle class definition, and is accessible by the following:

```
Listing 14-8
http://localhost/backend_dev.php/article
```

The look and feel of a generated module, illustrated in Figures 14-2 and 14-3, is sophisticated enough to make it usable out of the box for a commercial application.

> If you don’t see the expected look and feel (no stylesheet and no image), this is because you need to install the assets in your project by running the plugin:publish-assets task:

```
Listing 14-9
$ php symfony plugin:publish-assets
```

# Figure 14-2 - list view of the article module in the backend application

# Article List

| Id | Title | Content | Blog author | Blog category | Is published | Created at | Actions |
|---|---|---|---|---|---|---|---|
| 1 | Welcome to the symfony weblog! | This is the first post of this weblog. | 1 | 1 | ✓ | April 1, 2010 6:30 PM | Edit Delete |

1 result

Choose an action go New

# Figure 14-3 - edit view of the article module in the backend application