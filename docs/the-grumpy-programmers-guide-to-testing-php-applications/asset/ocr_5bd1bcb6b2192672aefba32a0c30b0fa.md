# Well-Documented Build Systems Encourage Continuous Deployment

When I first started figuring out how to make this happen, the tool of choice was Jenkins[2]. It's a Java-based automation tool which is ridiculously flexible in how it can help you and has a high number of plugins available. Chances are, if there is something you want to do with Jenkins, someone has figured out how to do it with a plugin.

The idea of build automation is to take things you normally do by hand as part of your deployment and testing process and automate those steps. After all, computers are great at doing what you've told them to do over and over again without complaining! Like with many things, once you've automated how your tests are run, you don't have to think about it anymore. You can save your brainpower for things like making jokes in your company chat or trolling people on social media.

Your options, however, are not limited to just Jenkins. A great alternative for those who don't want to host their own CI server is to use services like Travis CI[3], CircleCI[4], or GitHub Actions[5]. These services allow you to replicate the process you go through when someone grabs your code and wants to run your tests. They all have their own particular syntax and quirks, but they all end up at the same place-a Git-centric system that can react to pull requests or merges and execute a series of steps that should end with your tests being run.

For OpenCFP[6], I have started using GitHub Actions as my build automation tool. When I look at the configuration file for it, it does all the following things for me:

+   - Checkout the code
+   - Install the exact versions of PHP I want my tests to be run against
+   - Install all my dependencies using Composer
+   - Run a code linter and style fixer against the code
+   - Run my database migrations
+   - Build my CSS and JS assets
+   - Verify all the mappings and schemas for code that uses an ORM
+   - Run the tests

[2] Jenkins: https://jenkins-ci.org
[3] Travis CI: https://travis-ci.org
[4] CircleCI: https://circleci.com
[5] GitHub Actions: https://github.com/features/actions
[6] OpenCFP: https://github.com/opencfp/opencfp