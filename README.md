# fedora-desktop

Q: What is this for?
A: Basically my personal installation procedure documented somewhere so I don't have to remember it.

Step 1 - Host installation
--------------------------
Fedora with KDE desktop environment serving as the system running on the hardware and providing virtual desktop system(s) for the user.

Install from Fedora-KDE-Live-x86_64-35-1.2.iso with:

* Filesystem
  * add /VirtualMachines and /data

* root user
  * activate root user and allow SSH login

* add user with admin rights and specific uid and gid if required

After installation, login and connect to LAN or Wifi.
Start settings tool and set regional settings like language and timezone.

Open a terminal ("Konsole" under Favourites in the main menu) and enter
```
sudo dnf install -y ansible
wget https://github.com/joschro/fedora-desktop/raw/main/fedora-desktop-host.yml
```

Now run
```
ansible-playbook -K fedora-desktop-host.yml
```
providing your local user's password.

Step 2 - Desktop installation
-----------------------------
In the same terminal you used previously, run
```
wget https://github.com/joschro/fedora-desktop/raw/main/fedora-desktop.yml
ansible-playbook -K fedora-desktop.yml
```
to install desktop applications.

Create a virtual machine using virt-manager or the Cockpit web console and run the above commands within the virtual system as well.
