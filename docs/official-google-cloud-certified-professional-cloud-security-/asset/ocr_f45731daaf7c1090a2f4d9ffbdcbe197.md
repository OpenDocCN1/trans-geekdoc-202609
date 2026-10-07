# Creating a Cloud DLP inspection template

The first step in using classification capabilities is to create an inspection template. The inspection template will store all the data classification requirements:

+   1. In the Cloud console, use Cloud DLP.
2. From the CREATE menu, choose Template.

![](bbox=[0.143, 0.243, 0.856, 0.439])

Figure 10.4 – Creating a DLP inspection template

+   3. Alternatively, click the following button: Create new template.

This page contains the following sections:

+   * Define template
* Configure detection

# Defining the template

Under Define template, enter an identifier for the inspection template. This is how you will refer to the template when you run a job, create a job trigger, and so on. You can use letters, numbers, and hyphens. If you want, you can also enter a more human-friendly display name, well as a description to better remember what the template does.

# Configuring detection

Next, you configure what Cloud DLP detects in your content by choosing an infoType and other options.

Under InfoTypes, choose the infoType that correspond to a data type you want to scan for. You can also leave this field blank to scan for all infoTypes. More information about each detector is provided in the Further reading section at the end of this chapter.