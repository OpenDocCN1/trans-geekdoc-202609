
}
}
pack .mybtn -side top
```

Here's how it works:

- 1. The button's command calls the tk_dialog function, passing first a name for the dialog box (why, I don't know, but it's required, even though you don't use it again).
- 2. Next you pass a string that will appear in the title bar of the dialog box.
- 3. Then you pass the name of an icon bitmap. (Feel free to use one of the prepackaged bitmaps. See the sidebar "Displaying the standard bitmaps" in this chapter for more information on the prepackaged bitmaps.)
- 4. Next you add a number that's the default value returned by the dialog box in case the user closes the dialog box without choosing one of the buttons.
- 5. And finally, you include all the strings you want to display on the different buttons. Just list them one after the other.

You can see how this all looks in Figure 9-3.

![](img/3f967ab8a8fddc723173059f56621648_369_0.png)

## Chapter 10: Ten Useful Tcl/Tk Tools

### In This Chapter

- Komodo
- Visual Tcl
- VisualGIPSY
- SpecTcl
- tkBuilder
- FastBase MySQL + Tcl Interface
- mysqltcl
- [incr Widgets]
- Tcl Dev Kit (with plug-in for Web browsers)
- Tcl Developer Xchange

The great thing about Tcl and Tk is that because they’re both free, you can also find a lot of great tools for them that are also free. If you’re willing to spend some money, though, you can find even more great tools. In this chapter, I talk about several tools that can help your Tcl/Tk development, some free, some not.

### Tk GUI Designers

Because Tk is so popular, many people have created visual designers to help you graphically lay out the controls on your windows. In this section, I list five such designers. The first of these is actually an entire development tool created by ActiveState.

The remaining four are all free and very similar in nature: Each includes a complete IDE for typing in your Tcl code and also provides a way to lay out widgets visually, generating Tcl code for you. Therefore, for each of these four I simply point you to the appropriate Web site where you can download the tools and try them out yourself and figure out which one you like best.

### Komodo

(Not free.) This is a powerful tool that lets you develop and debug your programs. It includes a really nice text editor that colors your code based on the syntax. (This is called syntax highlighting.) It also includes a project window allowing you to quickly navigate between the files in your application. Among its remaining features is a complete debugger, allowing you to trace through your code and track down problems. You can purchase this from ActiveState at www.activestate.com/Products/Komodo/.

### Visual Tcl

Free! This is an incredibly powerful tool that makes laying out controls and adding code to the controls incredibly easy. It features a toolbar filled with common widgets such as frames, buttons, and so on. Additionally, it includes an attribute editor that allows you to customize each control in a window; with it you can set each control's properties, such as width, height, and color. Find this at vtcl.sourceforge.net/.

### VisualGUIPSY

Free! This tool lets you easily drop controls on a form and then set the control's properties using an Object Inspector window. Additionally, among many other features, it includes a tree view that lets you see how your controls are arranged hierarchically. (Remember, a frame can hold other controls, including other frames that can themselves hold controls.) Find this at www.prs.de/int/products/vg/index.html.

### SpecTcl

Free! This is a nice program that includes some very fancy icons (check out the Web page to see what I'm talking about). It lets you create a new window and then drag and drop widgets on the window, generating valid Tcl/Tk code. Find this at spectcl.sourceforge.net/.

### tkBuilder

Free! I've used this one a great deal for a previous job I had. With this tool you can create a window, and easily drag and drop controls onto the window. The program then generates valid Tcl/Tk code for you automatically. You can find it at sawpit.iwarp.com/.

### Developer Tools

Here are some general developer tools that can help you with your Tcl programming. Note that in the previous section, “Tk GUI Designers,” I mentioned Komodo from ActiveState. That tool could be in this category as well.

### FastBase MySQL + Tcl Interface

Free! This is a tool that provides an interface to MySQL. You can find it at www.fastbase.co.nz/fbsql/index.html.

### mysqltcl

Free! This is another tool that provides an interface to MySQL. This is also the one that is mentioned in the official MySQL docs, although the other one I mention here (FastBase) is at least as good as this one. You can find it at www.xdobry.de/mysqltcl/.

### [incr Widgets]

Free! This is a huge collection of additional Tk widgets. I encourage you to take a look at it. The library ships with many Tcl installations, including the one by ActiveState. Additionally, you can locate it online at www.tcltk.com/iwidgets/.

### Tcl Dev Kit (with plug-in for Web browsers)

(Not free) ActiveState is one of the frontrunners in the Tcl world. In addition to the Komodo tool, it offers a nice Tcl development tool called Tcl Dev Kit, which includes a feature that lets you package up your Tcl programs into standalone executable binaries; a browser plug-in that lets you run Tcl inside your browser; and more. Check it out at www.activestate.com/Products/Tcl_Dev_Kit/.

### Tcl Developer Xchange

Finally, this isn't a tool, but rather a site for Tcl tools. It's part of the official Tcl site. Here you can find a huge repository filled with various tools for Tcl, including applications written in Tcl, additional libraries, GUI designers, and so on. Check it out at www.tcl.tk/software/.

## Book V

## PHP Web Pages for Dynamic Content

## The 5th Wave By Rich Tennant

![](img/3f967ab8a8fddc723173059f56621648_374_0.png)

> "Before I go on to explain more advanced procedures like the 'Zap-Rowdy-Students-who-Don't-Pay-Attention' function, we'll begin with some basics."

## Contents at a Glance

- Chapter 1: What You Can Do with PHP ............................................347
- Chapter 2: Writing Server-Side Scripts ...........................................353
- Chapter 3: Storing Information....................................................367
- Chapter 4: Controlling the Program Flow ..........................................385
- Chapter 5: Arrays and Functions ....................................................401
- Chapter 6: Interacting with HTML ...................................................417
- Chapter 7: Advanced Programming with PHP .........................................435
- Chapter 8: Creating Graphics .........................................................453
- Chapter 9: Modeling Data with Classes ..............................................465
- Chapter 10: Ten Ways to Enhance Your Web Site ......................................475

## Chapter 1: What You Can Do with PHP

### In This Chapter

- Examining the advantages and drawbacks of PHP
- Discovering PHP function libraries
- Taking a look at applications of PHP

In this chapter, I talk about some of the possible applications of PHP.
When considering the potential of PHP — as well as when you should use it — keep in mind that PHP is a server-side scripting language. All PHP processing takes place on the side of the Web server, which dishes out Web pages. Unless someone runs a PHP processor on his or her own client computer and manually sends files through it, all PHP processing takes place on the server side.

Using a server-side scripting language can have complications. For example, if you’re writing a script that does a lot of processing (like grinding through hundreds of files and millions of calculations), your Web server performance may suffer if thousands of clients are accessing it each day. If that’s the case, strongly consider moving the processing to the individual users’ machines by using a client-side script or program.

However, by running the program on the server side, you have complete control over the computer that’s doing the processing and over the libraries available to it. You don’t, for example, have to require users to first download an entire “language runtime” (as you do in Java) and expect them to run it on their computers. Therefore, users with even the most basic machines — such as a 486 running Windows 95 and Internet Explorer 3.0 — can, potentially, still access your site if the pages your Web server sends out after the PHP processing are simple enough. Additionally, you don’t have to worry about different versions of PHP floating around. Regardless of what browser and what computer connects to your Web server, your PHP code runs on your Web server, and you control which version of PHP runs on the Web server. This results in what the gurus call platform independence.
