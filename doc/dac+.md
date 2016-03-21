Update Raspbian on the SD card to be the latest available.



To ensure that the IQAUDIO Device drivers are loaded make sure 

: Ajouter le load de 
/boot/config.txt file has the entry below ... 



```
sudo nano /boot/config.txt
```

Inserer la ligne suivante

```
dtoverlay=iqaudio-dacplus

```

Disable native audio

cd /etc/modprobe.d

sudo nano alsa-blacklist.conf
