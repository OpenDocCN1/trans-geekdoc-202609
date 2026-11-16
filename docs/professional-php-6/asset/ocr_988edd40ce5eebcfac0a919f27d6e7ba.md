You can probably guess the output. All such classes do is provide an interface to the existing PHP global methods — but with some degree of consistency between platforms.

As a PEAR class, this means that this MDB2 package is semi-official — but the emphasis there is on “semi.” It’s just not quite pervasive enough, meaning that the choice of wrapper in use in any given project (if, indeed, one has been used at all) can be unpredictable. How many of you have chanced upon a legacy PHP project with some class called `DatabaseConnection` or similar? Perhaps this is something the original author brewed himself or herself?

# Summing Up

To recap the problem: PHP’s database support is a chronic mess — a hodgepodge of static methods inside the global namespace that have arisen from the language growing too quickly by too many authors over the past several years.

The mess manifests itself as an inconsistency in approach, which makes portability between databases a virtual nonstarter. Some may argue “this doesn’t matter” — but don’t be fooled. It does matter. You may be confident in your choice of RDBMS now, but what if its manufacturer is bought out by a big corporation that decides to stop developing it? What if a new release of that same RDBMS changes the way it works? Portability — and consistency — matters. That’s why Java has Java Database Connectivity (JDBC), and .NET has ADO.NET. Even the much criticized Coldfusion has something along these lines, in the form of Coldfusion Data Sources.

Finally, as with so much in PHP, a well-meaning (but ill-advised) cabal of third-party developers have attempted to tackle the problem themselves — and made it somewhat worse. Virtually every PHP developer has recognized that the by-the-book approach is out of kilter with common sense; but every one has had his or her own unique approach, leading to an array of amateur classes to provide cleaner interfaces to PHP’s database functions. Some are good, some are less than good, but none is official, and, hence, none has achieved widespread usage.

Mercifully, PHP 6 has brought us a solution.

# Database Abstraction

The approach just discussed is generally described as *database abstraction*. At the simplest level, what this involves is any technique that decreases the number of points at which database-specific code occurs.

By decreasing the frequency of such touchpoints, the application becomes easier to maintain (because less code is required for simple database operations) and more portable (because the number of places where code may need changing is reduced), thus simplifying migration.

# What’s Needed

What is required is a universal, officially PHP-sanctioned approach for database abstraction. What is needed is something that achieves the goals of consistency and portability, while providing a universally accepted approach around which all developers can unite.