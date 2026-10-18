
![Remember](images/remember.png)You may use only public repositories when working with GitHub from Colab, even though GitHub also supports private repositories. To save a file to GitHub, choose File ⇒   Save a Copy in GitHub. If you aren’t already signed into GitHub, Colab displays a window that requests your sign-in information. After you sign in, you see a dialog box similar to the one shown in [Figure 6-12](#c06.xhtml#c06-fig-0012).

![FIGURE 6-12: Using GitHub means storing your data in a repository.](images/9781119724018-fg0612.png)

[FIGURE 6-12:](#c06.xhtml#rc06-fig-0012) Using GitHub means storing your data in a repository.

If your account doesn’t currently have a repository, you must either create a new repository or choose an existing repository in which to store your data. After you save the file, it will appear in the GitHub repository of your choice. The repository will include a link to open the data in Colab by default, unless you choose not to include this feature.

#### Using GitHub Gist to save notebooks

You use GitHub Gists as a means of sharing single files or other resources with other people. Some people use them for full projects as well, but the idea is that you have a concept that you want to share — something that isn’t quite fully formed and doesn’t represent a usable application. You can read more about Gists at [`https://help.github.com/articles/about-gists/`](https://help.github.com/articles/about-gists/).

As with GitHub, Gists come in both public and secret form. You can access both public and secret Gists from Colab, but Colab automatically keeps your files secret. To save your current project as a Gist, you choose File ⇒   Save a Copy as a GitHub Gist. Unlike GitHub, you don’t need to create a repository or do anything fancy in this case. The file saves as a Gist without any extra effort. The resulting entry always contains an Open in Colab button, as shown in [Figure 6-13](#c06.xhtml#c06-fig-0013).

![FIGURE 6-13: Use Gists to store individual files or other resources.](images/9781119724018-fg0613.png)

[FIGURE 6-13:](#c06.xhtml#rc06-fig-0013) Use Gists to store individual files or other resources.

### Downloading notebooks

Colab supports two methods for downloading notebooks to your local drive: `.ipynb` files (using File ⇒   Download .ipynb) and `.py` files (using File ⇒   Download .py). In both cases, the file appears in the default download directory for your browser; Colab doesn't offer a method for downloading the file to a specific directory.

## Performing Common Tasks

Most tasks in Colab work similar to their Notebook counterparts. For example, you can create code cells just as you do in Notebook by using the options on the Insert menu. Noncode cells come in three forms:

*   Text

*   Section header

*   Form field, which comes in these types: 

    *   Dropdown

    *   Input

    *   Slider

    *   Markdown

Noncode cells work somewhat differently from the Markdown cells found in Notebook, but the idea is the same. Two interesting additions not found in Notepad are the scratch code cell, which allows you to experiment with code in real time, and code snippets, which are canned code for performing specific tasks (you just insert them where needed).

You can also edit and move cells, just as you do with Notebook. One important difference is that you can’t change a cell type. A cell that you create as a section header can’t suddenly transform into a code cell. The following sections provide a brief overview of the various features.

### Creating code cells

The first cell that Colab creates for you is a code cell. The code you create in Colab uses all the same features that you find in Notebook. However, off to the side of the cell, you see a menu of extras that you can use with Colab that aren’t present in Notebook, as shown in [Figure 6-14](#c06.xhtml#c06-fig-0014).

![FIGURE 6-14: Colab code cells contain a few extras not found in Notebook.](images/9781119724018-fg0614.png)

[FIGURE 6-14:](#c06.xhtml#rc06-fig-0014) Colab code cells contain a few extras not found in Notebook.

You use the icons shown in [Figure 6-14](#c06.xhtml#c06-fig-0014) to augment your Colab code experience. The following list provides a short description of these features (in order of appearance, left to right, in the figure):

*   **Move cell up:** Moves the cell up one position in the cell hierarchy.

*   **Move cell down:** Moves the cell down one position in the cell hierarchy.

*   **Link to cell:** Displays a dialog box containing a link you can use to access a specific cell within the notebook. You can embed this link anywhere on a web page or within a notebook to allow someone to access that specific cell. The person still sees the entire notebook but doesn’t have to search for the cell you want to discuss.

*   **Add a comment (assuming that you have the right to make a comment):** Creates a comment balloon to the right of the cell. This is not the same as a code comment, which exists in line with the code but affects the entire cell. You can edit, delete, or resolve comments. A resolved comment is one that receives attention and is no longer applicable.

*   **Open editor settings:** Opens the same dialog box shown in [Figure 6-2](#c06.xhtml#c06-fig-0002) and discussed in the “[Working with Google Colab features](#c06.xhtml#c06-sec-0007)” section, earlier in this chapter. You need to select some code before this option appears.

*   **Mirror cell in tab:** Mirrors the currently selected cell in a Cell pane that appears on the right side of the window, as shown in [Figure 6-15](#c06.xhtml#c06-fig-0015). You can scroll wherever you want within the code in the left pane and keep this code accessible. The right-pointing arrow lets you execute the cell at any time after making changes in left pane code. A pair of double-pointing arrows lets you move the focus back to the selected code in the left pane with a single click. You can also move the cell code to a scratch cell, where you can play with it without modifying your original code. It’s possible to have more than one Cell pane. You simply select the one you want and move between them as needed, which lets you move easily from place to place in your code. Close a Cell pane by clicking the X next to the word Cell. ![FIGURE 6-15: Use Cell panes to keep key cells easily available as needed.](images/9781119724018-fg0615.png)

    [FIGURE 6-15:](#c06.xhtml#rc06-fig-0015) Use Cell panes to keep key cells easily available as needed.

*   **Delete Cell:** Removes the cell from the notebook.

*   **Vertical ellipses:** Contains a number of additional features in a menu: 

    *   **Copy Cell:** Copies the content of the currently selected cell to the Clipboard.

    *   **Cut Cell:** Deletes the content of the currently selected cell and places it on the Clipboard.

    *   **Clear Output:** Removes the output from the cell. You must run the code again to regenerate the output.

    *   **View Output Fullscreen:** Displays the output (not the entire cell or any other part of the notebook) in full-screen mode on the host device. This option is useful when displaying a significant amount of content or when a detailed view of graphics helps explain a topic. Press Esc to exit full-screen mode.

    *   **Add a Form:** Inserts a form into the cell to the right of the code. You use forms to provide a graphical input for parameters. Forms don’t appear in Notebook, but because of how you create them, they won’t prevent you from running the code in Notebook. You can read more about forms at [`https://colab.research.google.com/notebooks/forms.ipynb`](https://colab.research.google.com/notebooks/forms.ipynb).
