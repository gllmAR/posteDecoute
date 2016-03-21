https://www.raspberrypi.org/documentation/installation/installing-images/mac.md

telecharger raspbian frais chez raspberrypi.org


dans le terminal
```
diskutil list

diskutil unmountDisk /dev/disk2


sudo dd bs=1m if=/Users/gllm/Downloads/2016-03-18-raspbian-jessie-lite.img  of=/dev/rdisk2
```

ctrl+t pour voir le progrès
