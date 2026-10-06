# Using Quarto to Make Data-Rich Reports, Presentations, and Websites

+   - 02-nucleotide-sequence.qmd
- 03-amino-acid-sequence.qmd
- section: "Conclusions"
  contents:
    - 04-wrap-up.qmd

+   5. Re-render the site:

```
quarto render
```

This will give us a nice website with code interpreted and rendered nicely.

# How it works...

In step 1, we use the familiar fs package to pull out a directory name from the rbioinf cookbook and save it somewhere we can see it in our system. The directory is full of example qmd files that we can use as the basis for our website.

In step 2, we create a file called _quarto.yml in the directory we pulled from the package; this file contains all the configuration information in YAML format. The code should be saved in the file. The first stanza in _quarto.yml file is the project definition; we're telling Quarto we're building a site and that the output rendered HTML files go in a sub-directory docs (the name can be anything you want; docs is the default for GitHub Pages).

The second stanza defines stuff about the website; we give a title and set up the names of the pages that are included as links in a top navigation bar. The important file is the index .qmd file. Quarto website needs this one; it will be the front page people reach when they come to your site. The text attribute tells Quarto what text to refer to the index page.

In step 3, we actually render the site. The command is issued in the command line/terminal (not the R console) and will be familiar from other recipes. This time, we don't explicitly state a rendering type as that's done in the _quarto.yml file. The output goes to the directory you specified—in this case, docs. Browse and load index .html to view the site—in case, docs. Browse and load index .html to view the site.

In step 4, we add another layer of navigation. Larger websites are built with sidebar navigation, so the code here sets up, defining section titles and the pages that belong to each section. The use of numbers at the front of each page isn't required but is useful for organizing files in the filesystem. Again, this stanza should be entered into _quarto.yml, but pay attention to adding it to the file at the same indentation as the navbar.

Finally, in step 5, we render the whole thing.