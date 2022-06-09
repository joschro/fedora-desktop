# fedora-desktop

Q: What is this for?
A: Basically my personal installation procedure documented somewhere so I don't have to remember it.

Step 1 - Host installation
--------------------------
Fedora with KDE desktop environment serving as the system running on the hardware and providing virtual desktop system(s) for the user.

Write Fedora-KDE-Live-x86_64-[current_version].iso from https://spins.fedoraproject.org/kde/download/index.html to a USB stick and boot your system from it.
Then click on the "Install to Hard Drive" icon and modify the installation parameters to your needs, like:

* Installation target
  * add /data, /data/shared, /data/container and /data/virtualmachines
  * encrypt data

* root user
  * activate root user

* add user with admin rights and specific uid and gid if required

After installation, login and connect to LAN or Wifi.
Start settings tool and set regional settings like language and timezone.

Open a terminal ("Konsole" under Favourites in the main menu) and enter
```
sudo dnf install -y ansible
wget https://github.com/joschro/fedora-desktop/raw/main/fedora-desktop-host.yml
ssh-keygen
```
confirm all items with <enter>.
 
### If you perform the setup from a remote machine
In the open terminal, enter
```
sudo systemctl enable --now sshd
wget https://github.com/joschro/fedora-desktop/raw/main/hosts
ansible-playbook -i hosts -K fedora-desktop-host.yml
```
providing your local user's password.

### If you perform the setup from within the newly installed machine
In the open terminal, enter
```
wget https://github.com/joschro/fedora-desktop/raw/main/localhost
ssh-copy-id localhost
ansible-playbook -i localhost -K fedora-desktop-host.yml
```
providing your local user's password.

Step 2 - Desktop installation
-----------------------------
In the same terminal you used previously, run
```
wget https://github.com/joschro/fedora-desktop/raw/main/fedora-desktop.yml
ansible-playbook -i hosts -K fedora-desktop.yml
(or "ansible-playbook -i localhost -K fedora-desktop.yml" respectively)
```
to install desktop applications.

Create a virtual machine using virt-manager or the Cockpit web console and run the above commands within the virtual system as well.
