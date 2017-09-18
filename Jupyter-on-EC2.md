### Requirements
1. You must have an [[EC2 instance|Creating-an-EC2-Instance]] set up.
2. You need to [[SSH|SSH]] into your instance
3. Have [[Anaconda installed|Installing-Anaconda-on-EC2]]

### Important
Make sure you shut down all Jupyter notebooks on your laptop before proceeding!

### Setup
**NOTE:** If you've already set up and configured Jupyter, skip to **Running Jupyter**

Once you've [[SSH'ed|SSH]] into your instance, do the following:

1. Create an SSL certificate
```bash
cd
mkdir ssl
cd ssl
sudo openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout "cert.key" -out "cert.pem" -batch
```

2. Open the `iPython` terminal
```bash
ipython
```
3. At the iPython prompt, run the following:
```python
from IPython.lib import passwd 
passwd()
```

4. At which point you'll be prompted to enter a password. This will be your password when you visit Jupyter in the browser. **NOTE:** You won't see your password as you're typing it.
```
Enter password: 
Verify password: 
Out[2]: 'sha1:4011275e1d4a:3e9ca6580c1c29a3a05fa6e3ca0ee59d0e485136'
```

5. Copy the `sha:4011275e1d4a...` and visit [https://rldaggie.github.io/jupyter-config-app/](https://rldaggie.github.io/jupyter-config-app/). Paste the sha into the form. You'll use the code that shows up in step 11.

6. Type `exit` to leave iPython and return to the terminal

7. Create a Jupyter configuration file
```bash
jupyter notebook --generate-config
```

8. Open the Jupyter config file in `vim`:
```bash
vim ~/.jupyter/jupyter_notebook_config.py
```

9. Type `G` to go to the bottom of the page

10. Type `o` (lowercase) to add a line below in insert mode

11. Copy the code from Step 5 and paste it at the bottom of the file. It should look something like this...
```python
c = get_config()  # Get the config object.
c.NotebookApp.certfile = u'/home/ec2-user/ssl/cert.pem'
c.NotebookApp.keyfile = u'/home/ec2-user/ssl/cert.key'
c.IPKernelApp.pylab = 'inline'
c.NotebookApp.ip = '*'
c.NotebookApp.open_browser = False
c.NotebookApp.password = 'sha1:fc216:3a35a98ed980b9...'
```

12. Press `<esc>` to exit insert mode

13. Type `:` to enter into command mode

14. Type `wq` followed by `<enter>` to save and quit the file.
### Running Jupyter

15. `exit` from your SSH terminal back to your PC

16. `cd` to the directory your pem file is located

17. The following command will create a tunnel between your PC and your EC2 instance on port 8888:
```bash
ssh -i your-pem-file.pem -L 8888:127.0.0.1:8888 ec2-user@YOUR-EC2-DNS.com
```

18. Now that you're tunneled back into your EC2 instance, you can start up Jupyter:
```bash
jupyter notebook
```
19. Visit [https://localhost:8888](https://localhost:8888). You might see a warning from your browser. On Chrome, click "Advanced" and then "Proceed to localhost (unsafe)". [Screenshot](https://www.evernote.com/l/AChA3uTw05lB0qdJj-6WwJ73_cXN0bjsyWI) **NOTE**: You might want to use Chrome's incognito feature. I've run into issues with running Jupyter locally after trying to SSH.

20. At this point you'll be prompted by Jupyter to enter your password. This is the one you created in step 4.

After that, you're all set!