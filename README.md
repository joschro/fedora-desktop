# fedora-desktop-host

Install from Fedora-KDE-Live-x86_64-35-1.2.iso with:

* Filesystem
  * add /VirtualMachines and /data

* root user
  * activate root user and allow SSH login

* add user with admin rights

After installation, login and connect to LAN or Wifi.
Start settings tool and set regional settings like language and timezone.

Enter
```
sudo dnf install -y ansible vim
wget https://github.com/joschro/fedora-desktop-host/raw/main/fedora-desktop-host.yml
```

Now run
```
ansible-playbook -K fedora-desktop-host.yml
```
providing your local user's password.
