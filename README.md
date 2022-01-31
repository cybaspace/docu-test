## Install and configure Photon OS on 1blu root server

Root servers of the german provider 1blu are a perfect match to run a docker host on it - they are cheap and has enough power.

If you follow the steps you have a running docker host afterwards:

1. Assume you have already a 1blu root server - smallest size can already be perfect for testing and developing.
2. Download the minimal ISO of actual version (at the moment it's 4.0 GA): https://github.com/vmware/photon/wiki/Downloading-Photon-OS
3. In 1blu customer self service (Kundenservicebereich) goto "Meine Produkte", select your root server and choose _Administration_
4. Under _ISO-Image_ you will find URL and credentials for FTP server
5. Upload Photon OS iso image to FTP server
6. Rename iso image to _boot.iso_
7. In 1blu customer self service under your root server switch to "Übersicht"
8. Under _Server_ click to _DVD_ for "Booten von:"
9. Press _Neustart_ under "Betriebssystem" - don't be irritated if their stands something like "Ubuntu" - this is the preinstalled OS on harddisk, but you changed to Virtual DVD

