# Complex Credentials

The YAML syntax used in the security.yml file allows you to restrict access to users having
a combination of credentials, using either AND-type or OR-type associations. With such a
combination, you can build a complex workflow and user privilege management system—for
instance, a content management system (CMS) back-office accessible only to users with the
admin credential, where articles can be edited only by users with the editor credential and
published only by the ones with the publisher credential. Listing 6-25 shows this example.

```
Listing 6-25 - Credentials Combination Syntax

editArticle:
  credentials: [ admin, editor ]     # admin AND editor

publishArticle:
  credentials: [ admin, publisher ]  # admin AND publisher

userManagement:
  credentials: [ [ admin, superuser ]]  # admin OR superuser
```

Each time you add a new level of square brackets, the logic swaps between AND and OR. So
you can create very complex credential combinations, such as this:

```
credentials: [[root, [supplier, [owner, quasiowner]]], accounts]]
  # root OR (supplier AND (owner OR quasiowner)) OR accounts
```

# Filters

The security process can be understood as a filter by which all requests must pass before
executing the action. According to some tests executed in the filter, the processing of the
request is modified—for instance, by changing the action executed (default/secure instead
of the requested action in the case of the security filter). Symfony extends this idea to filter
classes. You can specify any number of filter classes to be executed before the action
execution or before the response rendering, and do this for every request. You can see filters
as a way to package some code, similar to preExecute() and postExecute(), but at a
higher level (for a whole application instead of for a whole module).

# The Filter Chain

Symfony actually sees the processing of a request as a chain of filters. When a request is
received by the framework, the first filter (which is always the sfRenderingFilter) is
executed. At some point, it calls the next filter in the chain, then the next, and so on. When
the last filter (which is always sfExecutionFilter) is executed, the previous filter can
finish, and so on back to the rendering filter. Figure 6-3 illustrates this idea with a sequence
diagram, using an artificially small filter chain (the real one contains more filters).

Figure 6-3 - Sample filter chain