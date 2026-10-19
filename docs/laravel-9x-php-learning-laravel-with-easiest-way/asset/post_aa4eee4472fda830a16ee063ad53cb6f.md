
## Update PHP

## Laravel 9.x

## Home Learning Center |

Learning Laravel with Easiest Way

The book will teach you Laravel 9.x step by step.

By: Andy Turner

*Best Laravel Books for All Time With Update Version:*

*This Learning Center Teach You Full LARAVEL Course Part by Part.*

Copyright (c) Taylor Hicks

*All rights reserved. Including the right to reproduce this book or portions thereof, in any form. No part of this text may be reproduced in any form without the express written permission of the author.*

| Title | Page |
|---|---|
| Introduction | 49 |
| Environment Configuration | 50 |
| Environment Variable Types | 53 |
| Retrieving Environment Configuration | 54 |
| Determining The Current Environment | 55 |
| Accessing Configuration Values | 57 |
| Configuration Caching | 58 |
| Debug Mode | 59 |
| Maintenance Mode | 60 |
| 5. Directory Structure | 68 |
| Introduction | 70 |
| The Root Directory | 70 |
| The app Directory | 70 |
| The bootstrap Directory | 71 |
| The config Directory | 71 |
| The database Directory | 72 |
| The public Directory | 73 |
| The resources Directory | 74 |
| The routes Directory | 74 |
| The storage Directory | 75 |
| The tests Directory | 77 |
| The vendor Directory | 77 |
| The App Directory | 77 |
| The Broadcasting Directory | 80 |
| The Console Directory | 80 |
| The Events Directory | 80 |
| The Exceptions Directory | 81 |
| The Http Directory | 81 |
| The Jobs Directory | 82 |
| The Listeners Directory | 82 |
| The Mail Directory | 83 |
| The Models Directory | 84 |
| The Notifications Directory | 84 |
| The Policies Directory | 85 |
| The Providers Directory | 86 |
| The Rules Directory | 86 |
| 6. Deployment | 97 |
| Introduction | 98 |
| Server Requirements | 99 |
| Server Configuration | 99 |
| Nginx | 99 |
| Optimization | 102 |
| Autoloader Optimization | 102 |
| Optimizing Configuration Loading | 103 |
| Optimizing Route Loading | 104 |
| Optimizing View Loading | 104 |
| Debug Mode | 105 |
| Deploying With Forge / Vapor | 106 |
| 7. Service Container | 119 |
| Introduction | 120 |
| Zero Configuration Resolution | 123 |
| When To Use The Container | 125 |
| Binding | 127 |
| Binding Basics | 127 |
| Binding Interfaces To Implementations | 131 |
| Contextual Binding | 133 |
| Binding Primitives | 134 |
| Binding Typed Variadics | 136 |
| Tagging | 139 |
| Extending Bindings | 140 |
| Resolving | 141 |
| The Make Method | 141 |
| Automatic Injection | 143 |
| Method Invocation & Injection | 146 |
| Container Events | 148 |
| PSR-11 | 149 |
| 8. Service Providers | 150 |
| Introduction | 151 |
| Writing Service Providers | 152 |
| The Register Method | 153 |
| The Boot Method | 157 |
| Registering Providers | 159 |
| Deferred Providers | 160 |
| 9. Facades | 163 |
| Introduction | 163 |
| When To Use Facades | 167 |
| Facades Vs. Dependency Injection | 168 |
| Facades Vs. Helper Functions | 170 |
| How Facades Work | 173 |
| Real-Time Facades | 176 |
| Facade Class Reference | 181 |
| 10. Routing | 184 |
| Basic Routing | 185 |
| Redirect Routes | 191 |
| View Routes | 192 |
| Route Parameters | 193 |
| Required Parameters | 193 |
| Optional Parameters | 195 |
| Regular Expression Constraints | 196 |
| Named Routes | 199 |
| Route Groups | 203 |
| Middleware | 204 |
| Controllers | 205 |
| Subdomain Routing | 205 |
| Route Prefixes | 206 |
| Route Name Prefixes | 207 |
| Route Model Binding | 208 |
| Implicit Binding | 208 |
| Implicit Enum Binding | 215 |
| Explicit Binding | 217 |
| Fallback Routes | 222 |
| Rate Limiting | 223 |
| Defining Rate Limiters | 223 |
| Attaching Rate Limiters To Routes | 227 |
| Form Method Spoofing | 229 |
| Accessing The Current Route | 230 |
| Cross-Origin Resource Sharing (CORS) | 231 |
| Route Caching | 232 |
| 11. Middleware | 234 |
| Introduction | 234 |
| Defining Middleware | 236 |
| Registering Middleware | 240 |
| Global Middleware | 240 |
| Excluding Middleware | 242 |
| Middleware Groups | 243 |
| Sorting Middleware | 245 |
| Middleware Parameters | 246 |
| Terminable Middleware | 248 |
| 12. CSRF Protection | 251 |
| Introduction | 251 |
| Preventing CSRF Requests | 253 |
| Excluding URIs | 256 |
| X-CSRF-Token | 258 |
| X-XSRF-Token | 259 |

breaking changes. While referring to the Laravel system or its parts from your application or bundle, you ought to constantly utilize a version requirement, for example, ^9.0, since significant releases of Laravel do introduce breaking changes. In any case, we endeavor to constantly guarantee you might refresh to another major release in one day or less.

## Named Arguments

Named arguments are not covered by Laravel's backwards compatibility rules. We may decide to rename method arguments when necessary to further develop the Laravel codebase. Accordingly, using named arguments while calling Laravel methods should be done carefully and with the understanding that the parameter names might change from now on.

## Support Policy

For LTS releases, for example, Laravel 9, bug fixes are provided for 2 years and security fixes are provided for 3 years. These releases give the longest window of help and support. For general releases, bug fixes are provided for a year and a half and security fixes are provided for 2 years. For all of the additional libraries, including Lumen, undoubtedly the most recent release gets bug fixes. Moreover, please review the database versions supported by Laravel.

The Laravel community and challenge our development team to ship amazing, robust new features without introducing breaking changes. Thus, we have shipped an assortment of robust features to Laravel 8 without breaking backwards compatibility, for example, parallel testing support, improved Breeze starter kits, HTTP client enhancements, and, surprisingly, new Eloquent relationship types, for example, "has one of many". As such, this commitment to ship amazing new features during the current release will likely lead to future "major" releases being primarily used for "maintenance" tasks, for example, upgrading upstream dependencies, which can be seen in these release notes. Laravel 9 continues with the improvements made in Laravel 8.x by introducing support for Symfony 6.0 components, Symfony Mailer, Flysystem 3.0, improved route:list output, a Laravel Scout database driver, new Eloquent accessor/mutator syntax, implicit route bindings through Enums, and an assortment of other bug fixes and convenience enhancements.

## Contribution Guide

- Bug Reports
- Support Questions
- Core Development Discussion
- Which Branch?
- Compiled Assets
- Security Vulnerabilities
- Coding Style
- PHPDoc
- StyleCI
- Code of Conduct

The source code is managed on GitHub, and there are repositories for each of the Laravel projects.

If you discover a security vulnerability within Laravel, please send an email to Taylor Otwell at taylor@laravel.com. All security vulnerabilities will be promptly addressed.

## Coding Style

Laravel follows the PSR-2 coding standard and the PSR-4 autoloading standard.

## PHPDoc

Below is an example of a valid Laravel documentation block. Note that the @param attribute is followed by two spaces, the argument type, two more spaces, and finally the variable name:

## StyleCI

You can definitely relax in the event that your code styling is flawed! StyleCI will automatically merge any style fixes into the Laravel repository after pull requests are merged. This allows us to focus on the content of the contribution and not the code style.

## Code of Conduct

The Laravel code of conduct is derived from the Ruby code of conduct. Any violation of the code of conduct may be reported to Taylor Otwell.

- Participants will be tolerant of opposing views.
- Participants must ensure that their language and actions are free of personal attacks and disparaging personal remarks.
- When interpreting the words and actions of others, participants should always assume good intentions.
- Behavior that can be reasonably considered harassment will not be tolerated.
