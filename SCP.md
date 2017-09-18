### Intro

SCP is how files are transferred from your machine to your EC2 instance (and vice versa). It works the same way as the `cp` command. The only difference is you're transferring files from one machine to another, rather than one directory to another.

### Steps

Go to your [EC2 Dashboard](https://console.aws.amazon.com/ec2/v2/home).

Click on '# Running Instances' ([Screenshot](https://www.evernote.com/l/ACgQaxMlF_RJNoJJcCYBYYaWZuh0yuRZILY))
**NOTE**: If you need to create an instance, click [[here|Creating-an-EC2-Instance]]

Click the checkbox of the instance in question ([Screenshot](https://www.evernote.com/l/ACgSQqFPnupNq6e_J5w_DHeBTWXAdHyrYGs))

Copy the Public DNS to your clipboard ([Screenshot](https://www.evernote.com/l/ACgxKQ946cBJ4ZdOdCH2cAz9dIzHIFA1qtM))

### SCP from your computer to EC2

In your terminal, navigate to the directory your .pem file is in

```bash
cd THE-DIR-YOUR-PEM-FILE-IS-LOCATED/
scp -i YOUR-PEM-FILE.pem THE-FILE-YOU-WANT-TO-SCP.csv ec2-user@PASTE-YOUR-PUBLIC-DNS-HERE:~/
```

**NOTE**: The `:~/` at the end of the DNS specifies which directory on the EC2 instance you want to transfer to. In this case, you're wanting your file to live in the home directory (hence the tilde).

### SCP from EC2 to your computer

SCP from EC2 to your machine works the exact same way, only in reverse. In your terminal, navigate to the directory your .pem file is in

```bash
cd THE-DIR-YOUR-PEM-FILE-IS-LOCATED/
scp -i YOUR-PEM-FILE.pem ec2-user@PASTE-YOUR-PUBLIC-DNS-HERE:~/THE-FILE-YOU-WANT-TO-SCP.csv .
```

**NOTE**: The `.` at the end of the command specifies that you want to copy the file from EC2 to the current directory on your machine.