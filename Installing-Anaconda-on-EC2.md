### Downloading the bash file

Go to the [Anaconda downloads page](https://www.continuum.io/downloads)

Scroll down a bit and click on the Linux tab. [Screenshot](https://www.evernote.com/l/ACiIm3yPQ-1Dba-daaGyGMsOVGzEmSI9vDg)

Right-click the green button under Python 3.x and copy the link address. [Screenshot](https://www.evernote.com/l/ACg18al-QBJAgZXESh7UgYbHF5ibFhKVqY0).

[[SSH|SSH]] into your EC2 instance and type the following:
```bash
wget PASTE-YOUR-ANACONDA-URL.sh
```

You should see a loading bar similar to the following [screenshot](https://www.evernote.com/l/ACggCQF7bB1GPZePBHY47znZfCr36h_BQis). 


### Installation

Once the file is downloaded, type the following:

```bash
bash Ana<tab>
```
`<tab>` will autocomplete with the full name of the Anaconda file you downloaded.

When you see the following, press enter:
```bash
In order to continue the installation process, please review the license
agreement.
Please, press ENTER to continue
>>> 
```

If you see `--More--` keep pressing `space` until you see the following:
```bash
Do you approve the license terms? [yes|no]
>>> 
```

Type `yes`.

When you see the following:
```bash
Anaconda3 will now be installed into this location:
/home/ec2-user/anaconda3

  - Press ENTER to confirm the location
  - Press CTRL-C to abort the installation
  - Or specify a different location below

[/home/ec2-user/anaconda3] >>> 
```
Hit `<enter>` to select the default location

At this point the script will start to download all the necessary packages. Once it's done, you'll see the following:
```bash
Do you wish the installer to prepend the Anaconda3 install location
to PATH in your /home/ec2-user/.bashrc ? [yes|no]
[no] >>> 
```

Type `yes` and hit `<enter>`. 

Finally, type `source ~/.bash_profile` to reload your terminal.

You're all set!