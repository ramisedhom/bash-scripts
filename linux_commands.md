# Boot Repair
```bash
$ sudo add-apt-repository ppa:yannubuntu/boot-repair
$ sudo apt update
$ sudo apt install boot-repair
$ boot-repair
```
# Clean up boot partition
```bash
$ uname -r 
$ sudo dpkg --list 'linux-image*'|awk '{ if ($1=="ii") print $2}'|grep -v `uname -r`
```
You will get the list of images
Now its time to remove old kernel one by one as:
```bash
$ sudo apt-get purge linux-image-3.19.0-25-generic
$ sudo apt-get autoremove
$ sudo update-grub
```
# Disable X at boot time so that the system boots in text mode
```bash
$ sudo vi /etc/default/grub
```
Find this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Change it to:
```
# GRUB_CMDLINE_LINUX_DEFAULT="text"
```
Update GRUB:
```bash
$ sudo update-grub
```
To find out what is the current run-level name
```bash
$ systemctl get-default
```
To change it to "multi-user.target"
```bash
$ systemctl set-default multi-user.target
```
# Using add-apt-repository command
```bash
$ sudo add-apt-repository ppa:libreoffice/ppa
```
For other hosted repositories, can be also configured by providing its reference as below:
```bash
$ add-apt-repository 'deb http://archive.getdeb.net/ubuntu wily-getdeb games'
```
# Arabic in Linux Console
```bash
$ sudo dpkg-reconfigure console-setup
$ sudo apt-get install libfribidi0 libfribidi-dev
$ wget https://launchpad.net/~behnam/+archive/ubuntu/ppa/+files/bicon_0.2.0-1ubuntu0~ppa4_amd64.deb
$ sudo dpkg -i ./bicon_0.2.0-1ubuntu0~ppa4_amd64.deb
$ /usr/bin/bicon.bin
```
# Check the available session managers
```bash
$ update-alternatives --list x-session-manager
```
Get a more verbose description
```bash
$ update-alternatives --display x-session-manager
```
Use the following ~/.xsession file:
```bash
  #!/bin/sh
  exec startlxde
```
# Try out other environments as a one-off
```bash
$ startx /usr/bin/startkde
```
