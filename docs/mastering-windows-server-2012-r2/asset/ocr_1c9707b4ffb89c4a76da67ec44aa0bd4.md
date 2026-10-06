# FIGURE 13.26

Viewing the file
screen templates

![](bbox=[0.316, 0.093, 0.882, 0.313])

file screens also have templates. Figure 13.26 shows Server Manager open to the file screen
templates.

Notice that several well-known file group types are identified in the templates such as audio
ideo files and image files. For example, the specific extensions of these file types are identified
the File Groups node. audio and video files include .mp1, .mp2, .mp3, .mp4, and
.mpeg and that's not all of them.

When you create a screen, you can select one of the file groups. This meet
your needs of the time you want to add file types or exclude file types from
screen, you can modify the contents to meet your needs.

Imagine that your company recently learned that many users are storing Outlook .pst
files on a server that are more than 1 GB in size and eating up the storage space. The company
states users cannot store email files on a file server. You can use the following steps to
enforce the rule:

+   1. Launch Server Manager, and browse to the File Screens node.

+   2. Right-click the Block E-mail Files template, and select the Create Screen from
Template option.

+   3. Enter the volume name that you want to screen (such as F:1) in the File Screen path
box.

Since we chose the Block E-mail Files Template, our screen properties are already prese-
lected. We could also change to a different template's screen properties or define our own
custom properties if we wish. Keep the default option and review the summary at the
bottom of the page.

+   4. Click Create.

+   5. Select the File Screens node (right above File Screens) in the FSRM directory
structure.

+   6. Right-click the new screen you just created, and edit File Screen Properties.
Your display will look similar to Figure 13.27.