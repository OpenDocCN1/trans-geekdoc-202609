# Chapter 1
Managing Complexity

A lot of what we do this weekend will seem like overkill. This is because the examples are simple in order to demonstrate the concepts in use on more complex systems. As projects get bigger, and complexity increases, you need ways to manage complexity. In web development, we tackle complexity by layering.

When you write code you write instruction statements. These statements are grouped into functions (or methods) which are grouped into classes, which are combined into systems. Once this all gets so big you can’t fit it in your head, you can’t reason about it. We need to keep the design of the system as simple as possible.

In order to simplify design, we split things into separate chunks. These chunks have many names, such as modules, packages, components, and libraries. The aim is to make them as self-contained as possible. When a component’s dependencies are minimised we say it is loosely coupled (as opposed to tightly coupled). We group all the related components (i.e. those that share dependencies) so that we can think about them independently from the rest of the system. It often looks like we’ve split the design of the system into layers. We call this process layering.

In modern PHP we talk about packages a lot. These are separate blocks of reusable code with minimal dependencies and a clean, well-defined API. When we create our own apps we prefer to reuse functionality provided by packages, rather than create our own. Packages vary in size from a few functions, through to entire sub-systems.

A framework is a collection of components that work well together. Traditionally the components in a framework will have been designed and bundled together to fulfil a specific type of problem. Increasing, thanks the wide open-source ecosystem of PHP packages, we’re able to pull together components from different sources and have them work together easily.

The packages that our project depends on are defined in a configuration file called composer.json which exists in the root folder of our codebase.

Use the Composer init command to create a composer.json file interactively. You will be prompted for some details about your project and asked if you want to define dependencies interactively. Respond with no to skip adding dependencies (require) and dev dependencies (require-dev) for now.

```
$ mkdir php-framework $ cd php-framework $ composer init
```

You should now have a project folder called php-frameworkwith a bare Composer config file (composer.json) that looks a bit like this:

```
1 {
2 "name": "darrenmothersole/php-framework",
3 "authors": [
4 {
```