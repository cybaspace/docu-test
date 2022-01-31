## Install and configure Photon OS on 1blu root server

Root servers of the german provider 1blu are a perfect match to run a docker host on it - they are cheap and has enough power.

If you follow the steps you have a running docker host afterwards:

1. Assume you have already a 1blu root server - smallest size can already be perfect for testing and developing.
2. Download the minimal ISO of actual version (at the moment it's 4.0 GA): https://github.com/vmware/photon/wiki/Downloading-Photon-OS
3. In 1blu customer self service (Kundenservicebereich - further ksb) goto "Meine Produkte", select your root server and choose _Administration_
4. Under _ISO-Image_ you will find URL and credentials for FTP server
5. Upload Photon OS iso image to FTP server
6. Rename iso image to _boot.iso_
7. In 1blu customer self service under your root server switch to "Übersicht"
8. Under _Server_ click to _DVD_ for "Booten von:"
9. Press _Neustart_ under "Betriebssystem" - don't be irritated if their stands something like "Ubuntu" - this is the preinstalled OS on harddisk, but you changed to Virtual DVD
10. In _ksb Administration_ activate "VNC-Fernsteuerung"
11. Start VNC and login to mentioned VNC Server with your username and your root password
12. Be aware that *VNC connection is not encrypted* - do the next steps at once
13. In VNC screen you will see startup screen of Photon OS - choose _install_
14. Answer most questions with default setting - but choose "Network manually"
15. You will find network configuration in _ksb Übersicht -> Netzwerkeinstellungen_
16. If installation is completed go to _ksb Übersicht_ for "Booten von:" choose _HDD_ and then click _Neustart_ under "Betriebssystem"
17. Photon OS will start from Harddisk - continue in VNC on photon terminal
18. create a new user
  ```
  useradd -a -G docker <username>
  ```
19. add your *public* key to the user
  ```
  mkdir /home/<username>/.ssh
  vim /home/<username>/.ssh/authorized_keys
  chown -R <username>:users /home/<username>/.ssh
  chmod 750 /home/<username>/.ssh
  chmod 640 /home/<username>/.ssh/authorized_keys
  ```
20. change or verify following settings in `/etc/ssh/sshd_config`
  ```
  PermitRootLogin no
  UsePAM no
  PasswordAuthentication no
  ```
