How to install containerlab on:


- Windows with WSL ?

  https://containerlab.dev/windows/

- Linux ?

  https://containerlab.dev/quickstart/

- Mac OS X with Orbstack (ARM version of cEOS)

  https://containerlab.dev/macos/


  Direct guide for Orbstack install: https://arista.my.site.com/AristaCommunity/s/article/cEOS-lab-on-Orbstack
  
First download & Install ORbstack from their website: https://orbstack.dev/download
Once you have it installed, create a new "Virtual Machine", Ubuntu 25.04 (or as you prefer)

-> Don't go for Rosetta, but create an ARM virtual machine, they are quicker!

After that, install docker with:

https://docs.docker.com/engine/install/ubuntu/

Then install Containerlab with:

curl -sL https://containerlab.dev/setup | sudo -E bash -s "all"

After that you have to pull the repository again in a folder of your choice and you are ready to go!

