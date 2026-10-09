# Automating Integration and Testing

The one common trait of places where every deployment-to-production was stressful was a lack of tests to act as that first line of defense against integrations that might have gone wrong. Yes, I know it can often be difficult to wrap tests around legacy applications. For me, it is worth it because it increases confidence that any given deployment is going to work as expected.

Once there are some tests in place, you then need to start thinking about all the steps required to get to the final step of “did my tests pass?” In the case of the project being used in this book, it looks a little like this:

+   Pull in any changes from GitHub and apply them to my work.
Create a fresh test database and seed it with data.
Run `composer install` to have expected dependencies in place.
Run my tests.

If the tests pass, then I do a manual deployment of the changes on the production server for the application.

What if I wanted to automate this? First, I would create something that does it locally with one command. For projects using Composer, I can add things to a `scripts` section of the `composer.json` file.

But first, I’ll create a `bash`[1] script with all the steps I need in it. I am leery of adding a step that automatically merges changes from the main branch because it might require me to fix conflicts or solve other Git-related issues before I can run my tests.

```
#!/usr/bin/env bash
PGPASSWORD=<redacted> psql -h 127.0.0.1 -U <redacted> ibl_test < ibl_stats.dump
composer install
vendor/bin/phpunit tests/
```

I’ve added this file to my project as `scripts/test-full.sh`.

For this project, I grab frequent snapshots of the production database and use them locally to always reset my test database to a known state. I then use Postgres’ CLI tools to import that snapshot. Next, I install all my project dependencies, followed by running my tests.

I’ve verified that it runs locally and that my tests currently pass at the end.

+   https://www.gnu.org/software/bash