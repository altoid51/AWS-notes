1. From your [AWS Console](https://console.aws.amazon.com/console/home), type `EC2` in the search bar. This will send you to the EC2 dashboard.

![](images/ec2-search-bar.png)

2. From the EC2 Dashboard, click "Launch Instance"

![](images/ec2-launch-instance-btn.png)

3. Choose the default image:

![](images/ec2-choose-image.png)

4. Choose instance size, and then click "Review and Launch":
**NOTE**: Be conservative, it's a huge pain to run out of memory.

![](images/ec2-instance-size.png)

5. Click "Launch"

![](images/ec2-launch.png)

6. After that a modal window will prompt you to either create or choose an
   existing `.pem` file. 
  - If you have one you'd like to use, choose that. 
  - If you
need a new one, do the following:
    1. Choose "Create a new key pair"
    2. Ideally give it a lower case name with no spaces.
    3. Click "Download key pair". AWS won't let you click "Launch Instances" until you download your key pair
    4. Using terminal, you'll need to `cd` to the directory that the .pem file is
      in and type the following: `chmod 400 YOUR-PEM-FILE.pem`

![](images/ec2-creating-key-pair.png)

7. Click the link similar to the one below to take you to your instance page:

![](images/ec2-launch-status.png)

8. Eventually you'll see a green dot next to your instance, letting you know
   it's ready. Take note of of the "Public DNS" line. You'll use that url to
[[SSH|SSH]] into your instance.

![](images/ec2-instance-page.png)
