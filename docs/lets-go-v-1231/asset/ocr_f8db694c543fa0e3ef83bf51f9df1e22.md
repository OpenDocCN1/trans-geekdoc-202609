Once you restart the server, the base template should now invoke the nav template and your home page should look like this:

![](bbox=[0.115, 0.128, 0.885, 0.488])

# Additional information

# The block action

In the code above we've used the {{template}} action to invoke one template from another. But Go also provides a {{block}}...{{end}} action which you can use instead. This acts like the {{template}} action, except it allows you to specify some default content if the template being invoked doesn't exist in the current template set.

In the context of a web application, this is useful when you want to provide some default content (such as a sidebar) which individual pages can override on a case-by-case basis if they need to.

Syntactically you use it like this: