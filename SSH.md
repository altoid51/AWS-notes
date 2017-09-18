Go to your [EC2 Dashboard](https://console.aws.amazon.com/ec2/v2/home).

Click on '# Running Instances' ([Screenshot](https://www.evernote.com/l/ACgQaxMlF_RJNoJJcCYBYYaWZuh0yuRZILY))
**NOTE**: If you need to create an instance, click [[here|Creating-an-EC2-Instance]]

Click the checkbox of the instance you want to SSH in to ([Screenshot](https://www.evernote.com/l/ACgSQqFPnupNq6e_J5w_DHeBTWXAdHyrYGs))

Copy the Public DNS to your clipboard ([Screenshot](https://www.evernote.com/l/ACgxKQ946cBJ4ZdOdCH2cAz9dIzHIFA1qtM))

In terminal, navigate to the directory your .pem file is in

```bash
cd the-directory-your-pem-file-is-located/
ssh -i YOUR-PEM-FILE.pem ec2-user@PASTE-YOUR-PUBLIC-DNS-HERE
```

You've successfully SSH'ed if you see the following:

```

       __|  __|_  )
       _|  (     /   Amazon Linux AMI
      ___|\___|___|

https://aws.amazon.com/amazon-linux-ami/2017.03-release-notes/
1 package(s) needed for security, out of 1 available
Run "sudo yum update" to apply all updates.
[ec2-user@ip-172-31-12-226 ~]$ 
```

If you see `Run "sudo yum update" to apply all updates.` then run: 
```
sudo yum update
```

You're all set! If this is your first time to `ssh` into this instance, you'll
probably want to [[install Anaconda|Installing-Anaconda-on-EC2]]


### Unprotected key file

If you see the following warning when trying to SSH:
```bash
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for 'YOUR-PEM-FILE.pem' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "dsi.pem": bad permissions
Permission denied (publickey).
```

Type the following:
```bash
chmod 400 YOUR-PEM-FILE.pem
```

After that, try the `ssh` command again.

