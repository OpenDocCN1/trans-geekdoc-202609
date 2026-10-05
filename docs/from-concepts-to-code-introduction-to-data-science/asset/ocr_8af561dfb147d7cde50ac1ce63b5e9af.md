She runs experiments and saves her finalized model (to S3) and her code to GitHub). When she's finished, Carla shuts down the SageMaker instance.

# 5.9 Chapter Summary

Hardware comprises the physical components of the computer, while software is the instructions to operate computers and execute tasks. The CPU is the brain of the computer that processes information and temporarily stores it in RAM. A GPU is a processor of specialized cores which are excellent at performing parallel computations. For machine learning, RAM, or memory, is much faster than hard disk drive storage, but it is more expensive. As a result, computers typically have much more HDD storage than RAM. Solid-state drives store data in integrated circuits, making them smaller and faster than HDD. The motherboard connects all of the principal components.

The most important software on the computer is the operating system. Operating systems organize files into a directory structure. This structure is different in Windows versus non-Windows operating systems, and perhaps looks slightly different.

The file format is the structure of a data file. Some common data formats are CSV, DOCX, and TXT. There are many specialized formats such as MP4, WAV, and PNG for media and Parquet for columnar data. Saving data in appropriate formats can speed up workloads significantly.

The shell supports interfacing with a computer. It is a computer program that takes commands, interprets them for the OS, and outputs the results. Users interact with the shell through a GUI or a command-line interface. Use of the CLI is general through terminal. Users enter commands at the prompt in the terminal.

Version control is essential for tracking file changes. The most widely used system for version control is Git. GitHub is a popular internet service for software development and version control, and it is based on Git. We reviewed details of how to set up Git and GitHub, and how to execute common tasks like forking and cloning a repo. A fork of a repo will make an independent copy in the user's account. A clone of a repo will create a linked copy which will continue to sync with the original repo.

We walked through installation, which provides a set of powerful, free tools for computing and data science. One of these tools is JupyterLab, which is a feature-rich notebook application and editing environment. This will be the primary method for interacting with files in this book. IDEs provide features for efficient code development, debugging, and testing. Spyder is the IDE that installs with Anaconda.