# poste D'écoute

Lecteur sonore sensible disséminé dans l'espace publique.
Spécilament conçu pour l'artiste Julie Faubert.  

Fonctionne avec les états suivants

##### ambiance.veille :
joue à volume bas,  en attente d'activation

##### ambiance.actif :
joue en boucle pour toujours

* lorsqu’écouteur inactif pour X temps,  réduction du volume de AMBIANCE
* lorsque CIRCONSTANCE est actif,  AMBIANCE est muet FADE OUT, OUI


##### circonstance.actif.new :
- joue un fichier aléatoire depuis le dossier circonstance lorsque ECOUTE  est activé pour la première fois après avoir attendu un  temps relativement aléatoire à la fin,  retour à ambiance

##### circonstance.actif.old :
- joue un fichier aléatoire depuis le dossier circonstance lorsque ECOUTE est activé suite à la première fois après avoir attendu un  temps relativement aléatoire, à la fin,  retour à ambiance


##### SYNCHRONE :
- joue un fichier pigé depuis le dossier Synchrome en addition avec AMBIANCE et CIRCONSTANCE lorsque 2 écouteurs sont actifs.
- Un délai aléatoire  entre les lectures de fichiers

##### DÉTECTE
- joue un fichier pigé depuis le dossier Détecte en addition avec AMBIANCE lorsqu'un senseur est déclenché.




### commande utiles

* pour déployer sur le raspberry-pi (installer depuis git)
```
cd ~/
git clone --recursive https://github.com/gllmAR/posteDecoute.git
```
* pour aller chercher la dernière version
```
cd ~/posteDecoute
git pull
```
* pour lancer la commande de senseur en local sur la broche 18 sans le mode de débug
```
python /home/pi/posteDecoute/rpi-gpioOsc/rpi-gpioOs.py -i 18 -o /ecoute.senseur.raw -d 127.0.0.1 -p 8000 -r 2 -D 0
```
* pour lancer pure data sans interface sur une carte audio externe avec une configuration de lieu
```
/home/pi/pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "3,1" -nogui -send "lieu.read /home/pi/situations/lieux/lieux_1.txt" /home/pi/posteDecoute/pd/_main.pd
```

### Service au boot

Pour automatiser le départ des application,  nous utilisons le principe de Services dans systemD

voir

https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs




### Dépendences :

pd-Vanilla 0.46.7
* disponible ici :  http://msp.ucsd.edu/software.html

* sur le pi
```
cd ~
wget http://msp.ucsd.edu/Software/pd-0.46-7.armv7.tar.gz
tar -zxvf pd-0.46-7.armv7.tar.gz
```


#### to do

##### prog Pd
* changer fadeout pour inactif
* changer cut pour muted


##### modifier readGpioOSC.py
* [X] implémenter le mode read (actif par default)
* [ ] implémenter un change.

##### Script d'initialisation

* trouver c'est quoi le plus logique avec systemD
	* https://blog.sleeplessbeastie.eu/2015/04/27/how-to-manage-system-services-on-debian-jessie/
* Documenter afin que ce soit simple pour un utilisateur à changer
* http://www.pihomeserver.fr/en/2013/05/27/raspberry-pi-home-server-lancer-un-programme-automatiquement-au-demarrage/
*

##### Connexion wireless on boot :

* [ ] hidden SSID
* [ ] Password sur le ssid
* investiguer et mieux documenter :

http://elinux.org/RPI-Wireless-Hotspot

http://www.novitiate.co.uk/?p=183

http://spin.atomicobject.com/2013/04/22/raspberry-pi-wireless-communication/

fonctionne,  mais n'as pas le bon dhcp serveur

http://www.ronnutter.com/raspberry-pi-installing-dhcp-server/

http://spin.atomicobject.com/2013/04/22/raspberry-pi-wireless-communication/

http://lcdev.dk/2012/11/18/raspberry-pi-tutorial-connect-to-wifi-or-create-an-encrypted-dhcp-enabled-ad-hoc-network-as-fallback/



#### notes supplémentaires

##### notes sur les cartes de sons
noter qu'il faut spécifiquement des carte n'ayant pas le même nom pour que PD soit capable de choisir la bonne carte au démarrage en command line.

Setup Fonctionnel de deux carte
```
aplay -l
```
card 0: ALSA [bcm2835 ALSA], device 1: bcm2835 ALSA [bcm2835 IEC958/HDMI] Subdevices: 1/1 Subdevice #0: subdevice #0
card 1: Set [C-Media USB Headphone Set], device 0: USB Audio [USB Audio] Subdevices: 1/1 Subdevice #0: subdevice #0
card 2: Device [USB Audio Device], device 0: USB Audio [USB Audio] Subdevices: 1/1 Subdevice #0: subdevice #0

Lancer deux instances de pd avec deux cartes audio différtentes
```
pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "3,1" ~/prog/test1.pd
pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "5,1" ~/prog/test2.pd
```

##### carte de son I2S
à investiguer
https://www.adafruit.com/products/3016


##### gestion des sous-modules

lire documentation utile ici :
https://chrisjean.com/git-submodules-adding-using-removing-and-updating/
