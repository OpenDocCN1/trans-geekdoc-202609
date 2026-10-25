![](bbox=[0.168, 0.101, 0.835, 0.305])

Figure 6.33: Steps for installing Microsoft Visual Studio (VS).

```
```bash
source ~/.bashrc
```
```

![](bbox=[0.168, 0.388, 0.831, 0.465])

Figure 6.34: Steps for initializing interactive shell session.

```
```bash
jupyter notebook --generate-config
cd ~/.jupyter/
vi jupyter_notebook_config.py
```
```

![](bbox=[0.168, 0.577, 0.834, 0.674])

Figure 6.35: Steps for configuring Jupyter Notebook in GCP.

This command will open the Jupyter Notebook configuration file for VM instance. Press “i” to edit this configuration file and add the lines shown in Fig. 6.36. The port number used in this example will be the one that you specified during Firewall settings (Fig. 6.27).

After editing the configuration file, press “Esc” and type “:wq” in your keyboard to save and exit (Fig. 6.37). If you are interested in setting up a password now, check the Jupyter Notebook configuration for public server [61]. You may close your session now.

Now you are ready to launch Jupyter Notebook and execute code in the server. Next, go to the SSH terminal and type terminal multiplexer command “tmux” (Fig. 6.38).