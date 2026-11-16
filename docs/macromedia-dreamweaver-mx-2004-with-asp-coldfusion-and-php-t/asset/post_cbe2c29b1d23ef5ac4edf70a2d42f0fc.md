

the site's shortcomings. These shortcomings can be divided into two categories: technical shortcomings, such as the outdated and non-compliant code used throughout the site, and business shortcomings, where the site no longer meets the needs of its business. Finally, you'll hop onto the Web and see the completed version of the site that you'll build over the course of the book.

## WHAT YOU WILL LEARN

In this lesson, you will:

- Define a static site in Dreamweaver
- Work in the Dreamweaver environment to create and lay out a new page of content
- Explore the existing HTML code
- Learn about the client's needs
- Explore the completed project as it appears at the end of the book
- Outline a strategy for upgrading the site

## APPROXIMATE TIME

This lesson takes approximately 60 minutes to complete.

## LESSON FILES

### Starting Files:

Lesson01/Start/newland/about.htm
Lesson01/Start/newland/contact_text.txt
Lesson01/Start/newland/index.htm
Lesson01/Start/newland/profiles.htm
Lesson01/Start/newland/tours.htm

### Completed Files:

Lesson01/Start/newland/contact.htm

## DEFINING A STATIC SITE

The Newland Tours site as you are inheriting it is a static HTML site. For this reason,
you can easily pull it into Dreamweaver and start working on it.

Working with Web sites often involves hundreds or even thousands of individual
files, including Web pages, images, cascading style sheets, multimedia assets, and
more. These files are linked together via HTML. Unfortunately, even a small typo
can create ugly (or indecipherable to users) error messages and even block access to
portions of your site. Dreamweaver provides many sophisticated site management
tools to help ensure the overall integrity of your site, both during development and
once it is launched. To take advantage of these features, you must first define a site,
a process in which at a minimum you tell Dreamweaver where the site's root folder
is located on your hard drive.

Defining a site has several benefits, many of which you will see quickly. It helps
prevent broken links, automatically updating files site-wide if you move or rename
a file. The Site Manager also enables you to perform site-wide operations, such as
Find and Replace, which greatly boosts productivity. Another key advantage of the
Site Manager is that it has built-in file uploading capabilities (including FTP), which
means you can publish your files to the Web whenever you want, with the click of a
single button. You can even synchronize local files (on your hard drive) and remote
files (on the Web or a staging server), to ensure that the most up-to-date versions of
the files are in the right place.

In this task, you'll define a regular, static site in the Site Definition dialog box, a
process involving little more than giving the site a name and telling Dreamweaver
where it is stored on the local disk. In a few lessons, once you've made appropriate
preparations, you'll return to this dialog box and define a dynamic site. Dynamic site
definition is a little more involved, and the additional overhead won't do us any good
at this early stage. Fortunately, you can always change a site definition, so we've
nothing to lose by defining a static site for now and getting right to work.

- 1) Create a new directory on your hard disk called dw_dynapps. You'll store the local version of the site in this folder.

- 2) Copy the newland folder (and its contents), found in the Lesson01/Start folder on the CD-ROM, into this new directory.

Often enough in real life, you'll inherit an existing site and be asked to upgrade it.
With any significant upgrade, it's best to make a copy of the existing site and work
on that. You should never directly edit a site in production (that is, the site that the
public sees).

- 3) Open Dreamweaver MX 2004.

Once the files are visible in Dreamweaver, you should edit them exclusively in Dreamweaver. Any text editor can open any HTML file, and every operating system has a file management utility (such as Macintosh Finder or Windows Explorer) that lets you move and delete files. But you should avoid using these tools, because any change is likely to foil Dreamweaver’s Site Manager, which is likely to cause broken links. So once the files are there, go straight to Dreamweaver and avoid the temptation to do anything to them by any other means.

- 4) On the Start page, click the Create New Dreamweaver Site link.

**NOTE** You can also choose Site > Manage Sites and click the New button.

Though the files are on your hard disk, Dreamweaver doesn’t yet see them. By defining a site, you enable Dreamweaver to see—and manage—the files. You define a site in the Site Definition dialog box. If the dialog you see doesn’t look like the one in the screenshot, it’s probably because you are in advanced view. Click the Basic tab near the top of the dialog to bring up the basic view shown in the screenshot.

![](img/43fd0127a958864ab2d93e28efe683e7_23_0.png)

- 5) Enter *Newland Tours* in the only field on the screen, and click Next.

The Site Definition dialog’s basic view uses a wizard-like approach, unlike the more complex dialog box in previous versions of Dreamweaver.

**TIP** If you prefer the old-style Site Definition dialog better, you can access it by clicking the Advanced tab.

- 6) On the Editing Files, Part 2 screen, select “No, I do not want to use a server technology.” Click Next.

Later in the book you will use a server technology. But by choosing No now, you get to skip several complex steps.

![](img/43fd0127a958864ab2d93e28efe683e7_24_0.png)

- 7) On the next screen, select the first option: Edit local copies on my machine, then upload to server when ready (recommended).

As a result of this decision, there will always be two sets of files for the site—one local (usually on your hard drive, though you can put it in a network folder if you want) and one remote (usually on a server). This is safer, because you always have at least one backup copy of your file. More importantly, it means that the files you work on will be stored on your hard drive, where customers will never see them.

Most professional sites work using a 3-tier setup. The local site contains all the files in development on the Dreamweaver user's hard drive. A staging server contains a mirror of the site used for testing and development purposes only. The public never sees content on the staging server, but it is a real Web server environment, which is typically identical or nearly identical to that of the production server. The production server is the public version of the site. Only tested, edited, polished, and approved files should be published on the production server.

- 8) Click the folder icon beside the “Where on your computer do you want to store your files” field, and browse to the newland folder within the dw_dynapps folder, and click Select to select the folder and return to the Site Definition dialog box. In this step you are defining the local site—this is where all the action takes place. Whenever you edit a file, you will be editing the file as it appears in the local site. The local site is generally not seen by the public, which means if you temporarily break the functionality of the site as you work, no harm is done.

![](img/43fd0127a958864ab2d93e28efe683e7_25_0.png)

- 9) On the next screen, choose None in the drop-down menu. Normally, you specify either a staging server or production server as the Remote site. When working with dynamic, database-driven content, a staging server is an absolute necessity. Later in the book, you will define a remote site, which you will use as a staging server. That staging server will be able to handle fully dynamic sites, which the local site you are defining can’t do—as you’ll see later. But for now, a remote site is an unnecessary complication.

> NOTE There is no production server for the site you are building in this book because Newland Tours is fictional.

