will be editing them to accomplish set goals.
Here are some tips that might help you:

+   - Name your applications based on different tasks that they’re going to execute.
- Build applications if the task can be accomplished using a separate application.

If you adhere to the above tips, you will create modularity within your project. This habit will not only help you in general practice, but anytime you be building future projects you can be specific as to what kind of apps to include in your current project. Hence, boosting your development speed and reducing the workload without losing any quality in your work. Below are files that will come pre-installed when your application is developed and the formats for every application file doesn’t change.

# 2. Install Django App

Once you have defined your application, the next step is to install the application.
So, you need to open the settings.py file and change it.
Keep in mind that you will be changing the main settings.py file of your Django project, not the one within the app directory.
You will only need to type your app-name in the INSTALLED_APPS list once you add the application in the list of Installed Apps.
Once you complete that, congratulations, you have installed custom Django application.
Now, you will need to include the app to your urls.py file that anyone who searches the URL of the app within the browser will open the above app.

# 3. Adding App in urls.py

To include the app in the urls.py, you will need to write some code. First, you need to define a new Python file in the demo directory and paste the following code in that file.