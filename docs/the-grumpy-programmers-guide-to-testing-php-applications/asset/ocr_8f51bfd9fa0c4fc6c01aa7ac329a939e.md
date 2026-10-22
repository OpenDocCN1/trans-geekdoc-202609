# 13. BUILDING A TESTING CULTURE

A process for automatically generating a development environment also means when a developer accidentally messes up their environment (I have lost track of the number of times this has happened), you can quickly get back to a known good state. This frees up developers to experiment, knowing there won’t be hours of downtime if they make a mistake.

Pretty much every programming language has automation tools, so chances are you won’t have to learn another language to help build out your automation efforts.

# Same Languages and Tools

The most important one of these issues is likely making sure everyone is using the same version of the chosen programming language. If your chosen language also supports extensions or add-on libraries, make sure everyone is using the same ones there, too! It seems like such an easy thing to do, but with every developer having their own personal policies about this sort of thing, it’s almost inevitable some drift will occur if there are not strict procedures in place.

This should be applied to the other complementary pieces of your application: database servers, caching servers, build tools for minifying and compressing things. Being consistent this way also eliminates weird bugs due to different versions of tools behaving in slightly different ways.

I am a believer in always using the latest, stable version of every tool the application uses. That way, you get to take advantage of any updates for bug fixes or patching of security issues. The longer you hold off on updating the tools your application uses, the more likely you are to either get compromised or be in a position where an upgrade to the latest stable version of things is a nightmare. Don’t let it get to that point.

# Same Practices

This is one I feel is extremely underrated and can often lead to a lot of friction. You’re probably familiar with coding standards—how the code itself should be structured in terms of indenting, positioning of braces, brackets, things like that. Most languages have produced community-driven tools that make it easy to enforce or even automatically apply them.

Beyond code style issues, you should also focus on making sure folks are using the same coding practices. This might not be an issue if your language of choice follows the “there is only one way to do it” path, but languages that mix procedural and object-oriented and functional practices (like PHP) give bored programmers lots of options to create code that is hard to maintain going forward.