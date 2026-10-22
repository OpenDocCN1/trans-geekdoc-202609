If you get back a translation that isn’t correct, it’s not necessarily a system failure because the accuracy expectation allows some margin of error. However, if you keep entering different English sentences into the system and keep getting back wrong translations, the second expectation is violated, which makes it a system failure.

Operational expectation violations are easier to detect, as they’re usually accompanied by an operational breakage such as a timeout, a 404 error on a webpage, an out-of-memory error, or a segmentation fault. However, ML performance expectation violations are harder to detect as doing so requires measuring and monitoring the performance of ML models in production. In the preceding example of the English-French machine translation system, detecting whether the returned translations are correct 99% of the time is difficult if we don’t know what the correct translations are supposed to be. There are countless examples of Google Translate’s painfully wrong translations being used by users because they aren’t aware that these are wrong translations. For this reason, we say that ML systems often fail silently.

To effectively detect and fix ML system failures in production, it’s useful to understand why a model, after proving to work well during development, would fail in production. We’ll examine two types of failures: software system failures and ML-specific failures.

# Software System Failures

Software system failures are failures that would have happened to non-ML systems. Here are some examples of software system failures:

*Dependency failure*

A software package or a codebase that your system depends on breaks, which leads your system to break. This failure mode is common when the dependency is maintained by a third party, and especially common if the third party that maintains the dependency no longer exists.²

*Deployment failure*

Failures caused by deployment errors, such as when you accidentally deploy the binaries of an older version of your model instead of the current version, or when your systems don’t have the right permissions to read or write certain files.

2 This is one of the reasons why many companies are hesitant to use products by startups, and why many companies prefer to use open source software. When a product you use is no longer maintained by its creators, if that product is open source, at least you’ll be able to access the codebase and maintain it yourself.