
(Ctrl+Shift+P) provides quick access to commands.

- **Simplify project management**: Store project-specific settings in .vscode/settings.json to keep your workspaces organized and consistent.

# Case study: How VS Code can revolutionize an AI team's workflow

Picture a team of data scientists eager to innovate but weighed down by repetitive coding, tricky debugging, and complex deployment processes for containerized AI models. These obstacles can stifle creativity and slow progress. However, what if there was a way to streamline their workflow and bring their ideas to life faster?

**Solution**: VS Code, a versatile, user-friendly platform, can transform the team's work. Here is how it makes a difference:

- **GitHub Copilot**: Takes over mundane and repetitive tasks, like crafting data preprocessing scripts, freeing the team to focus on solving more significant problems.

- **Python extension**: Simplifies debugging by consolidating everything into one intuitive interface, saving time and reducing frustration.

- **Docker extension**: Makes managing containers for AI model deployment seamless and efficient, cutting down on errors and delays.

**The results**: The results show how adopting VS Code significantly improved the development workflow.

Table 2.1 illustrates how the development workflow has improved before and after adopting VS Code:

| Aspect | Before VS Code | After VS Code |
|---|---|---|
| Code writing | Manual, time-consuming | Streamlined with Copilot |
| Debugging | Multiple tools required | Unified within VS Code |
| Deployment | Manual, error-prone | Simplified with Docker |

**Table 2.1:** How the development workflow improves before and after adopting VS Code

The impact was undeniable:

- Boilerplate coding can be reduced by 40%.
- Debugging time will likely decrease by 25%.
- Deployment time can drop by 30%.

By setting up and personalizing VS Code, any AI team will be equipped to tackle challenges easily. This tool can empower teams to explore new possibilities, innovate faster, and excel in their coding journey.

# Emerging AI tools for developers

While tools like GitHub Copilot and ChatGPT dominate mainstream AI-assisted programming, newer tools, such as Cursor and Windsurf, are rapidly gaining popularity in the developer community for their unique focus on enhancing the productivity and providing context-aware assistance.

The following tools highlight how AI is evolving to support developers with more intelligent, workflow-aware assistance:

- **Cursor:** A modern code editor built on top of VS Code, Cursor integrates seamlessly with large language models to provide AI-powered, inline code editing, documentation lookup, and contextual suggestions. Unlike Copilot, Cursor emphasizes a conversational UI that allows developers to chat with the model about the codebase directly in the IDE. It supports natural-language-based refactoring, bug fixes, and query answering across your entire project.
- **Windsurf:** Windsurf is an AI-native IDE designed for data scientists and ML engineers. It combines code suggestions with intelligent environment management, dataset exploration, and notebook-style interactivity. Its tight integration with cloud services and support for real-time collaboration make it ideal for AI/ML workflows.

These tools reflect a growing shift toward AI-native development environments that go beyond autocomplete, offering contextual understanding, workflow-specific automation, and intelligent reasoning across projects.

# Using Jupyter Notebook for data-driven projects

Imagine analyzing millions of customer reviews, forecasting energy consumption trends, or building advanced AI models within a single, interactive platform. Jupyter Notebook makes this possible with ease and efficiency. By combining code execution, visualization, and documentation in one place, it has become an essential tool for modern data science and AI workflows.

# Setting up Jupyter Notebook

Jupyter Notebook is more than just a development environment; it is a powerful tool that integrates coding, output, and explanations into a seamless interface. Here is the complete guide to installing the Jupyter Notebook:

1. **Using pip (simple and quick):** The pip method is suitable if Python is installed on your system. The steps are as follows:
- Open your terminal (Command Prompt, PowerShell, or your OS equivalent).
- Run the following command: `pip install notebook`

2. **Using Anaconda (ideal for data scientists):** Anaconda is a powerful distribution that includes Python and many popular data science and ML libraries, such as NumPy, Pandas, and Matplotlib. It also comes with Jupyter Notebook pre-installed. The steps are as follows:

```bash
pip install notebook
jupyter notebook
```

a. Download and install the Anaconda distribution from https://www.anaconda.com/.
b. During installation, check the option to add Anaconda to your system' PATH variable (recommended).
c. Once installed, you can launch Jupyter Notebook in two ways:
  i. **Using Anaconda Navigator**: Open the Anaconda Navigator application and click on Jupyter Notebook.
  ii. **Using command line**: Open your terminal (Mac/Linux) or Command Prompt (Windows) and type: `Jupyter notebook`
d. Jupyter Notebook will launch in your default web browser.

# Key points

The key points for setting up the Jupyter Notebook are as follows:

- Use **pip** or **conda** to add libraries and create virtual environments to organize your Python projects.
- If you want additional libraries, you can install them via **pip** or Anaconda's package manager (**conda**).
- Consider creating a virtual environment to isolate dependencies for better organization.

# Launching Jupyter Notebook

Launching Jupyter Notebook is simple and lets you work on interactive notebooks in your web browser, making it easy to code, analyze data, and collaborate. Let us look at the steps as follows:

1. **Open your terminal or Command Prompt:**
  a. **Windows**: Open Command Prompt or PowerShell.
  b. **macOS/Linux**: Open terminal.

2. **Navigate to the folder where your files are stored:**
  a. **Windows**: Right-click on the folder and Copy as Path.
  b. **macOS/Linux**: Drag the folder into your terminal after typing `cd`.

3. **Start the notebook server:** Once you are in the correct folder, type the following command to launch Jupyter Notebook: `jupyter notebook`

4. **Access Jupyter Notebook:** After running the preceding command, your default web browser will automatically open the interface. If it does not, you will see a link in the terminal that looks like this:

```
http://localhost:8888/?token=abcd1234
```
Copy and paste this URL into your browser.

# Common tips

Are you having trouble with Jupyter Notebook? Do not worry, here are some simple tips to fix common issues so you can return to work:

- Issue: jupyter: command not found
  Solution: Ensure Python or Anaconda is installed and added to your system’s PATH. Reinstall Jupyter Notebook if needed.
- Issue: "Kernel not connecting"
  Solution: Check your Python environment and ensure all dependencies are installed. Use `pip install ipykernel` if required.

# Advanced setups

Want to take your Jupyter Notebook experience to the next level? Here are some advanced options you can try out (optional):

- **Run Jupyter on a remote server:** This setup is ideal for high-performance computing environments:
```bash
jupyter notebook --no-browser --port=8888
ssh -N -f L:8888:localhost:8888 user@remote_server
```
- **Lab advanced projects:** JupyterLab provides a more flexible, tab-based interface:
```bash
pip install jupyterlab
jupyter lab
```

# Customization options

Personalize your Jupyter Notebook experience with these easy customization options:

- **Add extensions for productivity:** Extend Jupyter’s functionality with features like collapsible cells or a table of contents:
```bash
pip install jupyter_contrib_nbextensions
jupyter contrib nbextension install
```
- **Change themes for a personal touch:** Customize your interface to suit your style:
```bash
pip install jupyerthemes
j -t monotai
```

**Your first Notebook example:** Here is a simple "Hello World!" example to get started:
