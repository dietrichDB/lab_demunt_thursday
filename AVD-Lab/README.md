1. Install Ansible on your Virtual Server

https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html

2. Install the AVD Ansible Collection on your VM

https://avd.arista.com/5.7/docs/installation/collection-installation.html

3. Install dependencies (if needed)

   - pyavd: https://avd.arista.com/4.4/docs/pyavd.html
   - distlib: pip3 install distlib --break-system-packages
  
Possible for orbstack as Ubuntu forces apt for package management, you always need to specify the option "--break-system-packages" 

3. Check This Lab Excercise on your downloaded repository

https://avd.arista.com/5.7/ansible_collections/arista/avd/examples/single-dc-l3ls/index.html

