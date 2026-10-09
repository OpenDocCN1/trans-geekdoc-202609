
## Automating Integration and Testing

The one common trait of places where every deployment-to-production was stressful was a lack of tests to act as that first line of defense against integrations that might have gone wrong. Yes, I know it can often be difficult to wrap tests around legacy applications. For me, it is worth it because it increases confidence that any given deployment is going to work as expected.

Once there are some tests in place, you then need to start thinking about all the steps required to get to the final step of “did my tests pass?” In the case of the project being used in this book, it looks a little like this:

- Pull in any changes from GitHub and apply them to my work.
- Create a fresh test database and seed it with data.
- Run `composer install` to have expected dependencies in place.
- Run my tests.

If the tests pass, then I do a manual deployment of the changes on the production server for the application.

What if I wanted to automate this? First, I would create something that does it locally with one command. For projects using Composer, I can add things to a `scripts` section of the `composer.json` file.

But first, I’ll create a `bash`[^1] script with all the steps I need in it. I am leery of adding a step that automatically merges changes from the main branch because it might require me to fix conflicts or solve other Git-related issues before I can run my tests.

```bash
#!/usr/bin/env bash
PGPASSWORD=<redacted> psql -h 127.0.0.1 -U <redacted> ibl_test < ibl_stats.dump
composer install
vendor/bin/phpunit tests/
```

I’ve added this file to my project as `scripts/test-full.sh`.

For this project, I grab frequent snapshots of the production database and use them locally to always reset my test database to a known state. I then use Postgres’ CLI tools to import that snapshot. Next, I install all my project dependencies, followed by running my tests.

I’ve verified that it runs locally and that my tests currently pass at the end.

[^1]: https://www.gnu.org/software/bash

### 5. CONTINUOUS INTEGRATION

The next step is to update our `composer.json` file so this script can be executed with the command `composer test-full`. I've added this after the last thing currently defined in there:

```json
"scripts": {
    "test-full": "scripts/test-full.sh"
}
```

I've verified that the command `composer test-full` now runs the bash script I created. I can now do all this work with just one command.

#### Build Servers

Ideally, I want to also have these steps followed by an automated system. Systems like this are often referred to as “build servers” or “continuous integration” servers. Regardless of the name, it is a system that executes a series of user-defined commands based on an event or trigger.

My first exposure to continuous integration systems was via learning how to use Jenkins[^2] to run tests for a fantasy sports platform’s Python code that handled generating all the points for participants. Jenkins is still a good choice for folks looking to get into automation surrounding your build-and-deploy process.

These days, I use GitHub Actions[^3] to do this kind of work. With every single one of my coding projects using GitHub, it makes sense to take advantage of the integrations they provide.

Because GitHub Actions are language-agnostic, you have to tell it to do a lot of the configuration work and package installation you’ve done already just to get your local development environment up and running.

Their documentation is really good; I encourage you to read it to understand what is going on. Here is the GitHub Actions configuration file for my project. Don’t worry, I will explain what is going on:

[^2]: https://www.jenkins.io
[^3]: https://github.com/features/actions

```yaml
1. name: Grumpy CI
2. on: [push, pull_request]
3. jobs:
4.   CI:
5.     runs-on: ubuntu-latest
6.     services:
7.       postgres:
8.         image: postgres:10.8
9.         env:
10.          POSTGRES_USER: <redacted>
11.          POSTGRES_PASSWORD: <redacted>
12.          POSTGRES_DB: ibl_stats_test
13.      ports:
14.        - 5432:5432
15.      options: --health-cmd pg_isready --health-interval 10s --health-timeout 5s --health-retries 3
16.      steps:
17.        - name: Checkout
18.          uses: actions/checkout@v2
19.          with:
20.            lfs: true
21.        - name: Checkout LFS objects
22.          run: git lfs checkout
23.        - name: Setup PHP
24.          uses: shivammathur/setup-php@v2
25.          with:
26.            php-version: 7.4
27.            extensions: mbstring, intl, pdo_pgsql
28.        - name: Get composer cache directory
29.          id: composer-cache
30.          run: echo "::set-output name=dir::$(composer config cache-files-dir)"
31.        - name: Cache composer dependencies
32.          uses: actions/cache@v2
33.          with:
34.            path: ${{ steps.composer-cache.outputs.dir }}
35.            key: ${{ runner.os }}-composer-${{ hashFiles('**/composer.lock') }}
36.            restore-keys: ${{ runner.os }}-composer-
37.        - name: Install dependencies
38.          run: composer install --no-progress --prefer-dist --optimize-autoloader
39.        - name: Seed DB
40.          run: PGPASSWORD=<redacted> psql -U <redacted> ibl_test < ibl_stats.dump
41.        - name: Run PHPUnit tests
42.          run: vendor/bin/phpunit tests
```

All this work happens inside some kind of containerized environment.

Starting at the top, I give this process a name and tell it I want it to react to any GitHub-related push event or pull request.

Next, I tell it that I want to use the latest available version of Ubuntu[^4] Linux. GitHub installs some set of default packages as well. Adding other packages can be done in later steps.

With that defined, I have to declare I want to use one of their Postgres containers and specify some configuration values I need, along with adding an option for a health check that causes the whole process to pause until the Postgres container is up and running and ready to accept connections.

Then there are a series of steps I want to be followed. The first is to check out the code that is either being pushed or subject to a pull request.

The next step is unique to this project but might be of interest to you. Do you have large files (like, for instance, a Postgres database dump) that needs to be under version control? GitHub doesn't let you add files that large.

Luckily for me, when GitHub refused to accept a push that contained my database dump, it directed me to take a look at the Git Large File Storage[^5] project and use that instead. After doing some repository reset and rewind work, I successfully added the database dump file to the repo. The file tbl_stats.dump is actually a text file that contains some metadata and a pointer to where the file can be downloaded.

With the files checked out, I ask for PHP to be installed, specifying the version and any other extensions to be installed.

Next, I find out where Composer's cache is, followed by telling Composer to, well, use that cache! After that, I install all of my composer-related dependencies.

I follow that up by doing some database seeding by applying the contents of that database dump to my freshly-created Postgres database.

The final step is to ask the build system to run my PHPUnit tests.

Now, I have GitHub following the same steps I follow locally so I can continue to integrate my code and, hopefully, have fewer bugs making it into production.

I hope you can use my sample GitHub Action file as a template for your own build systems. Basically, almost anything you find yourself doing just to get to the point where you can run your tests can be duplicated here.

[^4]: https://ubuntu.com
[^5]: https://git-lfs.github.com

## 6
# What’s Next?

Like with almost everything associated with writing automated tests for your PHP code, it's a journey that won't stop. I learn new things all the time! My target goal for all of my work is this:

- Developers use TDD to create or update features.
- CI systems take their patches and run a comprehensive test suite against them.
- If all the tests pass, the patch is merged, and deployed to production.

Getting to this state can take a lot of work; some code bases and applications may never get there. However, we should never stop trying to use tools that encourage clear intent in code, alert us of problems before the users see them, and allow for confident deployments.

In this section, I wanted to talk briefly about some things I have noticed recently in regards to tools that complement testing. They don't need an entire chapter, but I think it's worth your time to dig in a little deeper.
