https://www.raspberrypi.org/documentation/installation/installing-images/mac.md

télécharger raspbian frais chez raspberrypi.org


dans le terminal
```
diskutil list

diskutil unmountDisk /dev/disk2


sudo dd bs=1m if=/Users/gllm/Downloads/2016-03-18-raspbian-jessie-lite.img  of=/dev/rdisk2

diskutil unmountDisk /dev/disk2
```

unmountDisk



ctrl+t pour voir le progrès


sudo apt-get update && sudo apt-get upgrade

sudo apt-get install git


* sur le pi
```
cd ~
wget http://msp.ucsd.edu/Software/pd-0.46-7.armv7.tar.gz
tar -zxvf pd-0.46-7.armv7.tar.gz
```
