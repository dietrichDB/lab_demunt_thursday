Following guide describes what you should install on your VM Prior to deployment:


1. sudo apt-update and apt-upgrade

Upgrade your OS to latest patches before continuing.

2. Install Docker

https://docs.docker.com/engine/install/ubuntu/

3. Install Containerlab

https://containerlab.dev/quickstart/

4. Download and install the correct Arista cEOS image you want/need for your lab.

https://www.arista.com/en/support/software-download

In our example, we are using 4.34.2F but this can be anyone you like, as long as it's cEOS based!

You can upload your file using SCP of sFTP to your VM. I use the application CyberDuck, but this can also be Filezilla, WinSCP or whatever utility you prefer!

5. import the image in docker

In my example: sudo docker import cEOS-lab-4.34.2F.tar.xz ceos:4.34.2F







