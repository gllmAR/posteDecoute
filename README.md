# poste D'écoute

utilise pd-Vanilla 0.46.7

télécharger ici :  http://msp.ucsd.edu/software.html


##### commande utiles

```
python rpi-gpioOs.py -i 18 -o /ecoute.senseur.raw -d 127.0.0.1 -p 8000 -r 2 -D 0
```

```
/home/pi/pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "3,1" -nogui -send "lieu.read /home/pi/posteDecoute/situations/situation_1/situation_1.txt" /home/pi/posteDecoute/pd/_main.pd
```





### to do

##### prog Pd
* changer fadeout pour inactif
* changer cut pour muted
*

##### Connexion wireless on boot :

* hidden SSID
* Password sur le ssid

##### Script d'initialisation

* trouver c'est quoi le plus logique avec systemD
* Documenter afin que ce soit simple pour un utilisateur à changer

##### Completer le script python GPIOread

Python script readGPIO
avec rate ou change

##### Brancher le GPIO



#####

gestion des sous-modules

https://chrisjean.com/git-submodules-adding-using-removing-and-updating/




hungryearth211

NETGEAR77
5GHz Wireless Network Name (SSID):	NETGEAR77-5G

note de projet



modifier readGPIO.py


http://www.novitiate.co.uk/?p=183


http://spin.atomicobject.com/2013/04/22/raspberry-pi-wireless-communication/


fonctionne,  mais n'as pas le bon dhcp serveur

http://www.ronnutter.com/raspberry-pi-installing-dhcp-server/



http://spin.atomicobject.com/2013/04/22/raspberry-pi-wireless-communication/



intéressant

http://lcdev.dk/2012/11/18/raspberry-pi-tutorial-connect-to-wifi-or-create-an-encrypted-dhcp-enabled-ad-hoc-network-as-fallback/





broacaster un SSID depuis le pi


wget http://msp.ucsd.edu/Software/pd-0.46-7.armv7.tar.gz



/home/pi/pd-0.46-7/bin./pd -nogui -alsa  -audioindev "1,1" -audiooutdev "1,1" /home/pi/prog/test1.pd &



pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "3,1" ~/prog/test1.pd

pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "5,1" ~/prog/test2.pd




card 0: ALSA [bcm2835 ALSA], device 1: bcm2835 ALSA [bcm2835 IEC958/HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Set [C-Media USB Headphone Set], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Device [USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



aplay -l


pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "3,1" ~/prog/test1.pd

pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "5,1" ~/prog/test2.pd

pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "3,1" ~/prog/playWav.pd


pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "5,1" ~/prog/playWav.pd




pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "3,1" ~/prog/test1.pd & pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "5,1" ~/prog/test2.pd




python interuptOsc.py -g 0 -i 18 -d 127.0.0.1 -p 8000 -r 1 -t 2 -D 1
